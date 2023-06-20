# Shortest Path Fast Algorithm

## Key Concepts

Can use priority queue in place of queue to fasten up the search

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
