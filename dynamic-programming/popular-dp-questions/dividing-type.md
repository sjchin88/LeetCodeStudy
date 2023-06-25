# Dividing Type

## **Key Summary**

1. Often need to operate on the whole array
2. The operation can be on two or more subarrays
   * Like adding the sum together (dividing an array with k parts with the goal to minimize the sum)
   * Maximum Scores of Popping a Balloon
   * Swapping string etc

## Common Pattern / Algorithm to solve

dp\[i]\[j]\[k] represents the optimal way to operate on an array starting from I to j  with k number of parts. the k state can be omitted if the number of parts operating is max 2.&#x20;

In case k = 2, Thus from i to j, we need to **enumerate** the **divider m** from index i to index j such that&#x20;

dp\[i]\[j] = min/max (dp\[i]\[j],  dp\[i]\[m]  + dp\[m]\[j]  plus the operation cost )

In case k > 2, we need to **enumerate the divider m** from index i to j which **separate k - 1 part to the last part.**  Note to get k - 1 part we often need to start enumerate from 1 first for all k

dp\[i]\[j]\[k] = min/max (dp\[i]\[j],  dp\[i]\[m]\[k - 1]  + dp\[m]\[j]\[1]  plus the operation cost )

## Practice Problems

312 Burst Ballon [https://leetcode.com/problems/burst-balloons/submissions/](https://leetcode.com/problems/burst-balloons/submissions/)

```python
 # state dp[i][j] -> optimal way to burst the ballon between i + 1 and j - 1, with i , j as the nonburstable wall 
 # initialization: we looking for max so initialize all with 0
 dp = [[0] * n for _ in range(n)]
        
 # we need to enumerate the mid (last ballon to burst)
 # Gain from last step is the left wall * last ballon value * right wall
 # additional gain from left of ballon will be dp[i][last]
 # additional gain from right of ballon will be dp[last][j]
 # dp[i][j] = max(dp[i][j], nums[i] * nums[last] * nums[j]  + dp[i][last] + dp[last][j])
 # we need the result of smaller sections first, so we start iterate with length of two (j - i == 2)
 for length in range(2, n):
        for i in range(n - length):
               j = i + length
               for last in range(i + 1, j):
                    gain = nums[i] * nums[last] * nums[j]
                    additional = dp[i][last] + dp[last][j]
                    dp[i][j] = max(dp[i][j], gain + additional)
 return dp[0][n - 1]
```

With up to k-part

410 Split Array Largest Sum [https://leetcode.com/problems/split-array-largest-sum/](https://leetcode.com/problems/split-array-largest-sum/)

Note binary search the possible answer can be more efficient for the split above



Bonus

87 (very hard) Scrambling String [https://leetcode.com/problems/scramble-string/submissions/](https://leetcode.com/problems/scramble-string/submissions/)
