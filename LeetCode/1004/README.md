# 1004. Max Consecutive Ones III (Medium)

Given a binary array `nums` and an integer `k`, return the maximum number of consecutive `1`'s in the array if you can flip at most `k` `0`'s.

#### Example 1:

```Python
Input: nums = [1,1,1,0,0,0,1,1,1,1,0], k = 2
Output: 6
Explanation: [1,1,1,0,0,1,1,1,1,1,1]
                        ^         ^
                        F         F
F = Flipped
```

#### Example 2:

```Python
Input: nums = [0,0,1,1,0,0,1,1,1,0,1,1,0,0,0,1,1,1,1], k = 3
Output: 10
Explanation: [0,0,1,1,1,1,1,1,1,1,1,1,0,0,0,1,1,1,1]
                      ^ ^       ^
                      F F       F
F = Flipped
```

#### Constraints:

`1 <= nums.length <= 10^5`

`nums[i] is either 0 or 1`

`0 <= k <= nums.length`

## My Solution

```Python
class Solution:
    def longestOnes(self, nums: List[int], k: int) -> int:
        left = curr = ans = 0
        
        for right in range(len(nums)):
            if nums[right] == 0:
                curr+=1
                
            while curr > k:
                if nums[left] == 0:
                    curr-=1
                left+=1
            
            ans = max(ans, right-left+1)
            
        return ans
```

## Explanation

The problem is essentially asking us to find the longest subarray that contains at most `k` `0`'s.

A great approach to use is the concept of a sliding window. As we move across the array we can keep track of how many `0`'s we've encountered.
If we reach our `k` limit of `0`'s, then the only way to remove any `0`'s is the shrink the window from the left side of the window.

And we essentially keeping doing this till we reach the end of the array, recording the length of the subarray at each iteration and storing the max.

So first I instantiated `left`, `curr`, and `ans` to 0. `left` will hold the index for the left bound of our window, `curr` hold the current amount of `0`'s we encounter, and `ans` will hold the maximum length of a subarray at each iteration.

In the first for loop we use `right` as our counter variable, and if `nums[right] == 0`, then we increment `curr` by 1.

While `curr > k`, if `nums[left] == 0`, then we should decrement `curr` and increment `left` by 1 regarless of if `nums[left] == 0` or not.

At the end of each interation, we set ans = to the max length of the subarray. By the end of the function, we'll return the length of the longest subarray that contains at most `k` `0`'s.