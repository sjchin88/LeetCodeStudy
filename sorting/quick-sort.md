# Quick Sort

Divide array based on pivot element

```python
def quicksort(A, left, right):
    if left < right:
        mid = partition(A, left, right)
        quicksort(A, left, mid - 1)
        quicksort(A, mid + 1, right)

def partition(A, left, right):
    pivot = A[right]
    i = left
    for j in range(left, right):
        if A[j] <= pivot:
            A[i], A[j] = A[j], A[i]
            i += 1
    A[i], A[right] = A[right], A[i]
    return i
        
        
```
