# Prefix Sum (Include Remainder)

GFG Description [https://www.geeksforgeeks.org/prefix-sum-array-implementation-applications-competitive-programming/](https://www.geeksforgeeks.org/prefix-sum-array-implementation-applications-competitive-programming/)

Idea,&#x20;

The value of **prefixSum\[i]** is **arr\[0] + arr\[1] + arr\[2] . . . arr\[i]**

the **sum of subarray \[i, j]** (inclusive) is **prefixSum\[j] - prefixSum\[ i - 1]**

This is useful if we need to iterate through the sum of subarray for i , j in range of (0, n)

## Practise Question

**Practise Question (Easy)**

[**https://www.lintcode.com/problem/138/**](https://www.lintcode.com/problem/138/)

**Practise Question**&#x20;

{% embed url="https://leetcode.com/discuss/interview-question/850974" %}

## Follow Up - Prefix Sum for 2-D

To compute prefix\_sum for a matrix from (0, 0) to (x, y)

prefix\[x + 1]\[y + 1] = matrix\[x]\[y] + prefix\[x + 1]\[y] + prefix\[x]\[y + 1] - prefix\[x]\[y]

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

Given prefix matrix, to compute the sum of submatrix from (x1, y1) to (x, y)

sum = prefix\[x + 1]\[y + 1] - prefix\[x1]\[y + 1] - prefix\[x + 1]\[y1] + prefix\[x1]\[y1]

## Follow Up - Count number of subarrays with sum == k

### Idea:

**Step 1:** reversing the concept to find the prefix sum from i to j = prefix\[j + 1] - prefix\[i]

if there exist a prefix\_sum = prefix\[j + 1] - target, that means there exist a subarray from i to j where the prefix sum == target

**Step 2:** we are interesting in the count only, so for every prefix sum we encountered when iterating from left to right of the array, just increment its count in a sum2count map(dict). When we reach number\[i] with prefix\_sum\[i + 1], if there exist two counts of prefix\_sum\[i + 1] - target in the map, thats mean number\[i] can form two subarray with all the left elements with target == k

Leetcode 560 - [https://leetcode.com/problems/subarray-sum-equals-k/](https://leetcode.com/problems/subarray-sum-equals-k/)

Leetcode 1074 - [https://leetcode.com/problems/number-of-submatrices-that-sum-to-target/](https://leetcode.com/problems/number-of-submatrices-that-sum-to-target/)



## Follow Up - Working with Remainder

\*Need Proof

Leetcode 3654 - [https://leetcode.com/problems/minimum-sum-after-divisible-sum-deletions/description/](https://leetcode.com/problems/minimum-sum-after-divisible-sum-deletions/description/)

#### Idea

## **Intuition** <a href="#intuition" id="intuition"></a>

Use a DP to track the result,\
`dp[prefix % k]` stores the smallest result with `prefix` sum mod `k`.

## **Explanation** <a href="#explanation" id="explanation"></a>

Iterates through the array,\
maintaining an evolving sum `res`.\
If `res` reaches a value that shares a remainder\
with a smaller previously seen prefix sum,\
the algorithm instantly "deletes" the difference\
by resetting `res` to that smaller value.

## **More Detail** <a href="#more-detail" id="more-detail"></a>

Note that, the evolving sum `res` isn't just a running total.\
It represents the minimum possible sum\
of the array prefix processed so far,\
after optimal deletions.

`res = dp[res % k] = min(dp[res % k], res)`\
This compact line is the engine of the solution:\
It looks up the smallest past sum with the same remainder (dp\[res % k]).\
It compares this past sum with the current `res`\
and updates the dp memory bank with the new minimum.

It replaces `res` with this minimum value,\
which is equivalent to performing the optimal deletion.\
The final value of `res` after the loop is the minimum possible sum for the entire array.

## **Complexity** <a href="#complexity" id="complexity"></a>

Time `O(n)`\
Space `O(k)`

#### Code

```python
class Solution:
    def minArraySum(self, nums: List[int], k: int) -> int:
        dp = [0] + [inf] * k
        res = 0
        for a in nums:
            res += a
            res = dp[res % k] = min(dp[res % k], res)
           # print(res, dp)
        return res

```

