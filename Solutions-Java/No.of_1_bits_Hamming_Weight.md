## 🧠 Number of 1 Bits (Hamming Weight) – Enhanced Explanation

> Given a **positive integer `n`**, return the number of **set bits (1s)** in its **binary representation**.

---

### 📋 Problem Statement

We need to compute the **Hamming weight** — i.e., the **count of 1s** in the binary form of a number.

---

### 🔍 Example

#### ✅ Example 1:
```
Input: n = 11
Binary: 1011
Output: 3
```

Explanation: The binary form of 11 is `1011`, which has three 1s.

---

### 💡 Intuition

We want to count how many bits are set to `1`.  
There are multiple ways to do this:
- Brute force: Convert to binary and count
- Bit manipulation: Efficient and elegant

---

### 🔑 Python Code

```python
def hammingWeight(n):
    count = 0
    while n:
        count += n & 1  # Add 1 if the last bit is set
        n >>= 1         # Right shift to move to the next bit
    return count
```

---

### 🧠 Bit Manipulation Optimization

```python
def hammingWeight(n):
    count = 0
    while n:
        n &= n - 1  # Removes the last set bit
        count += 1
    return count
```

💡 This uses **Brian Kernighan's Algorithm** to turn off the rightmost 1-bit in each iteration.

---

### 🧾 Dry Run (n = 11)

| Step | n (binary) | Operation     | count |
|------|------------|---------------|--------|
| 1    | 1011       | n & 1 = 1     | 1      |
| 2    | 0101       | n & 1 = 1     | 2      |
| 3    | 0010       | n & 1 = 0     | 2      |
| 4    | 0001       | n & 1 = 1     | 3      |
| 5    | 0000       | Loop ends     | 3 ✅    |

---

### 📊 Time & Space Complexity

| Type         | Brute Force         | Optimized (n & (n-1)) |
|--------------|---------------------|------------------------|
| Time         | O(log n)            | O(number of set bits) |
| Space        | O(1)                | O(1)                  |

---

### 🖼️ Diagram

<p align="center">
  <img src="../Images/hamming-weight.png" width="500" alt="Hamming Weight Diagram"/>
</p>