# Merge Sort

Divide and conquer,&#x20;

Cannot sort online

```python
def merge_sort(array):

def merge_sorting(a:List[int], start:int, end: int):
    if start == end:
        return 
    # Divide
    mid = start + (end - start) //2
    merge_sorting(a, start, mid)
    merge_sorting(a, mid + 1, end)
    
    # Now conquer
    sorted_start = start
    part_a = list(a[start: mid+1])
    start_a = 0
    start_b = mid + 1
    while start_a < len(part_a) and start_b <= end:
        if part_a[start_a] < a[start_b]:
            a[sorted_start] = part_a[start_a]
            start_a += 1
        else:
            a[sorted_start] = a[start_b]
            start_b += 1
        sorted_start += 1
    while start_a < len(part_a):
        a[sorted_start] = part_a[start_a]
        start_a += 1
        sorted_start += 1
    return
            
```

#### Hard Questions

[https://www.lintcode.com/problem/1293/description?fromId=18&\_from=collection](https://www.lintcode.com/problem/1293/description?fromId=18&_from=collection)
