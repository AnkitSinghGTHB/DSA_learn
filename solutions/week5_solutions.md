# Week 5 Solutions: Trees & Recursion

Here are the Java solutions for the Week 5 practice problems.

### 1. Maximum Depth of Binary Tree
**Concept:** DFS Recursion. The depth is 1 + the max of the left and right subtrees. Time: O(N), Space: O(H) where H is the height of the tree.
```java
class Solution {
    public int maxDepth(TreeNode root) {
        if (root == null) return 0;
        
        int leftDepth = maxDepth(root.left);
        int rightDepth = maxDepth(root.right);
        
        return Math.max(leftDepth, rightDepth) + 1;
    }
}
```

### 2. Invert Binary Tree
**Concept:** DFS Recursion. Swap the left and right children of every node. Time: O(N), Space: O(H).
```java
class Solution {
    public TreeNode invertTree(TreeNode root) {
        if (root == null) return null;
        
        // Swap left and right
        TreeNode temp = root.left;
        root.left = root.right;
        root.right = temp;
        
        // Recursively invert the rest
        invertTree(root.left);
        invertTree(root.right);
        
        return root;
    }
}
```

### 3. Same Tree
**Concept:** Compare roots, then recursively compare the left subtrees and right subtrees. Time: O(N), Space: O(H).
```java
class Solution {
    public boolean isSameTree(TreeNode p, TreeNode q) {
        // Both null? They are the same.
        if (p == null && q == null) return true;
        // Only one is null, or values don't match? Not the same.
        if (p == null || q == null || p.val != q.val) return false;
        
        // Check the branches
        return isSameTree(p.left, q.left) && isSameTree(p.right, q.right);
    }
}
```

### 4. Symmetric Tree
**Concept:** Similar to Same Tree, but we check if the left branch mirrors the right branch. Time: O(N), Space: O(H).
```java
class Solution {
    public boolean isSymmetric(TreeNode root) {
        if (root == null) return true;
        return isMirror(root.left, root.right);
    }
    
    private boolean isMirror(TreeNode t1, TreeNode t2) {
        if (t1 == null && t2 == null) return true;
        if (t1 == null || t2 == null || t1.val != t2.val) return false;
        
        // Notice the cross-matching: left with right, right with left
        return isMirror(t1.left, t2.right) && isMirror(t1.right, t2.left);
    }
}
```

### 5. Diameter of Binary Tree
**Concept:** The diameter passing through a node is `leftDepth + rightDepth`. Keep track of the maximum seen globally. Time: O(N), Space: O(H).
```java
class Solution {
    int maxDiameter = 0;
    
    public int diameterOfBinaryTree(TreeNode root) {
        getDepth(root);
        return maxDiameter;
    }
    
    private int getDepth(TreeNode node) {
        if (node == null) return 0;
        
        int left = getDepth(node.left);
        int right = getDepth(node.right);
        
        // Update the global maximum diameter
        maxDiameter = Math.max(maxDiameter, left + right);
        
        return Math.max(left, right) + 1;
    }
}
```

### 6. Subtree of Another Tree
**Concept:** DFS to find a matching root, then use `isSameTree` to verify. Time: O(N * M), Space: O(H).
```java
class Solution {
    public boolean isSubtree(TreeNode root, TreeNode subRoot) {
        if (root == null) return false;
        if (isSame(root, subRoot)) return true;
        
        return isSubtree(root.left, subRoot) || isSubtree(root.right, subRoot);
    }
    
    private boolean isSame(TreeNode p, TreeNode q) {
        if (p == null && q == null) return true;
        if (p == null || q == null || p.val != q.val) return false;
        return isSame(p.left, q.left) && isSame(p.right, q.right);
    }
}
```

### 7. Lowest Common Ancestor of a Binary Search Tree
**Concept:** Use the BST property (Left is smaller, Right is larger). If both nodes are smaller, go left. If both are larger, go right. Otherwise, you found the split point (the LCA)! Time: O(H), Space: O(1).
```java
class Solution {
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        TreeNode current = root;
        
        while (current != null) {
            if (p.val < current.val && q.val < current.val) {
                current = current.left;
            } else if (p.val > current.val && q.val > current.val) {
                current = current.right;
            } else {
                return current; // Found the split point
            }
        }
        return null;
    }
}
```
