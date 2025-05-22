## 🔁 Linked List Cycle – Enhanced Explanation

> Given the `head` of a linked list, determine if the linked list has a **cycle** in it.

---

### 📋 Problem Statement

A cycle occurs when a node's `next` pointer points back to a previous node, causing an infinite loop.  
We need to check if **any such cycle** exists.

---

### 🔍 Example

#### ✅ Example 1:
```
Input: head = [3,2,0,-4], pos = 1  
Output: true  
Explanation: Node -4 points back to node at index 1 (value = 2)
```

#### ✅ Example 2:
```
Input: head = [1,2], pos = 0  
Output: true
```

#### ❌ Example 3:
```
Input: head = [1], pos = -1  
Output: false
```

---

### 💡 Intuition

Use the **Floyd’s Tortoise and Hare algorithm**:
- Two pointers: one slow and one fast.
- The fast pointer moves two steps at a time, and the slow one moves one step.
- If they ever meet, a cycle exists.
- If fast reaches the end (`null`), then no cycle.

---

### 🔑 Java Code

```java
public boolean hasCycle(ListNode head) {
    ListNode fast = head;
    ListNode slow = head;

    while (fast != null && fast.next != null) {
        fast = fast.next.next;
        slow = slow.next;

        if (fast == slow) {
            return true;
        }
    }

    return false;
}
```

---

### 🧠 Why It Works

In a cyclic list, the fast pointer will eventually **lap** the slow pointer due to different speeds.  
It’s like two runners on a circular track — the faster runner will eventually catch up.

---

### 🖼️ Visual Diagram

<p align="center">
  <img src="../Images/linkedlist-cycle.png" width="500" alt="Linked List Cycle Detection"/>
</p>

---

### 📊 Time & Space Complexity

| Type         | Complexity        |
|--------------|-------------------|
| Time         | O(n)              |
| Space        | O(1)              |

- Constant space, no need for extra data structures like HashSets.

---

### ✅ Tip

This is one of the most efficient cycle detection algorithms for linked structures!