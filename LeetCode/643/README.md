# 643. Maximum Average Subarray I (Easy)

You are given an integer array `nums` consisting of `n` elements, and an integer `k`.

Find a contiguous subarray whose **length is equal to `k`** that has the maximum average value and return *this value*. Any answer with a calculation error less than `10^5` will be accepted.

#### Example 1:

```Python
Input: nums = [1,12,-5,-6,50,3], k = 4
Output: 12.75000
Explanation: Maximum average is (12 - 5 - 6 + 50) / 4 = 51 / 4 = 12.75
```

#### Example 2:

```Python
Input: nums = [5], k = 1
Output: 5.00000
```

#### Constraints:

`n == nums.length`

`1 <= k <= n <= 10^5`

`-10^4 <= nums[i] <= 10^4`

## My Solution

```Python
class Solution:
    def findMaxAverage(self, nums: List[int], k: int) -> float:
        curr = 0

        for i in range(k):
            curr+=nums[i]

        ans = curr

        for i in range(k, len(nums)):
            curr += nums[i] - nums[i-k]
            ans = max(ans, curr)

        return ans / k
```

## Explanation

For this problem we are finding a contiguous subarray (meaning elements must be next to each other and in order) of size `k` and store the average of all elements from that subarray. We then want to return the maximum average subarray that we recorded.

First thing I do is initialize `curr` to 0. `curr` will hold the total of k elements from `nums` as we slide our window.

In the first for loop we iterate through the first `k` elements of `nums` and add those values to `curr`. We assign `ans` to `curr` to hold this value for us, and give us the flexibility to manipulate `curr` with out losing the original total.

Once we have the total of the first k elements in curr, we can create another for loop so we can slide our window, appending the value of the next element and popping the value of last element from the running total in `curr` like so `curr += nums[i] - nums[i-k]`. Doing this allows use to store the total value of a subarray in nums, with length of k at each iteration.

Within each iteration, we compare the maximum between our previous max in `ans` and our current window total in `curr`, `ans = max(ans, curr)`.

