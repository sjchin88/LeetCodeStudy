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



