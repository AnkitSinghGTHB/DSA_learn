# Week 7: The Smart Shopper (Sliding Window & Greedy)

This week, we look at two very specific, very powerful techniques for solving array and string problems.

## 🖼️ The Sliding Window
Imagine you are looking at a long mural painted on a wall, but you are looking through a small, square window frame. You can slide the frame to the right to see the next part of the painting.

**When to use it:** Whenever a problem asks for a "longest", "shortest", or "maximum" contiguous subarray or substring.

### The Sliding Window Pattern
You use two pointers, `left` and `right`. You expand the window by moving `right`. If the window becomes invalid (e.g., it gets too big or contains a duplicate), you shrink it by moving `left` until it's valid again.

```java
// Example: Finding the maximum sum of a contiguous subarray of length K
public int maxSum(int[] arr, int k) {
    int maxSum = 0;
    int windowSum = 0;
    
    // Step 1: Create the initial window of size K
    for (int i = 0; i < k; i++) {
        windowSum += arr[i];
    }
    maxSum = windowSum;
    
    // Step 2: Slide the window across the rest of the array
    for (int right = k; right < arr.length; right++) {
        // Add the new element entering the window, subtract the old element leaving
        int left = right - k;
        windowSum = windowSum + arr[right] - arr[left];
        
        maxSum = Math.max(maxSum, windowSum);
    }
    
    return maxSum;
}
```

---

## 🍪 Greedy Algorithms
A Greedy algorithm is exactly what it sounds like. At every single step, it makes the choice that looks the best *right now*, without worrying about the future.

**Analogy:** You are given a pile of coins and told to take 3. A greedy person will instantly grab the largest coin available, then the next largest, then the next. 

**When to use it:** Problems asking for "minimum steps" or "maximum profit" where taking the obvious best local choice leads to the global best outcome.

### Greedy Pattern
```java
// Example: Best Time to Buy and Sell Stock
// You want to maximize profit.
public int maxProfit(int[] prices) {
    int lowestPriceSeen = Integer.MAX_VALUE;
    int maxProfit = 0;
    
    for (int currentPrice : prices) {
        // If we find a lower price, update our lowest seen
        if (currentPrice < lowestPriceSeen) {
            lowestPriceSeen = currentPrice;
        } 
        // Otherwise, check how much profit we'd make if we sold today!
        else {
            int profit = currentPrice - lowestPriceSeen;
            maxProfit = Math.max(maxProfit, profit);
        }
    }
    
    return maxProfit;
}
```

### 🎯 Your Practice Checklist (LeetCode)
1. `Best Time to Buy and Sell Stock`
2. `Assign Cookies`
3. `Maximum Average Subarray I`
4. `Minimum Add to Make Parentheses Valid` (Medium)
5. `Longest Substring Without Repeating Characters` (Medium)
6. `Longest Repeating Character Replacement` (Medium)
