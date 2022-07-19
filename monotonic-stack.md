# Monotonic Stack



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

1. Sum of Subarray Minimums [https://leetcode.com/problems/sum-of-subarray-minimums/](https://leetcode.com/problems/sum-of-subarray-minimums/)

The question can be transformed into:

For the entire array, find the count of subarray which has the minimum (as the given index element) for each of the index elements of the array.&#x20;



1. Sum of Subarray Ranges [https://leetcode.com/problems/sum-of-subarray-ranges/](https://leetcode.com/problems/sum-of-subarray-ranges/)
