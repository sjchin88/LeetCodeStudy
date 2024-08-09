# Binary Search Tree

A `binary search tree` (BST), a special form of a binary tree satisfies the binary search property:

1. The value in each node must be `greater than` (or equal to) any values stored in its left subtree.
2. The value in each node must be `less than` (or equal to) any values stored in its right subtree.

## Algorithm to check if BST is valid

```python
    
    def isValidBSTCheck(self, root: Optional[TreeNode], left_bound, right_bound) -> bool:
        if not root:
            return True
        if root.val <= left_bound or root.val >= right_bound:
            return False
        return self.isValidBSTCheck(root.left, left_bound, root.val) and 
        self.isValidBSTCheck(root.right, root.val, right_bound)
```

## Algorithm to find in order Successor

```python

def find_successor(root: Optional[TreeNode], p: TreeNode) -> TreeNode:
    successor = None
    while root:
        if root.val <= p.val:
            root = root.right
        else:
            successor = root
            root = root.left
    return successor
```

## Algorithm for inorder traversal in iterative mode

```python

def inorder_traversal(root: Optional[TreeNode]) -> List[int]:
    result = []
    curr = root
    stack = []
    while curr or stack:
        while curr:
        # keep going left till the end
            stack.append(curr) 
            curr = curr.left
        # Add the first value from the stack 
        curr = stack.pop()
        result.append(curr.val)
        
        # switch to the right branch
        curr = curr.right 
        
    # if the right branch is null, the while loop will pop the next item from the stack
    return result
```

## Find k-smallest&#x20;

```python
# In order traversal, using yield and next function of python
def solution(root, K):
    def dfs(node):
        if node:
            yield from dfs(node.left)
            yield node.value
            yield from dfs(node.right)
    
    f = dfs(root)
    for _ in range(K):
        ans = next(f)
    return ans
```

## Inserting new node

```python
// Some code
def insertIntoBST(self, root: Optional[TreeNode], val: int) -> Optional[TreeNode]:
        if not root:
            return TreeNode(val)
        parent = root
        curr = root
        while curr:
            parent = curr
            if curr.val < val: 
                curr = curr.right
            else:
                curr = curr.left
        if parent.val < val:
            parent.right = TreeNode(val)
        else:
            parent.left = TreeNode(val)
        return root
```

## Deleting Node

```python
// Some code
def deleteNode(self, root: Optional[TreeNode], key: int) -> Optional[TreeNode]:
        if not root:
            return root
        if root.val == key:
            if not root.left:
                return root.right
            elif not root.right:
                return root.left
            else:
                successor = root.right
                while successor.left:
                    successor = successor.left
                root.val = successor.val
                root.right = self.deleteNode(root.right, successor.val)
        elif root.val < key:
            root.right = self.deleteNode(root.right, key)
        else:
            root.left = self.deleteNode(root.left, key)
        return root
```
