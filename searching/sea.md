# Priority Queue / Heap

## Time Complexities

heapify = O(n)

insertion/deletion = O (log n)&#x20;

top = O(1)

Limitation = The rest of the items are not sorted, searching become O(n)

## Good for / When to use

* Maintaining top k smallest / biggest element
  * The value of the top (Kth smallest / K th biggest) can be useful
* Finding new max / min after insert a new element in O(log k) -> k = size of heap
  * This is ideal for working with data stream or linear scan of array
  * sorted array can find the relative position of new items in O(log n) through binary search, but inserting them and maintain the sorted list will cost O(n)



## Java

Java Priority Queue implementation. [https://www.freecodecamp.org/news/priority-queue-implementation-in-java/](https://www.freecodecamp.org/news/priority-queue-implementation-in-java/)

Calling Code:

```java
Queue<String> testStringsPQ = new PriorityQueue<>(); 
```

Ordering: a default natural ordering unless we use a **comparator.**&#x20;

{% embed url="https://www.geeksforgeeks.org/comparator-interface-java/" %}

## Python

```python
# code for heap operation
# note Python has only min_heap
import heapq
heap = []

# heapify
heapq.heapify(heap)

# Push new item
heapq.heappush(heap, new_item)

# Pop item
heapq.heappop(heap)

# Replace item, faster than pop then push
heapq.heapreplace(heap, new_item)

# Get the top 
heap[0]


```

## Example Problems:

Leetcode Collections: [https://leetcode.com/explore/learn/card/heap/646/practices/](https://leetcode.com/explore/learn/card/heap/646/practices/)

253\. Meeting Rooms II

{% embed url="https://leetcode.com/problems/meeting-rooms-ii/" %}

Solution Explanation :&#x20;

1. For every new meeting room request, we compare the starting time of the request with the top element (earliest ending time of all accommodated requests) to see if we can accommodate the new meeting request without the need to use an additional meeting room.&#x20;
2. If the start time > the earliest end time, remove the top element and add a new element with the end time of the new request into the priority queue.&#x20;
3. If the start time < earliest end time, add a new element with the end time of the new request into the priority queue.&#x20;
4. In the end, the heap size determines how many meeting rooms are required to accommodate all meeting requests.&#x20;

Algorithms:

1. Sort the given meeting requests by their start time
2. Initialize a priority queue (min-heap) and add the first meeting's ending time to the queue.&#x20;
3. For every other meeting request, check if the first room (earliest ending time) of the heap is available (where ending time < start time of new meeting request).&#x20;
4. &#x20;Remove the top and add the new meeting end time if available. Else simply add the new meeting end time (request a new room)
5. Return the size of the heap

### Hard

LeetCode 2519: [https://leetcode.com/problems/count-the-number-of-k-big-indices/](https://leetcode.com/problems/count-the-number-of-k-big-indices/)
