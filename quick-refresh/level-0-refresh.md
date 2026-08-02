# Level 0 Refresh

## Binary Search&#x20;

Algorithm

```python
// Binary Search
def search(self, nums, target):
    start = 0
    end = len(nums) - 1
    find = default_number when the search fails
    while start <= end:
        mid = start + (end - start)//2
        if f(mid):
            find = mid
            return find # if there is only one possible answer
        elif f(mid) < target:
            start = mid + 1
        else:
            end = mid - 1
    return find
```

Quick practise:&#x20;

* [https://leetcode.com/problems/binary-search/description/](https://leetcode.com/problems/binary-search/description/)

### Binary Search of Result Range

Similar algorithm as Binary Search

```python
// Binary Search
def search(self, nums):
    start = 0
    end = len(nums) - 1
    find = default_number when the search fails
    while start <= end:
        mid = start + (end - start)//2
        if f(nums, mid):
            find = mid
            start = mid + 1
        else:
            end = mid - 1
    return find
```

When to use

* Other solutions take at least O(n^2).&#x20;
* It is possible to verify if the solution exists in O(n)
* It is possible to determine the direction of movement (when the search fails, we should always look for a smaller or larger value)

Practise:

* [https://leetcode.com/problems/split-array-largest-sum/description/](https://leetcode.com/problems/split-array-largest-sum/description/)

## Binary (Search) Tree

A `binary search tree` (BST), a special form of a binary tree satisfies the binary search property:

1. The value in each node must be `greater than` (or equal to) any values stored in its left subtree.
2. The value in each node must be `less than` (or equal to) any values stored in its right subtree.

```python
    
    def isValidBSTCheck(self, root: Optional[TreeNode], left_bound, right_bound) -> bool:
        if not root:
            return True
        if root.val <= left_bound or root.val >= right_bound:
            return False
        return self.isValidBSTCheck(root.left, left_bound, root.val) and 
        self.isValidBSTCheck(root.right, root.val, right_bound)
```

### Inorder, Preorder, PostOrder

In-order : Left -> Root -> Right

Pre-order: Root -> left -> Right

Post-order: Left -> Right -> Root

Quick Practise:

* [https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/description/](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/description/)
* [https://leetcode.com/problems/construct-binary-tree-from-inorder-and-postorder-traversal/description/](https://leetcode.com/problems/construct-binary-tree-from-inorder-and-postorder-traversal/description/)
*

### LCA (Lowest Common Ancestor)

Quick Practise:

* [ttps://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/description/](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/description/)

## Bit Operation

<figure><img src="../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

a ^ b = c implies a = b ^ c or b = a ^ c

So if we have a set of prefix\_xor where prefix\_xor\[i] = 0 ^ nums\[1] ^ nums\[2] ^... ^ nums\[i - 1]

We can find the xor results of numbers between i and j by prefix\_xor\[j + 1] ^ prefix\_xor\[i]&#x20;

Quick Practise:

* [https://leetcode.com/problems/bitwise-ors-of-subarrays/description/](https://leetcode.com/problems/bitwise-ors-of-subarrays/description/)&#x20;
* (a ^ b) & (a ^ c) = a & (b ^ c) [https://leetcode.com/problems/find-xor-sum-of-all-pairs-bitwise-and/description/](https://leetcode.com/problems/find-xor-sum-of-all-pairs-bitwise-and/description/)

## BFS

Applications&#x20;

* Iteration of all possible answers (whether the nodes are connected etc)
* Topological sorting
* Search by layer / Traveling by a layer of a tree (Binary Tree)
* Simple graph shortest path
* Finding the longest diameter in binary / N-ary tree (use double BFS, first BFS find the first end, second BFS starting from the first end to find the second end)
* If you are working with 2-D grid / matrix, bfs is usually the better and only choice compared to dfs.&#x20;
* Sometimes we can use binary search to set a condition and check if the condition can be met using bfs to find solution in O((n + m) log (n)) time.&#x20;

Complexity

·       O(n + m), n is the number of nodes, m is the edge

·       O(n) space



```python
// BFS Advance Version 2
// Use a dist map to store the distance

def bfs():
    
    # Initialize the queue and visited set
    queue = collections.deque()
    dist_map = {}
    
    # Put in the starting node
    if first_node:
        queue.append(first_node)
        dist_map[first_node] = 0
        
    # while loop iteration
    while queue:        
        curr = queue.popleft()         
        for next_point in self.get_next(curr):
            
            # function self.is_valid can check if the next point is within the boundary
            # and not visited
            if self.is_valid(next_point):  
            
                # Add to queue and visited together
                queue.append(next_point)
                dist_map[next_point] = dist_map[curr] + 1 
            
        
    
```

### Bidirectional&#x20;

1197 Double BFS [https://leetcode.com/problems/minimum-knight-moves/description/](https://leetcode.com/problems/minimum-knight-moves/description/)

### Shortest Path

Dijkstra

```python
// Some code
def shortest_path(self, src: int):
        # Create a priority queue to store vertices that are being preprocessed
        heap = []
        heapq.heappush(heap, (0, src))
  
        # Create a vector for distances and initialize all distances as infinite (INF)
        dist = [math.inf] * V
        dist[src] = 0
  
        while heap:
            # The first vertex in the pair is the minimum distance vertex, 
            # extract it from the heap
            # vertex label is stored in the second of the pair
            distance, curr = heapq.heappop(heap)
  
            # 'i' is used to get all adjacent vertices of a vertex
            for v, weight in self.adj[curr]:
                # If there is a shorter path to v through u.
                if dist[v] > dist[curr] + weight:
                    # Updating distance of v
                    dist[v] = dist[curr] + weight
                    heapq.heappush(pq, (dist[v], v))
```

3594: [https://leetcode.com/problems/minimum-time-to-transport-all-individuals/description/](https://leetcode.com/problems/minimum-time-to-transport-all-individuals/description/)

### Topological Sort

```python
class Solution:

    def build_graph(self, node_number: int, edges: List[List[int]]):
        graph = {n: [] for n in range(node_number)}
        for x, y in edges:
            graph[x].append(y)
            graph[y].append(x)
        return graph
    
    def build_dist_map(self, node_number: int, graph):
        dist_map = {n: 0 for n in range(node_number)}
        for node in graph:
            for neighbor in graph[node]:
                dist_map[neighbor] += 1
        return dist_map
        
    def topo_sort(self, node_number: int, graph):
        dist_map = self.build_dist_map(node_number, graph)
        queue = collections.deque()
        orders = []
        for node in dist_map:
            if dist_map[node] == 0:
                queue.append(node)

        while queue:
            curr = queue.popleft()
            orders.append(curr)
            for neighbor in dist_map[curr]:
                dist_map[neighbor] -= 1
                if dist_map[neighbor] == 0:
                    queue.append(neighbor)
        if len(orders) != node_number:
            return got_loop
        return orders
                
```

1136 and Cycle Detection [https://leetcode.com/problems/parallel-courses/description/](https://leetcode.com/problems/parallel-courses/description/)

## DFS (Backtracking | Recursion)



## Dynamic Programming

Basic Question

## Heap (Priority Queue)



## Lexicographically Next

## LinkedList

## LongestIncreasingSubsequence (Russia Doll)

## Monostack

## Named Algorithms

### Kadane's

## OrderedDict | SortedSet | Bisect



## Prefix\_sum

### Prefix\_prod

### Prefix\_Xor



## Sweeping Lines | Linear Scan

## Two Pointers

## TrieNode

## Union Find





