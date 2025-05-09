# KMP Algorithm

## Application

1. Given two strings **txt** and **pat, t**he task is to return all indices of **occurrences** of **pat** within **txt**.
2. Find the Longest Prefix Suffix (lps)&#x20;

[http://jakeboxer.com/blog/2009/12/13/the-knuth-morris-pratt-algorithm-in-my-own-words/](http://jakeboxer.com/blog/2009/12/13/the-knuth-morris-pratt-algorithm-in-my-own-words/)

## Brute Forces Solution

```python
# Pseudocode for Brute Forces, 
n = len(txt)
m = len(pat)
for i in range(n - m + 1):
    matched = True
    for j in range(m):
        if txt[i+j] != pat[j]:
            matched = False
            break
    if matched:
        # append i as start of pat 

# Time complexities: O(n * m), n = length of txt, m = length of pat
```

## Main Idea

* uses the **structure of the pattern** to avoid redundant comparisons.&#x20;
* It preprocesses the **pattern** string and creates an array called the **Longest Prefix Suffix** (lps) array which indicates how much of the pattern can be reused after a mismatch.
* lps is also known as **Partial Match Table.** It basically tell for idx at i for the pattern, what is the length of the prefix of the pattern matched at i.&#x20;

```
# Example pattern    ABCDABD
# lps table will be [0, 0, 0, 0, 1, 2, 0]
# lps[0] is always 0
# at lps[1], the character B dont match the prefix of the pattern A, so its 0. 
# similarly for lps[2], lps[3], they dont match prefix, so its 0
# but for lps[4], character A match prefix of pattern A with length 1, so its 1
# for lps[5], suffix with length of 2 till idx 5 ('AB') match prefix with length of 2

```

* Example, pat="ababc", if we found a match in txt up to the fourth element "b”， and c doesnt match with txt, we can reuse the "ab" pattern and restart the matching with "ab" at idx = 2.&#x20;
*
* Time complexity:&#x20;
  * if pattern exist ⇒ O(n + m),&#x20;
  * if no pattern ⇒ O(n \* m), note Horspool may be more efficient in this case.&#x20;

## Code & Application

```python
def constructLps(pat):
    
    # len stores the length of longest prefix which 
    # is also a suffix for the previous index
    # it also equal to the next character idx of prefix we need to match
    len_ = 0
    m = len(pat)
    
    # lps[0] is always 0
    lps = [0] * m
    
    # start from 1
    i = 1
    while i < m:
        
        # If characters match, increment the size of lps
        # and update the lps table for idx i
        if pat[i] == pat[len_]:
            len_ += 1
            lps[i] = len_
            i += 1
        
        # If there is a mismatch
        else:
            if len_ != 0:
                
                # Update len to the previous lps value to avoid redundant comparisons
                # we still need to compare pat[i] with pat[new_len] in next loop
                # in worst case for pattern like aaaaab and we reach idx 5(b), we
                # will keep decreasing len_ till 0 
                # but the overall time complexities wont be worst than O(2*n)
                len_ = lps[len_ - 1]
            else:
                
                # If no matching prefix found, set lps[i] to 0
                lps[i] = 0
                i += 1
    return lps
```

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

```python
def search(pat, txt):
    n = len(txt)
    m = len(pat)

    lps = constructLps(pat)
    res = []


    # Pointers i and j, for traversing 
    # the text(i) and pattern(j)
    i = 0
    j = 0

    while i < n:
        
        # If characters match, move both pointers forward
        if txt[i] == pat[j]:
            i += 1
            j += 1

            # If the entire pattern is matched 
            # store the start index in result
            if j == m:
                res.append(i - j)
                
                # Use LPS of previous index to 
                # skip unnecessary comparisons
                j = lps[j - 1]
        
        # If there is a mismatch
        else:
            
            # Use lps value of previous index
            # to avoid redundant comparisons
            if j != 0:
                j = lps[j - 1]
            else:
                i += 1
    return res 
```

## Interesting Variant

214. [https://leetcode.com/problems/shortest-palindrome/description/](https://leetcode.com/problems/shortest-palindrome/description/)

<pre class="language-python"><code class="lang-python"># Example solution
class Solution:
    def shortestPalindrome(self, s: str) -> str:
        reverse_s = s[::-1]
        n = len(s)
        # We trying to find lps length at last idx
        # say s = "<a data-footnote-ref href="#user-content-fn-1">aacecaa</a>a"
        # rev   = 'a<a data-footnote-ref href="#user-content-fn-1">aacecaa</a>"
        # the lps tell the longest palindrome starting from idx 0
        combine_s = s + '#' + reverse_s
        longest_common = 0
        m = len(combine_s)

        i = 1
        len_ = 0
        lps = [0] * m
        while i &#x3C; m:
            if combine_s[i] == combine_s[len_]:
                len_ += 1
                lps[i] = len_
                i += 1
            else:
                if len_ != 0:
                    len_ = lps[len_ - 1]
                else:
                    lps[i] = 0
                    i += 1
        longest_common = lps[-1]
        r = s[longest_common:]
        r = r[::-1]
        return r + s
</code></pre>



[^1]: 
