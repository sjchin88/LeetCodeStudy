# Kadanes Algorithm

## Explanation:&#x20;

{% embed url="https://www.interviewbit.com/blog/maximum-subarray-sum/" %}

* Subarray - contiguous sequence of elements within an array
* Bruteforce to find all subarray is O(n^2).&#x20;
* Can be reduced to O(n), by only looking at max subarray sum ending at location i.&#x20;
* Say we know max subarray sum ending at location i,  there are two possibility
  * max subarray sum ending at i is **positive**, then max subarray sum ending at i + 1 will simply be previous sum + num\[i + 1]
  * max subarray sum ending at i is **negative**, then max subarray sum ending at i + 1 will simply be num\[i + 1] . In this case at i, we can reset the prev\_sum to 0.&#x20;
* Time complexity O(n), space complexity O(1)



Summary:

1. Use two sums, one to store the currentSum (ending till i), one to store the MaximumSum.&#x20;
2. Iterate through the array and add the value of the current element to currentSum
   1. if currentSum > MaximumSum, update MaximumSum
   2. if currentSum < 0, reset currentSum to 0.&#x20;

Problems:

53\. Maximum Subarray [https://leetcode.com/problems/maximum-subarray/](https://leetcode.com/problems/maximum-subarray/)



2272\. Substring With Largest Variance (Hard) [https://leetcode.com/problems/substring-with-largest-variance/](https://leetcode.com/problems/substring-with-largest-variance/)

{% embed url="https://www.lintcode.com/course/42" %}

## Variations

Max product of subarray

* Keep prev\_max, prev\_min, max\_prod values
* For each next num in the array, there are 3 choices for curr\_max & curr\_min. Eg for curr\_max
  * num is positive and prev\_max > 1 , max will be num \* prev\_max
  * num is positive and prev\_max is < 1, max will be num only.&#x20;
  * num is negative and prev\_max > 1, max will be num only
  * num is negative and prev\_max < 1, max will be num \* prev\_max.&#x20;
  * Update max\_prod with curr\_max

[https://www.lintcode.com/course/42/learn/191/](https://www.lintcode.com/course/42/learn/191/)
