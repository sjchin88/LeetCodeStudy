# Kadanes Algorithm

Explanation:&#x20;

{% embed url="https://www.interviewbit.com/blog/maximum-subarray-sum/" %}

Summary:

1. Use two sums, one to store the currentSum (ending till i), one to store the MaximumSum.&#x20;
2. Iterate through the array and add the value of the current element to currentSum
   1. if currentSum > MaximumSum, update MaximumSum
   2. if currentSum < 0, reset currentSum to 0.&#x20;

Problems:

53\. Maximum Subarray [https://leetcode.com/problems/maximum-subarray/](https://leetcode.com/problems/maximum-subarray/)



2272\. Substring With Largest Variance (Hard) [https://leetcode.com/problems/substring-with-largest-variance/](https://leetcode.com/problems/substring-with-largest-variance/)

[https://www.lintcode.com/course/42](https://www.lintcode.com/course/42)
