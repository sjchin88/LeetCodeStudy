# Tree Traversal

Preorder :  Root -> Left -> right

In order : Left -> Root -> Right

* Inorder is guaranteed to be sorted

Post order: Left -> Right -> Root

## Preorder traversal algorithm

```python
    def preorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        if not root:
            return []
        res = []
        stack = []
        stack.append(root)
        while stack:
            curr = stack.pop()
            res.append(curr.val)
            if curr.right:
                stack.append(curr.right)
            if curr.left:
                stack.append(curr.left)
        return res
```

Inorder Traversal



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

Post order traversal

```
     def postorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        if not root:
            return []
        res = []
        stack = []
        stack.append(root)
        while stack:
            curr = stack.pop()
            res.append(curr.val)
            if curr.left:
                stack.append(curr.left)
            if curr.right:
                stack.append(curr.right)
            
        return res[::-1]
```
