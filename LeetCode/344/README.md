# 344. Reverse String (Easy)

Write a function that reverses a string. The input string is given as an array of characters `s`.

You must do this by modifying the input array in-place with `O(1)` extra memory.

#### Example 1:

```c++
Input: s = ["h","e","l","l","o"]
Output: ["o","l","l","e","h"]
```


#### Example 2:

```c++
Input: s = ["H","a","n","n","a","h"]
Output: ["h","a","n","n","a","H"]
```

#### Constraints:
`1 <= s.length <= 105`

`s[i]` is a printable ascii character.


## My Solution
c++ solution:
```c++
class Solution {
public:
    void reverseString(vector<char>& s) 
    {
        int i = 0;
        int j = s.size()-1;
        
        while(i < j)
        {
            char temp;        // creating a temp var to perfrom swaps
            temp = s[i];      // temp holds value in s[i]
            s[i] = s[j];      // s[i] would be assigned the value in s[j] - half of the swap complete
            s[j] = temp;      // s[j] = temp which held s[i] initial value - full swap complete
    
            i++;
            j--;
        }
        
    }
};
```
