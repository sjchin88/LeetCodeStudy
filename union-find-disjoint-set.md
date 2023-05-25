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

## Practice Problem

### Hard

803  [https://leetcode.com/problems/bricks-falling-when-hit/submissions/](https://leetcode.com/problems/bricks-falling-when-hit/submissions/)

Ideas : Use Union Find in reverse order of hit. The Union Find will include a roof point (-1, -1) for others to attach to, it will record parent and set\_size information.&#x20;

First, add all the remaining bricks minus the hit bricks to the union.&#x20;

Second, in reverse order, add the hit brick back into the union one by one.

* Skip the addition if the hit brick is not there originally (empty hit)
* Rotate across all four directions to merge with neighbor bricks&#x20;
* merge with roof (-1, -1) if the hit brick is at row 0

The number of brick drop is then = set\_size(roof) before\_hit - set\_size(roof) after\_hit - 1

Add the hit brick back into the remain

```python
// Some code
#Normal Union Find structure, 
class UnionFind:
    
    # To avoid bugs
    # Insert roof at the beginning
    # Note the parent of roof may point to other points
    def __init__(self):
        self.parents = {}
        self.set_size = {}
        self.insert((-1, -1))
    
    def insert(self, x):
        if x not in self.parents:
            self.parents[x] = None
            self.set_size[x] = 1
    
    def find(self, x):
        if x not in self.parents:
            return None
        
        root = x
        while self.parents[root] != None:
            root = self.parents[root]
        
        curr = x
        while curr != root:
            ori_parent = self.parents[curr]
            self.parents[curr] = root
            curr = ori_parent
        return root
    
    def merge(self, x, y):
        self.insert(x)
        self.insert(y)
        root_x = self.find(x)
        root_y = self.find(y)
        if root_x != root_y:
            if self.set_size[root_x] > self.set_size[root_y]:
                self.merge(y, x)
                return 
            self.parents[root_x] = root_y
            self.set_size[root_y] += self.set_size[root_x]
        
    def get_size(self, x):
        return self.set_size[self.find(x)]



import copy
class Solution:
    def hitBricks(self, grid: List[List[int]], hits: List[List[int]]) -> List[int]:
        
        # Get the remaining bricks after hit
        remain = copy.deepcopy(grid)
        for row, col in hits:
            remain[row][col] = 0
        
        uf = UnionFind()
        
        # stick the bricks to the wall or together with top and left brick
        for r, rows in enumerate(remain):
            for c, val in enumerate(rows):
                if val == 1:
                    if r == 0:
                        uf.merge((-1, -1), (r, c))
                    if r > 0 and remain[r-1][c] == 1:
                        uf.merge((r, c), (r-1, c))
                    if c > 0 and remain[r][c - 1] == 1:
                        uf.merge((r, c), (r, c-1))
        
        # Starting from reverse, add the hit brick back one by one
        ans = []
        
        for row, col in reversed(hits):
            # skip if original brick is empty
            if grid[row][col] == 0:
                ans.append(0)
                continue
                
            # get size after hit
            after_hit = uf.get_size((-1, -1))

            # iterate through possible next 
            for brick in self.next_bricks(row, col, remain):
                uf.merge((row, col), brick)
            
            # Get size before hit and add the hit brick back to remain
            before_hit = uf.get_size((-1, -1))
            ans.append(max(0, before_hit - after_hit - 1))
            remain[row][col] = 1
        
        # remember to reverse the answer
        return ans[::-1]
            
    def next_bricks(self, row, col, grid: List[List[int]]):
        directions = [(-1, 0), (1, 0), (0, -1), (0, 1)]
        row_limit = len(grid)
        col_limit = len(grid[0])
        next_brick = []
        
        # default to roof (-1, -1) if row == 0
        if row == 0:
            next_brick.append((-1, -1))
        
        # if next position within range and contain brick
        for dr, dc in directions:
            new_r = row + dr
            new_c = col + dc
            #print(new_r, new_c)
            if new_r < 0 or new_r >= row_limit:
                continue
            if new_c < 0 or new_c >= col_limit:
                continue
            if grid[new_r][new_c] == 0:
                continue
            next_brick.append((new_r, new_c))

        return next_brick
```



