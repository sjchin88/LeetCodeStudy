# KnapSack Problem

{% embed url="https://www.geeksforgeeks.org/0-1-knapsack-problem-dp-10/" %}
Explanation
{% endembed %}

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



## Derivations of the problem

### What if

1. The items can be reused in unlimited times - then for each item, we have to iterate through the state (weight/volume/area) up to the capacity - [https://www.lintcode.com/problem/440](https://www.lintcode.com/problem/440)
2. The items can be reused but in limited times - treat each piece of duplicate items as one item in a 0-1 knapsack problem - [https://www.lintcode.com/problem/798/](https://www.lintcode.com/problem/798/)
3.

### Finding the number of ways to reach certain profits / weight

In addition to the traditional knapsack, we will need to store the specific profit reached as one of the states.&#x20;

* For example, dp\[p]\[w] represents the number of ways to reach profit p with the weight of w
  * The last p will store all ways to reach profit >= p
  * Transition function will be, dp\[p]\[w] = dp\[p]\[w] + dp\[p - p\[i]]\[w - w\[i]] for each item
  * We will need to iterate from the largest value down to the smaller value (because we had compressed the state of n items )
* If we only need to consider weight / value/ volume
  * dp\[state] represents number of ways to reach a particular state
  * For each item, dp\[state] += dp \[state - item\_value]
  * We will need to iterate from the largest value down to the smaller value (because we had compressed the state of n items )

Practise:

[https://www.lintcode.com/problem/1448/](https://www.lintcode.com/problem/1448/)



### All Stone mashing problems

#### Intuition

consider stones list of \[a , b , c , d]

if we smash a & b, c & d, then a - b with c - d, the final weight is&#x20;

( a - b) - (c - d) = a - b - c + d = (a + d) - (b + c)&#x20;

which essentially divides the stones into two bags.&#x20;

We can use this property to solve some problems like minimum weight left after optimizing smashing (which is a total - 2 \* maximum weight of the smallest bag)

#### Practise Questions:

1049  Last Stone Weight II [https://leetcode.com/problems/last-stone-weight-ii/](https://leetcode.com/problems/last-stone-weight-ii/)
