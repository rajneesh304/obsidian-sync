
| Method           | Time Complexity | Space Complexity | Comments                                                                                                                           |
| ---------------- | --------------- | ---------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| Union/Find       | O(n)            | O(n)             |                                                                                                                                    |
| Union by rank    | O(log n)        | O(n)             | maintains 2 arrays -> rank and parent. rank keeps track of children of the root node and parent keeps track of parent of the node. |
| path compression | O(α(n))         | O(n)             | maintains 2 arrays -> rank and parent. rank keeps track of children of the root node and parent keeps track of parent of the node. |
|                  |                 |                  |                                                                                                                                    |
