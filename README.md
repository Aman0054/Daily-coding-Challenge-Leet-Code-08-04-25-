## 🧠 Intuition

We are given an array and are allowed to remove **3 elements from the front** of the array in one operation. Our goal is to make the array **distinct**, i.e., all elements are unique.

If we detect a duplicate in the array, then we know that **some portion of the front** must be removed to eliminate it. But instead of trying to remove exact duplicates one by one, we should find **the last duplicate when traversing from the back**, and then remove all elements before (and including) that index, rounded up to the nearest group of 3.

This works because:
- Elements at the back are "safe" as we move backward and build a set of seen elements.
- As soon as we hit a duplicate, we know the portion before it needs to be removed.
- We compute the **minimum number of 3-element removal operations** needed to eliminate that front portion.

---

## 🛠️ Approach

1. Use a boolean array `seen` to track which numbers we've encountered while traversing **backward**.
2. Start from the end of the array and move to the front:
   - If a number is already marked as `seen`, we’ve hit a **duplicate**.
   - At this point, compute how many operations are needed to remove all elements from the start **up to and including** this duplicate index. That is:  
     `operations = (i + 3) / 3`
3. If the loop completes without finding any duplicates, return 0.

This approach ensures we find the **minimum number of operations** required.

---

## ✅ Example

**Input:** `[1,2,3,4,2,3,3,5,7]`  
**Output:** `2`

- After 1st operation: `[4,2,3,3,5,7]`
- After 2nd operation: `[3,5,7]` → All distinct ✔️



## 💡 Time Complexity

- **Time:** O(n), where `n` is the length of the array.
- **Space:** O(1), since `seen` array is of fixed size (for values 0–100).

