# Deep-First-Search(DFS)

## Application

binary tree (or tree) problem

combination problem - Finding all possible solutions

permutation problem - Finding all permutations

Note if the target is just to count the number of solution/ permutation, dp could be better&#x20;

## Algorithm Template

### Back Tracking

```python
// Some code
def dfs_backtrack(candidates, index, temp, result):
	# found solution satisfies required condition
	if index == len(candidates) || other conditions:
		#record result, if the temp is list need to make a deep copy
		result.append(temp)
	
	# iterate all possible candidates
	for next_candidate in candidates:
		#try this partial candidate solution
		temp.append(candidate)
		#update remaining required conditions
		index = index + 1
		self.dfs_backtrack(candidate, index, temp, result)
		#back track, use pop() for fastest removal
		temp.pop()

```



Can be done using stack or recursion

Problems:



200\. Number of Islands [https://leetcode.com/problems/number-of-islands/](https://leetcode.com/problems/number-of-islands/)

547\. Number of Provinces [https://leetcode.com/problems/number-of-provinces/](https://leetcode.com/problems/number-of-provinces/)

695\. Max Area of Island [https://leetcode.com/problems/max-area-of-island/](https://leetcode.com/problems/max-area-of-island/)

417\. Pacific Atlantic Water Flow [https://leetcode.com/problems/pacific-atlantic-water-flow/](https://leetcode.com/problems/pacific-atlantic-water-flow/)
