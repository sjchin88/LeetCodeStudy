# Fast/Slow pointer (same direction)

## Summary

Time complexity O(n)

Space complexity O(1)

Typically used for the following type of questions:

1. Finding shortest/longest subarrays with sum <= or >= k
   * Most often need to use prefix sum
2. Finding the shortest/longest substring which meets the conditions
   * contain target string
   * at least/most k different character
   * characters with at least/most k count&#x20;
   * most often need to use **hashmap/dict**
3. Iterate of two arrays together&#x20;
   * merge sort
   * house and heaters problem

## Template

<pre class="language-python"><code class="lang-python"><strong># First combo, find pair i, and j that met the condition
</strong><strong>j = 0 or j = 1 
</strong>for i in range(n):
    while j &#x3C; n and condition not met with j:
        # Update prefix / dict
        j += 1
    if i and j met the conditions:
        # update max/min length
    # Update prefix / dict to remove i
        
# Second combo, extend pair i, j until breaking the condition
j = 0 or j = 1
for i in range(n):
    while j &#x3C; n and i,j met condition:
        # Update prefix / dict
        j += 1
    if j &#x3C; n: 
        #means while loop end due to breaking condition
        # Reverse j
    if i and j met the conditions:
        # update max/min length
    # Update prefix / dict to remove i
        
</code></pre>

## Practice

141. &#x20; LinkedList Cycle [https://leetcode.com/problems/linked-list-cycle/](https://leetcode.com/problems/linked-list-cycle/)
142. &#x20;  LinkedList Cycle II [https://leetcode.com/problems/linked-list-cycle-ii/](https://leetcode.com/problems/linked-list-cycle-ii/)
