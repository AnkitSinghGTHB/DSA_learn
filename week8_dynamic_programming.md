# Week 8: Learning from the Past (Dynamic Programming)

Welcome to the Final Boss. Dynamic Programming (DP) strikes fear into the hearts of many, but it is actually a very simple concept wrapped in scary terminology.

## 🧠 What is DP? (Memoization & Caching)
Dynamic Programming simply means: **Remembering what you already did so you don't have to do the work twice.**

**The Classic Analogy:**
If I ask you "What is 1 + 1 + 1 + 1 + 1 + 1 + 1 + 1?", you will count them and say "8".
If I immediately add another "+ 1" to the end and ask "What is it now?", do you recount all of them from the beginning? No! You just take the previous answer (8) and add 1 to get "9". 
**That is Dynamic Programming.**

### The Problem with Recursion
If we try to calculate the Fibonacci sequence (`0, 1, 1, 2, 3, 5, 8...`) using plain recursion, we end up recalculating the exact same numbers hundreds of times. The tree of calculations explodes and it becomes `O(2^N)` time (which will crash your computer).

### The DP Solution (Top-Down with Memoization)
We create an array (a cache/memo) to store the answers we've already found. Before calculating something, we check the cache.

```java
class Solution {
    // Our Cache: We will store answers here.
    int[] memo;
    
    public int fib(int n) {
        // Initialize the cache with -1 (meaning "uncalculated")
        memo = new int[n + 1];
        for (int i = 0; i < memo.length; i++) {
            memo[i] = -1;
        }
        
        return calculateFib(n);
    }
    
    private int calculateFib(int n) {
        // Base cases
        if (n == 0) return 0;
        if (n == 1) return 1;
        
        // CHECK THE CACHE! If we already know the answer, return it instantly!
        if (memo[n] != -1) {
            return memo[n];
        }
        
        // If we don't know the answer, calculate it...
        int answer = calculateFib(n - 1) + calculateFib(n - 2);
        
        // ...and SAVE it to the cache for next time!
        memo[n] = answer;
        
        return answer;
    }
}
```

### The DP Solution (Bottom-Up)
Instead of starting at the end and working backward with recursion, we can start at the beginning and build our way up using a simple Array and a `for` loop. This is usually faster and cleaner!

```java
public int fibBottomUp(int n) {
    if (n == 0) return 0;
    if (n == 1) return 1;
    
    // Create an array to hold the building blocks
    int[] dp = new int[n + 1];
    
    // Set the base blocks
    dp[0] = 0;
    dp[1] = 1;
    
    // Build up to N
    for (int i = 2; i <= n; i++) {
        dp[i] = dp[i - 1] + dp[i - 2];
    }
    
    return dp[n];
}
```

### 🎯 Your Practice Checklist (LeetCode)
1. `Climbing Stairs` (This is literally just Fibonacci in disguise!)
2. `Min Cost Climbing Stairs`
3. `House Robber` (Medium)
4. `Coin Change` (Medium)
5. `Longest Increasing Subsequence` (Medium)

You did it. You have finished the Couch to Coder DSA roadmap. Now go crush those interviews! 🚀
