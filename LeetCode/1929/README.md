# 1929. Concatenation of Array (Easy)

Given an integer array `nums` of length `n`, you want to create an array `ans` of length `2n` where `ans[i] == nums[i]` and `ans[i + n] == nums[i]` for `0 <= i < n` **(0-indexed)**.

Specifically, `ans` is the **concatenation** of two `nums` arrays.

Return the *array* `ans`.

#### Example 1:

```Python
Input: nums = [1,2,1]
Output: [1,2,1,1,2,1]
Explanation: The array ans is formed as follows:
- ans = [nums[0],nums[1],nums[2],nums[0],nums[1],nums[2]]
- ans = [1,2,1,1,2,1]
```

#### Example 2:

```Python
Input: nums = [1,3,2,1]
Output: [1,3,2,1,1,3,2,1]
Explanation: The array ans is formed as follows:
- ans = [nums[0],nums[1],nums[2],nums[3],nums[0],nums[1],nums[2],nums[3]]
- ans = [1,3,2,1,1,3,2,1]
```

#### Constraints:

`n == nums.length`

`1 <= n <= 1000`

`1 <= nums[i] <= 1000`

## My Solution

```Python
class Solution:
    def getConcatenation(self, nums: List[int]) -> List[int]:
        n = len(nums)
        ans = [0] * (2*n)
        ans = nums * 2

        return ans
```

## Thought Process

The goal is to concatenate two `num` arrays in order and have that stored in another array called `ans` and return `ans`...

well for this we can just multiply the `nums` array by 2, and that would give us the value of two `nums` array.
    for ex: `nums` = [1,2,3], after doing `nums * 2`, `nums` = [1,2,3,1,2,3]

so all we have to do is create an array called `ans`, and set its length to twice the 
size of the `nums` array.

then store `nums * 2` inside the `ans` array.