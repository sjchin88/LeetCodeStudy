# Sorted Set

## Time Complexities

Insert/Search/Delete - O(logn)&#x20;

Finding next greater / next smaller element - O(logn)



In Java, sorted set is implemented by TreeSet()

The underlying data structure is TreeMap(); which is implemented by a Red Black Tree

* Each tree node is colored either _red_ or _black_.
* The _root_ node of the tree is always _black_.
* Every path from the root to any of the leaf nodes must have the same number of black nodes.
* No two red nodes can be _adjacent_, i.e., a red node cannot be the parent or the child of another red node.
