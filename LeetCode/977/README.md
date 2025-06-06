# 977. Squares of a Sorted Array (Easy)

Given an integer array `nums` sorted in **non-decreasing order**, return an array of **the squares of each number** sorted in non-decreasing order.

#### Example 1:

```python
Input: nums = [-4,-1,0,3,10]
Output: [0,1,9,16,100]
Explanation: After squaring, the array becomes [16,1,0,9,100].
After sorting, it becomes [0,1,9,16,100].
```


#### Example 2:

```python
Input: nums = [-7,-3,2,3,11]
Output: [4,9,9,49,121]
```

#### Constraints:
`1 <= nums.length <= 10^4`

`-10^4 <= nums[i] <= 10^4`

`nums` is sorted in **non-decreasing order** (aka increasing order).


## My Solution
python solution
```python
class Solution:
    def sortedSquares(self, nums: List[int]) -> List[int]:
        sorted_squares = []
        
        for num in nums:
            sorted_squares.append(pow(num,2))
            
        sorted_squares.sort()
        
        return sorted_squares  
```

c++ solution
```c++
class Solution {
public:
    vector<int> sortedSquares(vector<int>& nums)
    {
        int sizeOfArray = nums.size();
        
        for(int i = 0; i < sizeOfArray; i++)
        {
            nums[i] = nums[i] * nums[i];
        }
        
        sort(nums.begin(), nums.end());
        
        return nums;
    }
};
```

## Explanation

Using the conventional two pointer method to solve this problem is not a bad idea, but I think theres a more simpler approach...

We could simply create a new array called `sorted_squares`, and create a for loop that copies the original `num` into `sorted_squares` squared.

This is done by using the append and pow method => `sorted_squares.append(pow(num,2))`.

lastly we can use the sort method to sort our new array of squared numbers and return that array.