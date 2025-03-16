# Counting Valleys

An avid hiker keeps meticulous records of their hikes. During the last hike that took exactly *steps* steps, for every step it was noted if it was an uphill, *U*, or a downhill, *D* step. Hikes always start and end at sea level, and each step up or down represents a unit change in altitude. We define the following terms:

- A mountain is a sequence of consecutive steps above sea level, starting with a step up from sea level and ending with a step down to sea level.

- A valley is a sequence of consecutive steps below sea level, starting with a step down from sea level and ending with a step up to sea level.
Given the sequence of up and down steps during a hike, find and print the number of valleys walked through.

#### Example 1:

```c++
steps = 8 path = [DDUUUUDD]

The hiker first enters a valley 2 units deep. Then they climb out and up onto a mountain 2 units high. 
Finally, the hiker returns to sea level and ends the hike.
```


#### Function Description

```c++
Complete the countingValleys function in the editor below.

countingValleys has the following parameter(s):
- int steps: the number of steps on the hike
- string path: a string describing the path
```

#### Returns
int: the number of valleys traversed


#### Input Format
The first line contains an integer *steps*, the number of steps in the hike.

The second line contains a single string *path*, of *steps* characters that describe the path.

#### Constraints:
`2 <= steps <= 10^6`

`path[i] includes {U D}`


### Sample Input
`8`

`UDDDUDUU`

### Sample Output
`1`

## My Solution

```c++
int countingValleys(int steps, string path)
{
    int seaLevel = 0;
    int numOfValleys = 0;
    
    for(int i = 0; i < steps; i++)
    {
        if(path[i] == 'U')
        {
            seaLevel++;
        }
        else
        {
            seaLevel--;
        }
        
        if(seaLevel == 0 && path[i] == 'U')
        {
            numOfValleys++;
        }
    }
    return numOfValleys;
}
```

## Explanation

The goal is to return the number of times a hiker has traversed a valley. The problem explains that a valley is defined as a "sequence of consecutive steps below sea level, starting with a step down from sea level and ending with a step up to sea level". 

This is a pretty simple problem, all we have to do is keep track of the sea level. If the hiker takes a step down 'D', then we would decrement the value of the sea level and increment otherwise.

So I start by declaring and instantiating the values of *seaLevel* and *numOfValleys* to 0, these will keep track of the current sea level and the # of valleys traversed.

Then we create a for loop to iterate through the string *path*. The *steps* parameter will hold the # of steps taken by the hiker, we can also view this as the # of indices included in the string *path*, since can be treated as arrays. *steps* will serve as the limit our for loop should not pass.

Inside the loop, our first if statement will check to see whether the current element in the string *path* == 'U' (a step up). In which case we'll increment *seaLevel* by 1.
The else statement implies that if *path[i] != 'U'*, then it must be == 'D', In which case we'll decrement *seaLevel* by 1.

The final if statement will check to see if the current *seaLevel == 0* && *path[i] == 'U'*. As the problem states, this only occurs when the hiker has climbed out of a valley. So we increment the value *numOfValleys* by 1. Outside of the loop, we'll just return this same value to show the # of valleys the hiker has traversed.

