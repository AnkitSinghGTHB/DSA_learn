# 🧠 Week 8: Learning from the Past (Dynamic Programming)

Welcome to the Final Week! 🎉

You have reached the Final Boss. **Dynamic Programming (DP)** strikes fear into the hearts of many coding students, but I'm going to let you in on a secret: it is actually a very simple concept wrapped in scary academic terminology.

Let's demystify it. 👇

---

## 🧠 What exactly is DP? (Memoization)

Dynamic Programming simply means: **Remembering what you already did so you don't have to do the work twice.**

**Let's try an experiment:**
If I ask you *"What is 1 + 1 + 1 + 1 + 1 + 1 + 1 + 1?"*, you will count them and say *"8"*.
If I immediately add another `+ 1` to the end and ask *"What is it now?"*, do you recount all of them from the very beginning? 

**No!** You aren't crazy. You just take the previous answer (8), add 1 to it, and say *"9"*. 

Congratulations, you just did Dynamic Programming. 🏆

### The Problem with standard Recursion
If we try to calculate the Fibonacci sequence (`0, 1, 1, 2, 3, 5, 8...`) using plain old recursion, we end up recalculating the exact same numbers hundreds of times. It takes **O(2^N)** time. Your computer will literally freeze and crash on large numbers. 🐢💥

### 💻 The DP Solution (Top-Down with a Cache)
We just create an array (a cache) to store answers. Before doing any math, we ask the cache: *"Hey, have we done this before?"*

```java
class Solution {
    // Our Cache: We will store answers here!
    int[] cache;
    
    public int fib(int n) {
        cache = new int[n + 1];
        for (int i = 0; i < cache.length; i++) {
            cache[i] = -1; // -1 means "We haven't calculated this yet"
        }
        return calculateFib(n);
    }
    
    private int calculateFib(int n) {
        if (n == 0) return 0;
        if (n == 1) return 1;
        
        // 🛑 WAIT! Check the cache! If we already know the answer, return it instantly!
        if (cache[n] != -1) {
            return cache[n]; 
        }
        
        // If we don't know it, calculate it...
        int answer = calculateFib(n - 1) + calculateFib(n - 2);
        
        // ...and SAVE it to the cache for next time!
        cache[n] = answer;
        
        return answer;
    }
}
```

### 💻 The DP Solution (Bottom-Up)
Instead of starting at the end and using confusing recursion, what if we just start at the beginning and build our way up using a simple `for` loop? This is usually faster and cleaner!

```java
public int fibBottomUp(int n) {
    if (n == 0) return 0;
    if (n == 1) return 1;
    
    // Create an array to hold our building blocks
    int[] dp = new int[n + 1];
    
    // Set the base blocks
    dp[0] = 0;
    dp[1] = 1;
    
    // Build our way up to N!
    for (int i = 2; i <= n; i++) {
        dp[i] = dp[i - 1] + dp[i - 2];
    }
    
    return dp[n];
}
```

---

## 🎯 Your Final Mission (LeetCode Checklist)

1. [`Climbing Stairs`](https://leetcode.com/problems/climbing-stairs/) *(This is literally just the Fibonacci sequence in disguise!)*
2. [`Min Cost Climbing Stairs`](https://leetcode.com/problems/min-cost-climbing-stairs/)
3. [`House Robber`](https://leetcode.com/problems/house-robber/) *(Medium - You can't rob two houses next to each other. Maximize your loot!)*
4. [`Coin Change`](https://leetcode.com/problems/coin-change/) *(Medium)*
5. [`Longest Increasing Subsequence`](https://leetcode.com/problems/longest-increasing-subsequence/) *(Medium - The ultimate final test)*

> [!TIP]
> **You did it.** You have finished the Couch to Coder DSA roadmap. 
> Take a deep breath. You now know the patterns to solve over 50% of the questions they will throw at you in a real interview. Go crush it! 🚀
