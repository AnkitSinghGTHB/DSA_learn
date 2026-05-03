# Week 6: The Social Network (Graphs)

Graphs are just an evolution of Trees. While Trees flow strictly downwards from a root, Graphs are a wild web of connections, where anyone can be connected to anyone.

## 🕸️ Graphs
Think of a Graph like a map of cities. The cities are **Nodes** (or Vertices), and the highways connecting them are **Edges**. Or, think of Facebook: you are a node, your friends are nodes, and the friendship between you is an edge.

### How do we store a Graph in code?
We usually use an **Adjacency List**. It's just a HashMap where the Key is a Node, and the Value is a List of all the Nodes it connects to.

```java
import java.util.*;

// Creating a Social Network Graph
HashMap<String, List<String>> graph = new HashMap<>();

// Initializing the people
graph.put("Alice", new ArrayList<>());
graph.put("Bob", new ArrayList<>());
graph.put("Charlie", new ArrayList<>());

// Adding Friendships (Edges)
graph.get("Alice").add("Bob"); // Alice is friends with Bob
graph.get("Alice").add("Charlie"); // Alice is friends with Charlie
```

---

## 🧠 Core Patterns: BFS and DFS
To explore a graph, we need to make sure we don't walk in circles! We must keep track of where we've been using a `HashSet` (the VIP list of places we've visited).

### 1. Breadth-First Search (BFS) - The Water Ripple
BFS explores the graph layer by layer, exactly like dropping a stone in a pond and watching the ripples expand. It explores all direct neighbors first, then neighbors of neighbors. **We use a Queue for BFS.**

```java
public void bfs(String startNode, HashMap<String, List<String>> graph) {
    Queue<String> queue = new LinkedList<>();
    HashSet<String> visited = new HashSet<>();
    
    queue.offer(startNode);
    visited.add(startNode);
    
    while (!queue.isEmpty()) {
        String current = queue.poll();
        System.out.println("Visiting: " + current);
        
        // Add all unvisited neighbors to the back of the queue
        for (String neighbor : graph.get(current)) {
            if (!visited.contains(neighbor)) {
                queue.offer(neighbor);
                visited.add(neighbor); // Mark as visited immediately!
            }
        }
    }
}
```

### 2. Depth-First Search (DFS) - The Maze Runner
DFS picks a path and runs down it as far as possible until it hits a dead end, then it backs up and tries another path. **We use Recursion (or a Stack) for DFS.**

### 🎯 Your Practice Checklist (LeetCode)
1. `Flood Fill`
2. `Find if Path Exists in Graph`
3. `Number of Islands` (Medium - A classic!)
4. `Max Area of Island` (Medium)
5. `Rotting Oranges` (Medium - Perfect use case for BFS)
6. `Clone Graph` (Medium)
