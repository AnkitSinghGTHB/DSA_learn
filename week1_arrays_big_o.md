# 🚀 Week 1: Arrays & Big-O (The Basics)

Welcome to Week 1! 🎉 

Before we write any crazy algorithms, we need to answer two simple questions:
1. **How do we measure if our code is slow?**
2. **How do we store a bunch of stuff in a row?**

Let's dive in! 🤿

---

## ⏱️ Big-O Notation (Zero Math Edition)

**"Big-O" is just a fancy way of saying: "How many steps does this take?"**

Imagine you lost your favorite shoes in a very messy room.

* ⚡ **O(1) -> "Constant Time"** 
  You know *exactly* where they are. You reach under the bed. Boom. 1 step. Instant.
  
* 🚶 **O(N) -> "Linear Time"**
  You have no idea where they are. You check every single box in the room, one by one. If there are 100 boxes (`N`), it takes 100 steps.

* 🐢 **O(N²) -> "Quadratic Time"**
  You check the first box. Then, for no logical reason, you compare the item inside with *every other item in every other box*. Then you move to the second box and do it again. This is terribly slow!

> [!WARNING]  
> **The Golden Interview Rule:**  
> If your code is **O(N²)**, the interviewer will almost *always* ask: *"Can we make this faster?"* Our goal is usually O(N) or O(1)!

---

## 📦 Arrays (Your Digital Storage Boxes)

An **Array** is just a row of storage boxes. 
Every box gets a numbered label, starting at `0` (because programmers are weird like that).

> [!TIP]
> **The Good:** If you know the exact box number (the index), you can grab the item inside instantly in **O(1)** time!
> **The Bad:** If you want to shove a new box at the *very front* of the line, you have to push every other box back one spot. That takes **O(N)** time.

### 💻 Let's speak Java
Java is a bit of a control freak. You have to tell it *exactly* how many boxes you want, and *exactly* what type of stuff is going inside them.

```java
// 1. Create a row of 5 empty boxes for whole numbers (integers)
int[] closet = new int[5];

// 2. Put some stuff in the boxes! (Remember, we start counting at 0)
closet[0] = 10; // Box zero gets the number 10
closet[1] = 20; // Box one gets the number 20

// 3. What if we don't know how many boxes we need? 
// 🪄 Enter: ArrayList! It's a magic array that grows automatically.
import java.util.ArrayList;

ArrayList<Integer> magicCloset = new ArrayList<>();
magicCloset.add(10); // Toss 10 into the back of the closet
magicCloset.add(20); // Toss 20 in after it

// Peek inside the very first box
System.out.println(magicCloset.get(0)); // Prints 10!
```

---

## 🔄 Core Pattern: The Loop

To find something in an Array, we usually just walk down the line, checking every single box. We call this **looping**.

```java
int[] numbers = {1, 2, 3, 4, 5};

// 🥱 The old-school way (using an index variable 'i')
for (int i = 0; i < numbers.length; i++) {
    System.out.println("Checking box " + i + " which holds: " + numbers[i]);
}

// ✨ The modern, clean way (The "For-Each" loop)
// "For each number inside my numbers array..."
for (int num : numbers) {
    System.out.println("Found a number: " + num);
}
```

---

## 🧵 Strings (The Bead Necklace)

A **String** is just an array of characters. Think of it like a bead necklace where each bead is a letter.

> [!IMPORTANT]
> **The Java Catch:** In Java, Strings are "immutable" (unchangeable). If you want to change a letter in a string, Java actually creates a whole new necklace! 
> 
> To fix this, we use a **StringBuilder**. It's like a necklace that lets you pop beads on and off easily.

```java
String name = "Couch";
// name[0] = 'B'; // ❌ ERROR! You can't do this in Java.

// ✨ Use StringBuilder instead:
StringBuilder sb = new StringBuilder("Couch");
sb.setCharAt(0, 'B'); // Now it's "Bouch"
System.out.println(sb.toString());
```

---

## 🍀 Kadane's Algorithm (The Lucky Streak)

Imagine you are playing a game. Some rounds you win money (+), some rounds you lose money (-). 
**Kadane's Algorithm** helps you find the single "Luckiest Streak" (the contiguous subarray with the highest sum).

**The Logic:** 
As you play, you keep track of your `currentLuck`. 
1. If your `currentLuck` drops below zero, you say "Forget this!" and start your streak over from the current round. 
2. You always remember the `bestLuck` you've ever had during the whole game.

```java
public int maxSubArray(int[] nums) {
    int bestLuck = nums[0];
    int currentLuck = 0;
    
    for (int num : nums) {
        currentLuck += num; // Add the current round to your streak
        bestLuck = Math.max(bestLuck, currentLuck); // Is this our new record?
        
        if (currentLuck < 0) {
            currentLuck = 0; // If streak turns sour, reset it to zero!
        }
    }
    return bestLuck;
}
```

---

## 🤫 Sneak Peek: The Cheat Code (HashSets & HashMaps)

For problems like *Contains Duplicate* and *Two Sum*, checking every single box one-by-one is just too slow. 

To speed things up, we use **HashSets** and **HashMaps**. We will learn how they work next week, but for now, just think of them like this:
* **HashSet:** A VIP guest list. You can instantly check if someone is on the list in O(1) time.
* **HashMap:** A contacts app. You can instantly look up a name to get a phone number in O(1) time.

---

## 🎯 Your Mission (LeetCode Checklist)
Try these out! Don't spend more than 45 minutes on one problem. If you're stuck, look at the solutions file, understand it, and type it out!

1. [`Running Sum of 1d Array`](https://leetcode.com/problems/running-sum-of-1d-array/) *(Easy warmup!)*
2. [`Contains Duplicate`](https://leetcode.com/problems/contains-duplicate/) *(Hint: VIP List!)*
3. [`Two Sum`](https://leetcode.com/problems/two-sum/) *(Hint: Contacts App!)*
4. [`Move Zeroes`](https://leetcode.com/problems/move-zeroes/)
5. [`Majority Element`](https://leetcode.com/problems/majority-element/)
6. [`Squares of a Sorted Array`](https://leetcode.com/problems/squares-of-a-sorted-array/)
7. [`Maximum Subarray`](https://leetcode.com/problems/maximum-subarray/) *(The Lucky Streak!)*
8. [`Roman to Integer`](https://leetcode.com/problems/roman-to-integer/) *(String Practice)*
9. [`Longest Common Prefix`](https://leetcode.com/problems/longest-common-prefix/) *(String Practice)*

You've got this! ☕💻
