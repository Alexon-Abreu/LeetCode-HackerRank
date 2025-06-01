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

