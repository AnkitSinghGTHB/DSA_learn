# Week 1 Solutions: Arrays & Big O

Here are the Java solutions for the Week 1 practice problems.

### 1. Running Sum of 1d Array
**Concept:** Keeping a running total. Time: O(N), Space: O(1) if modifying in-place.
```java
class Solution {
    public int[] runningSum(int[] nums) {
        for (int i = 1; i < nums.length; i++) {
            // Add the previous element's value to the current one
            nums[i] += nums[i - 1]; 
        }
        return nums;
    }
}
```

### 2. Contains Duplicate
**Concept:** Using a HashSet to remember what we've seen. Time: O(N), Space: O(N).
*(Note: A **HashSet** is like a VIP guest list. We use it here to instantly check if we've seen a number before, rather than looping through the array a second time! We'll cover this fully in Week 2).*
```java
import java.util.HashSet;

class Solution {
    public boolean containsDuplicate(int[] nums) {
        HashSet<Integer> seen = new HashSet<>();
        for (int num : nums) {
            if (seen.contains(num)) return true; // Found a duplicate!
            seen.add(num);
        }
        return false;
    }
}
```

### 3. Two Sum
**Concept:** Using a HashMap to find the missing piece. Time: O(N), Space: O(N).
*(Note: A **HashMap** is like a contacts list. We use it here to instantly look up if the "missing piece" we need to reach the target is already in our list. We'll cover this fully in Week 2).*
```java
import java.util.HashMap;

class Solution {
    public int[] twoSum(int[] nums, int target) {
        // Map stores: <Number, Index>
        HashMap<Integer, Integer> map = new HashMap<>();
        
        for (int i = 0; i < nums.length; i++) {
            int needed = target - nums[i];
            
            if (map.containsKey(needed)) {
                // We found the pair!
                return new int[] { map.get(needed), i };
            }
            // Otherwise, put the current number in the map
            map.put(nums[i], i);
        }
        return new int[0];
    }
}
```

### 4. Move Zeroes
**Concept:** Using a pointer to keep track of where the next non-zero should go. Time: O(N), Space: O(1).
```java
class Solution {
    public void moveZeroes(int[] nums) {
        int insertPos = 0;
        
        // Push all non-zero numbers to the front
        for (int num : nums) {
            if (num != 0) {
                nums[insertPos] = num;
                insertPos++;
            }
        }
        
        // Fill the rest of the array with zeroes
        while (insertPos < nums.length) {
            nums[insertPos] = 0;
            insertPos++;
        }
    }
}
```

### 5. Majority Element
**Concept:** Boyer-Moore Voting Algorithm. Time: O(N), Space: O(1).
```java
class Solution {
    public int majorityElement(int[] nums) {
        int count = 0;
        Integer candidate = null;

        for (int num : nums) {
            if (count == 0) {
                candidate = num;
            }
            count += (num == candidate) ? 1 : -1;
        }

        return candidate;
    }
}
```

### 6. Squares of a Sorted Array
**Concept:** Two Pointers from outside moving inward (since negatives squared become positive). Time: O(N), Space: O(N).
```java
class Solution {
    public int[] sortedSquares(int[] nums) {
        int n = nums.length;
        int[] result = new int[n];
        int left = 0;
        int right = n - 1;
        
        // Fill the result array from back to front (largest first)
        for (int i = n - 1; i >= 0; i--) {
            int leftSquare = nums[left] * nums[left];
            int rightSquare = nums[right] * nums[right];
            
            if (leftSquare > rightSquare) {
                result[i] = leftSquare;
                left++;
            } else {
                result[i] = rightSquare;
                right--;
            }
        }
        return result;
    }
}
```
