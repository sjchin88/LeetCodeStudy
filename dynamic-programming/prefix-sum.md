# Prefix Sum

GFG Description [https://www.geeksforgeeks.org/prefix-sum-array-implementation-applications-competitive-programming/](https://www.geeksforgeeks.org/prefix-sum-array-implementation-applications-competitive-programming/)

Idea,&#x20;

The value of **prefixSum\[i]** is **arr\[0] + arr\[1] + arr\[2] . . . arr\[i]**

the **sum of subarray \[i, j]** (inclusive) is **prefixSum\[j] - prefixSum\[ i - 1]**

This is useful if we need to iterate through the sum of subarray for i , j in range of (0, n)

**Practise Question (Easy)**

[**https://www.lintcode.com/problem/138/**](https://www.lintcode.com/problem/138/)

**Practise Question**&#x20;

{% embed url="https://leetcode.com/discuss/interview-question/850974" %}
