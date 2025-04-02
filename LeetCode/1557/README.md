# 1557. Minimum Number of Vertices to Reach All Nodes (Medium/In Progress)

Given a **directed acyclic graph**, with `n` vertices numbered from `0` to `n-1`, and an array `edges` where `edges[i] = [from[i], to[i]]` represents a directed edge from node from[i] to node to[i].

Find the *smallest set of vertices from which all nodes in the graph are reachable*. It's guaranteed that a unique solution exists.

Notice that you can return the vertices in any order.

#### Example 1:

```c++
Input: n = 6, edges = [[0,1],[0,2],[2,5],[3,4],[4,2]]
Output: [0,3]
"Explanation: It's not possible to reach all the nodes from a single vertex. From 0 we can reach [0,1,2,5]. From 3 we can reach [3,4,2,5]. So we output [0,3]."
```


#### Example 2:

```c++
Input: n = 5, edges = [[0,1],[2,1],[3,1],[1,4],[2,4]]
Output: [0,2,3]
Explanation: Notice that vertices 0, 3 and 2 are not reachable from any other node, so we must include them. Also any of these vertices can reach nodes 1 and 4.
```

#### Constraints:



## My Solution

```c++
#include <iostream>
using namespace std;

class Solution {
public:

    vector<int> findSmallestSetOfVertices(int n, vector<vector<int>>& edges)
    {
        vector<int> nodeWithoutIncomingEdges;
        vector<bool> hasIncomingEdge(n, false);

        for(const auto& edge : edges)
        {
            hasIncomingEdge[edge[1]] = true;
        }

        for(int i = 0; i < n; i++)
        {
            if(!hasIncomingEdge[i])
            {
                nodeWithoutIncomingEdges.push_back(i);
            }
        }

        return nodeWithoutIncomingEdges;
    }
};
```

## Explanation
Since we're dealing with a directed graph and not all nodes will have an incoming edge, the only way to reach these unpopular nodes is by explicitly targeting them. All other nodes will have an incoming edge, which can be reached through "unpopular nodes" (nodes with no incoming edges). The problem is to find the smallest set of vertices from which all nodes in the graph are reachable. In a typical graph, nodes with no incoming edges are usually less common than nodes with incoming edges. So by starting at nodes with no incoming edges, we can almost always guarantee that it is the smallest set of vertices to reach all other nodes. Thus, the problem can be read as, which nodes have no incoming edges.