# Choices problem

## Typical Problem

Given an array a, for each element in a, there are two possible operations

Theoretically the total number of possibilities we need to consider is O(2^n) , where n is the number of elements

However, it is very possible that some of the outcomes are redundant when we reach considered first i elements, which we can store only the optimal solutions

Typical

dp\[i]\[j]  represent the optimal solution to reach target j consider first  i element

## Practise Problems

LintCode [https://www.lintcode.com/problem/1800/description](https://www.lintcode.com/problem/1800/description)

Leetcode 2746: [https://leetcode.com/contest/biweekly-contest-107/problems/decremental-string-concatenation/](https://leetcode.com/contest/biweekly-contest-107/problems/decremental-string-concatenation/)
