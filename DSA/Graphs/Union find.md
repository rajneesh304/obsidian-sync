
| Method           | Time Complexity                           | Space Complexity | Comments                                                                                                                           |
| ---------------- | ----------------------------------------- | ---------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| Union/Find       | O(n)                                      | O(n)             |                                                                                                                                    |
| Union by rank    | O(log n)                                  | O(n)             | maintains 2 arrays -> rank and parent. rank keeps track of children of the root node and parent keeps track of parent of the node. |
| path compression | O(α(n))<br>α is inverse ackerman function | O(n)             | maintains 2 arrays -> rank and parent. rank keeps track of children of the root node and parent keeps track of parent of the node. |
|                  |                                           |                  |                                                                                                                                    |

Union find with path compression:
```c++
// Find with path compression 
int find(int x) { 
	if (parent[x] != x) { // Path compression: set parent to the root directly 
		parent[x] = find(parent[x]); 
	} 
	return parent[x]; 
}
```
```
// Union by rank 
void unionSets(int x, int y) { 
	int rootX = find(x); 
	int rootY = find(y); 
	
	// If they're already in the same set 
	if (rootX == rootY) return;
// Union by rank: attach the smaller rank tree under the higher rank tree if (rank[rootX] < rank[rootY]) { parent[rootX] = rootY; }
```