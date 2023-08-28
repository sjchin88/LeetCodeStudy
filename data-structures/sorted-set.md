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

```java
// Initialize
TreeSet<Type> ts = new TreeSet<>();

// add
ts.add(element);

// Range check
// Returns the least element in this set greater than or equal to the given element, 
// or null if there is no such element.
ts.ceiling(element); 

// Returns the greatest element in this set less than or equal to the given element, 
// or null if there is no such element.
ts.floor(element);

// Say we have a range lowerBound, upperBound
if (ts.floor(upperBound) == null || ts.floor(upperBound) < lowerBound){
    // no item in range due to 
    // either no element that is less than or equal to the upperBound or 
    // the greatest element is less than the lowerBound
}

```

For python,&#x20;

One implementation provided by the custom library [https://grantjenks.com/docs/sortedcontainers/](https://grantjenks.com/docs/sortedcontainers/)

```python
#Import
from sortedcontainers import SortedSet

#initialize
ss = SortedSet(iterable)

#add
ss.add(element)

# find next bigger or equal idx, same as ts.ceiling
idx = ss.bisect_left(value)

# find next smaller or equal idx, same as ts.floor
idx = ss.bisect_right(value)
```
