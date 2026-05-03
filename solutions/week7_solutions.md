# Week 7 Solutions: Sliding Window & Greedy

Here are the Java solutions for the Week 7 practice problems.

### 1. Best Time to Buy and Sell Stock
**Concept:** Greedy. Keep track of the lowest price seen so far, and calculate potential profit every day. Time: O(N), Space: O(1).
```java
class Solution {
    public int maxProfit(int[] prices) {
        int minPrice = Integer.MAX_VALUE;
        int maxProfit = 0;
        
        for (int price : prices) {
            if (price < minPrice) {
                minPrice = price;
            } else {
                maxProfit = Math.max(maxProfit, price - minPrice);
            }
        }
        return maxProfit;
    }
}
```

### 2. Assign Cookies
**Concept:** Greedy. Sort both arrays. Give the smallest cookie that satisfies the child's greed. Time: O(N log N), Space: O(1) or O(log N) for sorting.
```java
import java.util.Arrays;

class Solution {
    public int findContentChildren(int[] g, int[] s) {
        Arrays.sort(g); // Children's greed
        Arrays.sort(s); // Cookie sizes
        
        int childIndex = 0;
        int cookieIndex = 0;
        
        while (childIndex < g.length && cookieIndex < s.length) {
            if (s[cookieIndex] >= g[childIndex]) {
                // Cookie is big enough!
                childIndex++;
            }
            // Always move to the next cookie
            cookieIndex++;
        }
        return childIndex;
    }
}
```

### 3. Maximum Average Subarray I
**Concept:** Fixed Sliding Window. Calculate the sum of the first `k` elements, then slide the window by subtracting the left element and adding the right. Time: O(N), Space: O(1).
```java
class Solution {
    public double findMaxAverage(int[] nums, int k) {
        double currentSum = 0;
        
        for (int i = 0; i < k; i++) {
            currentSum += nums[i];
        }
        
        double maxSum = currentSum;
        
        for (int i = k; i < nums.length; i++) {
            currentSum = currentSum - nums[i - k] + nums[i];
            maxSum = Math.max(maxSum, currentSum);
        }
        
        return maxSum / k;
    }
}
```

### 4. Minimum Add to Make Parentheses Valid
**Concept:** Greedy / Implicit Stack. Count opening brackets. If you see a closing bracket without an opening one, it's an error. Time: O(N), Space: O(1).
```java
class Solution {
    public int minAddToMakeValid(String s) {
        int openCount = 0;
        int errors = 0;
        
        for (char c : s.toCharArray()) {
            if (c == '(') {
                openCount++;
            } else {
                if (openCount > 0) openCount--; // Match found
                else errors++; // No opening bracket available, so it's an error
            }
        }
        return openCount + errors; // Unmatched opening + unmatched closing
    }
}
```

### 5. Longest Substring Without Repeating Characters
**Concept:** Dynamic Sliding Window. Use a HashSet. If you see a duplicate, shrink the window from the left until it's valid again. Time: O(N), Space: O(K) where K is the charset.
```java
import java.util.HashSet;

class Solution {
    public int lengthOfLongestSubstring(String s) {
        HashSet<Character> window = new HashSet<>();
        int left = 0;
        int maxLength = 0;
        
        for (int right = 0; right < s.length(); right++) {
            char curr = s.charAt(right);
            
            // If duplicate found, shrink window from left
            while (window.contains(curr)) {
                window.remove(s.charAt(left));
                left++;
            }
            
            window.add(curr);
            maxLength = Math.max(maxLength, right - left + 1);
        }
        
        return maxLength;
    }
}
```

### 6. Longest Repeating Character Replacement
**Concept:** Sliding Window. Keep a count of the most frequent character in the window. If the remaining characters in the window are greater than `k`, shrink it. Time: O(N), Space: O(1) (26 characters).
```java
class Solution {
    public int characterReplacement(String s, int k) {
        int[] counts = new int[26];
        int left = 0;
        int maxFreq = 0;
        int maxLength = 0;
        
        for (int right = 0; right < s.length(); right++) {
            char curr = s.charAt(right);
            counts[curr - 'A']++;
            maxFreq = Math.max(maxFreq, counts[curr - 'A']);
            
            // Window size - maxFreq = number of letters we need to replace
            // If we need to replace more than k, shrink the window
            while ((right - left + 1) - maxFreq > k) {
                counts[s.charAt(left) - 'A']--;
                left++;
            }
            
            maxLength = Math.max(maxLength, right - left + 1);
        }
        
        return maxLength;
    }
}
```
