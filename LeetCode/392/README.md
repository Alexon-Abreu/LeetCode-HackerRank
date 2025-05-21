# 392. Is Subsequence (Easy)

Given two strings `s` and `t`, return `true` **if `s` is a **subsequence** of `t`, or `false` otherwise.**

A **subsequence** of a string is a new string that is formed from the original string by deleting some (can be none) of the characters without disturbing the relative positions of the remaining characters. (i.e., `"ace"` is a subsequence of `"abcde"` while `"aec"` is not).

#### Example 1:

```python
Input: s = "abc", t = "ahbgdc"
Output: true
```

#### Example 2:

```python
Input: s = "axc", t = "ahbgdc"
Output: false
```

#### Constraints:

`0 <= s.length <= 100`

`0 <= t.length <= 104`

`s` and `t` consist only of lowercase English letters.


## My Solution

```python
class Solution:
    def isSubsequence(self, s: str, t: str) -> bool:
        i = j = 0

        while i < len(s) and j < len(t):
            if s[i] == t[j]:
                i+=1
            j+=1
        
        return i == len(s)
```

## Explanation

The question asks us to find out whether the first word s appears in the second word t, in the same order (i.e. car in scarf or tea in steam).

We can use a simple two pointer approach to solve this problem in linear time.

To begin, we set i and j equal to 0, these pointers will give us the letter at each index of the word.

We create a while loop with a condition to keep running while i and j are less than the size of s and t.

Inside the loop, we have an if statement, if we find at any point that s[i] == t[j], then we should increment i to point to the next character in s. Regardless of whether we found a match on that index, we still increment j to point to the next character in t.

At the end, we return the boolean value of i == len(s). if this is true, then we know that we have found every letter from s in t in order.