# Shortest Path Fast Algorithm

## Key Concepts

Modified from Reference: [https://www.geeksforgeeks.org/shortest-path-faster-algorithm/](https://www.geeksforgeeks.org/shortest-path-faster-algorithm/)

1. Create a **hashmap / dict** to store the shortest distance of all vertex from the source vertex. Initialize this array by infinity except for **dict\[S]** = 0 where **S** is the source vertex.
2. Create a [queue](http://www.geeksforgeeks.org/queue-data-structure/)  **Q** and push starting source vertex in it.&#x20;
   * while Queue is not empty, do the following for each **edge**(u, v) in the graph&#x20;
     * If dict\[v] > dict\[u] + weight of edge(u, v)
       * dict\[v] = dict\[u] + weight of edge(u, v)
       * if vertex v not in the queue, push the vertex v into the Queue. (need an inQueue array / set() to keep track)

**Time Complexity:** \
**Average Time Complexity:** O(|E|) \
**Worst case Time Complexity**: O(|V|.|E|)&#x20;

Can use a priority queue / min\_heap in place of the queue to fasten up the search (which became Dijkstra algorithm with heap).&#x20;

1. Same as previous
2. Create a priority queue / min\_heap and push (0, S) in it
   * while pq/heap not empty, do the following for each edge(u, v) in the graph
     * If dict\[v] > dict\[u] + weight of edge(u, v):
       * dict\[v] = dict\[u] + weight of edge(u, v)
       * push (dict\[v], v) into the pq/heap

**Time Complexity:** \
**Average Time Complexity:** O(|E| log |E|) \
**Worst case Time Complexity**: O(|E| log |E|)&#x20;

## Algorithms

```python
#Original
def shortestPathFaster(S, V):
 
    # Create a hashmap to store the shortest distance
    d = { v: math.inf for v in V}
 
    # Boolean array to check if the vertex
    # is present in the queue or not
    inQueue = [False]*(V + 1)
 
    d[S] = 0
 
    queue = collections.deque()
    queue.append(S)
    inQueue[S] = True
 
    while queue:
        # Take the front vertex from Queue
        curr = queue.popleft()
        inQueue[curr] = False
 
        # Relaxing all the adjacent edges of
        # vertex taken from the Queue
        for i in range(len(graph[u])):
 
            v = graph[u][i][0]
            weight = graph[u][i][1]
 
            if (d[v] > d[u] + weight):
                d[v] = d[u] + weight
 
                # Check if vertex v is in Queue or not
                # If not then append it to the Queue
                if (inQueue[v] == False):
                    q.append(v)
                    inQueue[v] = True
```
