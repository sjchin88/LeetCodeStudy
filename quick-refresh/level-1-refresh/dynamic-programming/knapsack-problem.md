# Knapsack Problem

## Typical Problem Statement

**Basic version** - given n items with weight/size in list A, and value in list V. and a backpack with weight/size of m, find the maximum value that can be pack into the backpack.&#x20;

## Solution summary

For each item, we have the option of not including / including it into the knapsack (0 or 1)

Brute forces will result in O(2^n)&#x20;

DP can often reduce the time complexity into O(n ^ x). x represent the number of states that we need to iterate through. The states required will include

* Example state dp\[i]\[w],&#x20;
* **i = The number of items** considered thus far&#x20;
* **w** = The weight/volume/area of the items included up to the **capacity** of the knapsack
* usually start from 0 to max number of items (n + 1 state) or 0 to max capacity (ie, w + 1 state) to account for edge cases.&#x20;
* Transition function dp\[i + 1]\[w] = max(dp\[i]\[w], dp\[i]\[w - w\[i]] + p\[i])

## Optimizations

for problems where the item price is the same as the item weight, and we want to find the max weight / specific weight is possible

* we can compress the dp from 2-d to 1-d
* Instead of iterating through all weight (0 to w + 1),  we just use a set to store all possible states up to item i - 1, and iterate through the possible states for new possible state with i&#x20;

### Optimization & Order of iterations

* for dp\[i]\[w] , can compress 2-d array down to 1-d array like dp\[w].&#x20;
* avoid repetition/overwrite by iterating from largest to smaller value backward. Eg, if we have w range from 0 - 10, for new state we start iterating from 10
* where dp\[w] = max(dp\[w], dp\[w - w\[i]] + p\[i])

Think about how to calculate the state required, and whether redundancy is allow

But if the items can be used infinitely, we will iterate from left to right as normal

## Unbounded Knapsack, where item can be reused

```python
class Solution:
    def coinChange(self, coins: List[int], amount: int) -> int:
        dp = [float('inf')] * (amount + 1)
        dp[0] = 0
        
        for coin in coins:
            for x in range(coin, amount + 1):
                dp[x] = min(dp[x], dp[x - coin] + 1)
        return dp[amount] if dp[amount] != float('inf') else -1 
```

LC 322 [**https://leetcode.com/problems/coin-change/description/**](https://leetcode.com/problems/coin-change/description/)

{% embed url="https://www.lintcode.com/problem/440" %}

1449 add string comparison, and append to previous str [https://leetcode.com/problems/form-largest-integer-with-digits-that-add-up-to-target/description/](https://leetcode.com/problems/form-largest-integer-with-digits-that-add-up-to-target/description/)&#x20;

## **0/1 knapsack, where each item can only be used once**

The items can be reused but in limited times - treat each piece of duplicate items as one item in a 0-1 knapsack problem - [https://www.lintcode.com/problem/798/](https://www.lintcode.com/problem/798/)

```python
class Solution:
    def canPartition(self, nums: List[int]) -> bool:
        # find sum of array elements
        total_sum = sum(nums)

        # if total_sum is odd, it cannot be partitioned into equal sum subsets
        if total_sum % 2 != 0:
            return False
        subset_sum = total_sum // 2

        # construct a dp table of size (subset_sum + 1)
        dp = [False] * (subset_sum + 1)
        dp[0] = True
        for curr in nums:
            for j in range(subset_sum, curr - 1, -1):
                dp[j] = dp[j] or dp[j - curr]

        return dp[subset_sum]
```

416 . Bucket DP/Coin Sum - [https://leetcode.com/problems/partition-equal-subset-sum/description/](https://leetcode.com/problems/partition-equal-subset-sum/description/)

2008 Sort it then treat it like knapsack [https://leetcode.com/problems/maximum-earnings-from-taxi/description/](https://leetcode.com/problems/maximum-earnings-from-taxi/description/)

<figure><img src="../../../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

## **Counting combinations instead of optimizing a value**

In addition to the traditional knapsack, we will need to store the specific profit reached as one of the states.&#x20;

* For example, dp\[p]\[w] represents the number of ways to reach profit p with the weight of w
  * The last p will store all ways to reach profit >= p
  * Transition function will be, dp\[p]\[w] = dp\[p]\[w] + dp\[p - p\[i]]\[w - w\[i]] for each item
  * We will need to iterate from the largest value down to the smaller value (because we had compressed the state of n items )
* If we only need to consider weight / value/ volume
  * dp\[state] represents number of ways to reach a particular state
  * For each item, dp\[state] += dp \[state - item\_value]
  * We will need to iterate from the largest value down to the smaller value (because we had compressed the state of n items )

Easy algorithms

&#x20;518 [https://leetcode.com/problems/coin-change-ii/description/](https://leetcode.com/problems/coin-change-ii/description/)

```python
class Solution:
    def change(self, amount: int, coins: List[int]) -> int:
        n = len(coins)
        dp = [[0] * (amount + 1) for _ in range(n + 1)]
        for i in range(n):
            dp[i][0] = 1

        for i in range(n - 1, -1, -1):
            for j in range(1, amount + 1):
                if coins[i] > j:
                    dp[i][j] = dp[i + 1][j]
                else:
                    dp[i][j] = dp[i + 1][j] + dp[i][j - coins[i]]

        return dp[0][amount]
```

Practise:

{% embed url="https://www.lintcode.com/problem/1448/" %}

## All Stone mashing problems

#### Intuition

consider stones list of \[a , b , c , d]

if we smash a & b, c & d, then a - b with c - d, the final weight is&#x20;

( a - b) - (c - d) = a - b - c + d = (a + d) - (b + c)&#x20;

which essentially divides the stones into two bags.&#x20;

We can use this property to solve some problems like minimum weight left after optimizing smashing (which is a total - 2 \* maximum weight of the smallest bag)

#### Practise Questions:

1049  Last Stone Weight II [https://leetcode.com/problems/last-stone-weight-ii/](https://leetcode.com/problems/last-stone-weight-ii/)



## Practise

