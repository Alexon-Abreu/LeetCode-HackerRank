# 1480. Running Sum of 1d Array (Easy)

Given an array `nums`. We define a running sum of an array as `runningSum[i] = sum(nums[0]…nums[i])`.

Return the running sum of `nums`.

#### Example 1:

```Python
Input: nums = [1,2,3,4]
Output: [1,3,6,10]
Explanation: Running sum is obtained as follows: [1, 1+2, 1+2+3, 1+2+3+4].
```

#### Example 2:

```Python
Input: nums = [1,1,1,1,1]
Output: [1,2,3,4,5]
Explanation: Running sum is obtained as follows: [1, 1+1, 1+1+1, 1+1+1+1, 1+1+1+1+1].
```

#### Example 3:

```Python
Input: nums = [3,1,2,10,1]
Output: [3,4,6,16,17]
```

#### Constraints:

`1 <= nums.length <= 1000`

`-10^6 <= nums[i] <= 10^6`

## My Solution

```Python
class Solution:
    def runningSum(self, nums: List[int]) -> List[int]:
        prefix = [nums[0]]
        
        for i in range(1, len(nums)):
            prefix.append(prefix[-1] + nums[i])
        
        return prefix
```

## Explanation

To get the running sum of a 1d array, we can a prefix sum algorithm.

In a prefix sum algo, each element is a sum of all elements that came before it.

We start creating an array called `prefix` and initialize it with the first element in `nums`, nums[0].

