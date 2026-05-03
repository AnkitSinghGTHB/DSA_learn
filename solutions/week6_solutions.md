# Week 6 Solutions: Graphs

Here are the Java solutions for the Week 6 practice problems.

### 1. Flood Fill
**Concept:** DFS starting from the clicked pixel, filling identical colored neighbors. Time: O(N), Space: O(N) for recursion stack.
```java
class Solution {
    public int[][] floodFill(int[][] image, int sr, int sc, int color) {
        int originalColor = image[sr][sc];
        if (originalColor != color) {
            dfs(image, sr, sc, originalColor, color);
        }
        return image;
    }
    
    private void dfs(int[][] image, int r, int c, int oldColor, int newColor) {
        // Base case: out of bounds or not the original color
        if (r < 0 || r >= image.length || c < 0 || c >= image[0].length || image[r][c] != oldColor) {
            return;
        }
        
        image[r][c] = newColor; // Paint!
        
        // Go 4-directional
        dfs(image, r - 1, c, oldColor, newColor); // Up
        dfs(image, r + 1, c, oldColor, newColor); // Down
        dfs(image, r, c - 1, oldColor, newColor); // Left
        dfs(image, r, c + 1, oldColor, newColor); // Right
    }
}
```

### 2. Find if Path Exists in Graph
**Concept:** Build an Adjacency List, then use BFS/DFS to find the destination. Time: O(V + E), Space: O(V + E).
```java
import java.util.*;

class Solution {
    public boolean validPath(int n, int[][] edges, int source, int destination) {
        // 1. Build Adjacency List
        List<List<Integer>> graph = new ArrayList<>();
        for (int i = 0; i < n; i++) graph.add(new ArrayList<>());
        for (int[] edge : edges) {
            graph.get(edge[0]).add(edge[1]);
            graph.get(edge[1]).add(edge[0]);
        }
        
        // 2. BFS
        Queue<Integer> q = new LinkedList<>();
        boolean[] visited = new boolean[n];
        
        q.offer(source);
        visited[source] = true;
        
        while (!q.isEmpty()) {
            int current = q.poll();
            if (current == destination) return true;
            
            for (int neighbor : graph.get(current)) {
                if (!visited[neighbor]) {
                    visited[neighbor] = true;
                    q.offer(neighbor);
                }
            }
        }
        return false;
    }
}
```

### 3. Number of Islands
**Concept:** Loop through the grid. When you find a '1', increment island count and use DFS to sink the entire island so you don't count it twice. Time: O(M * N), Space: O(M * N).
```java
class Solution {
    public int numIslands(char[][] grid) {
        int count = 0;
        
        for (int r = 0; r < grid.length; r++) {
            for (int c = 0; c < grid[0].length; c++) {
                if (grid[r][c] == '1') {
                    count++;
                    sinkIsland(grid, r, c); // Sink it!
                }
            }
        }
        return count;
    }
    
    private void sinkIsland(char[][] grid, int r, int c) {
        if (r < 0 || r >= grid.length || c < 0 || c >= grid[0].length || grid[r][c] == '0') {
            return;
        }
        grid[r][c] = '0'; // Turn land into water
        
        sinkIsland(grid, r + 1, c);
        sinkIsland(grid, r - 1, c);
        sinkIsland(grid, r, c + 1);
        sinkIsland(grid, r, c - 1);
    }
}
```

### 4. Max Area of Island
**Concept:** Same as Number of Islands, but DFS returns the size of the island. Time: O(M * N), Space: O(M * N).
```java
class Solution {
    public int maxAreaOfIsland(int[][] grid) {
        int maxArea = 0;
        
        for (int r = 0; r < grid.length; r++) {
            for (int c = 0; c < grid[0].length; c++) {
                if (grid[r][c] == 1) {
                    maxArea = Math.max(maxArea, getArea(grid, r, c));
                }
            }
        }
        return maxArea;
    }
    
    private int getArea(int[][] grid, int r, int c) {
        if (r < 0 || r >= grid.length || c < 0 || c >= grid[0].length || grid[r][c] == 0) {
            return 0;
        }
        grid[r][c] = 0; // Sink it
        
        return 1 + getArea(grid, r+1, c) + getArea(grid, r-1, c) 
                 + getArea(grid, r, c+1) + getArea(grid, r, c-1);
    }
}
```

### 5. Rotting Oranges
**Concept:** Multi-source BFS. Put all rotten oranges in a queue, then rot their neighbors layer by layer (minute by minute). Time: O(M * N), Space: O(M * N).
```java
import java.util.Queue;
import java.util.LinkedList;

class Solution {
    public int orangesRotting(int[][] grid) {
        Queue<int[]> q = new LinkedList<>();
        int freshCount = 0;
        
        for (int r = 0; r < grid.length; r++) {
            for (int c = 0; c < grid[0].length; c++) {
                if (grid[r][c] == 2) q.offer(new int[]{r, c});
                else if (grid[r][c] == 1) freshCount++;
            }
        }
        
        if (freshCount == 0) return 0;
        
        int minutes = 0;
        int[][] dirs = {{1,0}, {-1,0}, {0,1}, {0,-1}};
        
        while (!q.isEmpty() && freshCount > 0) {
            int size = q.size();
            for (int i = 0; i < size; i++) {
                int[] curr = q.poll();
                for (int[] dir : dirs) {
                    int nr = curr[0] + dir[0];
                    int nc = curr[1] + dir[1];
                    
                    if (nr >= 0 && nr < grid.length && nc >= 0 && nc < grid[0].length && grid[nr][nc] == 1) {
                        grid[nr][nc] = 2; // Rot the fresh orange
                        freshCount--;
                        q.offer(new int[]{nr, nc});
                    }
                }
            }
            minutes++;
        }
        return freshCount == 0 ? minutes : -1;
    }
}
```

### 6. Clone Graph
**Concept:** DFS using a HashMap to keep track of cloned nodes. Time: O(V + E), Space: O(V).
```java
import java.util.*;

class Solution {
    public Node cloneGraph(Node node) {
        if (node == null) return null;
        HashMap<Node, Node> map = new HashMap<>(); // Original Node -> Cloned Node
        return dfs(node, map);
    }
    
    private Node dfs(Node node, HashMap<Node, Node> map) {
        if (map.containsKey(node)) {
            return map.get(node); // Return already cloned node
        }
        
        Node clone = new Node(node.val);
        map.put(node, clone);
        
        for (Node neighbor : node.neighbors) {
            clone.neighbors.add(dfs(neighbor, map));
        }
        
        return clone;
    }
}
```
