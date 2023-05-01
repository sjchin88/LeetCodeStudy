# Priority Queue / Heap

## Running Time

heapify = O(n)

insertion/deletion = O (log n)&#x20;

top = O(1)

## Java

Java Priority Queue implementation. [https://www.freecodecamp.org/news/priority-queue-implementation-in-java/](https://www.freecodecamp.org/news/priority-queue-implementation-in-java/)

Calling Code:

```java
Queue<String> testStringsPQ = new PriorityQueue<>(); 
```

Ordering: a default natural ordering unless we use a **comparator.**&#x20;

{% embed url="https://www.geeksforgeeks.org/comparator-interface-java/" %}

Example Problems:

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

