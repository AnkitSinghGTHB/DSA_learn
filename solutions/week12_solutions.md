# Week 12 Solutions: Bit Manipulation & Math

### 1. Single Number
**Concept:** XOR everything. Pairs cancel out, leaving the single number.
```java
class Solution {
    public int singleNumber(int[] nums) {
        int result = 0;
        for (int num : nums) {
            result ^= num; // result = result XOR num
        }
        return result;
    }
}
```

### 2. Number of 1 Bits
**Concept:** Use bitwise AND to check the last bit, then shift right.
```java
class Solution {
    public int hammingWeight(int n) {
        int count = 0;
        while (n != 0) {
            count += (n & 1); // If last bit is 1, add to count
            n >>>= 1; // Unsigned right shift
        }
        return count;
    }
}
```

### 3. Palindrome Number
**Concept:** Reverse the number using math (no strings allowed!).
```java
class Solution {
    public boolean isPalindrome(int x) {
        if (x < 0) return false; // Negatives aren't palindromes
        
        int original = x;
        int reversed = 0;
        
        while (x > 0) {
            int lastDigit = x % 10;
            reversed = (reversed * 10) + lastDigit;
            x /= 10;
        }
        
        return original == reversed;
    }
}
```
