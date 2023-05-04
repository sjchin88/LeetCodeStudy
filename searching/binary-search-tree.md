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
