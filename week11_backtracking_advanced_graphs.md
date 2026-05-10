# 🧭 Week 11: The Maze Runner (Backtracking & Advanced Graphs)

Welcome to Week 11! 🎉

This week, we learn how to explore all possibilities (Backtracking) and how to handle complex connections (Union-Find).

---

## 🏃 Backtracking (The "Oops, Wrong Way" Method)

Imagine you are in a giant maze. You walk until you hit a dead end. What do you do? 
You go back one step and try the *other* path. That is **Backtracking**.

**The Pattern:**
1. **Choose:** Pick a path.
2. **Explore:** Walk down that path.
3. **Un-choose:** If it's a dead end, step back and "reset" so you can try a different choice.

**When to use it:** 
When asked for *"all possible combinations,"* *"all permutations,"* or *"solve this Sudoku."*

### 💻 Java Template
```java
public void solveMaze(int x, int y) {
    if (foundExit) return; // Base Case
    
    // 1. Choose (Mark this spot as visited)
    visited[x][y] = true;
    
    // 2. Explore (Try all directions)
    solveMaze(x + 1, y);
    solveMaze(x - 1, y);
    
    // 3. Un-choose (CLEAN UP! Remove the mark so other paths can use it)
    visited[x][y] = false;
}
```

---

## 🤝 Union-Find (The "Friend of a Friend" System)

Imagine a giant party. You want to know if two people, Alice and Zack, are in the same friend group. 
Alice knows Bob, Bob knows Charlie... Charlie knows Zack. Yup, they are connected!

**Union-Find** (also called Disjoint Set Union) helps us:
1. **Union:** Join two people into the same group.
2. **Find:** Ask, *"Who is the leader of your group?"*

If two people have the same leader, they are in the same group!

---

## 🎯 Your Mission (LeetCode Checklist)

1. [`Letter Combinations of a Phone Number`](https://leetcode.com/problems/letter-combinations-of-a-phone-number/) *(Backtracking Basic)*
2. [`Permutations`](https://leetcode.com/problems/permutations/) *(The Backtracking classic)*
3. [`Combinations`](https://leetcode.com/problems/combinations/)
4. [`Number of Islands`](https://leetcode.com/problems/number-of-islands/) *(Wait, we did this in Week 6! Try solving it with Union-Find this time for extra credit!)*
5. [`Surrounded Regions`](https://leetcode.com/problems/surrounded-regions/) *(Medium Graph/Backtracking)*

Almost there! The finish line is in sight. ☕💻
