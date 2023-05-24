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

### Basic Version (Python)

```python
# Template for union find
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

### Basic Version (Java)

```java
// Some code
class UnionFind(){
    public Map<Integer, Integer> parents;
    public UnionFind(){
        this.parents = new HashMap<>();
    }
    
    public void insert(int x){
        if (this.parents.containsKey(x)){
            return;
        }
        this.parents.put(x, null);
    }
    
    public int find(int x){
        if (!this.parents.containsKey(x)){
            return null
        }
        int root = x
        while (this.parents.get(root) != null){
            root = this.parents.get(root);
        }
        
        //update the parent along the chain to compress for next time
        int curr = x
        while (curr != root){
            int oriParent = this.parents.get(curr);
            this.parents.put(curr, root);
            curr = oriParent;
        }
        return root
    }
    
    public boolean isConnected(int x, int y){
        int root_x = this.find(x);
        int root_y = this.find(y);
        if (root_x == null or root_y == null){
            return false;
        }
        return (root_x == root_y);
    }
    
    public void addEdge(int x, int y){
        this.insert(x);
        this.insert(y);
        int root_x = this.find(x);
        int root_y = this.find(y);
        if (root_x != root_y){
            this.parents.put(root_x, root_y);
        }
    }

}
```

