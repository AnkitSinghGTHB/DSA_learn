# 🔍 Week 9: The Guessing Game (Binary Search & Intervals)

Welcome to Week 9! 🎉

This week, we learn how to search through sorted data at lightning speed and how to handle overlapping schedules (Intervals).

---

## 🔢 Binary Search (The High-Low Game)

Imagine I'm thinking of a number between 1 and 100.
If you guess **1, 2, 3...** one by one, that's **O(N)**. Too slow! 🐢

But if you guess **50**, and I say "Higher," you just eliminated half of the numbers in one step! That is **Binary Search**, and it takes **O(log N)** time. ⚡

**When to use it:** 
Whenever the input array is **SORTED**. If it's sorted, you should almost always think: *"Can I use Binary Search here?"*

### 💻 The Pattern
```java
public int binarySearch(int[] nums, int target) {
    int left = 0;
    int right = nums.length - 1;
    
    while (left <= right) {
        // Find the middle spot
        int mid = left + (right - left) / 2;
        
        if (nums[mid] == target) {
            return mid; // Found it! 🏆
        } else if (nums[mid] < target) {
            left = mid + 1; // Too low! Search the right half.
        } else {
            right = mid - 1; // Too high! Search the left half.
        }
    }
    return -1; // Not found.
}
```

---

## 🗓️ Intervals (The Busy Secretary)

Imagine you are a secretary at a doctor's office. You have a list of appointments, but some of them overlap! 
* **Appt A:** 1 PM to 3 PM
* **Appt B:** 2 PM to 4 PM

Since they overlap, you need to merge them into one long block: **1 PM to 4 PM**.

**The Trick:** 
Always **SORT** the intervals by their start time first. Once they are sorted, you only need to check if the *start* of the next meeting is before the *end* of the current one.

### 💻 The Logic
```java
// 1. Sort intervals by start time: [[1,3], [2,6], [8,10]]
// 2. Compare [1,3] and [2,6]. Since 2 is less than 3, they overlap!
// 3. New merged interval is [1, max(3,6)] = [1,6].
```

---

## 🎯 Your Mission (LeetCode Checklist)

1. [`Search Insert Position`](https://leetcode.com/problems/search-insert-position/) *(Binary Search Basic)*
2. [`Search a 2D Matrix`](https://leetcode.com/problems/search-a-2d-matrix/) *(Binary Search on a grid!)*
3. [`Find Minimum in Rotated Sorted Array`](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/) *(Medium - The ultimate Binary Search test)*
4. [`Merge Intervals`](https://leetcode.com/problems/merge-intervals/) *(The Secretary's Job)*
5. [`Insert Interval`](https://leetcode.com/problems/insert-interval/) *(Medium)*
6. [`Summary Ranges`](https://leetcode.com/problems/summary-ranges/) *(Easy Interval warmup)*

Keep going, you're almost a pro! ☕💻
