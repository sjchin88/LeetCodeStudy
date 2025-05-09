# Deep-First-Search(DFS)

## Application

binary tree (or tree) problem

combination problem - Finding all possible solutions

permutation problem - Finding all permutations

finding the best combination / permutation.

Note:

* if the target is just to count the number of solution/ permutation, dp could be better&#x20;
* for best combination / permutation , dp only work if there is certain restriction in the order (like contiguous subarray/substring  or subsequence. For subset, dp unlikely to work
* Sometime we can use binary search to set for potential limit to aid in pruning.&#x20;

## Complexities

Time complexities = O( k ^ n )  => where&#x20;

n = max number of elements of each path,&#x20;

k = max possible option of each path.&#x20;

Therefore if n is unbound , even with small k (like 2) , the time complexity can be very huge.&#x20;

For combination problem, this is O(2 ^ n)&#x20;

For permutation problem, this is O(n!)

Space complexities => similar to time complexities.&#x20;

## Things to note

1. Think carefully about how to store the state of the visited node (for example, the N-Queens problem)
2. Need to consider pruning early as soon as we found the first result. If we are looking for optimize dfs order that can produce the best result, think if there is a way to verify if it is possible to achieve better and stop if it doesnt.  (for example, [https://www.lintcode.com/problem/570](https://www.lintcode.com/problem/570), 3530 - [https://leetcode.com/problems/maximum-profit-from-valid-topological-order-in-dag/description/](https://leetcode.com/problems/maximum-profit-from-valid-topological-order-in-dag/description/))
3. Try 301 , [https://leetcode.com/problems/remove-invalid-parentheses/](https://leetcode.com/problems/remove-invalid-parentheses/)

## Solving Steps

1. Determine exit conditions for the DFS call
2. Determine the possible options to loop through in one iteration
   1. Think of the information you need. Most often is the **index of a list** to start looking for possible choices
   2. Additional index of target list may required
3. When using a list / set to record the previous choices, for each option of this choice
   1. temporary add the option into the list/set,&#x20;
   2. perform DFS on the next choice
   3. on the previous DFS return, remove the option just now to clean the list/set for the next option for this choice
4. Think of possible optimizations to fast up the process:
   1. Use of Set() / Dict ()
   2. Use of Trie&#x20;
   3. Use of Prefix

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

### Preorder Traversal

```python
# Definition for a binary tree node.
# class TreeNode:
#    def __init__(self, val=0, left=None, right=None):
#        self.val = val
#        self.left = left
#        self.right = right
class Solution:
    def preorder_traversal(self, root: Optional[TreeNode]) -> List[int]:
        result = []
        stack = []
        stack.append(curr)
        while stack:
            curr = stack.pop()
            # append curr node when it is popped
            result.append(curr.val)
            # put the right node into the stack first as we want it to come out 
            # after the left node
            if curr.right:
                stack.append(curr.right)
            if curr.left:
                stack.append(curr.left)
        return result
```

### Inorder Traversal

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def inorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        result = []
        stack = []
        curr = root
        while curr or stack:
            # Keeping going left until the end
            while curr:
                stack.append(curr)
                curr = curr.left
            # pop the stack and append the value into results
            curr = stack.pop()
            result.append(curr.val)
            # Go right once, if the right is null, next itr will skip going left and 
            # Continue backtrack to the previous parent
            curr = curr.right
        return result
```

### Postorder Traversal

```python
# Use preorder traversal, but push root.left to stack first
# then reverse the order
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def postorder_traversal(self, root: Optional[TreeNode]) -> List[int]:
        result = []
        stack = []
        if root:
            stack.append(root)
        while stack:
            curr = stack.pop()
            result.append(curr.val)
            if curr.left:
                stack.append(curr.left)
            if curr.right:
                stack.append(curr.right)
        return result[::-1]
```

Can be done using stack or recursion

## Practice Problems



200\. Number of Islands [https://leetcode.com/problems/number-of-islands/](https://leetcode.com/problems/number-of-islands/)

547\. Number of Provinces [https://leetcode.com/problems/number-of-provinces/](https://leetcode.com/problems/number-of-provinces/)

695\. Max Area of Island [https://leetcode.com/problems/max-area-of-island/](https://leetcode.com/problems/max-area-of-island/)

417\. Pacific Atlantic Water Flow [https://leetcode.com/problems/pacific-atlantic-water-flow/](https://leetcode.com/problems/pacific-atlantic-water-flow/)

### Hard

51 N-Queens [https://leetcode.com/problems/n-queens/](https://leetcode.com/problems/n-queens/)

1192 Critical Connections [https://leetcode.com/problems/critical-connections-in-a-network/](https://leetcode.com/problems/critical-connections-in-a-network/)

Need to detect cycles in a graph using dfs. \
Use node2rank to record the rank of the node, if dfs reached a node with a rank lower than the predecessor, the cycle is detected. Remove all edges related to the cycle
