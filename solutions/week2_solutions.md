# Week 2 Solutions: Hash Maps & Sets

Here are the Java solutions for the Week 2 practice problems.

### 1. Valid Anagram
**Concept:** Count the frequencies of letters. Time: O(N), Space: O(1) (array of size 26 is constant space).
```java
class Solution {
    public boolean isAnagram(String s, String t) {
        if (s.length() != t.length()) return false;
        
        int[] counts = new int[26];
        
        // Add for s, subtract for t
        for (int i = 0; i < s.length(); i++) {
            counts[s.charAt(i) - 'a']++;
            counts[t.charAt(i) - 'a']--;
        }
        
        // If it's an anagram, all counts will be back to 0
        for (int count : counts) {
            if (count != 0) return false;
        }
        return true;
    }
}
```

### 2. Ransom Note
**Concept:** Count the letters in the magazine, see if you have enough for the note. Time: O(N+M), Space: O(1).
```java
class Solution {
    public boolean canConstruct(String ransomNote, String magazine) {
        int[] letters = new int[26];
        
        // Count what we have in the magazine
        for (char c : magazine.toCharArray()) {
            letters[c - 'a']++;
        }
        
        // Try to write the ransom note
        for (char c : ransomNote.toCharArray()) {
            if (letters[c - 'a'] == 0) return false; // Not enough letters!
            letters[c - 'a']--;
        }
        
        return true;
    }
}
```

### 3. First Unique Character in a String
**Concept:** Count frequencies, then loop again to find the first one with a count of 1. Time: O(N), Space: O(1).
```java
class Solution {
    public int firstUniqChar(String s) {
        int[] counts = new int[26];
        
        for (char c : s.toCharArray()) {
            counts[c - 'a']++;
        }
        
        for (int i = 0; i < s.length(); i++) {
            if (counts[s.charAt(i) - 'a'] == 1) {
                return i;
            }
        }
        
        return -1;
    }
}
```

### 4. Intersection of Two Arrays
**Concept:** Use two sets to find common elements. Time: O(N+M), Space: O(N+M).
```java
import java.util.HashSet;

class Solution {
    public int[] intersection(int[] nums1, int[] nums2) {
        HashSet<Integer> set1 = new HashSet<>();
        for (int num : nums1) set1.add(num);
        
        HashSet<Integer> intersect = new HashSet<>();
        for (int num : nums2) {
            if (set1.contains(num)) {
                intersect.add(num);
            }
        }
        
        // Convert HashSet back to Array
        int[] result = new int[intersect.size()];
        int index = 0;
        for (int num : intersect) {
            result[index++] = num;
        }
        return result;
    }
}
```

### 5. Word Pattern
**Concept:** Mapping letters to words, ensuring it's a 1-to-1 map. Time: O(N), Space: O(N).
```java
import java.util.HashMap;

class Solution {
    public boolean wordPattern(String pattern, String s) {
        String[] words = s.split(" ");
        if (words.length != pattern.length()) return false;
        
        HashMap<Character, String> charToWord = new HashMap<>();
        HashMap<String, Character> wordToChar = new HashMap<>();
        
        for (int i = 0; i < pattern.length(); i++) {
            char c = pattern.charAt(i);
            String word = words[i];
            
            if (!charToWord.containsKey(c)) charToWord.put(c, word);
            if (!wordToChar.containsKey(word)) wordToChar.put(word, c);
            
            if (!charToWord.get(c).equals(word) || wordToChar.get(word) != c) {
                return false; // Mismatch found!
            }
        }
        return true;
    }
}
```

### 6. Group Anagrams
**Concept:** Sort the string to create a unique Key, map that Key to a List of words. Time: O(N * K log K), Space: O(N * K).
```java
import java.util.*;

class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        HashMap<String, List<String>> map = new HashMap<>();
        
        for (String word : strs) {
            // Sort the word to create a universal key (e.g., "eat", "tea", "ate" -> "aet")
            char[] chars = word.toCharArray();
            Arrays.sort(chars);
            String sortedWord = new String(chars);
            
            // Add the original word to the list for that key
            if (!map.containsKey(sortedWord)) {
                map.put(sortedWord, new ArrayList<>());
            }
            map.get(sortedWord).add(word);
        }
        
        return new ArrayList<>(map.values());
    }
}
```
