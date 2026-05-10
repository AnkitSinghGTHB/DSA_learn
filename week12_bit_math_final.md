# 💡 Week 12: The Light Switch (Bit Manipulation & Math)

Welcome to the FINAL WEEK! 🎉🏆

You've made it through the hardest parts of DSA. This week, we cover the "nerdy" stuff that is actually quite simple once you see the patterns: Bits and Math.

---

## 🔘 Bit Manipulation (The Row of Light Switches)

Deep inside your computer, everything is just a row of light switches: **ON (1)** or **OFF (0)**.

**The XOR Cheat Code (`^`):**
XOR is like a weird light switch:
* If you flip it with the same value twice, it cancels out!
* `5 ^ 5 = 0`
* `5 ^ 0 = 5`

**Interview Trick:** If an array has every number appearing twice except for ONE lonely number, just XOR everything together. All the pairs will cancel each other out, leaving only the lonely number! 🪄

---

## 🧮 Interview Math (The Shortcut Formulas)

You don't need to be a calculus genius. You just need to know a few "shortcuts" that interviewers love.

**The Modulo operator (`%`):**
It's just the remainder. `10 % 3 = 1`. 
* **Use case:** To get the last digit of a number, do `num % 10`. To remove the last digit, do `num / 10`.

**Palindrome Numbers:**
To check if `121` is a palindrome without converting to a String:
1. Reverse the number (using the `% 10` and `/ 10` trick).
2. Check if `original == reversed`.

---

## 🎯 Your Mission (LeetCode Checklist)

1. [`Single Number`](https://leetcode.com/problems/single-number/) *(The XOR Magic Trick)*
2. [`Number of 1 Bits`](https://leetcode.com/problems/number-of-1-bits/) *(Counting ON switches)*
3. [`Reverse Bits`](https://leetcode.com/problems/reverse-bits/)
4. [`Palindrome Number`](https://leetcode.com/problems/palindrome-number/) *(The Math way!)*
5. [`Plus One`](https://leetcode.com/problems/plus-one/) *(Array/Math hybrid)*
6. [`Factorial Trailing Zeroes`](https://leetcode.com/problems/factorial-trailing-zeroes/) *(Medium - Hint: Count the 5s!)*

---

# 🎓 Graduation!

Congratulations, Coder! 🥳 

You have covered the core concepts of the **LeetCode Top Interview 150**. You are no longer on the couch—you are ready for the arena. 

**What's next?**
1. **Mock Interviews:** Practice talking out loud while you code.
2. **Review:** Go back to Week 1 every now and then to keep your memory fresh.
3. **Keep Coding:** The best way to stay sharp is to do 1 LeetCode problem a day.

**You've got this!** ☕💻🚀
