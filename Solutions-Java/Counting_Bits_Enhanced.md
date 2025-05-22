## 🧠 Counting Bits – Enhanced Explanation

> Given a **non-negative integer `n`**, return an array `ans` where `ans[i]` is the **number of 1's in the binary representation** of `i` for every `i` in the range `[0, n]`.

---

### 📋 Problem Statement

We need to create a list where each element at index `i` contains the **Hamming weight (number of set bits)** of the integer `i`.

---

### 🔍 Example

#### ✅ Example:
```
Input: n = 5
Output: [0,1,1,2,1,2]

Explanation:
0 --> 0000 --> 0  
1 --> 0001 --> 1  
2 --> 0010 --> 1  
3 --> 0011 --> 2  
4 --> 0100 --> 1  
5 --> 0101 --> 2
```

---

### 💡 Intuition

We are calculating the number of `1` bits for all integers from `0` to `n`.  
For each number, convert it to binary and count how many `1`s exist.

---

### 🔑 Java Code

```java
public int[] countBits(int n) {
    int arr[] = new int[n + 1];
    arr[0] = 0;
    for (int i = 1; i <= n; i++) {
        arr[i] = count(i);
    }
    return arr;
}

private int count(int number) {
    int sum = 0;
    while (number > 0) {
        sum = sum + number % 2;
        number = number / 2;
    }
    return sum;
}
```

---

### 📈 Optimization Tip

Instead of recalculating bits every time, we can use the pattern:
```java
arr[i] = arr[i >> 1] + (i & 1);
```
Where:
- `i >> 1` is `i / 2`
- `i & 1` checks if the last bit is `1`

This helps to **reuse** already computed results and achieves **O(n)** time.

---

### 🧾 Dry Run (n = 5)

| i  | Binary | Set Bits (1s) | Output Array |
|----|--------|----------------|---------------|
| 0  | 0000   | 0              | [0]           |
| 1  | 0001   | 1              | [0,1]         |
| 2  | 0010   | 1              | [0,1,1]       |
| 3  | 0011   | 2              | [0,1,1,2]     |
| 4  | 0100   | 1              | [0,1,1,2,1]   |
| 5  | 0101   | 2              | [0,1,1,2,1,2] |

---

### 📊 Time & Space Complexity

| Type         | Brute Force       | Optimized (DP)     |
|--------------|-------------------|---------------------|
| Time         | O(n log n)        | O(n)                |
| Space        | O(n)              | O(n)                |

---

### 🖼️ Diagram

<p align="center">
  <img src="../Images/counting-bits.png" width="500" alt="Counting Bits Diagram"/>
</p>