## 🔁 217. Contains Duplicate – Enhanced Explanation

> Given an integer array `nums`, return `true` if **any value appears at least twice** in the array, and `false` if **every element is distinct**.

---

### 📋 Problem Statement

Check if any duplicate value exists in the array.

---

### ✅ Example

#### Input:
```java
nums = [1, 2, 3, 1]
```
#### Output:
```java
true
```
#### Explanation:
The element `1` occurs at indices `0` and `3`.

---

### 💡 Intuition

We need a way to **track seen elements efficiently**.  
A **HashSet** or **HashMap** works well for constant-time lookups.

---

### 🔑 Java Solutions

#### ✅ HashSet – Concise Add Check

```java
public boolean containsDuplicate(int[] nums) {
    HashSet<Integer> hs = new HashSet<>();
    for (int n : nums) {
        if (!hs.add(n)) return true;
    }
    return false;
}
```

#### ✅ HashSet – Manual Contains Check

```java
public boolean containsDuplicate(int[] nums) {
    HashSet<Integer> hs = new HashSet<>();
    for (int n : nums) {
        if (hs.contains(n)) return true;
        else hs.add(n);
    }
    return false;
}
```

#### ✅ Sorting-Based Approach

```java
public boolean containsDuplicate(int[] nums) {
    Arrays.sort(nums);
    for (int i = 0; i < nums.length - 1; i++) {
        if (nums[i] == nums[i + 1]) return true;
    }
    return false;
}
```

#### ✅ HashMap – Key Check

```java
public boolean containsDuplicate(int[] nums) {
    HashMap<Integer, Integer> hm = new HashMap<>();
    for (int i = 0; i < nums.length; i++) {
        if (hm.containsKey(nums[i])) return true;
        else hm.put(nums[i], i);
    }
    return false;
}
```

#### ✅ HashMap – Count Tracker

```java
public boolean containsDuplicate(int[] nums) {
    int count = 0;
    HashMap<Integer, Integer> hm = new HashMap<>();
    for (int i = 0; i < nums.length; i++) {
        if (hm.containsKey(nums[i])) count++;
        else hm.put(nums[i], i);
    }
    return count > 0;
}
```

---

### 🧠 Summary of Approaches

| Approach        | Time Complexity | Space Complexity | Note |
|----------------|------------------|-------------------|------|
| HashSet (add)  | O(n)             | O(n)              | Most efficient |
| Sorting        | O(n log n)       | O(1)               | Destructive to original array |
| HashMap        | O(n)             | O(n)              | More verbose |

---

### 🖼️ Optional Diagram

<p align="center">
  <img src="../Images/contains-duplicate.png" width="500" alt="Contains Duplicate Logic"/>
</p>

---

### 🧠 Tip

- For real-time systems or streaming data, prefer **HashSet** due to its quick lookups.