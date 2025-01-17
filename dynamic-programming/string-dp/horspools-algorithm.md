# Horspool's Algorithm

## Summary

Problem Statement -> find the first index of a pattern in a text;&#x20;

* pattern: a string of m characters to search for
* text: a (long) string of n characters to search in

Idea for Horspool's&#x20;

* Preprocess pattern to generate a shift table that determines how much to shift when a mismatch occurs
  * the shift will be based on the text's character c aligned with its last position in the pattern (excluding the last character of pattern).
  * For example, if we have a pattern BAOBAB, then excluding the last character ("B"). The shift number for remaining characters are&#x20;
    * A -> 1
    * B -> 2 (second B from the last)
    * O -> 3
    * The rest of alphabet (C, D, E, F.... Z) -> 6 (length of pattern)
* Now we start from last = m - 1 in the text, and trying to match the character with the pattern from m - 1 to 0.&#x20;
  * If mismatch occur, shift the last by the shift amount&#x20;
  * Example Text = BARD LOVED BANANAS
    * First iteration, last = 'L', didnt match the pattern, shift by 6
    * Second iteration, last = B, second last = "" which didnt match the pattern, shift by 2 (based on last character shift value in the shift table)
    * Third iteration, last = N, didnt match the pattern shift by 6
    * End&#x20;

Time complexities:

In the worst case, still O(nm) -> consider case where pattern = baaaaaa, with text of all a

best case -> O(n + m) -

## Algorithm & Practise Problem

Leetcode 28: [https://leetcode.com/problems/find-the-index-of-the-first-occurrence-in-a-string/](https://leetcode.com/problems/find-the-index-of-the-first-occurrence-in-a-string/)

```python
class Solution:
    def strStr(self, haystack: str, needle: str) -> int:
        #Horspool algorithm
        #preprocessing pattern (needle) to generate a shift table for every character
        chars = 'abcdefghijklmnopqrstuvwxyz'
        m = len(needle)
        shift_table = {}
        for ch in chars:
            shift_table[ch] = m
        for i in range(m - 2, -1, -1):
            ch = needle[i]
            if shift_table[ch] == m:
                shift_table[ch] = m - i - 1
                
        #now start comparing from the last character of haystack substring and needle
        #if all match, return the starting position of the substring in haystack
        #else, shift the last position in the haystack substring by the shift_table
        match_start = m - 1
        n = len(haystack)
        while match_start < n:
            matched = True
            for i in range(m):
                if haystack[match_start - i] != needle[m - i - 1]:
                    matched = False
                    break
            if matched:
                return match_start - m + 1
            else:
                match_start += shift_table[haystack[match_start]]
        return -1
```

