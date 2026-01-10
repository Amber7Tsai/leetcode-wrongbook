# LC 027 - Remove Element

## Pattern
(Code Thoughts: Array / Linked List / Hash Table / Two Pointers / …)

---

## ❌ Why I got it wrong (first attempt)
- I read C++ solutions but got confused when translating them into Python `while` loops.
- I was unsure where to put `fast += 1` and `slow += 1`, which led to skipping elements or overwriting wrong positions.
- I treated `slow` like a normal index instead of a **write pointer**.

---

## 🧠 Key mistake / mental gap
- I did not clearly define what `fast` and `slow` represent.
- I mixed up the **loop structure** (C++ `for`) with Python `while`, which caused off-by-one and pointer-movement errors.

---

## ✅ Correct idea
- Arrays are **contiguous** — deleting means **overwriting**, not removing.
- `fast` is the **reader** that scans every element.
- `slow` is the **writer** that points to the **next position to write a valid element**.
- When `nums[fast]` is valid, write it to `nums[slow]`, then move `slow`.
- `fast` must move **after** the current element is processed.

---

## 🧩 Code skeleton (what I must remember),i can also try for i in range()
```python
fast = 0
slow = 0
n = len(nums)

while fast < n:            # same as: for (fast = 0; fast < n; fast++)
    if nums[fast] is valid:
        nums[slow] = nums[fast]   # write first
        slow += 1                # then move write pointer
    fast += 1                    # move read pointer (for-loop increment)
return slow
