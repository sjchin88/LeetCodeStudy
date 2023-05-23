# Longest Palindrome Subsequence

## Idea

Construct a dp array of size \[n] \[n] , where n is length of string,&#x20;

Initialize the array with the default value&#x20;

```python
n = len(s)
dp = [[1] * n for _ in range(n)]
#we start from the second last position as the start, each loop move start by 1 to 
#the front
for start in range(n - 2, -1, -1):
    #for each start, we start with end = start + 1, and each loop move end by 1 to 
    #the end
    for end in range(start + 1, n):
        if s[start] == s[end]:
            if start + 1 == end:
                dp[start][end] = 2
            else:
                # get the maximum length of inner subsequence (start + 1, end - 1) + 2
                dp[start][end] = 2 + dp[start + 1][end - 1]
        else:
            # get the maximum length between (start + 1, end) and (start, end - 1)
            dp[start][end] = max(dp[start + 1][end], dp[start][end - 1])
return dp[0][n - 1]
```

## Practise Questions

5. Longest Palindromic Substring [https://leetcode.com/problems/longest-palindromic-substring/](https://leetcode.com/problems/longest-palindromic-substring/) Note this has a O(n) solution&#x20;

(516) Longest Palindromic Subsequence [https://leetcode.com/problems/longest-palindromic-subsequence/](https://leetcode.com/problems/longest-palindromic-subsequence/)

(1312) Minimum Insertion Steps to Make a String Palindrome [https://leetcode.com/problems/minimum-insertion-steps-to-make-a-string-palindrome/description/](https://leetcode.com/problems/minimum-insertion-steps-to-make-a-string-palindrome/description/)
