# 🕵️ Week 3: Scavenger Hunts & Two Pointers

Welcome to Week 3! 🎉

This week, we leave the neat, perfectly aligned Array boxes behind. We are entering the world where data is scattered all over the place, but connected by invisible strings. 

But first, let's learn a brilliant trick for reading arrays faster! 👇

---

## ✌️ Two Pointers (The Squeeze!)

Normally, you read an array from left to right. Boring. 
The **Two Pointer** technique means you put one finger at the start of the array, and your other finger at the very end, and you move them *at the same time*.

**Why do this?** 
Imagine checking if a word is a palindrome (like "RACECAR" 🏎️). You don't need to read the whole word backwards. Just check if the first letter matches the last letter. Then squeeze your fingers inward and check the second letters. Boom. Fast and easy!

```java
public boolean isPalindrome(String s) {
    // Left finger points to the start
    int left = 0;
    // Right finger points to the end
    int right = s.length() - 1;
    
    // While the fingers haven't crossed each other...
    while (left < right) {
        
        // Uh oh, the letters don't match! It's an imposter!
        if (s.charAt(left) != s.charAt(right)) {
            return false;
        }
        
        // They match! Squeeze fingers inward.
        left++;   
        right--;  
    }
    
    return true; // Fingers met in the middle perfectly!
}
```

---

## 🗺️ Linked Lists (The Scavenger Hunt)

A Linked List is a literal scavenger hunt. 
Instead of storage boxes sitting right next to each other, the data is scattered around in random places. Each piece of data is stored in a `Node`. 

A `Node` holds two things:
1. **The Treasure:** (The actual data, like a number).
2. **The Map:** (An arrow pointing to the exact location of the *next* Node).

> [!TIP]
> **The Good:** You can break the chain and insert a new Node anywhere instantly. Just redraw the arrows!
> **The Bad:** You can't jump straight to the 10th item. You HAVE to start at the 1st item and follow the map 10 times. (O(N) time 🐢).

### 💻 Linked Lists in Java

In Java, we don't get Linked List nodes for free. We have to build the blueprint ourselves!

```java
// The Blueprint for a Scavenger Hunt Clue
class ListNode {
    int val;           // The treasure 💰
    ListNode next;     // The map to the next clue 🗺️
    
    // How we forge a brand new clue
    ListNode(int val) {
        this.val = val;
        this.next = null; // Next is empty until we connect it!
    }
}

// Let's build a mini scavenger hunt!
public void play() {
    ListNode clue1 = new ListNode(10);
    ListNode clue2 = new ListNode(20);
    
    // Connect clue1 so it points to clue2
    clue1.next = clue2; 
    
    // How to actually walk the path:
    ListNode walker = clue1;
    
    // Keep walking until the map leads nowhere (null)
    while (walker != null) {
        System.out.println("Found treasure: " + walker.val);
        walker = walker.next; // Move to the next clue!
    }
}
```

---

## 🧠 Core Pattern: Fast and Slow Runners

How do you find the exact middle of a scavenger hunt if you don't know how long it is? 
**Use two runners!** 🏃‍♂️🏃‍♂️💨

* Send a `slow` runner who takes 1 step at a time.
* Send a `fast` runner who takes 2 steps at a time.
* When the `fast` runner hits the finish line... the `slow` runner will be exactly in the middle! It feels like magic.

---

## 🎯 Your Mission (LeetCode Checklist)

1. [`Reverse String`](https://leetcode.com/problems/reverse-string/) *(The ultimate two-pointer warmup)*
2. [`Valid Palindrome`](https://leetcode.com/problems/valid-palindrome/)
3. [`Middle of the Linked List`](https://leetcode.com/problems/middle-of-the-linked-list/) *(Fast/Slow runners!)*
4. [`Merge Two Sorted Lists`](https://leetcode.com/problems/merge-two-sorted-lists/)
5. [`Reverse a Linked List`](https://leetcode.com/problems/reverse-linked-list/) *(Extremely famous interview question)*
6. [`Linked List Cycle`](https://leetcode.com/problems/linked-list-cycle/)
7. [`Remove Nth Node From End of List`](https://leetcode.com/problems/remove-nth-node-from-end-of-list/) *(Medium)*
