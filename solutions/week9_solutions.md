# Week 9 Solutions: Binary Search & Intervals

Here are the Java solutions for the Week 9 practice problems.

### 1. Search Insert Position
**Concept:** Binary Search. If not found, `left` will be the index where it should be inserted.
```java
class Solution {
    public int searchInsert(int[] nums, int target) {
        int left = 0, right = nums.length - 1;
        while (left <= right) {
            int mid = left + (right - left) / 2;
            if (nums[mid] == target) return mid;
            else if (nums[mid] < target) left = mid + 1;
            else right = mid - 1;
        }
        return left;
    }
}
```

### 2. Search a 2D Matrix
**Concept:** Treat the 2D matrix as one long 1D array and use Binary Search.
```java
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        int m = matrix.length;
        int n = matrix[0].length;
        int left = 0, right = m * n - 1;
        
        while (left <= right) {
            int mid = left + (right - left) / 2;
            // Magic formula to convert 1D index back to Row/Col
            int val = matrix[mid / n][mid % n];
            
            if (val == target) return true;
            else if (val < target) left = mid + 1;
            else right = mid - 1;
        }
        return false;
    }
}
```

### 3. Merge Intervals
**Concept:** Sort by start time, then merge overlapping blocks.
```java
import java.util.*;

class Solution {
    public int[][] merge(int[][] intervals) {
        if (intervals.length <= 1) return intervals;
        
        // 1. Sort by start time
        Arrays.sort(intervals, (a, b) -> Integer.compare(a[0], b[0]));
        
        List<int[]> result = new ArrayList<>();
        int[] current = intervals[0];
        result.add(current);
        
        for (int[] next : intervals) {
            if (next[0] <= current[1]) {
                // Overlap! Update the end time
                current[1] = Math.max(current[1], next[1]);
            } else {
                // No overlap, move to the next block
                current = next;
                result.add(current);
            }
        }
        return result.toArray(new int[result.size()][]);
    }
}
```
