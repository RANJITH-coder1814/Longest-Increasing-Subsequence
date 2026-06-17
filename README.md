# Longest-Increasing-Subsequence
Given an integer array nums, return the length of the longest strictly increasing subsequence.  A subsequence is a sequence that can be derived from an array by deleting some or no elements without changing the order of the remaining elements.
# Longest Increasing Subsequence

## Problem Statement

Given an integer array `nums`, return the length of the longest strictly increasing subsequence.

A subsequence is a sequence that can be derived from an array by deleting some or no elements without changing the order of the remaining elements.

---

## Example 1

Input:
```text
nums = [10,9,2,5,3,7,101,18]
```

Output:
```text
4
```

Explanation:
```text
The longest increasing subsequence is [2,3,7,101].
Length = 4
```

---

## Example 2

Input:
```text
nums = [0,1,0,3,2,3]
```

Output:
```text
4
```

---

## Example 3

Input:
```text
nums = [7,7,7,7,7,7,7]
```

Output:
```text
1
```

---

## Approach

This solution uses a greedy strategy with binary search.

- Maintain a vector `temp`.
- For each number in the array:
  - Use `lower_bound()` to find the first element greater than or equal to the current number.
  - If no such element exists, append the number.
  - Otherwise, replace that element with the current number.
- The size of `temp` represents the length of the Longest Increasing Subsequence.

---

## Algorithm

1. Create an empty vector `temp`.
2. Traverse each element in `nums`.
3. Find its position using `lower_bound`.
4. If position is at the end, insert the element.
5. Otherwise replace the element at that position.
6. Return `temp.size()`.

---

## C++ Solution

```cpp
class Solution {
public:
    int lengthOfLIS(vector<int>& nums) {
        vector<int> temp;

        for (int num : nums) {
            auto it = lower_bound(temp.begin(), temp.end(), num);

            if (it == temp.end()) {
                temp.push_back(num);
            } else {
                *it = num;
            }
        }

        return temp.size();
    }
};
```

---

## Complexity Analysis

### Time Complexity
```text
O(n log n)
```

- `n` iterations through the array.
- Each `lower_bound()` operation takes `O(log n)` time.

### Space Complexity
```text
O(n)
```

- Extra vector `temp` is used.

---

## Topics

- Array
- Dynamic Programming
- Binary Search
- Greedy

---

## LeetCode

**Problem #300 - Longest Increasing Subsequence**
