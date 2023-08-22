# Selection Sort

Select the minimum / maximum to be placed on the left / right

Cannot sort online

```python
#selection sort
def selection_sort(array):
    n = len(array)
    for i in range(n):
        min_val = array[i]
        min_idx = i
        for j in range(i + 1, n):
            if array[j] < min_val:
                min_idx = j
                min_val = array[j]
        array[min_idx], array[i] = array[i], array[min_idx]
    
```
