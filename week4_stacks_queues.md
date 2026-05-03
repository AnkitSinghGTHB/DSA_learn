# Week 4: The Cafe Line & The Pancake Stack (Stacks & Queues)

This week is all about how we manage things that are piling up or waiting their turn.

## 🥞 Stacks (LIFO)
A Stack is exactly like a stack of pancakes. 
* **LIFO (Last In, First Out):** The last pancake you put on the top of the stack is the *first* one you eat.
* You can only add (`push`) to the top, and remove (`pop`) from the top.

**When to use a Stack:** Use a stack whenever you need to reverse things, undo actions (like Ctrl+Z in MS Word), or match pairs (like opening and closing brackets).

### Stacks in Java
Java has a built-in `Stack` class, but in modern Java, it's highly recommended to use an `ArrayDeque` (a double-ended queue) to act as a stack because it's much faster.

```java
import java.util.ArrayDeque;
import java.util.Deque;

Deque<Integer> stack = new ArrayDeque<>();

// 1. Pushing pancakes onto the stack
stack.push(10);
stack.push(20);
stack.push(30); // 30 is now on top!

// 2. Looking at the top pancake without eating it (Peek)
int top = stack.peek(); // Returns 30

// 3. Eating the top pancake (Pop)
int eaten = stack.pop(); // Removes and returns 30
// Now 20 is on top.

// 4. Checking if we ate all the pancakes
boolean isHungry = stack.isEmpty();
```

---

## ☕ Queues (FIFO)
A Queue is exactly like a line at a cafe.
* **FIFO (First In, First Out):** The first person who got in line is the *first* person to get their coffee.
* You join the back of the line (`offer` or `enqueue`), and get served from the front of the line (`poll` or `dequeue`).

**When to use a Queue:** Use a queue whenever things need to happen in a specific order, or when managing tasks waiting to be processed (like a printer queue).

### Queues in Java
In Java, `Queue` is just an interface (an idea). To actually create one, we usually use `LinkedList` or `ArrayDeque`.

```java
import java.util.Queue;
import java.util.LinkedList;

Queue<String> line = new LinkedList<>();

// 1. People joining the back of the line
line.offer("Alice");
line.offer("Bob");
line.offer("Charlie"); // Alice is at the front, Charlie is at the back.

// 2. Seeing who is next (Peek)
String nextUp = line.peek(); // Returns "Alice"

// 3. Serving the person at the front (Poll)
String served = line.poll(); // Removes and returns "Alice"
// Now Bob is at the front.
```

## 🧠 Core Pattern: Matching Parentheses
If you see a problem asking if brackets are balanced `({[]})`, instantly think of a Stack.
When you see an opening bracket `(`, push its opposite `)` onto the stack. When you see a closing bracket in the string, pop the stack and make sure they match!

### 🎯 Your Practice Checklist (LeetCode)
1. `Valid Parentheses`
2. `Baseball Game`
3. `Next Greater Element I`
4. `Implement Queue using Stacks`
5. `Min Stack` (Medium)
6. `Evaluate Reverse Polish Notation` (Medium)
