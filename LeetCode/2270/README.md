# 2270. Number of Ways to Split Array (Medium)

You are given a **0-indexed** integer array `nums` of length `n`.

`nums` contains a **valid split** at index `i` if the following are true:

The sum of the first `i + 1` elements is `greater than or equal to` the sum of the last `n - i - 1` elements.

There is **at least one** element to the right of `i`. That is, `0 <= i < n - 1`.

Return *the number of **valid splits** in `nums`*.

#### Example 1:

```Python
Input: nums = [10,4,-8,7]
Output: 2
Explanation: 
There are three ways of splitting nums into two non-empty parts:
- Split nums at index 0. Then, the first part is [10], and its sum is 10. The second part is [4,-8,7], and its sum is 3. Since 10 >= 3, i = 0 is a valid split.
- Split nums at index 1. Then, the first part is [10,4], and its sum is 14. The second part is [-8,7], and its sum is -1. Since 14 >= -1, i = 1 is a valid split.
- Split nums at index 2. Then, the first part is [10,4,-8], and its sum is 6. The second part is [7], and its sum is 7. Since 6 < 7, i = 2 is not a valid split.
Thus, the number of valid splits in nums is 2.
```

#### Example 2:

```Python
Input: nums = [2,3,1,0]
Output: 2
Explanation: 
There are two valid splits in nums:
- Split nums at index 1. Then, the first part is [2,3], and its sum is 5. The second part is [1,0], and its sum is 1. Since 5 >= 1, i = 1 is a valid split. 
- Split nums at index 2. Then, the first part is [2,3,1], and its sum is 6. The second part is [0], and its sum is 0. Since 6 >= 0, i = 2 is a valid split.
```

#### Constraints:

`2 <= nums.length <= 10^5`

`-10^5 <= nums[i] <= 10^5`

## My Solution

```Python
class Solution:
    def waysToSplitArray(self, nums: List[int]) -> int:
        ans = left = 0
        total = sum(nums)

        for i in range(len(nums) - 1):
            left += nums[i]
            right = total - left

            if left >= right:
                ans+=1
            
        return ans
```

## Explanation

The problem asks us to find how many time we can partition the array, such that the left side of the array is greater than the right.

To begin, I instantiated `ans` and `left` to 0. `ans` will hold the total number of valid partitions recorded, and `left` will hold the total sum of the left side. `total` is set to the sum of all elements in the array.

I created a for loop, and made sure to iterate through all indices except for the last one to always have a right side partition of the array.
Inside the loop, we add the value of the first element to `left`, `left+=nums[i]`, and the `right` side will be equal to total minus the sum on the left side, `right = total - left`.

If we find that the `left` partition is greater than the `right` partition, we should increment `ans` by 1.

As the loop goes on we repeat the process, so that the left partiton steadily grows, if `left` is still > `right`, we increment `ans` again. At the end we'll return ans, which will hold the total number of valid ways we can split the given array.