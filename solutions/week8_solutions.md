# Week 8 Solutions: Dynamic Programming

Here are the Java solutions for the Week 8 practice problems.

### 1. Climbing Stairs
**Concept:** 1D DP (Fibonacci). The number of ways to reach step `n` is `ways(n-1) + ways(n-2)`. Time: O(N), Space: O(N) or O(1) if optimized.
```java
class Solution {
    public int climbStairs(int n) {
        if (n <= 2) return n;
        
        int[] dp = new int[n + 1];
        dp[1] = 1;
        dp[2] = 2;
        
        for (int i = 3; i <= n; i++) {
            dp[i] = dp[i - 1] + dp[i - 2];
        }
        
        return dp[n];
    }
}
```

### 2. Min Cost Climbing Stairs
**Concept:** 1D DP. You can start at index 0 or 1. The cost to reach step `i` is the `cost[i] + min(cost of reaching i-1, cost of reaching i-2)`. Time: O(N), Space: O(N).
```java
class Solution {
    public int minCostClimbingStairs(int[] cost) {
        int n = cost.length;
        int[] dp = new int[n + 1]; // One extra step to reach the top
        
        dp[0] = 0;
        dp[1] = 0;
        
        for (int i = 2; i <= n; i++) {
            dp[i] = Math.min(dp[i - 1] + cost[i - 1], dp[i - 2] + cost[i - 2]);
        }
        
        return dp[n];
    }
}
```

### 3. House Robber
**Concept:** 1D DP. For each house, you can either: rob it (current + money from 2 houses ago) or skip it (take the max money up to the previous house). Time: O(N), Space: O(N).
```java
class Solution {
    public int rob(int[] nums) {
        if (nums.length == 0) return 0;
        if (nums.length == 1) return nums[0];
        
        int[] dp = new int[nums.length];
        dp[0] = nums[0];
        dp[1] = Math.max(nums[0], nums[1]);
        
        for (int i = 2; i < nums.length; i++) {
            dp[i] = Math.max(dp[i - 1], nums[i] + dp[i - 2]);
        }
        
        return dp[nums.length - 1];
    }
}
```

### 4. Coin Change
**Concept:** DP with Memoization / Tabulation. Create an array of size `amount + 1` filled with infinity. Calculate the minimum coins for every amount from 1 to `amount`. Time: O(amount * coins), Space: O(amount).
```java
import java.util.Arrays;

class Solution {
    public int coinChange(int[] coins, int amount) {
        int[] dp = new int[amount + 1];
        Arrays.fill(dp, amount + 1); // Fill with "infinity"
        dp[0] = 0; // 0 coins needed to make amount 0
        
        for (int a = 1; a <= amount; a++) {
            for (int coin : coins) {
                if (a - coin >= 0) {
                    dp[a] = Math.min(dp[a], 1 + dp[a - coin]);
                }
            }
        }
        
        return dp[amount] > amount ? -1 : dp[amount];
    }
}
```

### 5. Longest Increasing Subsequence
**Concept:** 1D DP. For every element, check all elements before it. If it's larger, `dp[i] = max(dp[i], dp[j] + 1)`. Time: O(N²), Space: O(N).
```java
import java.util.Arrays;

class Solution {
    public int lengthOfLIS(int[] nums) {
        int[] dp = new int[nums.length];
        Arrays.fill(dp, 1); // Every number is a subsequence of length 1 by itself
        
        int maxLIS = 1;
        
        for (int i = 1; i < nums.length; i++) {
            for (int j = 0; j < i; j++) {
                if (nums[i] > nums[j]) {
                    dp[i] = Math.max(dp[i], dp[j] + 1);
                }
            }
            maxLIS = Math.max(maxLIS, dp[i]);
        }
        
        return maxLIS;
    }
}
```
