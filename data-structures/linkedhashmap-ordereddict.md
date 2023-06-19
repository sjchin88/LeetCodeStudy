---
description: Common application - Least Recently Used (LRU) cache
---

# LinkedHashMap / OrderedDict

## Problems It solved:

maintain the order of the dict  (typically use LinkedList), so that we can achieve the following operations efficiently

1. find/update the key: value pair in O(1)
2. move any element to the end in O(1)
3. delete the first/last element in O(1)

Note: &#x20;

* A list / deque can perform 2 and 3 in O(1) but will take O(n) to do 1
* A dict will do 1 in O(1) but cannot perform 2 and 3 (as dict don't keep order history)

Common APIs .&#x20;

{% embed url="https://docs.oracle.com/javase/8/docs/api/java/util/LinkedHashMap.html" %}
Java API&#x20;
{% endembed %}

{% embed url="https://docs.python.org/3/library/collections.html#collections.OrderedDict" %}
Python OrderedDict API
{% endembed %}

<table><thead><tr><th width="158.33333333333331"></th><th>Java</th><th>Python</th></tr></thead><tbody><tr><td>Initialization</td><td><a href="https://docs.oracle.com/javase/8/docs/api/java/util/LinkedHashMap.html#LinkedHashMap-int-float-boolean-">LinkedHashMap</a><a data-footnote-ref href="#user-content-fn-1">(<mark style="color:green;">int initialCapacity, float loadFactor, boolean accessOrder</mark>)</a></td><td>collections.OrderedDict()</td></tr><tr><td>put </td><td>LHM.put(key, value)</td><td></td></tr><tr><td>get</td><td>LHM.get(key, value)</td><td></td></tr><tr><td>move_to_end</td><td></td><td>od.move_to_end(key, last = True)</td></tr><tr><td>popitem</td><td></td><td>od.popitem( last = False)      #return first item as FIFO if last is False</td></tr></tbody></table>

Practise Questions (Medium)

[https://www.lintcode.com/problem/685/](https://www.lintcode.com/problem/685/)

[^1]: all arguments are optional

    accessOrder = true means whenever we call get / put, the last accessed item will be placed last. When accessOrder = false, the order follows the insertion order
