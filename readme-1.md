# Python Note

## String Operation

Python string is an immutable array. Swapping characters inside will incur O(n) where n = length of String. For more efficient operation consider using array instead of string

blue - optional argument, note start idx (inclusive) - end idx (exclusive)

**str. join**(iterable): join all elements in the iterable with str. Example: "".join(\[1, 2]) become 12

**str.capitalize()  :** Upper case the first letter

**str.count**(sub, <mark style="color:blue;">begin = 0, end = len(str)</mark>)  - returns the number of occurrences of a substring

**str.endswith**(suffix, <mark style="color:blue;">begin = 0, end = len(str)</mark>) - return true / false if the str end with suffix (a string)

**str.find**(sub, <mark style="color:blue;">begin = 0, end = len(str)</mark>) - return first found, if unfound, return - 1

**str.index**(sub,  <mark style="color:blue;">begin = 0, end = len(str)</mark>) - like find, return ValueError when not found

**str.isalnum()**  - returns true if all characters in the string are alphanumeric

**str.isalpha()**  - returns true if all characters in the string are alphabet

**str.replace**(oldsub, newsub, <mark style="color:blue;">num = string.count(str1)</mark>) - replace first num of occurrences of oldsub to newsub, default is to replace all

**str.split**(delim, <mark style="color:blue;">maxsplit = string.count(str)</mark>) - if max split is given, at most max number of split is done, else default is split all

**str.lower()** -> convert all characters to lowercase

**str.upper()** -> convert all characters to uppercase

## Sequence Operation (include list\[] , tuples ( , ) and String)

indexing

iterating the lists:

* for item in list:   (directly go through each item)
* for i, item in enumerate(list):  (go through the index and item together)
* for x, y in list:   (unpack the item into x and y, the elements decoupled must be exactly same as each item in the list)
* for a\_, b\_ in zip(a, b):  (parallel iteration of list a and list b)

**slicing** - list\[start : end  : <mark style="color:blue;">step</mark> ] return the list elements from start to end - 1 every step

add

**multiplication :** \[element] \* n = \[element, element .... element(n)]  - useful for array initialization

membership check using **in** operator  - running time O(n)

list1 = list2 will return a shallow copy&#x20;

listA = list(listB) - return a deep copy of listB (only work for 1-D)

listA = copy.deepcopy(listB) - return a deep copy of list B (work for more than 1-D)

list.count(object) - count the occurrence of an object in the list, O(n)

list.index(object) - return the index of the first occurrence of the object, O(n)

list.extend(seq)  - Append items from _seq (list / tuple / set)_ to the end of the array

delete last element from list, either **list.pop()** or **del list\[-1]**

**list.pop(**<mark style="color:blue;">**i**</mark>**)** - remove the element at index i, if not specified, remove the last element and return it

list.remove(obj) - remove the first occurrence of the object

### Sorting

**list.sort(**_**\***_**, **_<mark style="color:blue;">**key=None**</mark>_<mark style="color:blue;">**,**</mark><mark style="color:blue;">** **</mark>_<mark style="color:blue;">**reverse=False**</mark>_**)** - sort the item in place, return none type

List.sort(reverse = True) / List.reverse()- sort the list by default key using reverse

list.sort(key=operator.itemgetter(0))&#x20;

list.sort(key = **lambda** a : a\[0])   #example for lambda function

For **tuple,** the default comparator will compare the first element, then the second element, and so forth

### **Secondary sorting**&#x20;

list.sort(key = **lambda** a : ( a\[0], a\[1] ))   #this sort first by a\[0] then by a\[1],&#x20;

list.sort(key = **lambda** a : ( a\[0], <mark style="color:red;">**-**</mark> a\[1] ))  # if we want to sort a\[0] by increasing order then a\[1] in reverse order

### Sorted(iterable)

**sorted(**_**iterable**_, _/_, _\*_, _<mark style="color:blue;">key=None</mark>_, _<mark style="color:blue;">reverse=False</mark>_) - Return a new sorted list from the items in _iterable_.

Allows sorting of any iterable (like set(), dict())

The results will return as a new list. For dict, only the keys are sorted and returned

To sort the whole dict and keep the value, use sorted(dict.items())

{% embed url="https://realpython.com/sort-python-dictionary/" %}

## Random Number

import random

random.randint(start, end) - return a random int from start to end (both inclusive)

random.choice(list) - Returns a random element from the given sequence

## Python tricks



Ord(char) – to get the ascii key value of the character

Chr (value) – to get the character of the corresponding ascii key.

### **ZIP**

combine two lists together, example a = \[1, 2, 3], b = \[a, b, c]&#x20;

list(zip (a, b)) = \[(1, a), (2, b), (3, c)]

## Python DataStructures

### HashSet()

* Initialize: HashSet = set()
* Add a new key: Hashset.add(new\_key)
* Remove a key:
  * Hashset.remove(key)    # will return key error if key not in the set
  * Hashset.discard(key)    # will discard key if key in the set, no key error
* Check if the key is in / not in : If key **in/not in** HashSet:
* Get the size :   len(HashSet)
  * Check if empty :  if len(HashSet) == 0:
* Iterate the HashSet:  For key in HashSet:
* Clear the HashSet:   Hashset.clear()
* Update from other set     HashSet.update(\*others)

#### Set Operations

<figure><img src=".gitbook/assets/set Operation.JPG" alt=""><figcaption></figcaption></figure>

### HashMap() / Dict()

Initialize a hashmap

o   Hashmap = {}

Insert a new (key, value) pair or update the value of the existing key:

o   Hashmap\[key] = value

Get the value of a key

o   Hashmap\[key]

o   Hashmap.get(key, default)     #default value can be 0 if key not exist

Set the value of the key if it does not exist

o   dict.setdefault(key, <mark style="color:blue;">default=None</mark>)

Delete a key-value pair

* del hashmap\[key]
* hashmap.pop(key, <mark style="color:blue;">default</mark>) - removes and returns an element from a dictionary having the given key.

Check if a key is in the hash map

o   If key in hashmap

Get the size of the hash map

o   len(hashmap)

Iterate the keyset of the hashmap

o   For key in hashmap:

Get all keys in the hashmap

o Hashmap.keys()

For all values in the hashmap

o   Hashmap.values()

For all key-value pair

o   Hashmap.items()

Clear the dict

o   Hashmap.clear()

Empty dict evaluate to false

o   if not Hashmap: will return true if Hashmap is empty

### Queue:

Initialize a queue

o   Queue = collections.deque(<mark style="color:blue;">iterable (optional), maxlen = n (optional)</mark>)

Working as a stack

o   Queue.append() >> insert value in its argument to the right end of the deque

o   Queue.pop()>>delete an argument from the right end of the deque

o   Queue.extend(iterable) >> add multiple values at the right end of the deque

Working as Queue

o   Queue.append()

o   Queue.popleft() >> delete an argument from the left end of the dequeue

### Heap

* import heapq
* heap = \[]   # a heap is a list
* heapq.heapify(iterable)    # Turn the iterable into a heap
* heapq.heappush(heap, item)
* heapq.heapreplace(_heap_, _item_) - Pop and return the smallest item from the _heap_, and also push the new _item_
* heapq.heappop(heap)
* heap\[0]  #return top of the list
* default sorting for heap is minimum on top, to sort with maximum on top, use negative of the number
  * Useful to find k smallest / largest elements

### collections

**collections.Counter**(\[_iterable-or-mapping_]) return a dict contains the occurrence counts for the elements. The elements in the list as dictionary keys, and their counts are stored as dictionary values.

**collections.**[**`defaultdict`**](https://docs.python.org/3/library/collections.html#collections.defaultdict)**`(`**<mark style="color:blue;">**`default = None`**</mark>**`) -`** dict subclass that calls a factory function to supply missing values, default = none.&#x20;

Example usage: collections.defaultdict(list)  - for each insert key which didn't exist before, default value is an empty list

collections.OrderedDict()  - dict subclass that remembers the order entries were added. Useful for RLU implementation

## math

math.inf -> return the maximum number

math.floor(x) -> get the floor for float number x

math.ceil(x) -> get the ceiling for float number x

## Function

```python
def func(a, *args, b=None, **kwargs):
    """
    :param a: position argument
    :param args: variable arguments (also a tuple)
    :param b: default argument
    :param kwargs: variable for named args (also a dict)
    """
    return None
```

·       C
