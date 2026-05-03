# 🛍️ Week 7: The Smart Shopper (Sliding Window & Greedy)

Welcome to Week 7! 🎉

We are taking a break from messy webs and branching trees to look at two insanely powerful cheat codes for Array and String problems.

If you master these two patterns, you will breeze through 50% of all "Medium" LeetCode questions. 👇

---

## 🖼️ The Sliding Window

Imagine you are looking at a beautiful mural painted on a wall, but you are looking through a small square picture frame. You can slide the frame to the right to see the next piece of the mural.

**When to use it:** 
If an interviewer says *"Find the **longest**, **shortest**, or **maximum** contiguous subarray or substring,"* immediately scream Sliding Window. 

### 💻 The Pattern
Instead of using messy nested loops, we use two pointers (`left` and `right`).
1. We expand the window by moving `right`.
2. If the window breaks a rule (gets too big, or gets a duplicate), we shrink it by moving `left` until the rule is fixed.

```java
// Example: Find the max sum of any 3 numbers sitting next to each other
public int maxSum(int[] arr, int k) {
    int maxSum = 0;
    int windowSum = 0;
    
    // Step 1: Build the first window of size K
    for (int i = 0; i < k; i++) {
        windowSum += arr[i];
    }
    maxSum = windowSum;
    
    // Step 2: Slide the window across the rest of the array!
    for (int right = k; right < arr.length; right++) {
        int left = right - k;
        
        // Add the new item entering the window, subtract the item leaving!
        windowSum = windowSum + arr[right] - arr[left]; 
        
        // Keep track of the best window we've seen
        maxSum = Math.max(maxSum, windowSum);
    }
    
    return maxSum;
}
```

---

## 🍪 Greedy Algorithms

A Greedy algorithm is exactly what it sounds like. At every single step, it makes the choice that looks the absolute best *right now*, without overthinking the future.

**Imagine this:** You are given a pile of coins and told to take 3. A greedy person will instantly grab the largest coin available, then the next largest, without calculating any complex math.

**When to use it:** 
When asked for "maximum profit" or "minimum steps", and taking the local best choice obviously leads to the global best outcome.

### 💻 The Pattern
```java
// Example: Best Time to Buy and Sell Stock 📈
// Greedy logic: Keep track of the cheapest price seen, and see what happens if we sell today!
public int maxProfit(int[] prices) {
    int lowestPriceSeen = Integer.MAX_VALUE;
    int maxProfit = 0;
    
    for (int currentPrice : prices) {
        if (currentPrice < lowestPriceSeen) {
            lowestPriceSeen = currentPrice; // Ooh, a new discount!
        } else {
            // How much would we make if we sold right now?
            int profit = currentPrice - lowestPriceSeen;
            maxProfit = Math.max(maxProfit, profit);
        }
    }
    return maxProfit;
}
```

---

## 🎯 Your Mission (LeetCode Checklist)

1. `Best Time to Buy and Sell Stock` *(Greedy)*
2. `Assign Cookies` *(Greedy)*
3. `Maximum Average Subarray I` *(Sliding Window)*
4. `Minimum Add to Make Parentheses Valid` *(Medium)*
5. `Longest Substring Without Repeating Characters` *(Medium - The ultimate Sliding Window test)*
6. `Longest Repeating Character Replacement` *(Medium)*
