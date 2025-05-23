# Segmented Tree

## Condition and Usage

Condition - length of array is fixed.&#x20;

Usage - when need to&#x20;

* frequently update the value of any position on the array
* while at the same time, retrieve results for a subarray interval (count subarrays meeting specific conditions, total of the interval etc)

## Key Characteristic

<figure><img src=".gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

Binary node tree to represent the entire array.&#x20;

Each node will store&#x20;

* Start position of array
* End position of the array
* Value for the entire segment (in this case is the total)
* Root to left node (min 1 or (n+1)//2 elements of the first half)
* Root to right node (remaining elements)



## Sample Code

```python
# Sample Python
class STNode:
    def __init__(self, start, end, x):
        self.start = start
        self.end = end
        # Here we store interval_sum, it could be anything
        self.interval_sum = x
        self.left = self.right = None

class SegmentTree:
    def __init__(self, nums, start, end):
        self.root = self.construct(nums, start, end)
        
    def construct(self, nums, start, end):
        if start > end:
            return None
        new_node = STreeNode(start, end, 0)
        if start != end:
            mid = start + (end - start) // 2
            new_node.left = self.construct(nums, start, mid)
            new_node.right = self.construct(nums, mid + 1, end)
            if new_node.left:
                new_node.interval_sum += new_node.left.interval_sum
            if new_node.right:
                new_node.interval_sum += new_node.right.interval_sum
        else:
            new_node.interval_sum = nums[start]
        return new_node
            
    def modify(self, root, index, value):
        if root.start == index and root.end == index:
            root.interval_sum = value
            return 
        mid = root.start + (root.end - root.start) // 2
        if root.start <= index <= mid:
            self.modify(root.left, index, value)
        if mid < index <= root.end:
            self.modify(root.right, index, value)
        root.interval_sum = root.left.interval_sum + root.right.interval_sum
    
    def query(self, root, start, end):
        if root.start == start and root.end == end:
            return root.interval_sum
        mid = root.start + (root.end - root.start) // 2
        result = 0
        if start <= mid < end:
            result += self.query(root.left, start, mid)
            result += self.query(root.right, mid + 1, end)
        elif start > mid:
            result += self.query(root.right, start, end)
        elif end <= mid:
            result += self.query(root.left, start, end)
        return result 
        

```

Example Problem

[https://leetcode.com/problems/find-x-value-of-array-ii/description/](https://leetcode.com/problems/find-x-value-of-array-ii/description/)
