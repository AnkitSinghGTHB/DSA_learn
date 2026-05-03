# Week 3 Solutions: Linked Lists & Two Pointers

Here are the Java solutions for the Week 3 practice problems.

### 1. Reverse String
**Concept:** Two Pointers swapping characters. Time: O(N), Space: O(1).
```java
class Solution {
    public void reverseString(char[] s) {
        int left = 0;
        int right = s.length - 1;
        
        while (left < right) {
            // Swap!
            char temp = s[left];
            s[left] = s[right];
            s[right] = temp;
            
            left++;
            right--;
        }
    }
}
```

### 2. Valid Palindrome
**Concept:** Two Pointers ignoring non-alphanumeric chars. Time: O(N), Space: O(1).
```java
class Solution {
    public boolean isPalindrome(String s) {
        int left = 0, right = s.length() - 1;
        
        while (left < right) {
            while (left < right && !Character.isLetterOrDigit(s.charAt(left))) left++;
            while (left < right && !Character.isLetterOrDigit(s.charAt(right))) right--;
            
            if (Character.toLowerCase(s.charAt(left)) != Character.toLowerCase(s.charAt(right))) {
                return false;
            }
            left++;
            right--;
        }
        return true;
    }
}
```

### 3. Middle of the Linked List
**Concept:** Fast and Slow Pointers. Time: O(N), Space: O(1).
```java
class Solution {
    public ListNode middleNode(ListNode head) {
        ListNode slow = head;
        ListNode fast = head;
        
        // Fast moves twice as fast as slow
        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
        }
        
        return slow; // When fast hits the end, slow is in the middle!
    }
}
```

### 4. Merge Two Sorted Lists
**Concept:** Creating a dummy node and threading the smaller values. Time: O(N+M), Space: O(1).
```java
class Solution {
    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
        ListNode dummy = new ListNode(-1);
        ListNode current = dummy;
        
        while (list1 != null && list2 != null) {
            if (list1.val <= list2.val) {
                current.next = list1;
                list1 = list1.next;
            } else {
                current.next = list2;
                list2 = list2.next;
            }
            current = current.next;
        }
        
        // Attach any remaining nodes
        if (list1 != null) current.next = list1;
        if (list2 != null) current.next = list2;
        
        return dummy.next;
    }
}
```

### 5. Reverse a Linked List
**Concept:** Three pointers (prev, current, next) to reverse the arrows. Time: O(N), Space: O(1).
```java
class Solution {
    public ListNode reverseList(ListNode head) {
        ListNode prev = null;
        ListNode current = head;
        
        while (current != null) {
            ListNode nextTemp = current.next; // Save the map!
            current.next = prev;              // Reverse the arrow!
            prev = current;                   // Move prev forward
            current = nextTemp;               // Move current forward
        }
        
        return prev; // Prev becomes the new head
    }
}
```

### 6. Linked List Cycle
**Concept:** Fast and Slow Pointers. If there's a loop, the fast runner will lap the slow runner. Time: O(N), Space: O(1).
```java
public class Solution {
    public boolean hasCycle(ListNode head) {
        ListNode slow = head;
        ListNode fast = head;
        
        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
            
            if (slow == fast) {
                return true; // They met on the track! Cycle found.
            }
        }
        return false;
    }
}
```

### 7. Remove Nth Node From End of List
**Concept:** Two Pointers. Give the fast pointer a head start of N steps. Time: O(N), Space: O(1).
```java
class Solution {
    public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode dummy = new ListNode(0);
        dummy.next = head;
        ListNode fast = dummy;
        ListNode slow = dummy;
        
        // Give fast a head start
        for (int i = 0; i <= n; i++) {
            fast = fast.next;
        }
        
        // Move both until fast hits the end
        while (fast != null) {
            slow = slow.next;
            fast = fast.next;
        }
        
        // Skip the node
        slow.next = slow.next.next;
        
        return dummy.next;
    }
}
```
