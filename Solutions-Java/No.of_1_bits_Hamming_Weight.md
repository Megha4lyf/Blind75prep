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

### 🔑 Java Code

```Java
public int hammingWeight(int n) {
        int count=0;
        String s= Integer.toBinaryString(n);
        for(int i=0; i<s.length(); i++){
            if(s.charAt(i)=='1'){
                count++;
            }
        }
        return count;
        
    }
```
using Brute force, converted int to binary string and found no.of 1's by charAt operation.
Time complexity: O(n)
Space complexity: O(1)

---

### 🧠 Bit Manipulation Optimization

```Java
public int hammingWeight(int n) {
       int count=0;
       while(n>0){
            count= count+ n%2;
            n=n/2;
        }
        return count;
        
    }
```
This solution works on bits and we get the solution with time complexity like O(log n) as each iteration we are cutting into half
Space complexity: O(1)

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

