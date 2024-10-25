# Longest Increasing Subsequence

## Solution Ideas:

1. Iterate from 0 to n - 1
2. Keep a list of the longest increasing subsequence found thus far, and compare the current index value to the end of the list.
3. If current value > end of the list  => We can increase the length of the LIS found by one, by appending this current value to the end of the list.&#x20;
4. Otherwise, use this current value to replace the next larger value in the LIS. The idea is to keep the LIS elements as small as possible. To illustrate

If we have a list of \[1, 5, 6, 2, 3, 4]&#x20;

when we reach val 2, our LIS is \[1, 5, 6], after replacement it becomes \[1, 2, 6]

when we reached val 3, the LIS became \[1, 2, 3]

Now when we reach val 4, since the end of LIS is already smaller, we can append.&#x20;



### Variants/Follow-Up

What if the problems become 2-D like a Russian doll,&#x20;

1. We just need to sort by Width / Height, and the find the LIS for Height / Width.&#x20;
2. To avoid same width/height being included more than once during LIS search, we will need to do a secondary sort on Height / Width in reverse order.&#x20;
3.

## Questions

LeetCode 300: [https://leetcode.com/problems/longest-increasing-subsequence/](https://leetcode.com/problems/longest-increasing-subsequence/)

LeetCode 354: [https://leetcode.com/problems/russian-doll-envelopes/](https://leetcode.com/problems/russian-doll-envelopes/)

