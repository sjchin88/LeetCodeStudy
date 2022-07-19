---
description: 'Lists of LeetCode Problems:'
---

# Monotonic Stack

496\. Next Greater Element I Visit [https://leetcode.com/problems/next-greater-element-i/](https://leetcode.com/problems/next-greater-element-i/)

**907.** Sum of Subarray Minimums [https://leetcode.com/problems/sum-of-subarray-minimums/](https://leetcode.com/problems/sum-of-subarray-minimums/)

2104\. Sum of Subarray Ranges [https://leetcode.com/problems/sum-of-subarray-ranges/](https://leetcode.com/problems/sum-of-subarray-ranges/)







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

For the entire array, find the counts of the subarray which has the minimum (as the given index element) for each of the index elements of the array.&#x20;

To do so, one way is to find the Previous Less Element **(PLE)** and the Next Less Element **(NLE)** for the given index element, the number of subarrays with the index element as the minimum will then be the **distance to PLE x distance to NLE.**&#x20;

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

Case1: What if there is no PLE or NLE or both?&#x20;

Solution: the distance to PLE / NLE will simply be the distance of the given index to the LHS end/RHS end of the array.&#x20;

Case2: What if the numbers are not unique for the array, there could be two or more identical numbers?

Solution: In this case, we need to set either PLE or NLE as **less than and equal,**&#x20;

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



2104\. Sum of Subarray Ranges [https://leetcode.com/problems/sum-of-subarray-ranges/](https://leetcode.com/problems/sum-of-subarray-ranges/)
