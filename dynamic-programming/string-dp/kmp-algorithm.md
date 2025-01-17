# KMP Algorithm

## Application

Given two strings **txt** and **pat, t**he task is to return all indices of **occurrences** of **pat** within **txt**.

## Main Idea

* uses the **structure of the pattern** to avoid redundant comparisons.&#x20;
* It preprocesses the **pattern** string and creates an array called the **Longest Prefix Suffix** (lps) array which indicates how much of the pattern can be reused after a mismatch.
* Example, pat="ababc", if we found a match in txt up to the fourth element "b”， and c doesnt match with txt, we can reuse the "ab" pattern and restart the matching with "ab"
* Time complexity:&#x20;
  * if pattern exist ⇒ O(n + m),&#x20;
  * if no pattern ⇒ O(n \* m), note Horspool may be more efficient in this case.&#x20;

## Code & Application

```python
def constructLps(pat):
    
    # len stores the length of longest prefix which 
    # is also a suffix for the previous index
    len_ = 0
    m = len(pat)
    
    # lps[0] is always 0
    lps = [0] * m
    
    i = 1
    while i < m:
        
        # If characters match, increment the size of lps
        if pat[i] == pat[len_]:
            len_ += 1
            lps[i] = len_
            i += 1
        
        # If there is a mismatch
        else:
            if len_ != 0:
                
                # Update len to the previous lps value 
                # to avoid redundant comparisons
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
