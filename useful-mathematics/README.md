# Useful Mathematics

## Subset

The number of subsets for a set with length n is equal to 2^n (empty set included)

For a set with a specific element (minimum/maximum). Adding a new element to the set

The number of subsets with this element will double

Practise

2681 Power of Heroes [https://leetcode.com/problems/power-of-heroes/](https://leetcode.com/problems/power-of-heroes/)



## Combinations

number of possible arrangements in a collection of items where the **order of the selection does not matter**

**Formula：** C(n, k) = (n , k) = n! / ((n - k) ! \* k !)



## Permutations

When orders matter

Formula , P(n, r) = n! / (n - r)!&#x20;

r = item taken for permutations

when r = n, the formula become P = n!

if there are identical items within n, then the formula need to updated to&#x20;

&#x20;$$n! / (a! * b! * c! ...)$$, where a! is the count of item a and so on.&#x20;

### Related Problem - Kth Permutation&#x20;

Usually given an array of number \[1, 2, 3] or string "aabbcc" and asked to find the Kth permutation of the problem.&#x20;

Sample problems:

60: [https://leetcode.com/problems/permutation-sequence/description/](https://leetcode.com/problems/permutation-sequence/description/)

3518: [https://leetcode.com/problems/smallest-palindromic-rearrangement-ii/description/](https://leetcode.com/problems/smallest-palindromic-rearrangement-ii/description/)

```python
# sample code
def help(lefts, temp, k, res):
    # Return statement, if k == 1, this is the order
    if k == 1:
        temp.extend(sorted(lefts))
        ans = [str(num) for num in temp]
        res[0] = "".join(ans)
        return 
            
    curr = 0
    n = len(lefts)
    next_ = math.factorial(n - 1)
    # for curr pos, try to fix the first letter from lexigraphically smallest, 
    # and calculate possible combinations for remaining letters. 
    # if possible combination >= k, this mean Kth permutation lies with the current 
    # letter fixed. 
    # the math.factorial calculation can be very large and time consuming, this could 
    # be further optimize
    for num in sorted(lefts):
        if curr + next_ >= k:
            lefts.remove(num)
            temp.append(num)
            help(lefts, temp, k - curr, res)
            return 
        else:
            curr += next_
```
