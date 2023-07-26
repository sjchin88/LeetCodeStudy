# Jumping Pointer(s)

328 [https://www.lintcode.com/problem/328/description](https://www.lintcode.com/problem/328/description)

```python
class Solution:
    """
    @param s: a string
    @return:  an array containing the length of each part
    """
    def split_string(self, s: str) -> List[int]:
        # write your code here.
        ch2count = {}
        ch2last = {}
        first_ch = []
        for i, ch in enumerate(s):
            if ch not in ch2count:
                ch2count[ch] = 0
                first_ch.append((i, ch))
            ch2count[ch] += 1
            ch2last[ch] = i
        
        res = []
        prev_start = -1
        curr_count = 0
        last = -1
        for start, ch in first_ch:
            curr_count += ch2count[ch]
            last = max(last, ch2last[ch])
            if curr_count == last - prev_start:
                res.append(curr_count)
                curr_count = 0
                prev_start = last
        return res
            
```

Follow Up

LeetCode 1520: [https://leetcode.com/problems/maximum-number-of-non-overlapping-substrings/](https://leetcode.com/problems/maximum-number-of-non-overlapping-substrings/)
