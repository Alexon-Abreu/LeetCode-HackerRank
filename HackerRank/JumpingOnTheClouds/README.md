# Jumping on the Clouds

There is a new mobile game that starts with consecutively numbered clouds. Some of the clouds are thunderheads and others are cumulus. The player can jump on any cumulus cloud having a number that is equal to the number of the current cloud plus 1 or 2. The player must avoid the thunderheads. Determine the minimum number of jumps it will take to jump from the starting postion to the last cloud. It is always possible to win the game.


For each game, you will get an array of clouds numbered 0 if they are safe or 1 if they must be avoided.

#### Example 1:

```c++
c = [0,1,0,0,0,1,0]
```
Index the array from 0... 6. The number on each cloud is its index in the list so the player must avoid the clouds at indices 1 and 5.

They could follow these two paths: 0 → 2 → 4 → 6 or 0 → 2 → 3 → 4 → 6. The first path takes 3 jumps while the second takes 4. Return 3.



#### Function Description

Complete the jumpingOnClouds function in the editor below.

jumpingOnClouds has the following parameter(s):
```c++
• int c[n]: an array of binary integers
```

#### Returns
```c++
• int: the minimum number of jumps required
```

#### Input Format

The first line contains an integer n, the total number of clouds. 

The second line contains n space-separated binary integers describing clouds c[i] where 0 ≤ i < n.


#### Constraints:
```c++
• 2 ≤ n ≤ 100

• c[i] E {0,1}

• c[0] = c[n - 1] = 0

E = is in
```


### Sample Input
```c++
7

0010010
```

### Sample Output
```c++
4
```

## My Solution
python solution:
```python
def jumpingOnClouds(c):
    num_of_jumps = 0
    pos = 0
    
    while pos < len(c)-1:
        if pos + 2 < len(c) and c[pos+2] == 0:
            pos+=2
            num_of_jumps+=1
        else:
            pos+=1
            num_of_jumps+=1
    return num_of_jumps
```

c++ solution:
```c++
int jumpingOnClouds(vector<int> c)
{
    int jumps = 0;
    int pos = 0;
    
    while(pos < c.size()-1)
    {
        if(pos + 2 < c.size() && c[pos+2] == 0)
        {
            pos+=2;
            jumps++;
        }
        else
        {
            pos+=1;
            jumps++;
        }
    }
    
    return jumps;
}
```

## Explanation

It is always possible to win the game.
 
Which means that the first & last indexes should be cumulus clouds (0, aka safe clouds).

The point of the game is to get to the last cloud in the least amount of jumps possible.
The most we can jump at once is 2, and because we're guaranteed to win, we must always be able to jump, even if its just 1.

With that in mind, we should start by checking to see if we can jump by 2, in other words, does position + 2 == 0. Otherwise, our only other move is to jump by 1.