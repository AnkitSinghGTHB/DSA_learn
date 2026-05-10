# 🌳 Week 5: Family Trees & Inception

Welcome to Month 2! 🎉

We are officially leaving the land of flat data. No more straight lines. 
We are now entering the 2D world where data branches out in multiple directions.

But before we climb trees, we have to talk about the concept that scares everyone (but really shouldn't): **Recursion**. 👇

---

## 🪞 Recursion (The Mirror inside the Mirror)

Recursion is simply a function that calls *itself*. 
It sounds like a terrible idea that would loop forever, but it relies on one strict rule to stop: **The Base Case**.

**Imagine this:** You are in a long line, blindfolded. You want to know what position you are in. 
1. You tap the person in front of you: *"Hey, what position are you?"*
2. They don't know either! So they tap the person in front of them. 
3. This repeats (Recursion!) until someone taps the very first person in line.
4. **The Base Case:** The first person says *"I am number 1!"* 
5. The 2nd person adds 1 and says *"I am number 2!"* ... all the way back down the line to you.

### 💻 Recursion in Java

```java
public int countDown(int n) {
    // 1. The Base Case (The emergency brake 🛑)
    if (n == 0) {
        System.out.println("Liftoff! 🚀");
        return 0;
    }
    
    // 2. The Recursive Step (Doing work, then calling ourselves again)
    System.out.println(n + "...");
    return countDown(n - 1); // Calling the mirror!
}
```

---

## 🌳 Binary Trees 

A Tree is just like a family tree. It starts at a single `Root` ancestor at the top. 
That root can have children (branches). Those children can have children, all the way down to the `Leaves` (nodes with no children at the bottom).

In a **Binary Tree**, each node can have a maximum of **two** children: a left child, and a right child.

### 💻 Trees in Java

Just like Linked Lists, we have to build the tree branches ourselves.

```java
// The Blueprint for a Tree Branch
class TreeNode {
    int val;           // The data
    TreeNode left;     // Pointer to the left child
    TreeNode right;    // Pointer to the right child
    
    // Planting the seed
    TreeNode(int val) {
        this.val = val;
        this.left = null;
        this.right = null;
    }
}
```

---

## 🧠 Core Pattern: Depth-First Search (DFS)

How do you explore a tree? You use Recursion! 
We use a technique called **DFS** (Depth-First Search). We plunge as deep as we possibly can down the left side of the tree, hit the bottom, and then backtrack to explore the right side. 

```java
public void exploreTree(TreeNode root) {
    // BASE CASE: We fell off the tree! (Hit an empty leaf)
    if (root == null) {
        return; 
    }
    
    System.out.println("Currently visiting: " + root.val);
    
    // Go as deep as possible to the left...
    exploreTree(root.left);
    
    // ...then go as deep as possible to the right!
    exploreTree(root.right);
}
```

> [!TIP]
> **Tree problems are almost always just 4 lines of code.** 
> You write the Base Case (if root == null), you do something to the left child, you do something to the right child, and you're done!

---

## ↩️ Backtracking (The "Oops, Wrong Way" Bridge)

Before we finish, there's a special way to use Recursion called **Backtracking**. 

Think of it like exploring a tree, but you are carrying a backpack. As you go down a branch, you put something in your backpack. When you hit a dead end, you **take that item back out** of your backpack before you climb back up. This leaves you ready to explore the next branch!

*We will dive deep into this in **Week 11**, but for now, just know that Recursion is the engine that powers these "Choose Your Own Adventure" algorithms.*

---

## 🎯 Your Mission (LeetCode Checklist)

1. [`Maximum Depth of Binary Tree`](https://leetcode.com/problems/maximum-depth-of-binary-tree/)
2. [`Invert Binary Tree`](https://leetcode.com/problems/invert-binary-tree/) *(Google famously asked this!)*
3. [`Same Tree`](https://leetcode.com/problems/same-tree/)
4. [`Symmetric Tree`](https://leetcode.com/problems/symmetric-tree/)
5. [`Diameter of Binary Tree`](https://leetcode.com/problems/diameter-of-binary-tree/)
6. [`Subtree of Another Tree`](https://leetcode.com/problems/subtree-of-another-tree/)
7. [`Lowest Common Ancestor of a Binary Search Tree`](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/) *(Medium)*
