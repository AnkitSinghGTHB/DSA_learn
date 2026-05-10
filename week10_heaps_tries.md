# 🏗️ Week 10: The VIP Queue (Heaps & Tries)

Welcome to Week 10! 🎉

Today we learn about two specialized structures that make complex tasks feel easy: Heaps (for priorities) and Tries (for words).

---

## 👑 The Heap (The VIP Hospital Queue)

Imagine a hospital waiting room. Usually, it's "First Come, First Served" (a Queue). 
But if a celebrity or someone with a broken leg walks in, they jump to the front. This is a **Priority Queue** (implemented using a **Heap**).

**The Magic:** 
A Heap always keeps the "most important" item (the largest or smallest) at the very top. Even if you add 1,000 items, it can give you the #1 item in **O(1)** time and reorganize itself in **O(log N)**.

**When to use it:** 
When the interviewer says *"Find the Top K items"* or *"Find the Kth largest/smallest"*.

### 💻 Java Template
```java
import java.util.PriorityQueue;

// A "Min-Heap" (Smallest numbers first)
PriorityQueue<Integer> hospitalQueue = new PriorityQueue<>();

hospitalQueue.add(10);
hospitalQueue.add(5);
hospitalQueue.add(100);

// Even though 10 was first, 5 is the "Priority" (smallest)
System.out.println(hospitalQueue.peek()); // Prints 5!
```

---

## ⌨️ The Trie (Google Auto-complete)

How does Google know you're typing "Banana" after you just type "Ban"? It uses a **Trie** (pronounced "try").

Instead of storing whole words, a Trie stores letters in a tree. 
`B` -> `a` -> `n` -> `a` -> `n` -> `a`

**The Magic:** 
You can check if a word exists in **O(WordLength)** time, regardless of how many millions of words are in your dictionary.

### 💻 The Visual
```text
      (root)
       /  \
      c    d
     / \    \
    a   o    o
   /    |    |
  t     g    g
(cat) (dog) (dog)
```

---

## 🎯 Your Mission (LeetCode Checklist)

1. [`Kth Largest Element in an Array`](https://leetcode.com/problems/kth-largest-element-in-an-array/) *(The VIP Queue test)*
2. [`Find Median from Data Stream`](https://leetcode.com/problems/find-median-from-data-stream/) *(Hard - Hint: Use TWO heaps, one for the bottom half, one for the top half!)*
3. [`Implement Trie (Prefix Tree)`](https://leetcode.com/problems/implement-trie-prefix-tree/) *(The Auto-complete foundation)*
4. [`Word Search II`](https://leetcode.com/problems/word-search-ii/) *(Hard - The ultimate Trie challenge)*
5. [`K Closest Points to Origin`](https://leetcode.com/problems/k-closest-points-to-origin/) *(Heap practice)*

You're doing amazing! ☕💻
