Monotonic stack is a ordered stack. 
<br>The elements in the stack are monotonically increasing/decreasing after each new element is pushed into the stack.

First LeetCode Problem: 
<br>496. Next Greater Element I
Visit https://leetcode.com/problems/next-greater-element-i/

The typical paradigm for monotonous increase stack:
```
Java
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
```
Java
for(int i = 0; i < Nums.size(); i++){
  //pop all elements on the stack which is smaller than next element Nums[i]
  //So that the element below the stack will always greater than the next one
  while(!stack.isEmpty() && stack.peek() < Nums[i]){
    stack.pop();
  }
  stack.push(Nums[i]);
}
```

907. Sum of Subarray Minimums
https://leetcode.com/problems/sum-of-subarray-minimums/
2104. Sum of Subarray Ranges
https://leetcode.com/problems/sum-of-subarray-ranges/
