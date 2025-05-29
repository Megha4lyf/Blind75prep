
# 📈 Best Time to Buy and Sell Stock

**Difficulty**: Easy  
**Topic**: Array, Greedy  
**Leetcode Link**: [Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)

---

## 🧩 Problem Statement

You are given an array `prices` where `prices[i]` is the price of a given stock on the i-th day.

You want to maximize your profit by choosing a single day to **buy** one stock and choosing a different day **in the future** to **sell** that stock.

Return the **maximum profit** you can achieve from this transaction. If you cannot achieve any profit, return `0`.

---

## 🧪 Examples

### ✅ Example 1:

```
Input: prices = [7,1,5,3,6,4]
Output: 5

Explanation:
Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6 - 1 = 5.
```

### ❌ Example 2:

```
Input: prices = [7,6,4,3,1]
Output: 0

Explanation:
No transaction is done, max profit is 0.
```

---

## 🧠 Approach

- Initialize `min` as infinity and `maxProfit` as 0.
- Iterate through the price list.
- Track the lowest price seen so far (`min`).
- For each price, calculate `profit = current_price - min_price_so_far`.
- Update `maxProfit` if this profit is greater than the current `maxProfit`.

---

## ✅ Code (Java)

```java
class Solution {
    public int maxProfit(int[] prices) {
        
        int min = Integer.MAX_VALUE;
        int profit = 0, maxProfit = 0;

        for(int i = 0; i < prices.length; i++) {
            min = Math.min(min, prices[i]);
            profit = prices[i] - min;
            maxProfit = Math.max(maxProfit, profit);
        }

        return maxProfit;
    }
}
```

---

## 💡 Key Insights

- You must **buy before you sell**.
- The goal is to **maximize the difference** between selling and buying prices.
- A **greedy** single-pass solution is optimal here.

---

## 📊 Time & Space Complexity

- **Time Complexity**: O(n)
- **Space Complexity**: O(1)
