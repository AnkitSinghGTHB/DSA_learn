# Week 1: Organizing the Closet (Big-O & Arrays)

Welcome to Week 1! We are going to start with the most fundamental concept in all of computer science: figuring out how fast code is, and organizing items in a row.

## ⏱️ Big-O Notation (Without the Math)
Imagine you lost your shoes in your room. 
* **O(1) "Constant Time":** You know exactly where your shoes are. You reach under the bed and grab them instantly. It takes 1 step.
* **O(N) "Linear Time":** Your room is messy. You have to check every single box one by one until you find your shoes. If there are `N` boxes, it takes `N` steps.
* **O(N²) "Quadratic Time":** You check the first box, but instead of just looking inside, you take the item out and compare it with *every other item in every other box*. Then you do it for the second item. This is terribly slow!

> **Golden Rule:** We want our code to be O(1) or O(N). If it's O(N²), the interviewer will probably ask if we can do better.

---

## 📦 Arrays (The Storage Boxes)
An array is just a contiguous row of storage boxes. Each box has a numbered label (starting at 0). 

* **The Good:** If you know the box number (the "index"), you can grab the item inside instantly in `O(1)` time.
* **The Bad:** If you want to insert a new box at the very beginning, you have to shift every other box over by one spot. This takes `O(N)` time.

### The Java Translation
While Python lets you throw anything into a list, Java is strict. You have to tell Java exactly what size the boxes are and what goes inside them (e.g., only whole numbers `int`).

```java
// 1. Creating an array of 5 integers
int[] closet = new int[5];

// 2. Putting items in the boxes
closet[0] = 10; // First box
closet[1] = 20; // Second box

// 3. What if we don't know the size upfront? We use an ArrayList!
// ArrayLists are like magic closets that expand automatically.
import java.util.ArrayList;

ArrayList<Integer> magicCloset = new ArrayList<>();
magicCloset.add(10); // Adds to the end
magicCloset.add(20);
System.out.println(magicCloset.get(0)); // Gets the item at index 0 (prints 10)
```

## 🧠 Core Pattern: Looping (Checking every box)
To find something in an array, we usually just walk through it one by one.

```java
// Traditional For Loop
int[] numbers = {1, 2, 3, 4, 5};
for (int i = 0; i < numbers.length; i++) {
    System.out.println("Checking box " + i + " which holds: " + numbers[i]);
}

// Enhanced For Loop (For-each loop) - Much cleaner!
for (int num : numbers) {
    System.out.println("Found: " + num);
}
```

## 🤫 Sneak Peek: The Magic Contacts List (Hash Maps & Sets)
For a few of the problems this week (like *Two Sum* and *Contains Duplicate*), checking every single box one-by-one is too slow (it takes `O(N²)` time). 
To make it fast, we use a cheat code called a **HashSet** or **HashMap**. We will learn these fully in Week 2, but for now, just know this:
* **HashSet:** A VIP list. You can instantly check if a number is already on the list in `O(1)` time.
* **HashMap:** A contacts app. You can instantly look up a number to find its exact index in `O(1)` time.

### 🎯 Your Practice Checklist (LeetCode)
1. `Running Sum of 1d Array`
2. `Contains Duplicate`
3. `Two Sum`
4. `Move Zeroes`
5. `Majority Element`
6. `Squares of a Sorted Array`

Take your time and remember: don't stay stuck for more than 45 minutes!
