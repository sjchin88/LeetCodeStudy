# Monotonic Stack



## Concept & Code

A Monotonic stack is an ordered stack.\
The elements in the stack are monotonically increasing/decreasing after each new element is pushed into the stack.

First LeetCode Problem:\
496\. Next Greater Element I Visit [https://leetcode.com/problems/next-greater-element-i/](https://leetcode.com/problems/next-greater-element-i/)

The typical paradigm for monotonous increase stack:

```java
for(int i = 0; i < Nums.size(); i++){
  //pop all elements on the stack which is greater than next element Nums[i]
  //So that the element below the stack will always smaller than the next one
  while(!stack.isEmpty() && stack.peek() > Nums[i]){
    stack.pop();
  }
  stack.push(Nums[i]);
}
```

Similarly for monotonous decrease stack:

```java
for(int i = 0; i < Nums.size(); i++){
  //pop all elements on the stack which is smaller than next element Nums[i]
  //So that the element below the stack will always greater than the next one
  while(!stack.isEmpty() && stack.peek() < Nums[i]){
    stack.pop();
  }
  stack.push(Nums[i]);
}
```

**907.** Sum of Subarray Minimums [https://leetcode.com/problems/sum-of-subarray-minimums/](https://leetcode.com/problems/sum-of-subarray-minimums/)

The question can be transformed into:

For the entire array, find the counts of the subarray which has the minimum (as the given index element) for each of the index elements of the array.

To do so, one way is to find the Previous Less Element **(PLE)** and the Next Less Element **(NLE)** for the given index element, the number of subarrays with the index element as the minimum will then be the **distance to PLE x distance to NLE.**

**Example:**

```
Given numbers array [3,1,2,4,1] 
For the element 2 (index = 2), the PLE is 1 (index = 1), and NLE is 1 (index = 4)
distance to PLE = 2-1 = 1
distance to NLE = 4-2 = 2
Thus number of subarrays with 2 as the minimum = 1*2 = 2
With all the subarrays as follow：
[2]
[2,4]
```

**Two exceptional cases:**

Case1: What if there is no PLE or NLE or both?

Solution: the distance to PLE / NLE will simply be the distance of the given index to the LHS end/RHS end of the array.

Case2: What if the numbers are not unique for the array, there could be two or more identical numbers?

Solution: In this case, we need to set either PLE or NLE as **less than and equal,**

**Modifying the monotonic stack algorithm to find the PLE and NLE. For PLE:**

```java
int length = Nums.size();
int[] ples = new int[length];
Stack<Integer> stack = new Stack<>();
for(int i = 0; i < length; i++){
  while(!stack.isEmpty() && stack.peek() > Nums[i]){
    stack.pop();
  }
  //Extra code: insert top of stack or -1 if the stack is empty to ples array
  if(stack.isEmpty()){
    ples[i]=-1;
  }else{
    ples[i]=stack.peek();
  }
  stack.push(Nums[i]);
}
```

As we are only interest in the distance to PLE/NLE for this problem, we can modify the algorithm to operate with the index of the element instead of the value of the element, and put the distance to PLE/NLE into the ple/nle array. For PLE:

```java
int length = Nums.size();
int[] ples = new int[length];
Stack<Integer> stack = new Stack<>();
for(int i = 0; i < length; i++){
//compare the Nums[stack.top] to Nums[i]
  while(!stack.isEmpty() && Nums[stack.peek()] > Nums[i]){
    stack.pop();
  }
  //if stack is empty, store the distance to LHS edge which is i + 1;
  if(stack.isEmpty()){
    ples[i]= i+1;
  }else{
  //else, distance is i - stack.top
    ples[i]= i-stack.peek();
  }
  //now push the index instead of the given element
  stack.push(i);
}
```

For NLE, the key difference to PLE algorithm is the iteration will be from right to left opposite to PLE (which is from left to right)

```java
int length = Nums.size();
int[] nles = new int[length];
Stack<Integer> stack = new Stack<>();

for(int i = length-1; i >= 0; i--){
  while(!stack.isEmpty() && Nums[stack.peek()] > Nums[i]){
    stack.pop();
  }
  //if stack is empty, store the distance to RHS edge which is length - i;
  if(stack.isEmpty()){
    nles[i]= length - i;
  }else{
  //else, distance is stack.top - i
    nles[i]= stack.peek()-i;
  }
  //now push the index instead of the given element
  stack.push(i);
}
```

We can modify the NLE algorithm slightly so that the iteration start from left to right, which allows the NLE to be find in the same pass as the PLE.

```java
int length = Nums.size();
int[] nles = new int[length];
Stack<Integer> stack_nle = new Stack<>();
//first we initialize the nles array with the distance to RHS end
for(int i = 0; i < length; i++){
  nles[i] = length - i;
}
//Then we only update the nles array for index with an NLE to the RHS
for(int i = 0; i < length; i++){
  while(!stack.isEmpty() && Nums[stack_nle.peek()] > Nums[i]){
    //Use the index at stack.top
    int temp_index = stack_nle.peek();
    //update nles array distance to i - the index at stack.top
    nles[temp_index] = i - temp_index;
    stack_nle.pop();
  }
  stack_nle.push(i);
}
```

## Sample Problems

2104\. Sum of Subarray Ranges [https://leetcode.com/problems/sum-of-subarray-ranges/](https://leetcode.com/problems/sum-of-subarray-ranges/)

496\. Next Greater Element I Visit [https://leetcode.com/problems/next-greater-element-i/](https://leetcode.com/problems/next-greater-element-i/)

**907.** Sum of Subarray Minimums [https://leetcode.com/problems/sum-of-subarray-minimums/](https://leetcode.com/problems/sum-of-subarray-minimums/)



## Interesting Extension

Idea,&#x20;

* find largest histogram , row by row, iterate from top to bottom
* for each new row, add the height of rows on top

85. [https://leetcode.com/problems/maximal-rectangle/description/](https://leetcode.com/problems/maximal-rectangle/description/)

```python
class Solution:
    def maximalRectangle(self, matrix: List[List[str]]) -> int:
        def largest_rectangle(heights:List[int]):
            max_area = 0
            # keep a monotonic increasing stack, 
            # when element of stack is pop(), we found the next smaller element
            # current area with pop element as left side can be determined
            stack = []
            temp = list(heights)
            temp.append(0)
            for i, h in enumerate(temp):
                while stack and stack[-1][0] >= h:
                    prev_h, _ = stack.pop()
                    if stack:
                        prev_i = stack[-1][1] 
                    else:
                        prev_i = -1
                    area = prev_h * (i - prev_i - 1)
                    #print(i, h, prev_i, prev_h, stack)
                    max_area = max(area, max_area)
                stack.append((h, i))
            #print(max_area, heights)
            return max_area
        max_area = 0
        rows = len(matrix)
        cols = len(matrix[0])
        heights = [0] * cols
        for r in range(rows):
            for c in range(cols):
                if matrix[r][c] == '1':
                    heights[c] += 1
                else:
                    heights[c] = 0
            curr_max = largest_rectangle(heights)
            max_area = max(max_area, curr_max)
        return max_area
```



