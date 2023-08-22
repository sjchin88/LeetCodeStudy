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

{% embed url="https://www.lintcode.com/problem/685/" %}

## LRU Implementation&#x20;

Idea -> hashmap/dict to find the key - value pair in O(1)

Double linked list so we can remove any node in O(1)

```python
#ListNode for double linkedlist
class ListNode:
    def __init__(self, key=None, val=None):
        self.key = key
        self.val = val
        self.next = None
        self.prev = None

class LRUCache:
    def __init__(self, capacity: int):
        self.key2node = {}
        self.head = ListNode()
        self.tail = ListNode()
        self.head.next = self.tail
        self.tail.prev = self.head
        self.capacity = capacity
        
    def get(self, key: int) -> int:   
        if key not in self.key2node:
            return -1    
        curr_node = self.key2node[key]
        # Move the node to the last, retrive the value
        self.remove(curr_node)
        self.add(curr_node)
        return curr_node.val

    def put(self, key: int, value: int) -> None:
        if key in self.key2node:
            curr_node = self.key2node[key]
            self.remove(curr_node)
        
        new_node = ListNode(key, value)
        self.key2node[key] = new_node
        self.add(new_node)
        # Remove the first node (least recently used)
        if len(self.key2node) > self.capacity:
            lru_node = self.head.next
            self.remove(lru_node)
            del self.key2node[lru_node.key]
        
    def add(self, node):
        prev_end = self.tail.prev
        prev_end.next = node
        node.prev = prev_end
        node.next = self.tail
        self.tail.prev = node
        
    def remove(self, node):
        node.prev.next = node.next
        node.next.prev = node.prev
```

[^1]: all arguments are optional

    accessOrder = true means whenever we call get / put, the last accessed item will be placed last. When accessOrder = false, the order follows the insertion order
