---
description: Common application - Least Recently Used (LRU) cache
---

# LinkedHashMap / OrderedDict

Common APIs .&#x20;

{% embed url="https://docs.oracle.com/javase/8/docs/api/java/util/LinkedHashMap.html" %}
Java API&#x20;
{% endembed %}

{% embed url="https://docs.python.org/3/library/collections.html#collections.OrderedDict" %}
Python OrderedDict API
{% endembed %}

|                | Java                                                                                                                                                                                                                                             | Python                                                                         |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ |
| Initialization | [LinkedHashMap](https://docs.oracle.com/javase/8/docs/api/java/util/LinkedHashMap.html#LinkedHashMap-int-float-boolean-)[(<mark style="color:green;">int initialCapacity, float loadFactor, boolean accessOrder</mark>)](#user-content-fn-1)[^1] | OrderedDict()                                                                  |
| put            | LHM.put(key, value)                                                                                                                                                                                                                              |                                                                                |
| get            | LHM.get(key, value)                                                                                                                                                                                                                              |                                                                                |
| move\_to\_end  |                                                                                                                                                                                                                                                  | od.move\_to\_end(key, last = True)                                             |
| popitem        |                                                                                                                                                                                                                                                  | od.popitem( last = False)      #return first item as FIFO if last is FalsFalse |

Practise Questions (Medium)

[https://www.lintcode.com/problem/685/](https://www.lintcode.com/problem/685/)

[^1]: all arguments are optional

    accessOrder = true means whenever we call get / put, the last accessed item will be placed last. When accessOrder = false, the order follows the insertion order
