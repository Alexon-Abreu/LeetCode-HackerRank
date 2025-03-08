# Sales by Match

There is a large pile of socks that must be paired by color. Given an array of integers representing the color of each sock, determine how many pairs of socks with matching colors there are.

#### Example 1:

```c++
n = 7
ar = [1,2,1,2,1,3,2]
There is one pair of color 1 and one of color 2. There are three odd socks left, one of each color. The number of pairs is 2.
```


#### Function Description

```c++
Complete the sockMerchant function in the editor below.
sockMerchant has the following parameter(s):
int n: the number of socks in the pile
int ar[n]: the colors of each sock
```

#### Returns
int: the number of pairs

### Input Format
The first line contains an integer *n*, the number of socks represented in *ar*.
The second line contains *n* space-separated integers, *ar[i]*, the colors of the socks in the pile.

#### Constraints:
`1 <= s.length <= 105`

`s[i]` is a printable ascii character.


## Solution

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
