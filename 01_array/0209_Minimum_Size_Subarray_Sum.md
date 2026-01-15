# LC 0209 Minimum Size Subarray Sum

## Pattern
(Code Thoughts: Sliding Window / Two Pointers)

---

## ❌ Why I got it wrong (first attempt)
- I didn’t immediately recognize this as a contiguous subarray problem

- I tried brute force (nested loops), which is O(n²) and times out

- I didn’t know when to move left vs right


---

## 🧠 Key mistake / mental gap
- I didn’t think in terms of a window representing a continuous range

- I misunderstood that once sum ≥ target, I should shrink, not expand

- I was thinking about “finding a sum” instead of minimizing window length
---

## ✅ Correct idea
- Use two pointers to maintain a window [left, right]

- right expands the window to make the sum large enough

- Once sum ≥ target, move left to shrink the window

- Every time the condition is met, update the minimum length

- This guarantees:

Every valid subarray is checked, and the shortest one is kept.

---

## 🧩 Code skeleton (what I must remember)
```python
class Solution: def minSubArrayLen(self, s: int, nums: List[int]) -> int: 
    l = len(nums) 
    left = 0 
    right = 0 
    min_len = float('inf') 
    cur_sum = 0 
    
    while right < l: 
        cur_sum += nums[right]
         
        while cur_sum >= s: 
             min_len = min(min_len, right - left + 1) 
             cur_sum -= nums[left] 
             left += 1 
        right += 1 

    return min_len if min_len != float('inf') else 0
