Absolutely! Here's your **step-by-step guide to learn, master, and solve problems** based on **Kadane’s Algorithm (Maximum Subarray Sum)** — from **beginner to expert level**.

---

# ✅ Step-by-Step Roadmap to Master Kadane's Algorithm

---

## 🔰 STEP 1: Understand the Problem Kadane Solves

### ❓ What’s the problem?

**Find the contiguous subarray (with at least one element) that has the maximum sum.**

### 🧠 Real-life analogy:

Imagine you have a graph of daily profits/losses. You want to find the best streak of days (continuous segment) where your profit is the highest.

---

## ✅ STEP 2: Learn the Algorithm with Explanation

### 🔍 Core Idea:

At every element, you have **2 choices**:

* Either **start a new subarray** from this element.
* Or **extend the previous subarray** by including this element.

Whichever gives a **higher sum**, you choose that.

### 📚 Kadane's Algorithm:

```cpp
int maxSubArray(vector<int>& nums) {
    int maxEndingHere = nums[0];
    int maxSoFar = nums[0];

    for (int i = 1; i < nums.size(); i++) {
        maxEndingHere = max(nums[i], maxEndingHere + nums[i]);
        maxSoFar = max(maxSoFar, maxEndingHere);
    }

    return maxSoFar;
}
```

---

### 🧪 Dry Run Example:

Let’s take: `nums = [-2, 1, -3, 4, -1, 2, 1, -5, 4]`

| Index | Element | maxEndingHere     | maxSoFar       |
| ----- | ------- | ----------------- | -------------- |
| 0     | -2      | -2                | -2             |
| 1     | 1       | max(1, -2+1) = 1  | max(-2, 1) = 1 |
| 2     | -3      | max(-3, 1-3) = -2 | max(1, -2) = 1 |
| 3     | 4       | max(4, -2+4) = 4  | max(1, 4) = 4  |
| 4     | -1      | max(-1, 4-1) = 3  | max(4, 3) = 4  |
| 5     | 2       | max(2, 3+2) = 5   | max(4, 5) = 5  |
| 6     | 1       | max(1, 5+1) = 6   | max(5, 6) = 6  |
| 7     | -5      | max(-5, 6-5) = 1  | max(6, 1) = 6  |
| 8     | 4       | max(4, 1+4) = 5   | max(6, 5) = 6  |

✅ Maximum Sum = `6` from subarray `[4, -1, 2, 1]`

---

## 🏋️‍♂️ STEP 3: Practice Basic Problems (Learn and Code)

1. ✅ **Leetcode 53 – Maximum Subarray**
   [🔗 Leetcode Link](https://leetcode.com/problems/maximum-subarray/)

2. ✅ **GFG - Kadane’s Algorithm**
   [🔗 GFG Link](https://practice.geeksforgeeks.org/problems/kadanes-algorithm-1587115620)

3. ✅ **Max sum subarray of size K** (Sliding Window)
   [🔗 GFG Link](https://practice.geeksforgeeks.org/problems/max-sum-subarray-of-size-k5313/1)

---

## ⚙️ STEP 4: Extend Kadane's Algorithm (Variants)

### 1. 🔁 Print the subarray

Track `start`, `end`, `s` (temp start):

```cpp
int maxSubArray(vector<int>& nums) {
    int start = 0, end = 0, s = 0;
    int maxSoFar = nums[0], maxEndingHere = nums[0];

    for (int i = 1; i < nums.size(); i++) {
        if (nums[i] > maxEndingHere + nums[i]) {
            maxEndingHere = nums[i];
            s = i;
        } else {
            maxEndingHere += nums[i];
        }

        if (maxSoFar < maxEndingHere) {
            maxSoFar = maxEndingHere;
            start = s;
            end = i;
        }
    }

    cout << "Subarray: ";
    for(int i = start; i <= end; i++)
        cout << nums[i] << " ";

    return maxSoFar;
}
```

---

### 2. 🔁 Circular Maximum Subarray

For arrays where subarrays can wrap around end to start.

**Formula:**

```cpp
maxSum = max(Kadane(arr), totalSum - Kadane(minSubarray))
```

---

### 3. ⚡ Maximum Product Subarray (Leetcode 152)

Similar idea but maintain both max and min (because of negative \* negative = positive).

---

## 🔥 STEP 5: Master Level Problems

| Problem Name                           | Platform      | Variant               |
| -------------------------------------- | ------------- | --------------------- |
| Maximum Sum Rectangle                  | GFG           | 2D Kadane             |
| Best Time to Buy and Sell Stock        | Leetcode 121  | Kadane on price diffs |
| Maximum Subarray Sum with One Deletion | Leetcode 1186 | Dynamic Kadane        |
| Maximum Circular Subarray              | Leetcode 918  | Circular Kadane       |
| Maximum Subarray of Size K             | GFG           | Sliding Window        |

---

## 🧪 STEP 6: Test Yourself

✅ Try writing the algorithm **without help**

✅ Try explaining it to a friend or using your own words

✅ Solve these 5 challenge problems:

* Print all subarrays with max sum
* Circular subarray with all negatives
* Max product subarray
* 2D Kadane
* Max subarray with one deletion allowed

---

## 🎯 Final Goal: Intuition + Implementation Mastery

| Concept             | Mastery Goal               |
| ------------------- | -------------------------- |
| Kadane Basic        | ✅ Can code without looking |
| Track Subarray      | ✅ Print indices or values  |
| Circular Case       | ✅ Handle wrap-around       |
| Product Variant     | ✅ Handle negative/zero     |
| Advanced DP variant | ✅ One deletion / Two split |

---

## 🧠 Summary Chart

| Step | What to Do            | Output                     |
| ---- | --------------------- | -------------------------- |
| 1    | Understand basic idea | Kadane logic clear         |
| 2    | Code + dry run basic  | No syntax error            |
| 3    | Solve basic problems  | ✅ AC in LeetCode/GFG       |
| 4    | Learn variants        | Can solve circular/product |
| 5    | Hard problems         | Solve at least 3 advanced  |
| 6    | Practice + recall     | Full mastery               |

---

Absolutely! Here's your **well-structured and visually clear guide** to mastering **Kadane’s Algorithm**, complete with a **level-wise curated problem set**, learning path, and optional add-ons.

---

# 🧠 Mastering Kadane’s Algorithm – Structured Problem Roadmap

## 🔰 Step-by-Step Learning Path

| Step | Focus Area                         | What You Learn                      |
| ---- | ---------------------------------- | ----------------------------------- |
| 1️⃣  | Understand the core problem        | Contiguous subarray with max sum    |
| 2️⃣  | Implement basic Kadane’s algorithm | Handle positive + negative arrays   |
| 3️⃣  | Track start and end indices        | Print subarray with max sum         |
| 4️⃣  | Handle circular subarrays          | Kadane + totalSum – minSubarray     |
| 5️⃣  | Product-based variations           | Maintain max & min (negatives)      |
| 6️⃣  | Apply Kadane in 2D                 | Max sum rectangle in matrix         |
| 7️⃣  | Advanced dynamic variants          | Deletion allowed, bounded max, etc. |

---

## ✅ Kadane’s Algorithm – Curated Problem Set

### 🟢 Level 1: **Basic Kadane (Foundation)**

| No. | Problem Name                     | Platform    | Tags         | Difficulty |
| --- | -------------------------------- | ----------- | ------------ | ---------- |
| 1   | Maximum Subarray                 | LeetCode 53 | Basic Kadane | Easy       |
| 2   | Kadane’s Algorithm               | GFG         | Basic Logic  | Easy       |
| 3   | Contiguous Subarray with Max Sum | HackerRank  | Warm-up      | Easy       |

---

### 🟡 Level 2: **Print / Track Subarray**

| No. | Problem Name                | Platform      | Tags                  | Difficulty |
| --- | --------------------------- | ------------- | --------------------- | ---------- |
| 4   | Print Subarray with Max Sum | Custom Code   | Kadane + Indices      | Medium     |
| 5   | Subarray with Maximum Sum   | Coding Ninjas | Track start/end index | Medium     |

---

### 🟠 Level 3: **Kadane Variants**

| No. | Problem Name                       | Platform      | Tags                    | Difficulty |
| --- | ---------------------------------- | ------------- | ----------------------- | ---------- |
| 6   | Maximum Circular Subarray          | LeetCode 918  | Kadane + Min Subarray   | Medium     |
| 7   | Maximum Product Subarray           | LeetCode 152  | Track min & max product | Medium     |
| 8   | Max Subarray Sum with One Deletion | LeetCode 1186 | Dynamic Programming     | Hard       |

---

### 🔵 Level 4: **Real-Life Applications**

| No. | Problem Name                       | Platform     | Tags                  | Difficulty |
| --- | ---------------------------------- | ------------ | --------------------- | ---------- |
| 9   | Best Time to Buy and Sell Stock    | LeetCode 121 | Kadane on price diffs | Easy       |
| 10  | Best Time to Buy and Sell Stock II | LeetCode 122 | Greedy variation      | Medium     |

---

### 🔴 Level 5: **2D Kadane & Matrix**

| No. | Problem Name                    | Platform     | Tags                | Difficulty |
| --- | ------------------------------- | ------------ | ------------------- | ---------- |
| 11  | Maximum Sum Rectangle in Matrix | GFG          | 2D Kadane           | Hard       |
| 12  | Maximum Sum Submatrix           | LeetCode 363 | Kadane + Prefix Sum | Hard       |

---

### 🟣 Level 6: **Special Patterns / Advanced**

| No. | Problem Name                             | Platform     | Tags                  | Difficulty |
| --- | ---------------------------------------- | ------------ | --------------------- | ---------- |
| 13  | Minimum Subarray Length with Sum ≥ K     | LeetCode 209 | Sliding Window        | Medium     |
| 14  | Number of Subarrays with Bounded Maximum | LeetCode 795 | Count Valid Subarrays | Medium     |
| 15  | Largest Sum Subarray of Size at least K  | GFG          | Kadane + Window Size  | Medium     |

---

## 📌 Practice Plan by Skill Level

| Skill Level        | What to Solve         |
| ------------------ | --------------------- |
| 🧑‍🎓 Beginner     | Problems 1 – 3        |
| 👨‍💻 Intermediate | Problems 1 – 8        |
| 🧙 Mastery         | Solve all 15 problems |

---

## 🎁 Optional Add-ons (Free – Say Yes to Get Them)

| Add-on Name                       | What It Provides                        |
| --------------------------------- | --------------------------------------- |
| 📅 5-Day Challenge Plan           | Daily set of problems to solve in order |
| 📝 Printable Cheatsheet (PDF)     | Kadane algorithm + variants in 1 page   |
| 📊 Visual Notes (Diagrams + Flow) | Illustration of logic and dry runs      |

---

Would you like me to generate:

* ✅ A **5-day challenge** using this list?
* ✅ A **printable cheatsheet**?
* ✅ **Visual slides/notes** on variants like circular or 2D Kadane?

Let me know how you’d like to continue!
