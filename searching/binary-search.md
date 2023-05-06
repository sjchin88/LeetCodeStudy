# Binary Search

## **Algorithms**

```python
// Binary Search
def search(self, nums, target):
    start = 0
    end = len(nums) - 1
    find = default_number when the search fails
    while start <= end:
        mid = start + (end - start)//2
        if f(mid):
            find = mid
            return find # if there is only one possible answer
        elif f(mid) < target:
            start = mid + 1
        else:
            end = mid - 1
    return find
```

## &#x20;  Corner cases & Discussions

1. len(nums) == 1, the first loop will check mid == start == end, the second loop will terminate as the start is guarantee > end
2. What if we need to compare with the number next to mid? Example: finding the peak element. we can add the boundary check in f(mid), and by using **find** to record the previously found value, we can safely discard the search place before/after mid (including mid), if there is no other valid answer remaining, then **find will still record the valid answer found previously**.&#x20;
3. The benefit of using find is if f(mid) takes O(n), this will save the time to reconfirm the f(mid) at the end compared to some other template



**Practice Questions (Easy)**

704\. Binary Search [https://leetcode.com/problems/binary-search/](https://leetcode.com/problems/binary-search/)

69.Sqrt(x) [https://leetcode.com/problems/sqrtx/](https://leetcode.com/problems/sqrtx/)

270\. Closest Binary Search Tree Value [https://leetcode.com/problems/closest-binary-search-tree-value/](https://leetcode.com/problems/closest-binary-search-tree-value/)

374\. Guess Number Higher or Lower [https://leetcode.com/problems/guess-number-higher-or-lower/](https://leetcode.com/problems/guess-number-higher-or-lower/)

**Practice Questions (Medium)**

33\. Search in Rotated Sorted Array [https://leetcode.com/problems/search-in-rotated-sorted-array/](https://leetcode.com/problems/search-in-rotated-sorted-array/)

34\. Find First and Last Position of Element in Sorted Array [https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/)

81\. Search in Rotated Sorted Array II [https://leetcode.com/problems/search-in-rotated-sorted-array-ii/](https://leetcode.com/problems/search-in-rotated-sorted-array-ii/)

153. &#x20; Find Minimum in Rotated Sorted Array [https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/)

162\. Find Peak Element [https://leetcode.com/problems/find-peak-element/](https://leetcode.com/problems/find-peak-element/)&#x20;

658\. Find K Closest Elements [https://leetcode.com/problems/find-k-closest-elements/](https://leetcode.com/problems/find-k-closest-elements/) (need to be careful about corner case)

702\. Search in a Sorted Array of Unknown Size [https://leetcode.com/problems/search-in-a-sorted-array-of-unknown-size/](https://leetcode.com/problems/search-in-a-sorted-array-of-unknown-size/)

**Practice Questions (Hard)**

4\. Median of Two Sorted Arrays [https://leetcode.com/problems/median-of-two-sorted-arrays/](https://leetcode.com/problems/median-of-two-sorted-arrays/)
