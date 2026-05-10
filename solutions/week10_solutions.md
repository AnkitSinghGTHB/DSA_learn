# Week 10 Solutions: Heaps & Tries

### 1. Kth Largest Element in an Array
**Concept:** Use a Min-Heap of size K. The top of the heap will be the Kth largest.
```java
import java.util.PriorityQueue;

class Solution {
    public int findKthLargest(int[] nums, int k) {
        PriorityQueue<Integer> heap = new PriorityQueue<>();
        for (int num : nums) {
            heap.add(num);
            if (heap.size() > k) {
                heap.poll(); // Remove the smallest to keep only the largest K
            }
        }
        return heap.peek();
    }
}
```

### 2. Implement Trie (Prefix Tree)
**Concept:** A node with an array of 26 children (for a-z).
```java
class Trie {
    class Node {
        Node[] children = new Node[26];
        boolean isEndOfWord = false;
    }
    
    Node root = new Node();

    public void insert(String word) {
        Node curr = root;
        for (char c : word.toCharArray()) {
            if (curr.children[c - 'a'] == null) {
                curr.children[c - 'a'] = new Node();
            }
            curr = curr.children[c - 'a'];
        }
        curr.isEndOfWord = true;
    }

    public boolean search(String word) {
        Node node = find(word);
        return node != null && node.isEndOfWord;
    }

    public boolean startsWith(String prefix) {
        return find(prefix) != null;
    }
    
    private Node find(String str) {
        Node curr = root;
        for (char c : str.toCharArray()) {
            if (curr.children[c - 'a'] == null) return null;
            curr = curr.children[c - 'a'];
        }
        return curr;
    }
}
```
