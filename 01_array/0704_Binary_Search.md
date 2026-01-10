# LC 704 - Binary Search

## Pattern
(Code Thoughts: Array / Binary Search)

---

## ❌ Why I got it wrong (first attempt)
- Off-by-one mistakes with `left`, `right`, and the loop condition
- Unsure whether `right` should be `len(nums) - 1` or `len(nums)`
- Forgot to move pointers correctly (risk of infinite loop)

---

## 🧠 Key mistake / mental gap
Binary search only works if I clearly commit to ONE interval definition:
- **Closed interval**: `[left, right]`
- **Half-open interval**: `[left, right)`

Mixing the two causes boundary bugs and missed targets.

---

## ✅ Correct idea
Use a **closed interval** `[left, right]`:

**Invariant**
- If the target exists, it is always within `[left, right]`.

**Update rule**
- If `nums[mid] < target`, discard left half: `left = mid + 1`
- If `nums[mid] > target`, discard right half: `right = mid - 1`
- If equal, return `mid`

Stop when the search space is empty: `left > right`.

---

## 🧩 Code skeleton (what I must remember)
```python
def search(nums, target):
    left, right = 0, len(nums) - 1  # [left, right]
    while left <= right:
        mid = (left + right) // 2
        if nums[mid] > target:
            right = mid - 1   
        elif nums[mid] < target:
            left = mid + 1
        else:
            return mid
    return -1
