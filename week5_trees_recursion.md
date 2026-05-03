# Week 5: The Family Tree (Trees & Recursion)

Welcome to Month 2! It's time to deal with data that branches out.

## 🪞 Recursion (The Mirror inside a Mirror)
Recursion is when a function calls itself. It sounds like an endless loop, but it has a strict rule to stop it: the **Base Case**.

**Analogy:** You are standing in a long line and want to know what position you are in. You don't want to leave your spot, so you tap the person in front of you and ask "What position are you?". They don't know, so they tap the person in front of them. This repeats (recursion) until it reaches the person at the very front of the line (the base case!). They say "I am number 1!". The 2nd person adds 1 to that and tells the 3rd person "I am 2", all the way back to you.

### Recursion in Java
```java
public int countDown(int n) {
    // 1. The Base Case (When do we stop?)
    if (n == 0) {
        System.out.println("Liftoff!");
        return 0;
    }
    
    // 2. The Recursive Step (Doing a little work, and calling the function again)
    System.out.println(n + "...");
    return countDown(n - 1);
}
```

---

## 🌳 Binary Trees
A Tree is just like a family tree. It starts at a single `Root` ancestor. That root can have children (branches). Those children can have children, all the way down to the `Leaves` (nodes with no children).
In a **Binary Tree**, each node can have at most **two** children (a left child and a right child).

### Trees in Java
Just like Linked Lists, we have to build the Nodes ourselves.

```java
class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;
    
    TreeNode(int val) {
        this.val = val;
        this.left = null;
        this.right = null;
    }
}
```

## 🧠 Core Pattern: Depth-First Search (DFS)
To explore a tree, we almost always use Recursion. We go as deep as we possibly can down the left side, then we backtrack and go down the right side. This is called DFS.

```java
public void exploreTree(TreeNode root) {
    // Base Case: We hit an empty space (a leaf's imaginary child)
    if (root == null) {
        return;
    }
    
    // Process the current node
    System.out.println("Visiting node: " + root.val);
    
    // Recursively explore the left branch
    exploreTree(root.left);
    
    // Recursively explore the right branch
    exploreTree(root.right);
}
```

### 🎯 Your Practice Checklist (LeetCode)
1. `Maximum Depth of Binary Tree`
2. `Invert Binary Tree`
3. `Same Tree`
4. `Symmetric Tree`
5. `Diameter of Binary Tree`
6. `Subtree of Another Tree`
7. `Lowest Common Ancestor of a Binary Search Tree` (Medium)
