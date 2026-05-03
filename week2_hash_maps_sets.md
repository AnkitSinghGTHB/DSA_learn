# 🪄 Week 2: The Magic Contacts List (Hash Maps & Sets)

Welcome to Week 2! 🎉

If you only remember *one* thing for your future coding interviews, make it this week. **Hash Maps are basically cheat codes.** They show up everywhere.

Let's break them down. 👇

---

## 📖 The "Why": Hash Maps vs. Searching

Imagine trying to find your friend "Alex" in a giant, unorganized physical phone book. You'd have to read every single page until you found the name. That takes **O(N)** time. Yuck. 🐢

Now, think about your smartphone's contact app. You just type "Alex" (the **Key**), and it instantly spits out the phone number (the **Value**). That takes **O(1)** time. Magic! ⚡

> [!NOTE]  
> **Hash Map:** A digital contacts list. You put in a Key, you instantly get a Value.
> **Hash Set:** A VIP Guest List. There are no values, just Keys. You simply ask, *"Is Alex on the list?"* and it instantly says YES or NO.

---

## 🗺️ Hash Maps in Java (`HashMap`)

In Java, we have to be specific. We must declare what type of data the Key is, and what type the Value is.

```java
import java.util.HashMap;

// Let's create our Contacts App! 
// Keys = Strings (Names), Values = Integers (Ages)
HashMap<String, Integer> contacts = new HashMap<>();

// 1. Adding people to our contacts (O(1) time ⚡)
contacts.put("Alice", 25);
contacts.put("Bob", 30);

// 2. Looking someone up (O(1) time ⚡)
int alicesAge = contacts.get("Alice"); 
System.out.println("Alice is " + alicesAge + " years old!");

// 3. Checking if someone exists before we call them!
if (contacts.containsKey("Bob")) {
    System.out.println("Yup, we have Bob's number.");
}

// 4. Overwriting a value (Happy Birthday Alice!)
contacts.put("Alice", 26); 
```

---

## 🚫 Hash Sets in Java (`HashSet`)

Don't care about ages or phone numbers? Just want to know who showed up to the party? Use a `HashSet`! It completely ignores duplicates.

```java
import java.util.HashSet;

// Let's create our VIP Guest List!
HashSet<String> guestList = new HashSet<>();

// 1. Adding guests at the door
guestList.add("Alice");
guestList.add("Bob");

// Wait, Alice tries to sneak in again wearing a fake mustache...
guestList.add("Alice"); 
// 🛑 Access Denied! The HashSet knows she's already inside. It ignores this.

// 2. Checking the list (O(1) time ⚡)
if (guestList.contains("Bob")) {
    System.out.println("Right this way, Bob.");
}
```

---

## 🧠 The Core Interview Pattern: "Have I seen this before?"

This is the ultimate trick. 
You are looping through an array. At every single step, you ask your HashMap or HashSet: **"Hey, have I seen this piece before?"**

**Example (Two Sum):**
You need two numbers that add up to 10. 
1. You see a `3`. 
2. You instantly ask your HashMap: *"Hey, have you seen a `7` earlier?"* 
3. If yes, you win! 🏆 If no, you throw the `3` into the HashMap to remember it for later, and move on.

---

## 🎯 Your Mission (LeetCode Checklist)
Time to use those cheat codes! 

1. `Valid Anagram`
2. `Ransom Note`
3. `First Unique Character in a String`
4. `Intersection of Two Arrays`
5. `Word Pattern`
6. `Group Anagrams` *(Medium - This one is tricky, check the solution if stuck!)*
