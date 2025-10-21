## Largest Element

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

## Index of the Largest Element

You are given an array `nums` consisting of integers. Your task is to find the **index of the largest element** in the array. If multiple elements share the maximum value, return the **index of the first occurrence**.

Two approaches (`solve1` and `solve2`) are implemented to solve this problem.

---

## Sample Input and Output

### Example 1

**Input:**

```python
nums = [3, 7, 8, 8, 4, 9, 2]
```

**Output:**

```
5
```

**Explanation:**

* The largest element in the array is `9`.
* Its index is `5` (0-based indexing).
* Hence, the output is `5`.

### Example 2

**Input:**

```python
nums = [2, 3, 4, 6, 8, 9, 5]
```

**Output:**

```
5
```

**Explanation:**

* The maximum element is `9`, which is located at index `5`.
* The function correctly returns this index.

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
            ans = i
            break
    return ans
```

#### **Logic:**

* For each element `nums[i]`, compare it with every other element `nums[j]`.
* If any number greater than `nums[i]` exists, set `flag = True`.
* If `flag` remains `False` after checking all elements, it means `nums[i]` is the largest.
* Return its index `i`.

#### **Example Trace:**

For `nums = [3, 7, 8, 8, 4, 9, 2]`:

* When `i = 5`, `nums[i] = 9`.
* No element is greater than 9, so `flag` stays `False`.
* Function returns index `5`.

#### **Time Complexity:** O(n²) — nested loops compare each element with every other.

#### **Space Complexity:** O(1) — uses constant extra space.

---

### **Method 2: solve2(nums)**

```python
def solve2(nums):
    n = len(nums)
    ans = float("-inf")
    for i in range(n):
        if nums[i] > ans:
            ans = i
    return ans
```

#### **Logic:**

* Initialize `ans` as negative infinity.
* Traverse the list once, updating `ans` to the index `i` whenever a larger element is found.
* Return the index of the largest element.

#### **Example Trace:**

For `nums = [2, 3, 4, 6, 8, 9, 5]`:

* `nums[0] = 2` → largest so far → index = 0
* `nums[1] = 3` → new largest → index = 1
* `nums[5] = 9` → new largest → index = 5
* Final answer = 5.

#### **Time Complexity:** O(n) — single traversal.

#### **Space Complexity:** O(1) — only uses constant space.

---
## Smallest Element

You are given an array `nums` consisting of integers. Your task is to find the **smallest element** in the array. The goal is to identify the minimum value using different approaches.

Three methods (`solve1`, `solve2`, and `solve3`) are implemented to achieve this.

---

## Sample Input and Output

### Example

**Input:**

```python
nums = [3, 4, 6, 5, 2, 9]
```

**Output:**

```
2
2
2
```

**Explanation:**

* The smallest element in the array `[3, 4, 6, 5, 2, 9]` is `2`.
* All three functions correctly return `2` as the minimum value.

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
            if nums[i] <= nums[j]:
                continue
            else:
                flag = True
        if flag == False:
            ans = nums[i]
            break
    return ans
```

#### **Logic:**

* For every element `nums[i]`, compare it with all other elements `nums[j]`.
* If a smaller number exists, mark `flag = True`.
* If no smaller number exists (i.e., `flag == False`), `nums[i]` is the smallest.
* Return that element.

#### **Example Trace:**

For `nums = [3, 4, 6, 5, 2, 9]`:

* When `i = 4`, `nums[i] = 2`.
* There is no element smaller than 2.
* The loop breaks and returns `2`.

#### **Time Complexity:** O(n²) — two nested loops comparing each pair.

#### **Space Complexity:** O(1) — uses only constant extra space.

---

### **Method 2: solve2(nums)**

```python
def solve2(nums):
    n = len(nums)
    ans = nums[0]
    for i in range(n):
        if nums[i] < ans:
            ans = nums[i]
    return ans
```

#### **Logic:**

* Initialize `ans` with the first element.
* Traverse through the array and update `ans` if a smaller value is found.
* Return the smallest value after the loop ends.

#### **Example Trace:**

For `nums = [3, 4, 6, 5, 2, 9]`:

* `ans = 3` initially.
* Compare with each element — when reaching `2`, update `ans = 2`.
* Final answer = 2.

#### **Time Complexity:** O(n) — single traversal.

#### **Space Complexity:** O(1).

---

### **Method 3: solve3(nums)**

```python
def solve3(nums):
    n = len(nums)
    ans = float("inf")
    for i in range(n):
        if nums[i] < ans:
            ans = nums[i]
    return ans
```

#### **Logic:**

* Initialize `ans` with positive infinity (`float('inf')`).
* Loop through all elements, updating `ans` whenever a smaller number is encountered.
* Return the smallest element after completion.

#### **Example Trace:**

For `nums = [3, 4, 6, 5, 2, 9]`:

* Start with `ans = ∞`.
* Sequentially update until smallest value found → `ans = 2`.
* Return 2.

#### **Time Complexity:** O(n)

#### **Space Complexity:** O(1)

---

🧩 Problem Description

You are given an array of integers nums.
Your task is to find the index of the smallest element in the array.
If multiple elements share the same smallest value, return the first occurrence (smallest index).
🧪 Sample Test Case
Example 1

Input:

nums = [4, 1, 2, 9]


Output:

1
⚙️ Approach Explanation
Method 1: Brute Force (solve1)
def solve1(nums):
    n = len(nums)
    ans = -1
    for i in range(n):
        flag = False
        for j in range(n):
            if nums[i] <= nums[j]:
                continue
            else:
                flag = True
        if flag == False:
            ans = i
            break
    return ans

🔍 Logic:

For each element nums[i], compare it with every other element nums[j].

If a smaller element exists, mark flag = True.

If no smaller element is found (flag == False), that means nums[i] is the smallest.

Return its index i.

🧾 Step-by-step Trace:

For nums = [4, 1, 2, 9]:

i	nums[i]	Comparison Result	flag	ans
0	4	Smaller element found (1 < 4)	True	-
1	1	No smaller element found	False	1

✅ Output = 1

⏱️ Time Complexity:

Outer loop → O(n)

Inner loop → O(n)

Total = O(n²)

💾 Space Complexity:

Only a few variables → O(1)

