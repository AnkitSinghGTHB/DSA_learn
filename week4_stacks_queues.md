# 🥞 Week 4: Pancake Stacks & Cafe Lines

Welcome to Week 4! 🎉

This week is all about keeping things in order. When data starts piling up, how do we decide who goes first? We have two options: eating pancakes, or waiting for coffee. ☕

Let's dive in! 👇

---

## 🥞 Stacks (LIFO - Last In, First Out)

A Stack is exactly what it sounds like: a giant stack of pancakes. 
When you add a pancake, it goes on top. When you want to eat a pancake, you grab the one on top. 

> [!NOTE]
> **LIFO Rule:** The *Last* pancake you put on the stack is the *First* one you eat! 
> You can't magically pull from the bottom without ruining the whole stack.

**When do we use Stacks?** 
Anytime you need to "Undo" something (like pressing Ctrl+Z on your keyboard), or anytime you need to make sure pairs match up (like opening and closing brackets).

### 💻 Stacks in Java

Java actually has an old `Stack` class, but all the cool kids now use `ArrayDeque` because it's much faster.

```java
import java.util.ArrayDeque;
import java.util.Deque;

// Create an empty plate for our pancakes
Deque<Integer> stack = new ArrayDeque<>();

// 1. Pushing pancakes onto the plate 🥞
stack.push(10);
stack.push(20);
stack.push(30); // 30 is now sitting at the very top!

// 2. Peek: Just looking at the top pancake (without eating it 👀)
int top = stack.peek(); // Returns 30

// 3. Pop: Eating the top pancake! 😋
int eaten = stack.pop(); // Removes 30 from the stack
// Now 20 is the new top pancake!

// 4. Checking if we ate everything
boolean isHungry = stack.isEmpty();
```

---

## ☕ Queues (FIFO - First In, First Out)

A Queue is just a polite line of people waiting at Starbucks.
When you arrive, you join the *back* of the line. The barista serves the person at the *front* of the line.

> [!NOTE]
> **FIFO Rule:** The *First* person to get in line is the *First* person to get their coffee. Fair is fair!

**When do we use Queues?**
Anytime things need to happen in a strict order, like songs queued up on Spotify, or documents waiting to be printed.

### 💻 Queues in Java

In Java, `Queue` is just a concept. To actually build one, we usually use a `LinkedList` under the hood.

```java
import java.util.Queue;
import java.util.LinkedList;

// Create an empty line
Queue<String> line = new LinkedList<>();

// 1. Offer: People join the back of the line 🚶‍♂️
line.offer("Alice");
line.offer("Bob");
line.offer("Charlie"); // Alice is at the front, Charlie is at the back.

// 2. Peek: Who is next to be served? 👀
String nextUp = line.peek(); // Returns "Alice"

// 3. Poll: Serving the person at the front! ☕
String served = line.poll(); // Removes "Alice" from the line
// Now Bob is at the front!
```

---

## 🧠 Core Pattern: The Bracket Matcher

If an interviewer asks you to check if brackets are balanced—like `({[]})`—you should immediately scream **STACK!** (Well, don't scream, but you get it).

**The logic:** 
Every time you see an opening bracket `(`, you push its partner `)` onto your stack. 
When you finally see a closing bracket in the string, you just pop your stack and say: *"Hey, do you match?"* If they don't, the brackets are broken!

---

## 🎯 Your Mission (LeetCode Checklist)

1. [`Valid Parentheses`](https://leetcode.com/problems/valid-parentheses/) *(The ultimate Stack problem)*
2. [`Baseball Game`](https://leetcode.com/problems/baseball-game/)
3. [`Next Greater Element I`](https://leetcode.com/problems/next-greater-element-i/)
4. [`Implement Queue using Stacks`](https://leetcode.com/problems/implement-queue-using-stacks/)
5. [`Min Stack`](https://leetcode.com/problems/min-stack/) *(Medium)*
6. [`Evaluate Reverse Polish Notation`](https://leetcode.com/problems/evaluate-reverse-polish-notation/) *(Medium)*
