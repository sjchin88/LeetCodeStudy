# Counting Subarray

This type of problem involves counting each and every subarray of a given array.&#x20;

Problems:

828\. Count Unique Characters of All Substrings of a Given String [https://leetcode.com/problems/count-unique-characters-of-all-substrings-of-a-given-string/](https://leetcode.com/problems/count-unique-characters-of-all-substrings-of-a-given-string/)

**907.** Sum of Subarray Minimums [https://leetcode.com/problems/sum-of-subarray-minimums/](https://leetcode.com/problems/sum-of-subarray-minimums/)\
2262\. Total Appeal of A String [https://leetcode.com/problems/total-appeal-of-a-string/](https://leetcode.com/problems/total-appeal-of-a-string/)

Example problem description (2262).&#x20;

> The **appeal** of a string is the number of **distinct** characters found in the string.
>
> * For example, the appeal of `"abbca"` is `3` because it has `3` distinct characters: `'a'`, `'b'`, and `'c'`.
>
> Given a string `s`, return _the **total appeal of all of its substrings.**_
>
> A **substring** is a contiguous sequence of characters within a string.

A brute force solution will&#x20;

1. Iterate through every possible substring of the given string
2. For each substring, count the number of distinct characters and add them to the total sum.&#x20;

The time efficiency of the brute force solution will be at least O(n^2). Can we find a better algorithm?&#x20;

