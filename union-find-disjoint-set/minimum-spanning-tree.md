# Minimum Spanning Tree

## Kruskal Algorithm

1. Sort all edges according to their weightage from small to large
2. Starting from the smallest weight edge, try to add the edge to the tree
   1. If the nodes are not connected in the formed tree (use Union Find)
   2. If the nodes are connected, the edge is useless (and should be discard)
3. After looping through all the edges,
   1. Check if the formed tree covered all nodes required
