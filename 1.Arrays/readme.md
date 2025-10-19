## Problem Description

You are given an array `nums` consisting of integers. Your task is to find the **largest element** in the array. The problem can be solved in multiple ways — below are three different implementations (`solve1`, `solve2`, and a class-based solution `Solution.largestElement`).

Each function aims to determine the maximum element in the given list.

---

## Sample Input and Output

### Example 1

**Input:**

```python
nums = [2, 3, 4, 6, 2]
```

**Output:**

```
6
6
6
```

**Explanation:**

* The maximum (largest) element in the array `[2, 3, 4, 6, 2]` is `6`.
* All three methods correctly identify and return this value.

---

## Approach Explanation

### **Method 1: solve1(nums)**

```python
def solve1(nums):
    n = len(nums)
    ans = -1
    for i in range(n):
        flag = False
        for j in range(n):
            if nums[i] >= nums[j]:
                continue
            else:
                flag = True
        if flag == False:
            ans = nums[i]
            break
    return ans
```

#### **Logic:**

* For every element `nums[i]`, check all other elements `nums[j]`.
* If there exists no element greater than `nums[i]`, then `nums[i]` is the largest.
* Return that element.

#### **Explanation:**

* Outer loop selects an element.
* Inner loop compares it with all other elements.
* If no larger element is found (`flag == False`), that means it is the maximum.

#### **Time Complexity:** O(n²)

#### **Space Complexity:** O(1)

---

### **Method 2: solve2(nums)**

```python
def solve2(nums):
    n = len(nums)
    ans = -1
    for i in range(n):
        flag = False
        for j in range(n):
            if nums[i] < nums[j]:
                flag = True
        if flag == False:
            ans = nums[i]
            break
    return ans
```

#### **Logic:**

* Similar to `solve1`, but instead of skipping larger elements, it directly checks whether a larger element exists.
* If no element greater than `nums[i]` is found, then that element is the largest.

#### **Time Complexity:** O(n²)

#### **Space Complexity:** O(1)

---

### **Method 3: Using Class Solution**

```python
class Solution:
    def largestElement(self, nums):
        n = len(nums)
        ans = float('-inf')
        for i in range(n):
            if nums[i] > ans:
                ans = nums[i]
        return ans
```

#### **Logic:**

* Initialize `ans` with negative infinity.
* Iterate through the array and update `ans` whenever a larger value is found.
* Return `ans` after traversing all elements.

#### **Time Complexity:** O(n)

#### **Space Complexity:** O(1)

---

## Summary

| Method                  | Approach Type                      | Time Complexity | Space Complexity | Remarks                                   |
| ----------------------- | ---------------------------------- | --------------- | ---------------- | ----------------------------------------- |
| solve1                  | Double loop (compare all pairs)    | O(n²)           | O(1)             | Simple brute force                        |
| solve2                  | Double loop (find greater element) | O(n²)           | O(1)             | Slightly different logic, same efficiency |
| Solution.largestElement | Single traversal                   | O(n)            | O(1)             | Most efficient and optimal solution       |

