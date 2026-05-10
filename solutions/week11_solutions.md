# Week 11 Solutions: Backtracking & Graphs

### 1. Letter Combinations of a Phone Number
**Concept:** Backtracking/Recursion to explore all letter combos.
```java
import java.util.*;

class Solution {
    private String[] map = {"", "", "abc", "def", "ghi", "jkl", "mno", "pqrs", "tuv", "wxyz"};
    
    public List<String> letterCombinations(String digits) {
        List<String> res = new ArrayList<>();
        if (digits.isEmpty()) return res;
        backtrack(res, digits, "", 0);
        return res;
    }
    
    private void backtrack(List<String> res, String digits, String current, int index) {
        if (index == digits.length()) {
            res.add(current);
            return;
        }
        
        String letters = map[digits.charAt(index) - '0'];
        for (char c : letters.toCharArray()) {
            backtrack(res, digits, current + c, index + 1);
        }
    }
}
```

### 2. Permutations
**Concept:** Backtracking while keeping track of "used" numbers.
```java
import java.util.*;

class Solution {
    public List<List<Integer>> permute(int[] nums) {
        List<List<Integer>> res = new ArrayList<>();
        backtrack(res, new ArrayList<>(), nums);
        return res;
    }
    
    private void backtrack(List<List<Integer>> res, List<Integer> current, int[] nums) {
        if (current.size() == nums.length) {
            res.add(new ArrayList<>(current));
            return;
        }
        
        for (int num : nums) {
            if (current.contains(num)) continue; // Skip if already chosen
            current.add(num); // Choose
            backtrack(res, current, nums); // Explore
            current.remove(current.size() - 1); // Un-choose (Backtrack!)
        }
    }
}
```
