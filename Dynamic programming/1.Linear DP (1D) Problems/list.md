Perfect Ajith! 🚀 Now let’s **map these problems to their LeetCode numbers** so you can practice them in the exact order (easy → harder).

---

# 🔹 Fibonacci / Linear DP (1D) Problems (with LeetCode IDs)

### 1. **Fibonacci Numbers**

* 📌 **LeetCode 509 – Fibonacci Number**
* Relation: `dp[i] = dp[i-1] + dp[i-2]`.

---

### 2. **Climbing Stairs**

* 📌 **LeetCode 70 – Climbing Stairs**
* Same as Fibonacci with different base cases.

---

### 3. **Min Cost Climbing Stairs**

* 📌 **LeetCode 746 – Min Cost Climbing Stairs**
* Transition: `dp[i] = cost[i] + min(dp[i-1], dp[i-2])`.

---

### 4. **House Robber (I & II)**

* 📌 **LeetCode 198 – House Robber (I)**
* 📌 **LeetCode 213 – House Robber II** (circular version)
* Transition: `dp[i] = max(dp[i-1], dp[i-2] + nums[i])`.

---

### 5. **Delete and Earn**

* 📌 **LeetCode 740 – Delete and Earn**
* Reduction of House Robber.

---

### 6. **N-th Tribonacci Number**

* 📌 **LeetCode 1137 – N-th Tribonacci Number**
* `dp[i] = dp[i-1] + dp[i-2] + dp[i-3]`.

---

### 7. **Jump Game (I & II)**

* 📌 **LeetCode 55 – Jump Game (I)**
* 📌 **LeetCode 45 – Jump Game II**
* Linear DP/Greedy hybrid.

---

### 8. **Paint Fence**

* 📌 **LeetCode 276 – Paint Fence**
* Constraint: no more than 2 adjacent same colors.

---

### 9. **Friends Pairing Problem**

* ❌ Not on LeetCode (on **GFG**: “Friends Pairing Problem”).
* Formula: `dp[i] = dp[i-1] + (i-1) * dp[i-2]`.

---

### 10. **Tiling Problems**

* 📌 **LeetCode 70 variant (2 x n tiling)** – Climbing stairs generalization.
* 📌 **LeetCode 790 – Domino and Tromino Tiling**.

---

✅ **Practice Order Recommendation**
Start with:
`509 → 70 → 746 → 198 → 213 → 740 → 1137 → 55 → 45 → 276 → 790 (+ GFG Friends Pairing)`

---

Ajith, do you want me to make a **practice sheet (with direct LeetCode links + difficulty level tags)** so you can track and grind them one by one?
