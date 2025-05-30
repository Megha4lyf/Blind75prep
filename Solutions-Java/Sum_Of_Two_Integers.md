
# 🧠 Sum of Two Integers (Without Using `+` or `-` Operators)

### 🚀 Problem Statement

Given two integers `a` and `b`, return the sum of the two integers **without using** the operators `+` and `-`.

---

### 📥 Example Inputs & Outputs

#### ✅ Example 1:

**Input:**  
```  
a = 1, b = 2  
```  
**Output:**  
```  
3  
```

#### ✅ Example 2:

**Input:**  
```  
a = 2, b = 3  
```  
**Output:**  
```  
5  
```

---

### 🧠 Approach

This solution makes use of **bitwise operations**.

- `XOR (^)` is used to compute the sum without carry.
- `AND (&)` followed by a left shift `<< 1` gives the carry.
- Repeat until there's no carry left.

---

### 🧾 Code (Java)

```java
class Solution {
    public int getSum(int a, int b) {
        while(b != 0){
            int temp = (a & b) << 1; // carry
            a = a ^ b; // sum without carry
            b = temp;  // assign carry for next iteration
        }
        return a;
    }
}
```

---

### 🎯 Visual Explanation

Here's a diagram illustrating the bitwise addition process:

<p align="center">
  <img src="../Images/sum of 2 integers.png" width="500" alt="Sum of Two Integers Diagram"/>
</p>

---

### 🧩 Constraints

- `-1000 <= a, b <= 1000`
- No use of `+` or `-` allowed
