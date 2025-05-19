# Two Sum II - Input Array Is Sorted (Medium)

Given a 1-indexed array of integers `numbers` that is already **sorted in non-decreasing order**, find two numbers such that they add up to a specific `target` number. Let these two numbers be `numbers[index1]` and `numbers[index2]` where `1 <= index1 < index2 <= numbers.length`.

Return *the indices of the two numbers, `index1` and `index2`, **added by one** as an integer array `[index1, index2]` of length 2*.

The tests are generated such that there is **exactly one solution**. You **may not** use the same element twice.

Your solution must use only constant extra space.

#### Example 1:

```c++
Input: numbers = [2,7,11,15], target = 9
Output: [1,2]
Explanation: The sum of 2 and 7 is 9. Therefore, index1 = 1, index2 = 2. We return [1, 2].
```


#### Example 2:

```c++
Input: numbers = [2,3,4], target = 6
Output: [1,3]
Explanation: The sum of 2 and 4 is 6. Therefore index1 = 1, index2 = 3. We return [1, 3].
```

#### Example 3:

```c++
Input: numbers = [-1,0], target = -1
Output: [1,2]
Explanation: The sum of -1 and 0 is -1. Therefore index1 = 1, index2 = 2. We return [1, 2].
```

#### Constraints:

`2 <= numbers.length <= 3 * 10^4`

`-1000 <= numbers[i] <= 1000`

`numbers` is sorted in **non-decreasing order**.

``-1000 <= target <= 1000``

The tests are generated such that there is **exactly one solution**.

## My Solution
python solution:
```python
class Solution:
    def twoSum(self, numbers: List[int], target: int) -> List[int]:
        left = 0
        right = len(numbers) - 1

        while left < right:
            curr = numbers[left] + numbers[right]

            if curr == target:
                return [left+1, right+1]
            elif curr < target:
                left+=1
            else:
                right-=1

        return []
```

## Explanation

The goal is to find two numbers in an array whose sum is equal to the given target.

The array itself is already **sorted in a non-decreasing order**, aka ascending order.

For this problem we can use a common technique called `Two Pointers`. This is where we set up two variables, i and j, or left and right, to move along an iterable like an array or string.

For this problem we can start by setting the left and right variable to the start and end of the array. curr, our total/sum variable, will store the sum of the values the pointers are currently pointing to.

The rest of this problem is done inside a while loop (while left < right), we keep going until the left and right pointer meet each other. 

It's **important to note** that because the array is in ascending order, incrementing the left variable "permanently" increases the value the left pointer points to, and decrementing the right varible "permanently" decreases the value the right pointer points to.

So if we set our curr variable equal to the beginning sum of our left and right pointers (curr = numbers[left] + numbers[right]), we could use that value to determine whether we have to increment our left pointer or decrement our right pointer. if curr < target, then we must increment the left pointer to increase the value of curr. Otherwise, we simply decrement the right pointer to decrease the value of curr.

In the case where our initial curr value is equal to the target, or when curr finanlly reaches the target value, we would just return those indicies + 1, since we're dealing with a a 1-indexed array.