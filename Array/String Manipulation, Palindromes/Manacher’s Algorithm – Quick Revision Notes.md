Here’s a **quick revision sheet** for your Manacher’s algorithm implementation, with **concept**, **dry run**, and **time/space complexity**.

---

## **Manacher’s Algorithm – Quick Revision Notes**

### **Purpose**

Find the **longest palindromic substring** in **O(n)** time by expanding around centers in a *transformed* string (with sentinels to handle even/odd lengths uniformly).

---

### **Key Steps**

1. **Transform the string**:
   Insert `#` between characters, and `^` / `$` as boundaries to avoid bounds checking.
   Example: `"babad"` → `"^#b#a#b#a#d#$"`

2. **p\[i]**:
   Stores radius of palindrome centered at index `i` in transformed string.

3. **mirror index**:
   `mirror = 2 * center - i` (mirrored position of `i` across `center`).

4. **Initialization from mirror**:
   If `i < right`, set:

   ```
   p[i] = min(right - i, p[mirror])
   ```

5. **Expand**:
   While characters match on both sides, increase `p[i]`.

6. **Update right boundary**:
   If `i + p[i] > right`, update `center = i`, `right = i + p[i]`.

7. **Track max length**:
   Keep `len` (max radius) and `st` (center index of longest palindrome).

8. **Map back to original string**:

   ```
   start = (st - len) / 2
   return s.substr(start, len)
   ```

---

### **Dry Run – Example `"babad"`**

**Transformed:**

```
t = ^#b#a#b#a#d#$
index: 0 1 2 3 4 5 6 7 8 9 10 11 12
```

**Steps:**

| i   | char | mirror | p\[i] init | expand    | p\[i] final | center | right | len | st  |
| --- | ---- | ------ | ---------- | --------- | ----------- | ------ | ----- | --- | --- |
| 2   | b    | -2     | 0          | b==b      | 1           | 2      | 3     | 1   | 2   |
| 4   | a    | 0      | 0          | a==a,b==b | 3           | 4      | 7     | 3   | 4   |
| 6   | b    | 2      | 1          | a==a      | 3           | 6      | 9     | 3   | 4   |
| 8   | a    | 4      | 1          | stop      | 1           |        |       | 3   | 4   |
| ... | ...  | ...    | ...        | ...       | ...         | ...    | ...   | ... | ... |

**Mapping back:**

```
start = (4 - 3) / 2 = 0
substring = "bab"
```

---

### **Dry Run – Example `"cbbd"`**

**Transformed:**

```
t = ^#c#b#b#d#$
index: 0 1 2 3 4 5 6 7 8 9 10
```

**Steps:**

| i | char | mirror | p\[i] init | expand | p\[i] final | center | right | len | st |
| - | ---- | ------ | ---------- | ------ | ----------- | ------ | ----- | --- | -- |
| 4 | b    | 0      | 0          | match  | 1           | 4      | 5     | 1   | 4  |
| 5 | #    | 3      | 0          | bb     | 2           | 5      | 7     | 2   | 5  |

**Mapping back:**

```
start = (5 - 2) / 2 = 1
substring = "bb"
```

---

### **Time Complexity**

* **O(n)** — Each character is visited at most twice (once in mirror check, once in expansion).

### **Space Complexity**

* **O(n)** — Transformed string + `p` array.

---

If you want, I can make a **colored visual diagram** showing how the expansion works for each `i`, so you can instantly recall the process during interviews. That can make Manacher’s algorithm stick in your mind permanently.
