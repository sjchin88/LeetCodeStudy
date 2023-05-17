# Dijkstra’s Algorithm

```python
// Some code
def shortest_path(self, src: int):
        # Create a priority queue to store vertices that are being preprocessed
        heap = []
        heapq.heappush(heap, (0, src))
  
        # Create a vector for distances and initialize all distances as infinite (INF)
        dist = [math.inf] * V
        dist[src] = 0
  
        while heap:
            # The first vertex in the pair is the minimum distance vertex, 
            # extract it from the heap
            # vertex label is stored in the second of the pair
            distance, curr = heapq.heappop(heap)
  
            # 'i' is used to get all adjacent vertices of a vertex
            for v, weight in self.adj[curr]:
                # If there is a shorter path to v through u.
                if dist[v] > dist[curr] + weight:
                    # Updating distance of v
                    dist[v] = dist[curr] + weight
                    heapq.heappush(pq, (dist[v], v))
```
