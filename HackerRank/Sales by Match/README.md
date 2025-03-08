# Sales by Match

There is a large pile of socks that must be paired by color. Given an array of integers representing the color of each sock, determine how many pairs of socks with matching colors there are.

#### Example 1:

```c++
n = 7
ar = [1,2,1,2,1,3,2]
```
There is one pair of color 1 and one of color 2. There are three odd socks left, one of each color. The number of pairs is 2.


#### Function Description

```c++
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
`1 <= n <= 100`

`1 <= arr[i] <= 100 where 0 <= i <= n`


### Sample Input
STDIN                       Function
-----                       --------
9                           n = 9

10 20 20 10 10 30 50 10 20  ar = [10, 20, 20, 10, 10, 30, 50, 10, 20]

### Sample Output
3

## My Solution

```c++
int sockMerchant(int n, vector<int> ar)
{
    int pairs = 0;
    
    for(int i = 0; i < n; i++)
    {
        if(ar[i] != 0)
        {
            for(int j = i+1; j < n; j++)
            {
                if(ar[i] == ar[j])
                {
                    pairs++;
                    ar[j] = 0;
                    break;
                }
            }
        }
    }
    return pairs;
}
```

## Explanation

The sockMerchant function works by taking in 2 paramaters, an integer n that represents the # of socks in the pile, and an array ar, which represents the color of each sock. The goal is to  determine how many pairs of socks with matching colors there are.

The way I solved this problem was by comparing one element to it adjacent element.
If they're a match, we increment pairs and mark that sock in the array to avoid overcounting, and repeat...

I start by creating a pairs variable, which serves as our counter variable.
Then I created a for loop to iterate through the array one by one. After that we have an if statement, which I'll explain shortly..

I created another for loop. This inner loop will allow us to grab the adjacent value and recursively increment it's index until we find a match or none at all. If a match is found, we'll increment the pairs variable, mark the adjacent value with a value of 0, and break out of the inner loop.

Once we break out of the inner loop, the process is repeated again with the outer loop.
Here's where the if statment is crucial, by marking socks with a value of 0, we want to make sure we dont count them in future pairs. So if the element at ar[i] == 0, then we do not enter the inner loop and increment to the next index in the array instead.