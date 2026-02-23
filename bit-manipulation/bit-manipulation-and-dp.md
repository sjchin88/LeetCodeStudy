# Bit Manipulation and DP

## Q1 - Maximum product of two integers with no common bits

Leetcode question: [https://leetcode.com/problems/maximum-product-of-two-integers-with-no-common-bits/description/](https://leetcode.com/problems/maximum-product-of-two-integers-with-no-common-bits/description/)

### Starting thought&#x20;

**complement**: b is complement of a if b & a == 0, &#x20;

or if we know the max number of bits k, b ^ a = 1 << k - 1

b = a ^ (1 << k - 1)

**bitmask & subset**: for given bitmask b (say 101101), it's subsets are 101101, 001101, 100101, 100001 and so on, there are four set bit (1) so the possibility are like 2^4

To solve the question, goal is to get an array dp\[] of length max\_number, where dp\[complement] is the maximum number available for given a.&#x20;

now, we should notice that if we calculate the max number for a bit mask 001101 before, then when we come to 101101, we don't need to calculate every combination for 001101 again (like 000101, 0001001 etc). So we only need to iterate 4 times.&#x20;

### Solution algorithm







SOS (Sum over Subset) using Dynamic Programming [https://codeforces.com/blog/entry/45223](https://codeforces.com/blog/entry/45223)
