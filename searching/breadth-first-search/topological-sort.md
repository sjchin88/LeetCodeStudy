# Topological Sort

## Algorithms

### Python&#x20;

```python
class Solution:

    def build_graph(self, node_number: int, edges: List[List[int]]):
        graph = {n: [] for n in range(node_number)}
        for x, y in edges:
            graph[x].append(y)
            graph[y].append(x)
        return graph
    
    def build_dist_map(self, node_number: int, graph):
        dist_map = {n: 0 for n in range(node_number)}
        for node in graph:
            for neighbor in graph[node]:
                dist_map[neighbor] += 1
        return dist_map
        
    def topo_sort(self, node_number: int, graph):
        dist_map = self.build_dist_map(node_number, graph)
        queue = collections.deque()
        orders = []
        for node in dist_map:
            if dist_map[node] == 0:
                queue.append(node)

        while queue:
            curr = queue.popleft()
            orders.append(curr)
            for neighbor in dist_map[curr]:
                dist_map[neighbor] -= 1
                if dist_map[neighbor] == 0:
                    queue.append(neighbor)
        if len(orders) != node_number:
            return got_loop
        return orders
                
```
