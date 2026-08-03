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

Can be done using stack (First-in-Last-Out FILO) or recursion

binary tree (or tree) problem

combination problem - Finding all possible solutions

permutation problem - Finding all permutations

finding the best combination / permutation.

Note:

* if the target is just to count the number of solution/ permutation, dp could be better&#x20;
* for best combination / permutation , dp only work if there is certain restriction in the order (like contiguous subarray/substring  or subsequence. For subset, dp unlikely to work
* Sometime we can use binary search to set for potential limit to aid in pruning.&#x20;

#### Complexities

Time complexities = O( k ^ n )  => where&#x20;

n = max number of elements of each path,&#x20;

k = max possible option of each path.&#x20;

Therefore if n is unbound , even with small k (like 2) , the time complexity can be very huge.&#x20;

For combination problem, this is O(2 ^ n)&#x20;

For permutation problem, this is O(n!)

Space complexities => similar to time complexities.&#x20;

#### Things to note

1. Think carefully about how to store the state of the visited node (for example, the N-Queens problem)
2. Need to consider pruning early as soon as we found the first result. If we are looking for optimize dfs order that can produce the best result, think if there is a way to verify if it is possible to achieve better and stop if it doesnt.  (for example, [https://www.lintcode.com/problem/570](https://www.lintcode.com/problem/570), 3530 - [https://leetcode.com/problems/maximum-profit-from-valid-topological-order-in-dag/description/](https://leetcode.com/problems/maximum-profit-from-valid-topological-order-in-dag/description/))
3. Try 301 , [https://leetcode.com/problems/remove-invalid-parentheses/](https://leetcode.com/problems/remove-invalid-parentheses/)

#### Solving Steps

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

## Dynamic Programming

Basic Question

## Heap (Priority Queue)

#### Time Complexities

heapify = O(n)

insertion/deletion = O (log n)&#x20;

top = O(1)

Limitation = The rest of the items are not sorted, searching become O(n)

#### Good for / When to use

* Maintaining top k smallest / biggest element
  * The value of the top (Kth smallest / K th biggest) can be useful
* Finding new max / min after insert a new element in O(log k) -> k = size of heap
  * This is ideal for working with data stream or linear scan of array
  * sorted array can find the relative position of new items in O(log n) through binary search, but inserting them and maintain the sorted list will cost O(n)&#x20;

```python
# code for heap operation
# note Python has only min_heap
import heapq
heap = []

# heapify
heapq.heapify(heap)

# Push new item
heapq.heappush(heap, new_item)

# Pop item
heapq.heappop(heap)

# Replace item, faster than pop then push
heapq.heapreplace(heap, new_item)

# Get the top 
heap[0]


```

Practise:&#x20;

253 [https://leetcode.com/problems/meeting-rooms-ii/description/](https://leetcode.com/problems/meeting-rooms-ii/description/)

## Lexicographically Next

<figure><img src="../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

* Iterate from the end (n - 1) till 0, find i-1 where a\[i-1] < a\[i]
* Iterate again from the end (n - 1) till i, find j where a\[j] > a\[i-1]
* swap a\[i-1] with a\[j]
* reverset a\[i] till the end

Practise question:

/leetcode.com/problems/next-greater-element-iii/description/

## LinkedList

```python
## Detect cycle
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def detectCycle(self, head: Optional[ListNode]) -> Optional[ListNode]:
        if not head:
            return None
        if head.next == head:
            return head
        fast = head
        slow = head
        cycle = False
        while fast.next and fast.next.next:
            fast = fast.next.next
            slow = slow.next
            if fast == slow:
                cycle = True
                break
        if not cycle:
            return None
        fast = head
        while fast != slow:
            fast = fast.next
            slow = slow.next
        return fast
```

## LongestIncreasingSubsequence (Russia Doll)

this algorithm does not always generate a valid subsequence of the input, but the length of the subsequence will always equal the length of the longest increasing subsequence

```python
class Solution:
    def lengthOfLIS(self, nums: List[int]) -> int:
        sub = []
        for num in nums:
            i = bisect_left(sub, num)

            # If num is greater than any element in sub
            if i == len(sub):
                sub.append(num)
            
            # Otherwise, replace the first element in sub greater than or equal to num
            else:
                sub[i] = num
        
        return len(sub)
```

## Monostack

#### Used For

* Finding the previous smaller/larger element or the next smaller/larger element for all elements in the array in O(n) time.&#x20;
  * Stored them in the array to be queried in O(1) time.
* Maintain Local Min / Max element within a given range in O(1) time



#### Property

* All elements on the queue/stack are strictly increasing or decreasing&#x20;
* Allow finding of previous smaller/larger element in O(1) time
* Python deque structure can be used to access the bottom (left) of the stack in O(1) -> Useful if we need to maintain and keep the order for k elements&#x20;

<figure><img src="../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

```python
# Previous Less Element
## the stack store the previous lesser element(ple) index
def find_ples(nums:List[int]) -> List[int]:
    ples = [default value] * len(nums)
    stack = collections.deque()
    for i, num in enumerate(nums):
        while stack and nums[stack[-1]] >= num:
            stack.pop()
        if stack:
            ples = stack[-1]
        stack.append(i)
    return ples

##the stack store the next lesser element(nle) index
def find_nles(nums:List[int]) -> List[int]:
    nles = [default value] * len(nums)
    stack = collections.deque()
    # Example, nums = [3, 2, 3]
    # starting from 3, 
    # the stack is empty (no update), add 3 -> stack = [3]
    # next iterate till 2, stack top (3) is > 2, 
    # pop the stack and update the idx nles[0] to be 1
    # last iteration, stack top (2) is not > 3, no update
    for i, num in enumerate(nums):
        while stack and nums[stack[-1]] > num:
            prev = stack.pop()
            nles[prev] = i
        stack.append(i)
    return nles
```

## Named Algorithms

### Kadane's

```py
class Solution:
    def maxSubArray(self, nums: List[int]) -> int:
        # Initialize our variables using the first element.
        current_subarray = max_subarray = nums[0]

        # Start with the 2nd element since we already used the first one.
        for num in nums[1:]:
            # If current_subarray is negative, throw it away. Otherwise, keep adding to it.
            current_subarray = max(num, current_subarray + num)
            max_subarray = max(max_subarray, current_subarray)

        return max_subarray
```

## OrderedDict&#x20;

maintain the order of the dict  (typically use LinkedList), so that we can achieve the following operations efficiently

1. find/update the key: value pair in O(1)
2. move any element to the end in O(1)
3. delete the first/last element in O(1)

Note: &#x20;

* A list / deque can perform 2 and 3 in O(1) but will take O(n) to do 1
* A dict will do 1 in O(1) but cannot perform 2 and 3 (as dict don't keep order history)

<figure><img src="../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>



## Prefix\_sum

The value of **prefixSum\[i]** is **arr\[0] + arr\[1] + arr\[2] . . . arr\[i]**

the **sum of subarray \[i, j]** (inclusive) is **prefixSum\[j] - prefixSum\[ i - 1]**

This is useful if&#x20;

* Given two position i, j  where i <= j, we want to quickly find the sum between i & j (all unclusive)
  * when we need to iterate through the sum of subarray for i , j in range of (0, n)
* Or given j, we want to quickly find out previous position i where the subarray i -> j satisfy specific conditions
  * subarray i -> j satisfy the condition where sum == k. (find i through sum\_till\_j - k )
  * subarray i -> j satisfy the condition where sum % k == 0 . (find i where the remainder is equal to sum\_till\_j % k, then the sum between is divisible by k).&#x20;
  * subarray i -> j satisfy the condition where count\_a == count\_b .&#x20;
    * find i where a tuple/number depicting relative relationship between count\_a and count\_b are equal (like a - b).&#x20;
    * can be expand to count more than two elements.&#x20;

Quick Practise:

325 . [https://leetcode.com/problems/maximum-size-subarray-sum-equals-k/description/](https://leetcode.com/problems/maximum-size-subarray-sum-equals-k/description/)

### Prefix\_prod

1352 [https://leetcode.com/problems/product-of-the-last-k-numbers/description/](https://leetcode.com/problems/product-of-the-last-k-numbers/description/)

### Prefix\_Xor

1310 [https://leetcode.com/problems/xor-queries-of-a-subarray/description/](https://leetcode.com/problems/xor-queries-of-a-subarray/description/)

## SortedSet | Bisect

Insert/Search/Delete - O(logn)&#x20;

Finding next greater / next smaller element - O(logn)

For python,&#x20;

One implementation provided by the custom library [https://grantjenks.com/docs/sortedcontainers/](https://grantjenks.com/docs/sortedcontainers/)

```python
# 
#Import
from sortedcontainers import SortedSet

#initialize
ss = SortedSet(iterable)

#add
ss.add(element)

# find next bigger or equal idx, same as ts.ceiling
idx = ss.bisect_left(value)

# find next smaller or equal idx, same as ts.floor
idx = ss.bisect_right(value)
```

## Sweeping Lines | Linear Scan

## Two Pointers

## TrieNode

#### **Application**

1. Checking if the prefix/word exists in the dictionary
   1. Fastest in finding common prefix - putting the words into the Trie one by one, and find the max/min common prefix of the new word with the previous word
2. Perform DFS on the trie
   1. When we want to dfs based on the prefix, to check if the prefix can lead to a word will need O(L)
   2. But if we already at the node of previous character in the Trie, to check if the next character can lead to a word will only need O(1) time
3. Used to optimize other algorithms (like DP) to check the prefix/word quickly
   1. When we have a set of words with some common prefix, and we need to dp based on the word and target
   2. Like all words that can be transformed into target with less than or equal to k operation&#x20;

```python
class TrieNode:
    def __init__(self):
        self.children = {}
        self.is_word = False
        self.word = None

class Trie:
    def __init__(self):
        self.root = TrieNode()
    
    def get_root(self):
        return self.root
        
    def insert(self, word:str):
        node = self.root
        for i in range(len(word)):
            if word[i] not in node.children:
                node.children[word[i]] = TrieNode()
            node = node.children[word[i]]
        node.is_word = True
        node.word = word
```

Quick Practise

112 . Trie + DFS [https://leetcode.com/problems/word-search-ii/description/](https://leetcode.com/problems/word-search-ii/description/)

## Union Find

#### Applications

Support the following two useful operations in near O(1) times  (actual is close to O(log n)

1. find(x) - determine which subset an element is in
2. union(x, y) - merge the subset x in and the subset y in into a single set&#x20;

Efficient in&#x20;

adding edges to a graph,&#x20;

determine if the existing nodes and edges form a tree&#x20;

and if there is any cycle when want to add new edges

```python
# Template for union find (Unknown size)
class UnionFind:
    def __init__(self):
        self.parents = {}
        self.set_sizes = {}
        self.num_sets = 0
    
    def insert(self, x):
        if x in self.parents:
            return
        self.parents[x] = None
        self.set_sizes[x] = 1
        self.num_sets += 1
    
    def find(self, x):
        if x not in self.parents:
            return None
        root = x
        while self.parents[root] != None:
            root = self.parents[root]
        
        #Update each parent along the chain to compress the search time later
        curr = x
        while curr != root:
            ori_parent = self.parents[curr]
            self.parents[curr] = root
            curr = ori_parent
        return root
        
    def is_connected(self, x, y):
        #self to self is connected
        if x == y:
            return True
        root_x = self.find(x)
        root_y = self.find(y)
        # If either x or y not exist
        if root_x == None or root_y == None:
            return False
        return root_x == root_y
        
    def add_edge(self, x, y):
        self.insert(x)
        self.insert(y)
        root_x = self.find(x)
        root_y = self.find(y)
        #Very Important to avoid self-pointing at root
        if root_x != root_y:
            self.parents[root_x] = root_y
            self.num_sets -= 1
            self.set_sizes[root_y] = self.set_sizes[root_x] + self.set_sizes[root_y]
    
    def get_set_size(self, x):
        root = self.find(x)
        if root == null:
            return 0
        return self.set_sizes[self.find(x)]
        
        
```

Union Find Algorithm, Known size

```python
class UnionFind:
    def __init__(self, n: int):
        # parent[i] stores the parent of node i
        # Initially, every node is its own parent
        self.parent = list(range(n))
        
        # size[i] tracks the size of the union set
        self.size = [1] * n

    def find(self, i: int) -> int:
        """Finds the root of node i with Path Compression."""
        if self.parent[i] == i:
            return i
        
        # Path Compression: points parent directly to the ultimate root
        self.parent[i] = self.find(self.parent[i])
        return self.parent[i]

    def union(self, i: int, j: int) -> bool:
        """Unites sets containing i and j using Union by Rank."""
        root_i = self.find(i)
        root_j = self.find(j)

        if root_i == root_j:
            return False  # Already in the same set
        
        # else
        self.parent[root_i] = root_j
        self.size[root_j] += self.size[root_i]
        return True

    def connected(self, i: int, j: int) -> bool:
        """Checks if nodes i and j belong to the same component."""
        return self.find(i) == self.find(j)
```

Quick Practise

* [https://leetcode.com/problems/making-a-large-island/description/](https://leetcode.com/problems/making-a-large-island/description/)

