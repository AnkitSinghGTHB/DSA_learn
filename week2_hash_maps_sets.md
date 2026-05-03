# Week 2: The Magic Contacts List (Hash Maps & Sets)

If you only learn one data structure for interviews, **learn Hash Maps**. They are essentially cheat codes for algorithms.

## 📖 The Magic Contacts List
Imagine trying to find a friend's phone number in a giant, unorganized phone book by reading every single page. That would take `O(N)` time.

A **Hash Map** is like your phone's digital contacts list. You type in a name (the **Key**), and it instantly gives you the phone number (the **Value**) in `O(1)` time. 

A **Hash Set** is similar, but it only stores the Keys (no Values). It's just a VIP guest list. You ask "Is John on the list?" and it instantly replies "Yes" or "No".

---

## 🔑 Hash Maps in Java (HashMap)
In Java, we use `HashMap`. We have to declare the type of the Key and the type of the Value.

```java
import java.util.HashMap;

// Creating a HashMap where Keys are Strings (Names) and Values are Integers (Ages)
HashMap<String, Integer> contacts = new HashMap<>();

// 1. Adding items (Putting them in the map) -> O(1) time
contacts.put("Alice", 25);
contacts.put("Bob", 30);

// 2. Getting items -> O(1) time
int alicesAge = contacts.get("Alice"); 
System.out.println("Alice is " + alicesAge);

// 3. Checking if a Key exists -> O(1) time
if (contacts.containsKey("Bob")) {
    System.out.println("Bob's number is in the contacts!");
}

// 4. Overwriting a value
contacts.put("Alice", 26); // Happy Birthday Alice!
```

## 🚫 Hash Sets in Java (HashSet)
Use a `HashSet` when you just want to keep track of things you've already seen, ensuring there are no duplicates.

```java
import java.util.HashSet;

HashSet<String> guestList = new HashSet<>();

// 1. Adding guests
guestList.add("Alice");
guestList.add("Bob");
guestList.add("Alice"); // Has no effect! Alice is already on the list.

// 2. Checking if someone is on the list -> O(1) time
if (guestList.contains("Bob")) {
    System.out.println("Let Bob in.");
}
```

## 🧠 Core Pattern: The "Have I seen this before?" Trick
This is the most common pattern in all of DSA. You loop through an array, and at each step, you ask your HashMap/HashSet if you've seen the required matching piece before.

**Example Logic (Two Sum):**
You are looking for two numbers that add up to 10. 
You see a `3`. You instantly ask your HashMap: "Hey, have you seen a `7` earlier?" 
If yes, you win! If no, you put the `3` in the HashMap and move to the next number.

### 🎯 Your Practice Checklist (LeetCode)
1. `Valid Anagram`
2. `Ransom Note`
3. `First Unique Character in a String`
4. `Intersection of Two Arrays`
5. `Word Pattern`
6. `Group Anagrams` (Medium)
