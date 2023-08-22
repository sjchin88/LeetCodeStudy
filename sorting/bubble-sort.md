# Bubble Sort

Keep swapping element not in the correct order

cannot sort online

```python
#Bubble sort
def bubble_sort(array):
    n = len(array)
    for end in range(n - 1, 0, -1):
        for i in range(end):
            if array[i] > array[i + 1]:
                array[i], array[i + 1] = array[i + 1], array[i]
    
```
