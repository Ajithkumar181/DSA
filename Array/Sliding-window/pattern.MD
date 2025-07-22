Great! The **Sliding Window Pattern** is a powerful technique for solving problems involving **arrays or strings** — especially those involving **subarrays, substrings, or sequences** with constraints (like size, sum, or distinct elements).

---

### ✅ **What Is the Sliding Window Pattern?**

The **Sliding Window** is a **subarray/subsequence technique** where you maintain a **"window" (a range of indices)** that slides over the input data.

---

### 🧠 **When to Use Sliding Window?**

Use it when the problem involves:

* Subarrays or substrings
* Fixed or variable window size
* Conditions like:

  * Sum
  * Max/Min
  * Frequency of elements
  * Number of distinct elements
  * Longest/Shortest subarray/substring

---

## 🪟 TYPES OF SLIDING WINDOWS

### 1. **Fixed Size Window**

* Window size is given
* You move the window forward by adding a new element and removing the old one

#### 🔸Example Problems:

* **Maximum sum subarray of size K**
* **Average of all subarrays of size K**

---

### 2. **Variable Size Window**

* Window size is not fixed — it changes depending on some condition
* Usually involves maintaining a condition like count of elements, sum, etc.

#### 🔸Example Problems:

* **Longest substring with K distinct characters**
* **Longest subarray with sum at most K**
* **Minimum window that contains all characters of another string**

---

## 🔁 Basic Sliding Window Template

### ➤ Fixed-size window

```cpp
int sum = 0;
int maxSum = 0;

for (int i = 0; i < k; i++) {
    sum += arr[i]; // first window
}
maxSum = sum;

for (int i = k; i < n; i++) {
    sum += arr[i] - arr[i - k]; // slide the window
    maxSum = max(maxSum, sum);
}
```

---

### ➤ Variable-size window

```cpp
int left = 0;

for (int right = 0; right < n; right++) {
    // expand the window

    while (condition is violated) {
        // shrink the window from the left
        left++;
    }

    // update answer if needed
}
```

---

## 🔥 Must-Solve Sliding Window Problems

| Type       | Problem                                                                                                                                     | Description                                 |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------- |
| ✅ Fixed    | [Maximum Sum Subarray of Size K](https://www.geeksforgeeks.org/find-maximum-minimum-sum-subarray-size-k/)                                   | Max sum in a window of size k               |
| ✅ Fixed    | [First Negative Integer in Every Window of Size K](https://leetcode.com/problems/first-negative-integer-in-every-window-of-size-k/)         | Track first negative element in each window |
| ✅ Variable | [Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/)             | Use set/hashmap to ensure no repeat         |
| ✅ Variable | [Longest Substring with At Most K Distinct Characters](https://leetcode.com/problems/longest-substring-with-at-most-k-distinct-characters/) | Hashmap of character counts                 |
| ✅ Variable | [Minimum Size Subarray Sum](https://leetcode.com/problems/minimum-size-subarray-sum/)                                                       | Find shortest subarray with sum ≥ target    |
| ✅ Variable | [Max Consecutive Ones III](https://leetcode.com/problems/max-consecutive-ones-iii/)                                                         | Flip at most K 0’s to 1’s                   |
| ✅ Variable | [Permutation in String](https://leetcode.com/problems/permutation-in-string/)                                                               | Check if s1 permutation is in s2            |

---

## 🧩 Practice Strategy

1. **Start with fixed-size window problems**
2. Understand the **window sliding logic**
3. Then go to **variable-size window problems** involving:

   * Hash maps (for frequencies)
   * Conditions (e.g. at most K distinct, sum constraints)

---

## 🧠 Tips for Mastery

* Always try a **brute-force O(n²)** solution first to understand.
* Then **optimize using a window**.
* Keep **prefix sum** in mind when needed.
* When dealing with characters/frequencies → use a **map or array of size 26**.

---

## 📝 Want a Learning Plan?

Let me know your pace (daily/weekly), and I’ll give you a **structured 5- or 7-day plan** with:

* Learning goals
* Daily problems (easy → medium → hard)
* Templates and tips

Would you like that?
