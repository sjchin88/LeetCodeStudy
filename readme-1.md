# Python Note

## String Operation

blue - optional argument, note start idx (inclusive) - end idx (exclusive)

**str.join**(iterable): join all elements in the iterable with str. Example: "".join(\[1, 2]) become 12

**str.capitalize()**

**str.count**(sub, <mark style="color:blue;">begin = 0, end = len(str)</mark>)

**str.endswith**(suffix, <mark style="color:blue;">begin = 0, end = len(str)</mark>) - return true / false

**str.find**(sub, <mark style="color:blue;">begin = 0, end = len(str)</mark>) - return first found, if unfound, return - 1

**str.index**(sub,  <mark style="color:blue;">begin = 0, end = len(str)</mark>) - like find, return ValueError when not found

str.isalnum()

str.isalpha()

**str.replace**(oldsub, newsub, <mark style="color:blue;">num = string.count(str1)</mark>) - replace first num of occurrences

**str.split**(delim, <mark style="color:blue;">maxsplit = string.count(str)</mark>) - if max split is given, at most max number of split is done

## Sequence Operation (include list\[] , tuples ( , ) and String)

indexing

**slicing** - list\[start : end  : <mark style="color:blue;">step</mark> ] return the list elements from start to end - 1 every step

add

**multiplication :** \[element] \* n = \[element, element .... element(n)]

membership check using **in** operator

list1 = list2 will return a shallow copy&#x20;

list.sort() return none type

List.sort(reverse = True) - sort the list by default key using reverse

list.sort(key=operator.itemgetter(0))&#x20;

list.sort(key = lamda a : a\[0])   #example for lamda function

delete last element from list, either **list.pop()** or **del list\[-1]**

&#x20;**list.pop(**<mark style="color:blue;">**i**</mark>**)** - remove element at index i, if not specified, remove the last element

## Random Number

import random

random.randint(start, end) - return a random int from start to end (both inclusive)

random.choice(list) - Returns a random element from the given sequence

## Python tricks

collections.Counter( list ) – return the dict with the elements in the list as dictionary keys, and their counts stored as dictionary values.

Ord(char) – to get the ascii key value of the character

Chr (value) – to get the character of the corresponding ascii key.

## Python DataStructures

### HashSet()

Initialize: HashSet = set()

Add a new key: Hashset.add(new\_key)

Remove a key:

o   Hashset.remove(key)

·Check if the key is in / not in :

o   If key in/not in HashSet:

Get the size

o   Len(HashSet)

Check if empty

o   If len(hashset) == 0

Iterate the HashSet

o   For key in HashSet:

Clear the HashSet

o   Hashset.clear()

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
* heapq.heapify(iterable)
* heapq.heappush(heap, item)
* heapq.heapreplace(_heap_, _item_) - Pop and return the smallest item from the _heap_, and also push the new _item_
* heapq.heappop(heap)
* heap\[0]  #return top of the list



·      &#x20;
