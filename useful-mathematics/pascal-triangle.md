# Pascal Triangle

Example pascal Triangle&#x20;

1&#x20;

1 1

1 2 1

at row n+1, to calculate k item, this is equivalent = nCk (pick k item from n, order not important)

formula = n! / (k! \* (n - k)!) ⇒ n \* (n - 1) \* (n - 2) ... \* (n - k + 1) // { 1 \* 2 \* ... \* k)&#x20;

```python
# In iterative way 
nCk = 1
# starting from 2nd item
for k1 in range(n):
    nCk *= n - k1
    nCk //= k1 + 1
```

[https://leetcode.com/problems/check-if-digits-are-equal-in-string-after-operations-ii/description/](https://leetcode.com/problems/check-if-digits-are-equal-in-string-after-operations-ii/description/)
