# Counting Subarray

This type of problem involves counting each and every subarray of a given array.&#x20;

Problems (from easy to hard). :

2063\. Vowels of All Substrings [https://leetcode.com/problems/vowels-of-all-substrings/](https://leetcode.com/problems/vowels-of-all-substrings/)

2262\. Total Appeal of A String [https://leetcode.com/problems/total-appeal-of-a-string/](https://leetcode.com/problems/total-appeal-of-a-string/)

828\. Count Unique Characters of All Substrings of a Given String [https://leetcode.com/problems/count-unique-characters-of-all-substrings-of-a-given-string/](https://leetcode.com/problems/count-unique-characters-of-all-substrings-of-a-given-string/)

**907.** Sum of Subarray Minimums (need to use monotonic stack) [https://leetcode.com/problems/sum-of-subarray-minimums/](https://leetcode.com/problems/sum-of-subarray-minimums/)\


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

One way is to transform the question into, for every character(element) in the given string(array), what is its contribution to the solution?

For example, for the total appeal of a string problem, the question will be asking for every character, what is the total number of substrings where this character is considered a distinct character?&#x20;

For example, we have a string of xxaxxxaxxxabx, for the second char a,&#x20;

the possible substring combinations will start after the first char a, and they have to include the second a, hence there is a count of  i - last('a') to start with , (i = index of second char a).&#x20;

For every character after the second char 'a', the previous combination will simply be multiplied by 1x. As we can add the previous substring with the extra char. For example, for substring a, the following substrings are possible, ax, axx, axxx, axxxa, axxxab, axxxabx.&#x20;

&#x20;Hence the total number of substrings where this character is considered a distinct character will be (i - last('a')) \*( L - i) , where L = string.length();

Other questions can be solved similarly, for problem 828 to find unique characters we can store the last two occurrences of the character and count the possible substring combinations for the last occurrence of the character.&#x20;

Ie, for a string of xxaxxxaxxxabx, for the char 'a', we will&#x20;

i. store the index of first  'a'&#x20;

ii. when found the index of second 'a', count the contributions by the first 'a'

iii. when found the index of third 'a', count the contributions by the second 'a',&#x20;

iv. at the end if no further 'a' found, count the contributions by the last 'a'.&#x20;

