---
description: For String Matching
---

# Rabin-Karp (Rolling Hash)

## Key Idea

* Use to find the match of a pattern in a text
  * can be modify to accomodate changing pattern&#x20;
* Find a hash value of a pattern&#x20;
  * Need a base (usually prime number, need to bigger than size of character set), which guarantee the hash value wont be repeated for different combination of txt
  * Need a modulus to avoid overflow issues.&#x20;
  * hash value = sum of ![](<../../.gitbook/assets/image (5).png>)
  * last character is always just c
* Slide the length of pattern over the text
  * find the hash value of the length of text&#x20;
  * the hash of next slide can be calculated by substracting the contribution of leftmost character and add the contribution of new character on the right
  *

      <figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>



## Sample Algorithm

```python
# 
def search(pattern:str, text:str) -> list[int]:
    len_pattern = len(pattern)
    len_text = len(text)
    base = 31
    mod = 10**9 + 7
    hash_pattern = 0
    hash_txt = 0
    hash_multi = 1
    
    # Precalculate hash_multi to save compute time
    for i in range(len_pattern - 1):
        hash_multi = (hash_multi * base) % mod
        
    # Calculate the hash value of pattern and first window of text
    for i in range(len_pattern):
        hash_pattern = (hash_pattern * base + (ord(pattern[i]) - ord('a') + 1)) % mod
        hash_text = (hash_text * base + (ord(text[i]) - ord('a') + 1)) % mod
    
    result = [] 
    for i in range(len_text - len_pattern + 1):
        if hash_pattern == hash_text:
            if text[i:i+len_pattern] == pattern:
                result.append(i)
        
        # find hash value for next window of text 
        if i < len_text - len_pattern:
            hash_text = hash_text - (ord(text[i]) - ord('a') + 1))*hash_multi
            hash_text = (hash_text * base + (ord(text[i]) - ord('a') + 1))) % mod
            if hash_text < 0:
                hash_text += mod
```

## Variant&#x20;

Leetcode 214: Shortest Palindrome [https://leetcode.com/problems/shortest-palindrome/description/](https://leetcode.com/problems/shortest-palindrome/description/)

```python
class Solution:
    def shortestPalindrome(self, s: str) -> str:
        n = len(s)
        def convert_chr(ch):
            return ord(ch) - ord('a') + 1
        max_palindrome_len = 1 

        forward_hash = 0
        reverse_hash = 0
        mod = 10**9 + 7
        base = 31
        base_multiply = 1
        for i in range(n):
            int_ch = convert_chr(s[i])
            forward_hash = (forward_hash * base + int_ch) % mod
            reverse_hash = (reverse_hash + int_ch * base_multiply) % mod
            base_multiply = base_multiply * base % mod
            if forward_hash == reverse_hash:
                max_palindrome_len = i + 1
        
        r = s[max_palindrome_len:]
        r = r[::-1]


        return r + s
```
