# 3310. Score of a String (Easy)

You are given a string `s`. The **score** of a string is defined as the sum of the absolute difference between the **ASCII** values of adjacent characters.

Return the **score** of `s`.

#### Example 1:

```Python
Input: s = "hello"

Output: 13

Explanation:

The ASCII values of the characters in s are: 'h' = 104, 'e' = 101, 'l' = 108, 'o' = 111. So, the score of s would be |104 - 101| + |101 - 108| + |108 - 108| + |108 - 111| = 3 + 7 + 0 + 3 = 13.
```

#### Example 2:

```Python
Input: s = "zaz"

Output: 50

Explanation:

The ASCII values of the characters in s are: 'z' = 122, 'a' = 97. So, the score of s would be |122 - 97| + |97 - 122| = 25 + 25 = 50.
```

#### Constraints:

`2 <= s.length <= 100`

`s consists only of lowercase English letters.`

## My Solution

```Python
class Solution:
    def scoreOfString(self, s: str) -> int:
        result = 0
        for i in range(len(s) - 1):
            result += abs(ord(s[i]) - ord(s[i+1]))
        return result
```

## Thought Process

So we're given a string `s`, and we're told to find the `score` of `s`.

the `score` is defined by the absolute difference in **ASCII** values of adjacent chars
    so if `s = "he"`, the `score` would be `abs(ord(h) - ord(e))`
    we can store this value in `result` and add additional values if `s` includes more chars

we need to do this before reaching the last char, to stay in bounds