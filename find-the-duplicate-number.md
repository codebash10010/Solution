# 🧩 Find the Duplicate Number

**Problem Statement:**  
Given an array of integers `nums` containing `n + 1` integers where each integer is in the range `[1, n]` inclusive, there is only one repeated number in `nums`. Return this repeated number.  
You must solve the problem **without modifying the array** and using **only constant extra space**.

---

## 📝 Input & Output

**Input:**  
- `nums`: An array of integers of length `n + 1` where all integers are within `[1, n]`.
- Exactly one integer appears more than once.

**Output:**  
- The single repeated integer.

---

## ✅ Examples

**Example 1:**
Explanation: Numbers are from 1 to 4. `2` appears twice.

**Example 2:**
Explanation: `3` appears twice.

**Example 3:**
Explanation: All elements are `3`.

---

## ⚙ Constraints
- Array length: `n + 1`
- Elements: `[1, n]`
- Only **one** repeated number
- No array modification
- **O(1)** extra space

---

## 💡 Approach – Floyd's Cycle Detection (Tortoise and Hare)
- Treat the array as a linked list where `nums[i]` points to `nums[nums[i]]`.
- Phase 1: Use two pointers (`slow`, `fast`) moving at different speeds to find an intersection.
- Phase 2: Reset `fast` to `nums[0]` and move both one step at a time until they meet again — the meeting point is the duplicate number.

**Time Complexity:** O(n)  
**Space Complexity:** O(1)

---

## 💻 Solutions

### C++
