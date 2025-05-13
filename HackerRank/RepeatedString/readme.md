# Repeated String

There is a string, *s* , of lowercase English letters that is repeated infinitely many times. Given an integer,*n* , find and print the number of letter a's in the first *n* letters of the infinite string.



#### Example 1:

```c++
s = 'abcac'
n = 10
```
The substring we consider is *abcacabcac*, the first **10** characters of the infinite string.

There are **4** occurrences of a in the substring.



#### Function Description

Complete the repeatedString function in the editor below.

repeatedString has the following parameter(s):

```c++
s: a string to repeat
n: the number of characters to consider
```

#### Returns
```c++
int: the frequency of a in the substring
```

#### Input Format

The first line contains a single string, *s*.

The second line contains an integer, *n*.


#### Constraints:
```c++
1 ≤ |s| ≤ 100
1 ≤ n ≤ 10^12
```
For 25% of the test cases, *n* ≤ 10^6.



### Sample Input
```c++
aba
10
```

### Sample Output
```c++
7
```

### Explanation of sample output
The first *n* = 10 letters of the infinite string are `abaabaabaa`. Because there are 7 a's, we return 7.

## My Solution
Python solution:
```python
def repeatedString(s, n):
    # Write your code here
    count_of_a_in_s = s.count('a') # how many a's are in the string s
    repeats_of_s_in_n = n//len(s)  # how many times s fits in n
    
    remainder = n % len(s) # checking to see how many characters are left over
    leftover_count = s[: remainder].count('a') # counting the num of a's in the remainder string

    total_num_of_a = (count_of_a_in_s * repeats_of_s_in_n) + leftover_count
    
    return total_num_of_a
```

## Explanation

 The goal is to find how many a's are in a substring of an infinte string, where s is our string and n is the number of character to consider in the string.

 because s itself is not already an infinite format, I decided to multiply s to fully conform with the length of the substring we're considering.
 
 To begin, we count the # of times letter 'a' appears in the original string s
 Then we find out how many times we can repeat string s to fill the length of the required substring, we do this by using dividing n by the length of s.
 
 so far the total number of a's is (the # of a's in s) * (the # of times s fits in n)
 but we also have to account for any remainder characters of s, because it wont always be the case we the s perfectly fit inside of n, and even # of times.

 so we need to find the remainder of n/s, which we can do by using modulo, n % len(s)
 Once we have the remainder, we can go ahead and set up a variable, leftover_count, that counts the number of leftover a's by slicing s from 0 to its remainder.

 It's really not intuitive to do it this way, but because we're dealing with a repeating string, s[0] will likely be equivalent to its remainder character, s[remainder].

 Once we have the leftover_count, we add that to the total # of a's in the substring
 total_num_of_a = (count_of_a_in_s * repeats_of_s_in_n) + leftover_count
```