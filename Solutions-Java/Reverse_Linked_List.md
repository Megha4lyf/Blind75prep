
# 🔁 Reverse Linked List

## 🧩 Problem Statement

Given the head of a singly linked list, reverse the list, and return the reversed list.

### 💡 Examples

#### ✅ Example 1:
**Input:** `head = [1,2,3,4,5]`  
**Output:** `[5,4,3,2,1]`  

#### ✅ Example 2:
**Input:** `head = [1,2]`  
**Output:** `[2,1]`  

#### ✅ Example 3:
**Input:** `head = []`  
**Output:** `[]`  

---

## 🔍 Approach

We use **iterative reversal** with three pointers:

- `prev` — initially `null`
- `curr` — starts at `head`
- `next` — stores `curr.next` to avoid breaking the chain

Each step points `curr.next` to `prev`, then shifts all pointers forward.

---

## 🧠 Java Code

```java
public ListNode reverseList(ListNode head) {
    if (head == null) {
        return head;
    }

    ListNode prev = null;
    ListNode curr = head;
    ListNode next = curr.next;

    while (curr != null) {
        curr.next = prev;
        prev = curr;
        curr = next;
        if (next != null) {
            next = curr.next;
        }
    }
    head = prev;
    return head;
}
```

---

## 📌 Key Takeaways

- **In-place reversal** of singly linked list using iterative method.
- Time Complexity: `O(n)`
- Space Complexity: `O(1)`

---

📘 You can visualize the pointer changes step-by-step to understand how each node’s direction is reversed.
