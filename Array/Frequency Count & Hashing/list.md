Here is a **structured and comprehensive guide** to **mastering Frequency Count & Hashing in arrays**, perfectly formatted for revision, interviews, and daily practice:

---

# 🧠 Mastering Frequency Count & Hashing in Arrays

Mastering **Frequency Count & Hashing** in arrays is *crucial* for solving a wide range of **DSA problems** efficiently, especially those involving:

✔️ Element counts
✔️ Duplicates
✔️ Subarrays
✔️ Prefix sum and sliding windows

---

## 🔑 What is Frequency Count & Hashing?

A technique to **count occurrences** of elements in arrays or strings using **hash tables** like:

* `unordered_map`, `map` (in C++ / Java)
* Arrays (for fixed ranges like a–z)

---

## 🔧 Step-by-Step Guide to Master

### ✅ 1. Understand the Basic Idea

Use frequency maps when you're asked to:

* Count how many times something appears
* Find duplicates
* Check if something exists quickly

#### 📌 Example 1 – Hash Map

```cpp
unordered_map<int, int> freq;
for (int x : arr) {
    freq[x]++;
}
```

#### 📌 Example 2 – Frequency Array (for lowercase letters)

```cpp
int freq[26] = {0};
for (char c : s) {
    freq[c - 'a']++;
}
```

---

### ✅ 2. Learn the Key Use Cases

| Use Case                     | Example Problem                     |
| ---------------------------- | ----------------------------------- |
| Count frequency              | GFG: Count Frequencies in Array     |
| Majority element             | LeetCode 169: Majority Element      |
| Detect duplicates            | LeetCode 442: Find All Duplicates   |
| Check anagram                | LeetCode 242: Valid Anagram         |
| Subarray sum with constraint | LeetCode 560: Subarray Sum Equals K |
| Pair with given sum          | LeetCode 1: Two Sum                 |

---

## 🔁 Common Patterns with Code

### 🔹 Pattern 1: Basic Frequency Count

```cpp
unordered_map<int, int> freq;
for (int num : nums)
    freq[num]++;
```

---

### 🔹 Pattern 2: Fixed-Size Hashing

```cpp
int count[26] = {0};
for (char ch : str)
    count[ch - 'a']++;
```

---

### 🔹 Pattern 3: Sliding Window + Hashing

Used in problems like:

* Longest substring without repeating characters
* Anagram finders
* Windowed frequency count

---

## 💯 Important Problems to Practice (in difficulty order)

### 🔰 Easy Level

| 🔢  | Problem                       | Concept                 | Link                                                                                               |
| --- | ----------------------------- | ----------------------- | -------------------------------------------------------------------------------------------------- |
| ✅ 1 | Count frequencies in an array | Basic counting          | [GFG Problem](https://www.geeksforgeeks.org/count-frequencies-elements-array-o1-extra-space-time/) |
| ✅ 2 | Valid Anagram                 | Frequency of characters | [LeetCode 242](https://leetcode.com/problems/valid-anagram/)                                       |

---

### 🟡 Medium Level

| 🔢  | Problem                                        | Concept                  | Link                                                                                        |
| --- | ---------------------------------------------- | ------------------------ | ------------------------------------------------------------------------------------------- |
| ✅ 3 | Subarray Sum Equals K                          | Prefix sum + hash map    | [LeetCode 560](https://leetcode.com/problems/subarray-sum-equals-k/)                        |
| ✅ 4 | Longest Substring Without Repeating Characters | Sliding window + hashmap | [LeetCode 3](https://leetcode.com/problems/longest-substring-without-repeating-characters/) |
| ✅ 5 | Longest Consecutive Sequence                   | Set-based lookup         | [LeetCode 128](https://leetcode.com/problems/longest-consecutive-sequence/)                 |

---

### 🔴 Hard Level

| 🔢  | Problem                                           | Concept                        | Link                                                                                            |
| --- | ------------------------------------------------- | ------------------------------ | ----------------------------------------------------------------------------------------------- |
| ✅ 6 | Count Distinct Elements in Every Window of Size K | Sliding window + frequency map | [GFG Problem](https://www.geeksforgeeks.org/count-distinct-elements-in-every-window-of-size-k/) |
| ✅ 7 | Count Number of Nice Subarrays                    | Prefix sum + frequency map     | [LeetCode 1248](https://leetcode.com/problems/count-number-of-nice-subarrays/)                  |

---

### 🔁 Optional Add-Ons (Complete Mastery)

| 🔢  | Problem                      | Concept             | Link                                                                        |
| --- | ---------------------------- | ------------------- | --------------------------------------------------------------------------- |
| ⭐ 8 | Top K Frequent Elements      | Hash map + min heap | [LeetCode 347](https://leetcode.com/problems/top-k-frequent-elements/)      |
| ⭐ 9 | Sort Characters by Frequency | Hashing + sorting   | [LeetCode 451](https://leetcode.com/problems/sort-characters-by-frequency/) |

---

## 🧠 Tips to Master the Topic

1. Practice `unordered_map` and frequency arrays with dry runs.
2. Always start with brute force, then optimize with hashing.
3. Learn when to use sliding window + hash vs prefix sum + hash.
4. Build your own **template snippets** for frequency-related logic.

---

## 📘 Quick Reference Snippets

### ✅ Frequency Map Template

```cpp
unordered_map<int, int> mp;
for (auto x : arr)
    mp[x]++;
```

### ✅ Character Count Template

```cpp
int freq[26] = {0};
for (char c : str)
    freq[c - 'a']++;
```

### ✅ Two Sum Check

```cpp
unordered_map<int, int> mp;
for (auto x : arr) {
    if (mp[k - x]) return true;
    mp[x]++;
}
```

---

## ✅ Final Checklist

✅ Cover all key patterns
✅ Practice at least 7 core problems
✅ Add 2 advanced ones for extra edge
✅ Master hash-based lookup, count, sliding window, and prefix sum

---

Let's now solve and dry run the ⭐ **Optional (Advanced)** Frequency Count & Hashing problems:

---

## ✅ **8. Top K Frequent Elements**

**🔗 LeetCode 347:** [Link](https://leetcode.com/problems/top-k-frequent-elements/)
**Pattern:** Frequency Map + Min Heap

---

### 🧠 Problem:

Given an array of integers `nums` and an integer `k`, return the `k` most frequent elements.

---

### 👨‍💻 Input:

```cpp
nums = {1, 1, 1, 2, 2, 3}, k = 2
```

### ✅ Expected Output:

```
[1, 2]  // 1 appears 3 times, 2 appears 2 times
```

---

### ✅ Code:

```cpp
vector<int> topKFrequent(vector<int>& nums, int k) {
    unordered_map<int, int> freq;
    for (int num : nums)
        freq[num]++;

    // Min heap of {frequency, number}
    priority_queue<pair<int, int>, vector<pair<int, int>>, greater<>> minHeap;

    for (auto& [num, f] : freq) {
        minHeap.push({f, num});
        if (minHeap.size() > k)
            minHeap.pop();
    }

    vector<int> result;
    while (!minHeap.empty()) {
        result.push_back(minHeap.top().second);
        minHeap.pop();
    }
    return result;
}
```

---

### 🧪 Dry Run:

```
nums = {1,1,1,2,2,3}, k = 2
```

**Step 1: Frequency Map**

```
{1:3, 2:2, 3:1}
```

**Step 2: Min Heap (size k=2)**

* Push (3,1) → heap = \[(3,1)]
* Push (2,2) → heap = \[(2,2), (3,1)]
* Push (1,3) → heap becomes \[(1,3), (3,1), (2,2)] → pop (1,3)

Heap now contains: `[(2,2), (3,1)]`

**Step 3: Extract**
→ Result = \[2, 1]

✅ Output: `[2, 1]` or `[1, 2]` (order doesn’t matter)

---

## ✅ **9. Sort Characters by Frequency**

**🔗 LeetCode 451:** [Link](https://leetcode.com/problems/sort-characters-by-frequency/)
**Pattern:** Frequency + Sorting

---

### 🧠 Problem:

Given a string `s`, sort it in descending order by character frequency.

---

### 👨‍💻 Input:

```cpp
s = "tree"
```

### ✅ Expected Output:

```
"eert" or "eetr"  // e appears twice
```

---

### ✅ Code:

```cpp
string frequencySort(string s) {
    unordered_map<char, int> freq;
    for (char c : s) freq[c]++;

    vector<pair<char, int>> freqList(freq.begin(), freq.end());

    // Sort by frequency descending
    sort(freqList.begin(), freqList.end(), [](auto& a, auto& b) {
        return a.second > b.second;
    });

    string result;
    for (auto& [ch, count] : freqList)
        result += string(count, ch);

    return result;
}
```

---

### 🧪 Dry Run:

```
s = "tree"
```

**Step 1: Frequency Map**

```
{'t':1, 'r':1, 'e':2}
```

**Step 2: Sorted list (by frequency)**

```
[('e',2), ('t',1), ('r',1)]
```

**Step 3: Build string**

```
"ee" + "t" + "r" = "eetr"
```

✅ Output: `"eetr"` (also valid: `"eert"`)

---

## ✅ Summary Table

| # | Problem                      | Output   | Pattern            |
| - | ---------------------------- | -------- | ------------------ |
| 8 | Top K Frequent Elements      | `[1, 2]` | HashMap + Min Heap |
| 9 | Sort Characters by Frequency | `"eetr"` | HashMap + Sorting  |

---

Would you like:

* 📄 A **PDF revision sheet** with all 9 dry runs (easy to hard)?
* 🧪 A **10-question DSA quiz** on this topic?
* 📊 An **Excel/Notion tracker** with your progress?

Let me know!

