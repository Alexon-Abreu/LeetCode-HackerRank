
# 713. Subarray Product Less Than K (Medium)

Given an array of integers `nums` and an integer `k`, return the number of contiguous subarrays where the product of all the elements in the subarray is strictly less than `k`.

#### Example 1:

```c++
Input: nums = [10,5,2,6], k = 100
Output: 8
Explanation: The 8 subarrays that have product less than 100 are:
[10], [5], [2], [6], [10, 5], [5, 2], [2, 6], [5, 2, 6]
Note that [10, 5, 2] is not included as the product of 100 is not strictly less than k.
```


#### Example 2:

```c++
Input: nums = [1,2,3], k = 0
Output: 0
```

#### Constraints:
`1 <= nums.length <= 3 * 10^4`

`1 <= nums[i] <= 1000`

`0 <= k <= 10^6`


## My Solution
python solution

```python
class Solution:
    def numSubarrayProductLessThanK(self, nums: List[int], k: int) -> int:
        left = ans = 0
        curr = 1 # needs to be 1 since we're dealing with multiplication

        if k <= 1:
            return 0

        for right in range(len(nums)):
            curr *= nums[right]

            while curr >= k and left <= right:
                curr //= nums[left]
                left+=1
            
            ans += right-left+1
        
        return ans
```
c++ solution
```c++
class Solution
{
    public:
        int numSubarrayProductLessThanK(vector<int>& nums, int k) 
        {
            if(k <= 1)
            {
                return 0;
            }

            int ans = 0;
            int left = 0;
            int currNumOfSubArrays = 1;   

            for(int right = 0; right < nums.size(); right++)
            {
                currNumOfSubArrays *= nums[right];

                while(currNumOfSubArrays >= k)
                {
                    currNumOfSubArrays /= nums[left];
                    left++;
                }

                ans += right - left + 1;
                // the # of valid windows ending at the right index is = to size of window = right - left + 1;
            } 

            return ans;
        }
};
```
