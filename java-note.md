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

## Map

## Queue

## PriorityQueue
