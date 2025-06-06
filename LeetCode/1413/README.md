# 1413. Minimum Value to Get Positive Step by Step Sum (Easy)

Given an array of integers `nums`, you start with an initial **positive** value *startValue*.

In each iteration, you calculate the step by step sum of *startValue* plus elements in `nums` (from left to right).

Return the minimum **positive** value of `startValue` such that the step by step sum is never less than 1.

#### Example 1:

```Python
Input: nums = [-3,2,-3,4,2]
Output: 5
Explanation: If you choose startValue = 4, in the third iteration your step by step sum is less than 1.
step by step sum
startValue = 4 | startValue = 5 | nums
  (4 -3 ) = 1  | (5 -3 ) = 2    |  -3
  (1 +2 ) = 3  | (2 +2 ) = 4    |   2
  (3 -3 ) = 0  | (4 -3 ) = 1    |  -3
  (0 +4 ) = 4  | (1 +4 ) = 5    |   4
  (4 +2 ) = 6  | (5 +2 ) = 7    |   2
```

#### Example 2:

```Python
Input: nums = [1,2]
Output: 1
Explanation: Minimum start value should be positive.
```

#### Example 3:

```Python
Input: nums = [1,-2,-3]
Output: 5
```

#### Constraints:

`1 <= nums.length <= 100`

`-100 <= nums[i] <= 100`

## My Solution

```Python
class Solution:
    def minStartValue(self, nums: List[int]) -> int:
        minimum_value = total = 0

        for num in nums:
            total+=num
            minimum_value = min(minimum_value, total) # finding the smallest prefix sum in nums
        
        return -minimum_value + 1
```

## Explanation

Theres a myriad of ways to solving this problem, but I think a very clever way is to find the smallest `total` value encountered during the running sum.

If we know what the smallest `total` is, then we can take this value, negate it, add one to it, and use this as our `minStartValue`. This allows us to have a `minStartValue` that'll always result in a sum of 1 or greater throughout the iteration.

We start by setting `minimum_value` and `total` == 0, then initiate a for loop.

For each `num` in the `nums` list, we add `num` to `total`, `total+=num`. At each iteration, we check to see which if `total` is less than `minimum_value`, if so, set `minimum_value` = `total`, `minimum_value = min(minimum_value, total)`.

At the end we'll negate `minimum_value` and add 1 to it. That way we elimate the negative value to 0, and by adding 1 we ensure that we'll always have a positive `minimum_value`, whose step by step sum is never less than 1.