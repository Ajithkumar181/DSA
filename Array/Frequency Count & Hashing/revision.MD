Let’s **solve and dry run** the first two problems from the 🔰 Easy list of Frequency Count & Hashing.

---

## ✅ **1. Count Frequencies in an Array (GFG)**

**🔗 Link:** [GFG Problem](https://www.geeksforgeeks.org/count-frequencies-elements-array-o1-extra-space-time/)

### 🧠 Problem:

Given an array of size `n` with elements in the range `1 to n`, count the **frequency of all elements from 1 to n** in-place (modify the input array to store frequency).

---

### 👨‍💻 Input:v

```cpp
arr = {2, 3, 2, 3, 5}
n = 5
```

### ✅ Expected Output:

```
0 2 2 0 1
// frequency of 1 to 5: 1 → 0, 2 → 2, 3 → 2, 4 → 0, 5 → 1
```

---

### ✅ Solution Idea (O(1) space):

```cpp
void countFrequencies(int arr[], int n) {
    // Decrease all values by 1 to convert to 0-indexed
    for (int i = 0; i < n; i++) arr[i]--;

    // Use elements as index to increment
    for (int i = 0; i < n; i++) {
        arr[arr[i] % n] += n;
    }

    // Print final frequencies
    for (int i = 0; i < n; i++) {
        cout << arr[i] / n << " ";
    }
}
```

---

### 🧪 Dry Run:

**Original:** `arr = {2, 3, 2, 3, 5}`
**Step 1 (Convert to 0-index):**
`arr = {1, 2, 1, 2, 4}`

**Step 2 (Frequency Count by Modulo Trick):**

| i | arr\[i] | arr\[arr\[i] % n] += n | Array after       |
| - | ------- | ---------------------- | ----------------- |
| 0 | 1       | arr\[1] += 5 → 2+5=7   | {1, 7, 1, 2, 4}   |
| 1 | 7       | arr\[2] += 5 → 1+5=6   | {1, 7, 6, 2, 4}   |
| 2 | 6       | arr\[1] += 5 → 7+5=12  | {1, 12, 6, 2, 4}  |
| 3 | 2       | arr\[2] += 5 → 6+5=11  | {1, 12, 11, 2, 4} |
| 4 | 4       | arr\[4] += 5 → 4+5=9   | {1, 12, 11, 2, 9} |

**Step 3 (Divide by n):**

```
arr[0] / 5 = 0
arr[1] / 5 = 12/5 = 2
arr[2] / 5 = 11/5 = 2
arr[3] / 5 = 2/5 = 0
arr[4] / 5 = 9/5 = 1
```

✅ Final Output: `0 2 2 0 1` ✅

---

## ✅ **2. Valid Anagram (LeetCode 242)**

**🔗 Link:** [LeetCode 242](https://leetcode.com/problems/valid-anagram/)

---

### 🧠 Problem:

Check if two strings are **anagrams** (same letters, same count).

---

### 👨‍💻 Input:

```cpp
s = "anagram"
t = "nagaram"
```

### ✅ Expected Output:

```
true
```

---

### ✅ Code (Using Frequency Array for lowercase letters):

```cpp
bool isAnagram(string s, string t) {
    if (s.length() != t.length()) return false;

    int freq[26] = {0};

    for (char c : s)
        freq[c - 'a']++;

    for (char c : t)
        freq[c - 'a']--;

    for (int count : freq)
        if (count != 0) return false;

    return true;
}
```

---

### 🧪 Dry Run:

**s = "anagram"**
**t = "nagaram"**

#### Step 1: Frequency after `s`

```
a → +3
n → +1
g → +1
r → +1
m → +1
```

`freq = [3,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,1,0,0,0,0,0,0,0,0]`

#### Step 2: Frequency after `t`

Decrement:

* n → 1 → 0
* a → 3 → 2 → 1 → 0
* g → 1 → 0
* r → 1 → 0
* m → 1 → 0

**All counts become 0 → ✅ True**

---

### ✅ Final Output:

```cpp
true
```

---

## ✅ Summary:

| Problem                    | Approach                | Key Concept      |
| -------------------------- | ----------------------- | ---------------- |
| Count Frequencies in Array | In-place, mod trick     | Index hashing    |
| Valid Anagram              | Frequency array \[0–25] | Char count match |

Want me to continue dry running **Medium level** next?
Here are the **dry runs** for the 🟡 Medium-level Frequency Count & Hashing problems, broken down step-by-step for clear understanding:

---

## ✅ **3. Subarray Sum Equals K**

**🔗 LeetCode 560:** [Link](https://leetcode.com/problems/subarray-sum-equals-k/)
**Pattern:** Prefix Sum + HashMap

---

### 🧠 Problem:

Given an array and an integer `k`, return the total number of subarrays whose sum equals `k`.

---

### 👨‍💻 Input:

```cpp
nums = {1, 2, 3}, k = 3
```

### ✅ Expected Output:

```
2  // subarrays: [1,2] and [3]
```

---

### ✅ Code:

```cpp
int subarraySum(vector<int>& nums, int k) {
    unordered_map<int, int> prefixSumCount;
    prefixSumCount[0] = 1;  // base case
    int sum = 0, count = 0;

    for (int num : nums) {
        sum += num;
        count += prefixSumCount[sum - k];
        prefixSumCount[sum]++;
    }

    return count;
}
```

---

### 🧪 Dry Run:

| i | num | sum | sum - k | count | prefixSumCount           |
| - | --- | --- | ------- | ----- | ------------------------ |
|   |     | 0   |         | 0     | {0: 1}                   |
| 0 | 1   | 1   | -2      | 0     | {0: 1, 1: 1}             |
| 1 | 2   | 3   | 0       | 1     | {0: 1, 1: 1, 3: 1}       |
| 2 | 3   | 6   | 3       | 2     | {0: 1, 1: 1, 3: 1, 6: 1} |

✅ Final count: `2`

---

## ✅ **4. Longest Substring Without Repeating Characters**

**🔗 LeetCode 3:** [Link](https://leetcode.com/problems/longest-substring-without-repeating-characters/)
**Pattern:** Sliding Window + HashMap

---

### 🧠 Problem:

Find the length of the **longest substring** without repeating characters.

---

### 👨‍💻 Input:

```cpp
s = "abcabcbb"
```

### ✅ Expected Output:

```
3  // "abc"
```

---

### ✅ Code:

```cpp
int lengthOfLongestSubstring(string s) {
    unordered_map<char, int> indexMap;
    int maxLen = 0, start = 0;

    for (int end = 0; end < s.length(); end++) {
        if (indexMap.count(s[end])) {
            start = max(start, indexMap[s[end]] + 1);
        }
        indexMap[s[end]] = end;
        maxLen = max(maxLen, end - start + 1);
    }

    return maxLen;
}
```

---

### 🧪 Dry Run:

| end | s\[end] | indexMap           | start | maxLen |
| --- | ------- | ------------------ | ----- | ------ |
| 0   | 'a'     | {'a': 0}           | 0     | 1      |
| 1   | 'b'     | {'a':0, 'b':1}     | 0     | 2      |
| 2   | 'c'     | {'a':0, b:1, c:2}  | 0     | 3 ✅    |
| 3   | 'a'     | duplicate, start=1 | 1     | 3      |
| 4   | 'b'     | duplicate, start=2 | 2     | 3      |
| 5   | 'c'     | duplicate, start=3 | 3     | 3      |
| 6   | 'b'     | duplicate, start=4 | 4     | 3      |
| 7   | 'b'     | duplicate, start=5 | 5     | 3      |

✅ Final Output: `3`

---

## ✅ **5. Longest Consecutive Sequence**

**🔗 LeetCode 128:** [Link](https://leetcode.com/problems/longest-consecutive-sequence/)
**Pattern:** Set for Lookup (Hashing)

---

### 🧠 Problem:

Return the length of the **longest sequence of consecutive integers** in the array.

---

### 👨‍💻 Input:

```cpp
nums = {100, 4, 200, 1, 3, 2}
```

### ✅ Expected Output:

```
4  // longest sequence: 1, 2, 3, 4
```

---

### ✅ Code:

```cpp
int longestConsecutive(vector<int>& nums) {
    unordered_set<int> s(nums.begin(), nums.end());
    int longest = 0;

    for (int num : s) {
        if (!s.count(num - 1)) { // start of sequence
            int current = num;
            int streak = 1;

            while (s.count(current + 1)) {
                current++;
                streak++;
            }

            longest = max(longest, streak);
        }
    }

    return longest;
}
```

---

### 🧪 Dry Run:

**Set s = {100, 4, 200, 1, 3, 2}**

Iterating through each element:

* `100 → not in s(99)` → streak=1 ✅
* `4 → already part of 1` → skip
* `200 → not in s(199)` → streak=1
* `1 → not in s(0)` → start new streak

  * 2 → yes
  * 3 → yes
  * 4 → yes → streak=4 ✅
* `3, 2` → already in streak

✅ Final Output: `4`

---

## ✅ Summary Table:

| # | Problem                                | Output | Technique            |
| - | -------------------------------------- | ------ | -------------------- |
| 3 | Subarray Sum Equals K                  | 2      | Prefix sum + hashmap |
| 4 | Longest Substring Without Repeat Chars | 3      | Sliding window + map |
| 5 | Longest Consecutive Sequence           | 4      | Set-based lookup     |

---

Let's solve and dry run the 🔴 **Hard-level problems** involving **Frequency Count & Hashing** step by step.

---

## ✅ **6. Count Distinct Elements in Every Window of Size K**

**🔗 GFG Problem:** [Link](https://www.geeksforgeeks.org/count-distinct-elements-in-every-window-of-size-k/)
**Pattern:** Sliding Window + Frequency Map

---

### 🧠 Problem:

Given an array of size `n` and an integer `k`, find the **count of distinct elements in every window** of size `k`.

---

### 👨‍💻 Input:

```cpp
arr = {1, 2, 1, 3, 4, 2, 3}, k = 4
```

### ✅ Expected Output:

```
3 4 4 3
```

---

### ✅ Code:

```cpp
vector<int> countDistinctInWindow(vector<int>& arr, int k) {
    unordered_map<int, int> freq;
    vector<int> result;

    for (int i = 0; i < k; i++)
        freq[arr[i]]++;

    result.push_back(freq.size());

    for (int i = k; i < arr.size(); i++) {
        // Remove the element going out
        if (--freq[arr[i - k]] == 0)
            freq.erase(arr[i - k]);

        // Add the new element
        freq[arr[i]]++;

        result.push_back(freq.size());
    }

    return result;
}
```

---

### 🧪 Dry Run:

```
arr = {1, 2, 1, 3, 4, 2, 3}, k = 4
```

| Window     | Frequency Map        | Distinct Count |
| ---------- | -------------------- | -------------- |
| \[1,2,1,3] | {1:2, 2:1, 3:1}      | 3 ✅            |
| \[2,1,3,4] | {2:1, 1:1, 3:1, 4:1} | 4 ✅            |
| \[1,3,4,2] | {1:1, 3:1, 4:1, 2:1} | 4 ✅            |
| \[3,4,2,3] | {3:2, 4:1, 2:1}      | 3 ✅            |

✅ Final Output: `3 4 4 3`

---

## ✅ **7. Count Number of Nice Subarrays**

**🔗 LeetCode 1248:** [Link](https://leetcode.com/problems/count-number-of-nice-subarrays/)
**Pattern:** Prefix Sum + Hash Map

---

### 🧠 Problem:

Given `nums`, count the number of **subarrays with exactly `k` odd numbers.**

---

### 👨‍💻 Input:

```cpp
nums = {1, 1, 2, 1, 1}, k = 3
```

### ✅ Expected Output:

```
2  // [1,1,2,1], [1,2,1,1]
```

---

### ✅ Code:

```cpp
int numberOfSubarrays(vector<int>& nums, int k) {
    unordered_map<int, int> prefixCount;
    prefixCount[0] = 1;
    int odd = 0, result = 0;

    for (int num : nums) {
        if (num % 2 == 1) odd++;
        result += prefixCount[odd - k];
        prefixCount[odd]++;
    }

    return result;
}
```

---

### 🧪 Dry Run:

Convert to count of **odd numbers** prefix sum:

```
nums = {1, 1, 2, 1, 1}, k = 3

prefixCount = {0:1}
odd = 0, result = 0

Step by step:

i=0 → num=1 → odd=1
    result += prefixCount[-2] → 0
    prefixCount[1]++

i=1 → num=1 → odd=2
    result += prefixCount[-1] → 0
    prefixCount[2]++

i=2 → num=2 → odd=2
    result += prefixCount[-1] → 0
    prefixCount[2]++

i=3 → num=1 → odd=3
    result += prefixCount[0] = 1 → result=1 ✅
    prefixCount[3]++

i=4 → num=1 → odd=4
    result += prefixCount[1] = 1 → result=2 ✅
    prefixCount[4]++
```

✅ Final Output: `2`

---

## ✅ Summary Table

| # | Problem                                           | Output    | Pattern                   |
| - | ------------------------------------------------- | --------- | ------------------------- |
| 6 | Count Distinct Elements in Every Window of Size K | `3 4 4 3` | Sliding window + freq map |
| 7 | Count Number of Nice Subarrays                    | `2`       | Prefix sum + freq map     |

---

Would you like me to generate a **PDF or printable sheet** summarizing all easy + medium + hard dry runs in tabular form?
