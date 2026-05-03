# 🕸️ Week 6: The Social Network (Graphs)

Welcome to Week 6! 🎉

Graphs are basically Trees that have gone completely wild. 
While a Tree flows neatly downwards from a single root, a **Graph** is a messy web where absolutely anyone can be connected to anyone.

Let's untangle it. 👇

---

## 🕸️ What exactly is a Graph?

Think of Facebook. You are a **Node**. Your friends are also **Nodes**. The friendship between you is the **Edge** connecting you.

Google Maps is a Graph too! The cities are Nodes, and the highways connecting them are Edges.

### 💻 Storing a Graph in Java (Adjacency List)
We can't just use a simple `left` and `right` pointer anymore because you might have 500 friends.
Instead, we use a `HashMap` where the Key is You, and the Value is a List of all your friends!

```java
import java.util.*;

// Creating our Social Network
HashMap<String, List<String>> graph = new HashMap<>();

// Adding people to the network
graph.put("Alice", new ArrayList<>());
graph.put("Bob", new ArrayList<>());

// Connecting them (Drawing the Edges)
graph.get("Alice").add("Bob"); // Alice added Bob!
```

---

## 🧠 Core Patterns: How to explore the Web

If you wander around a Graph randomly, you will walk in circles forever. We MUST use a `HashSet` (a VIP visited list) to keep track of where we've already been.

There are two ways to explore:

### 1. The Water Ripple (Breadth-First Search / BFS) 💧
Imagine dropping a stone in a pond. The ripples expand outward layer by layer. 
BFS explores all of your direct friends first. Then it explores your friends-of-friends. 
**Cheat Code:** BFS always uses a **Queue**.

```java
public void bfs(String startNode, HashMap<String, List<String>> graph) {
    Queue<String> queue = new LinkedList<>();
    HashSet<String> visited = new HashSet<>(); // Keep track!
    
    queue.offer(startNode);
    visited.add(startNode);
    
    while (!queue.isEmpty()) {
        String current = queue.poll();
        System.out.println("Visiting: " + current);
        
        // Add all unvisited neighbors to the line
        for (String neighbor : graph.get(current)) {
            if (!visited.contains(neighbor)) {
                queue.offer(neighbor);
                visited.add(neighbor); // Mark visited BEFORE they even process!
            }
        }
    }
}
```

### 2. The Maze Runner (Depth-First Search / DFS) 🏃‍♂️
DFS picks one path and sprints down it as fast and far as possible until it hits a dead end. Then it backs up and tries another path. 
**Cheat Code:** DFS uses **Recursion** (or a Stack).

> [!WARNING]
> If a problem asks for the **"Shortest Path"**, you MUST use **BFS**. 
> If a problem asks you to find a generic path or fill an area, **DFS** is usually easier to code.

---

## 🎯 Your Mission (LeetCode Checklist)

1. `Flood Fill` *(Literally the MS Paint bucket tool)*
2. `Find if Path Exists in Graph`
3. `Number of Islands` *(Medium - A legendary interview question)*
4. `Max Area of Island` *(Medium)*
5. `Rotting Oranges` *(Medium - Perfect BFS simulation!)*
6. `Clone Graph` *(Medium)*
