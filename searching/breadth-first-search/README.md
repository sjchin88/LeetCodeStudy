# Breadth First Search

## Applications&#x20;

* Iteration of all possible answers (whether the nodes are connected etc)
* Topological sorting
* Search by layer / Traveling by a layer of a tree (Binary Tree)
* Simple graph shortest path
* Finding the longest diameter in binary / N-ary tree (use double BFS, first BFS find the first end, second BFS starting from the first end to find the second end)
* If you are working with 2-D grid / matrix, bfs is usually the better and only choice compared to dfs.&#x20;
* Sometimes we can use binary search to set a condition and check if the condition can be met using bfs to find solution in O((n + m) log (n)) time.&#x20;

## Complexity

·       O(n + m), n is the number of nodes, m is the edge

·       O(n) space

## Useful Techniques

### To Handle 2-D points

* Python - used a tuple
* Java  - choices of&#x20;
  * compressed 2-D into 1-D -> (x, y) -> (x \* columnLength + y)
  * Use a 2-D arrays to marked as visited

### Possible arrangements in a chessboard

* compressed the state into 1-D array&#x20;
* Precalculate possible moves (swaps) to save computation times
* stored tuple in the dist\_map / visited set()
* Practise
  * [https://www.lintcode.com/problem/794/](https://www.lintcode.com/problem/794/)
  * 773 Sliding Puzzle [https://leetcode.com/problems/sliding-puzzle/](https://leetcode.com/problems/sliding-puzzle/)

### Use heap in place of the queue for shortest path problem

* explore the extension from the known shortest path first
* Reducing time & space complexity
* Practice:&#x20;
  * 499 The Maze III [https://leetcode.com/problems/the-maze-iii/](https://leetcode.com/problems/the-maze-iii/)
    * Keys :&#x20;
    * Store the shortest distance and **lexicographically minimum path in as a tuple in a dict.** Guarantee to keep the shortest distance or minimum path among the shortest distance
    * Use a heap in place of a queue for bfs&#x20;
    * Roll till the end and check the endpoint only&#x20;





## Algorithm

### Basic Version

#### Python

```python
// BFS Basic version

def bfs():
    
    # Initialize the queue and visited set
    queue = collections.deque()
    visited = set()
    
    # Put in the starting node
    if first_node:
        queue.append(first_node)
        visited.add(first_node)
        
    # while loop iteration
    while queue:
        curr = queue.popleft()
        
        for next_point in self.get_next(curr):
        
            # function self.is_valid can check if the next point is within the boundary
            # and not visited
            if self.is_valid(next_point):
            
                # Add to queue and visited together
                queue.append(next_point)
                visited.add(next_point)
        
```

#### Java

```java
// BFS Basic version (Java)
public void bfs(){
    //Initialize the queue and visited set
    Queue<Type> queue = new ArrayDeque<>();
    Set<Type> visited = new HashSet<>();
    
    //Put in the starting node
    if (firstNode != null){
        queue.offer(firstNode);
        visited.add(firstNode)
    }
        
    //while loop iteration
    while (! queue.isEmpty()){
        Type curr = queue.poll()
        
        // Get the next points
        for (Type nextPoint: getNext(curr)){
        
            //function self.is_valid can check if the next point is within the boundary
            // and not visited
            if (isValid(nextPoint)){
            
                // Add to queue and visited together
                queue.offer(nextPoint);
                visited.add(nextPoint);
            }
        }
    }     
}
```

### Advance Version 1 - Using queue size and for loop to iterate by layer

#### Python

```python
// BFS Advance Version 1 - Using queue size and for loop to iterate by layer

def bfs():
    
    # Initialize the queue and visited set
    queue = collections.deque()
    visited = set()
    
    # Put in the starting node
    if first_node:
        queue.append(first_node)
        visited.add(first_node)
        
    # while loop iteration
    while queue:
        
        # Get the current queue size and run a for-loop iteration
        q_size = len(queue)
        
        # in python, range(value) will take in value once and keep it without 
        # checking back
        for i in range(q_size):
            curr = queue.popleft()
            
            for next_point in self.get_next(curr):
            
                # function self.is_valid can check if the next point is within the boundary
                # and not visited
                if self.is_valid(next_point):
                
                    # Add to queue and visited together
                    queue.append(next_point)
                    visited.add(next_point)
        
```

#### Java

```java
// BFS Advance version 1 Java
public void bfs(){
    //Initialize the queue and visited set
    Queue<Type> queue = new ArrayDeque<>();
    Set<Type> visited = new HashSet<>();
    
    //Put in the starting node
    if (firstNode != null){
        queue.offer(firstNode);
        visited.add(firstNode)
    }
        
    //while loop iteration
    while (! queue.isEmpty()){
        int size = queue.size()
        
        for (int i = 0; i < size; i++){
            Type curr = queue.poll()
            
            // Get the next points
            for (Type nextPoint: getNext(curr)){
            
                //function self.is_valid can check if the next point is within the boundary
                // and not visited
                if (isValid(nextPoint)){
                
                    // Add to queue and visited together
                    queue.offer(nextPoint);
                    visited.add(nextPoint);
                }
            }
        }
    }     
}
```

### Advance Version 2 - Dist Map (Mostly used)

#### Python

<pre class="language-python"><code class="lang-python">// BFS Advance Version 2
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
<strong>            if self.is_valid(next_point):  
</strong><strong>            
</strong>                # Add to queue and visited together
                queue.append(next_point)
                dist_map[next_point] = dist_map[curr] + 1 
            
        
</code></pre>

#### Java

```java
// BFS Advance Version 2 (Java)
// Use a dist map to store the distance

public void bfs(){
    //Initialize the queue and visited set
    Queue<Type> queue = new ArrayDeque<>();
    Map<Type, Integer> distMap = new HashMap<>();
    
    //Put in the starting node
    if (firstNode != null){
        queue.offer(firstNode);
        distMap.put(firstNode, 0);
    }
        
    //while loop iteration
    while (! queue.isEmpty()){
        Type curr = queue.poll()
        
        // Get the next points
        for (Type nextPoint: getNext(curr)){
        
            //function self.is_valid can check if the next point is within the boundary
            // and not visited
            if (isValid(nextPoint)){
            
                // Add to queue and visited together
                queue.offer(nextPoint);
                distMap.put(nextPoint, distMap.get(curr) + 1);
            }
        }
    }     
}
```

### Useful Technique to Handle 2-D points

* Python - used a tuple
* Java  - choices of&#x20;
  * compressed 2-D into 1-D -> (x, y) -> (x \* columnLength + y)
  * Use a 2-D arrays to marked as visited&#x20;

## Practise Questions

624  [https://www.lintcode.com/problem/624/](https://www.lintcode.com/problem/624/)



## Other Interesting Problem

Leetcode 296 [https://leetcode.com/problems/best-meeting-point/](https://leetcode.com/problems/best-meeting-point/)

If we try to find the best meeting point for all friends using Manhattan distance, one possible optimization is to separate 2-D problem into 1-D, ie, we only need to&#x20;

* find mid\_x such that sum of | x - mid\_x | is minimize and&#x20;
* find mid\_y such that sum of | y - mid\_y | is minimize
* We can group the x-coordinate and y-coordinate together in a frequency map
