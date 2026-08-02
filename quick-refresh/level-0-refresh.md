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

### Bidirectional&#x20;

### Shortest Path

### Topological Sort

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





