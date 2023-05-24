# Union Find / Disjoint Set

## Applications

Support the following two useful operations in near O(1) times  (actual is close to O(log n)

1. find(x) - determine which subset an element is in
2. union(x, y) - merge the subset x in and the subset y in into a single set&#x20;

Efficient in&#x20;

adding edges to a graph,&#x20;

determine if the existing nodes and edges form a tree&#x20;

and if there is any cycle when want to add new edges

## Algorithm Template

```python
# Template for union find
class UnionFind:
    def __init__(self):
        self.parents = {}
    
    def insert(self, x):
        if x in self.parents:
            return
        self.parents[x] = None
    
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
        self.parents[root_x] = root_y
        
        
```

