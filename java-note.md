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
```

