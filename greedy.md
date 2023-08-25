# Greedy

## Condition for Greedy

* Local optimum solutions need to lead to global optimum solutions

## Example Problems

### String and Char Permutations

LeetCode 1081 : [https://leetcode.com/problems/smallest-subsequence-of-distinct-characters/](https://leetcode.com/problems/smallest-subsequence-of-distinct-characters/)

Idea :&#x20;

* iterate the string from left to right, keep the left character as small as possible as long as there is enough unique characters to the right
* If there is not enough unique characters to the right
  * Fixed the prefix with the smallest permutation obtained thus far
  * remove all characters used in the rest of string
  * find the smallest combination based on substring starting from last char used

### Number Permutations

LeetCode 1053: [https://leetcode.com/problems/previous-permutation-with-one-swap/](https://leetcode.com/problems/previous-permutation-with-one-swap/)

Idea :&#x20;

* Iterate from right to left, find the first index i with value greater than i + 1
* swap i with largest number to its right that is smaller than num\[i]&#x20;

### Other

[https://leetcode.com/problems/super-washing-machines/](https://leetcode.com/problems/super-washing-machines/)
