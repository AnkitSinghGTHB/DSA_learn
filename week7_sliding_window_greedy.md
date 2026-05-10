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

## 🏁 The Matrix (The Chessboard)

A **Matrix** is just an array of arrays. Think of it like a Chessboard or a parking lot where you have **Rows** and **Columns**.

**The Logic:** 
To visit every spot, you use a "Nested Loop" (a loop inside a loop). 
1. The outer loop picks a **Row**.
2. The inner loop walks through every **Column** in that row.

```java
int[][] board = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};

for (int r = 0; r < board.length; r++) {
    for (int c = 0; c < board[0].length; c++) {
        System.out.println("At Row " + r + ", Col " + c + " is: " + board[r][c]);
    }
}
```

---

## 🎯 Your Mission (LeetCode Checklist)

1. [`Best Time to Buy and Sell Stock`](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/) *(Greedy)*
2. [`Assign Cookies`](https://leetcode.com/problems/assign-cookies/) *(Greedy)*
3. [`Maximum Average Subarray I`](https://leetcode.com/problems/maximum-average-subarray-i/) *(Sliding Window)*
4. [`Longest Substring Without Repeating Characters`](https://leetcode.com/problems/longest-substring-without-repeating-characters/) *(The ultimate Sliding Window test)*
5. [`Spiral Matrix`](https://leetcode.com/problems/spiral-matrix/) *(Medium - Matrix practice)*
6. [`Rotate Image`](https://leetcode.com/problems/rotate-image/) *(Medium - Matrix practice)*
7. [`Set Matrix Zeroes`](https://leetcode.com/problems/set-matrix-zeroes/) *(Medium - Matrix practice)*
