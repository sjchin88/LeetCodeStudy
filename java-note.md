# Java Note

## String Operation

String.concat()  -> appends a string to the end of another string

String.contain() -> checks whether a string contains a sequence of characters

equals() / equalsIgnoreCase()

length()

replace()

split()

toCharArray() -> return a new character array

toLowerCase()

toUpperCase()

trim() -> removes whitespace from both ends

## Array

```java
// Initialize
String[] array = new String[capacity];

// Alternatively
String[] array = {"a", "b", "c"};

// Access element by index
String a = array[index];

// Looping through , traditional way
for (int i = 0; i < array.length; i++){
    System.out.println(array[i]);
}

// For each loop
for (String str : array){
    System.out.println(str);
}

// Copying array - shallow copy
String[] array2 = array;

// Copying array - deep copy
System.arraycopy(Object src, int srcPos,Object dest, int destPos, int length)

int[] destination1 = Arrays.copyOfRange(source, initial_idx(inclusive), 
final_idx(exclusive));

// Sort array
Arrays.sort(array)

// With comparator
Arrays.sort(strings, (String s1, String s2) -> {
      int c = s2.length() - s1.length();
      if (c == 0)
        c = s1.compareToIgnoreCase(s2);
      return c;
  });
 
```

## ArrayList

```java
// Initialize
List<Type> list = new ArrayList<>();

// Add element
list.add(element);
list.addAll(collection);

// Get element
list.get(index);
// Get index
list.indexOf(element);
//Returns the index of the first occurrence of the specified element in this list, 
//or -1 if this list does not contain the element.

// Remove element
list.remove(index);
list.remove(element);
list.clear()

// Replace element
list.set(index, newElement);

// Other 
list.toArray();

// sorting
Collections.sort(al);
```

## Set

```java
// Initialize
Set<Type> set = new HashSet<>();

// add member
set.add(element);

// remove member
set.remove(element);
set.clear()

// check member
set.contains(element);

// empty and size
set.isEmpty();
set.size();
```

## Map

```java
// Initialize
Map<Type k, Type v> map = new HashMap<>();

// add / modify key
map.put(key, value);
map.putIfAbsent(key, value);
map.computeIfAbsent(key, mappingFunction);
map.replace(key, newValue);
map.replace(key, oldValue, newValue);

// check / get key
map.containsKey(key);
map.get(key);
map.getOrDefault(key, defaultValue);

// check size
map.isEmpty();
map.size();

// remove 
map.remove(key);
map.remove(key, value); 
// remove entry for the specified key only if it is mapped to specified value

//Get the set
map.entrySet();  // all k-v pairs
map.keySet();
map.values();
                                

```

## Queue

implemented by linkedlist

```java
// Initialize
Queue<Type> queue = new LinkedList<>();

// add
queue.add(element); // add to last
queue.push(element);
queue.add(idx, element);
queue.addAll(startIdx, collection);
queue.addFirst(elemennt); //add to first
queue.addLast(element);
queue.offer(element); // add to last


//Check and get
queue.contains(element);
queue.element(); // retrieve without remove the head
queue.peek(); // same as above)
queue.get(index);
queue.getFirst();
queue.getLast();
queue.indexOf(element);

queue.poll(); //first element
queue.pop(); //last element

```

## PriorityQueue

```java
// Initialize
PriorityQueue<Type> pq = new PriorityQueue<>();
PriorityQueue<Type> pq = new PriorityQueue<>(int initialCap, Comparator<ype> );

//Add
pq.add(element);
pq.offer(element);

//peek
pq.peek();

//retrieve
pq.poll();
```

## TreeSet()

Time complexities:

Insertion -> O(logn)

Search -> O(logn)

Range\_search -> O(logn)

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
