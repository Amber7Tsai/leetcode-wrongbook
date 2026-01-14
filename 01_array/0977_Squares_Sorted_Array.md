# LC 977 Squares of a Sorted Array

## Pattern
(Code Thoughts: Array / Two Pointers)

---

## ❌ Why I got it wrong (first attempt)
- I was confused why two pointers on left/right side will be faster than check each num by order
- I am still really struggle with the unfamiller python grammer.
- I didn't sure the Time Complexity O(N) means, and the built in sorted founction got me.

---

## 🧠 Key mistake / mental gap
 - I didn’t separate **algorithmic idea** (two pointers selecting the next square) from **output formatting** (reverse at the end).
 - I didn't understand why i should two pointer to solve this problem

---

## ✅ Correct idea
- Squaring breaks the original sorted order because negative numbers become positive.
- The largest square must come from one of the two ends: `nums[left]` or `nums[right]`.
- Use two pointers:
  - Compare `abs(nums[left])` vs `abs(nums[right])`
  - Append the larger square (this produces a descending result)
- Final reverse is acceptable because we’re returning a new array (not required to be in-place).

**Invariant / pattern**
- At each step, we place (or append) the next **largest** square from the current window `[left, right]`.
- After choosing one end, we shrink the window by moving that pointer inward.

---

## 🧩 Code skeleton (what I must remember)
```python
left, right = 0, len(nums) - 1
res = []

while left <= right:
    if abs(nums[left]) <= abs(nums[right]):
        res.append(nums[right] * nums[right])
        right -= 1
    else:
        res.append(nums[left] * nums[left])
        left += 1

return res[::-1]   # OK here: problem allows extra space; this is just formatting