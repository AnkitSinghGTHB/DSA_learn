# Week 3: The Scavenger Hunt (Two Pointers & Linked Lists)

This week, we leave the neat and tidy Arrays behind and enter the world where data is scattered, but connected. We also learn a clever trick for reading arrays faster.

## ✌️ Two Pointers
Sometimes, looping from left to right isn't enough. The "Two Pointer" technique uses two variables (usually representing indices) moving through the data at the same time.

**Analogy:** Imagine trying to find out if a word is a palindrome (reads the same forwards and backwards). Instead of reading the whole word backwards, you put your left index finger on the first letter, and your right index finger on the last letter. If they match, you move both fingers inward.

### Two Pointers in Java
```java
public boolean isPalindrome(String s) {
    int left = 0;
    int right = s.length() - 1;
    
    while (left < right) {
        // If the letters at our fingers don't match, it's not a palindrome
        if (s.charAt(left) != s.charAt(right)) {
            return false;
        }
        left++;   // Move left finger inwards
        right--;  // Move right finger inwards
    }
    return true; // Fingers met in the middle, we are good!
}
```

---

## 🗺️ Linked Lists
A Linked List is a scavenger hunt. Unlike an Array where boxes are next to each other, a Linked List is made of `Nodes` scattered randomly in memory. Each `Node` holds two things:
1. The actual data (the treasure).
2. A pointer (a map) to the *next* Node.

* **The Good:** You can insert a new Node anywhere instantly (just change where the map points).
* **The Bad:** You can't jump instantly to the 5th Node. You must start at the 1st Node, read the map to the 2nd, read the map to the 3rd... it takes `O(N)` time to find things.

### Linked Lists in Java
In Java, we have to create a custom blueprint (a Class) for our Nodes.

```java
// The Blueprint for a Scavenger Hunt Clue
class ListNode {
    int val;           // The treasure (data)
    ListNode next;     // The map to the next clue
    
    // Constructor (How we create a new clue)
    ListNode(int val) {
        this.val = val;
        this.next = null; // Next is null until we connect it
    }
}

// Creating the scavenger hunt
public void makeList() {
    ListNode node1 = new ListNode(10);
    ListNode node2 = new ListNode(20);
    
    // Connecting node1 to node2
    node1.next = node2; 
    
    // Walking through the hunt
    ListNode current = node1;
    while (current != null) {
        System.out.println("Found treasure: " + current.val);
        current = current.next; // Move to the next clue
    }
}
```

## 🧠 Core Pattern: Fast and Slow Pointers
If you want to find the middle of a Linked List, or check if the clues go in a circle, use two runners: A `slow` runner that takes 1 step at a time, and a `fast` runner that takes 2 steps. When the fast runner reaches the end, the slow runner will be exactly in the middle!

### 🎯 Your Practice Checklist (LeetCode)
1. `Reverse String`
2. `Valid Palindrome`
3. `Middle of the Linked List`
4. `Merge Two Sorted Lists`
5. `Reverse a Linked List`
6. `Linked List Cycle`
7. `Remove Nth Node From End of List` (Medium)
