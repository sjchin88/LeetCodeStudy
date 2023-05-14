# Monotonic stack

## Property

* All elements on the stack are strictly increasing or decreasing&#x20;
* Allow finding of previous smaller/larger element in O(1) time
* Python deque structure can be used to access the bottom (left) of the stack in O(1) -> Useful if we need to maintain and keep the order for k elements&#x20;

## Algorithm to find the previous lesser element

```python
// the stack store the previous lesser element(ple) index
def find_ples(nums:List[int]) -> List[int]:
    ples = [default value] * len(nums)
    stack = collections.deque()
    for i, num in enumerate(nums):
        while stack and nums[stack[-1]] >= num:
            stack.pop()
        if stack:
            ples = stack[-1]
        stack.append(i)
    return ples
```

## Algorithm to find the next minimum element

```python
// the stack store the next lesser element(nle) index
def find_nles(nums:List[int]) -> List[int]:
    nles = [default value] * len(nums)
    stack = collections.deque()
    # Example, nums = [3, 2, 3]
    # starting from 3, 
    # the stack is empty (no update), add 3 -> stack = [3]
    # next iterate till 2, stack top (3) is > 2, 
    # pop the stack and update the idx nles[0] to be 1
    # last iteration, stack top (2) is not > 3, no update
    for i, num in enumerate(nums):
        while stack and nums[stack[-1]] > num:
            prev = stack.pop()
            nles[prev] = i
        stack.append(i)
    return nles
```


