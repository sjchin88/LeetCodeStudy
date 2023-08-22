# Insertion Sort

find the next position of sorted array&#x20;

can sort inline

```python
#Insertion sort
def insertion_sort(array):
    n = len(array)
    for i in range(1, n):
        key = array[i]
        j = i - 1
        while j >= 0 and array[j] > key:
            array[j + 1] = array[j]
            j -= 1
        array[j + 1] = key
```
