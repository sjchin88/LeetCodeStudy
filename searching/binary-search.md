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
3. The benefit of using find is if f(mid) takes O(n), this will save the time to reconfirm the f(mid) at the end compared to some other template.&#x20;
4. Binary Search cannot work for rotated sorted array which contains duplicate (think of case where \[2, 2, 2, 2]



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

Solving idea :&#x20;

1. Convert questions to find the kth of two sorted arrays. If the total is odd, find k = total//2 + 1. If the total is even, find average of k = total //2 and k = total // 2 + 1
2. For finding kth :&#x20;
   * Check edge cases (a at the end or b at the end or k == 1)
   * binary search by trying to discard half of the a or b
     * a = a\[mid]  if a\[idx\_a + k//2] else math.inf
     * b = b\[mid]  if b\[idx\_b + k//2] else math.inf
     * compared a and b and discard the smaller one

```python
class Solution:
    def findMedianSortedArrays(self, nums1: List[int], nums2: List[int]) -> float:
        n = len(nums1)+len(nums2)
        if n%2==1:
            return self.findKth(nums1, 0, nums2, 0, n//2 + 1)
        else:
            return (self.findKth(nums1, 0, nums2, 0, n//2) + self.findKth(nums1, 0, nums2, 0, n//2+1))/2
    
    def findKth (self, nums1:List[int], aStart:int, nums2:list[int], bStart:int, k:int) ->int:
        #base case
        if aStart >= len(nums1):
            return nums2[bStart+k-1]
        elif bStart >= len(nums2):
            return nums1[aStart+k-1]
        elif k == 1:
            return min(nums1[aStart], nums2[bStart])
        
        #Recursive case
        midA = math.inf
        midB = math.inf
        if aStart+k//2-1 < len(nums1):
            midA = nums1[aStart+k//2-1]
            
        if bStart+ k//2-1 < len(nums2):
            midB = nums2[bStart+ k//2-1]
            
        if midA < midB:
            return self.findKth(nums1, aStart+k//2, nums2, bStart, k-k//2)
        else:
            return self.findKth(nums1, aStart, nums2, bStart+k//2, k-k//2)
```
