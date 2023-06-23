# Subsequence problem

a subsequence of a given sequence is a sequence that can be derived from the given sequence by deleting some or no elements without changing the order of the remaining elements

The number of possible subsequences for a sequence with length n is **2 ^ n** (including empty subsequences).

We can calculate the solution for subsequences by constructing a dp array , where dp\[i] represent the number of solutions up to i elements.&#x20;

Then dp\[i] = dp \[i - 1] \* 2  (whether to include or not the i element)

and dp\[i]  -= other possible redundant / invalid solutions

## Practise

940\. [https://leetcode.com/problems/distinct-subsequences-ii/](https://leetcode.com/problems/distinct-subsequences-ii/)&#x20;

2681. &#x20;    [https://leetcode.com/problems/power-of-heroes/](https://leetcode.com/problems/power-of-heroes/)
