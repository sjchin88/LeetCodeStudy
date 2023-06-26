# KnapSack Problem

{% embed url="https://www.geeksforgeeks.org/0-1-knapsack-problem-dp-10/" %}
Explanation
{% endembed %}

Key Summary

0 / 1 as for each item, we have the option of not including / including it into the knapsack

Brute forces will result in O(2^n)&#x20;

DP can often reduce the time complexity into O(n ^ x). x represent the number of states that we need to iterate through. The states required will include

* **The number of items** considered thus far (Note this is not required to be stored if we can iterate the remaining states backward (from bigger value down to smaller value)
* The weight/volume/area of the items included up to the **capacity** of the knapsack&#x20;
* Additional parameters required
* Note the value stored inside the dp is a state itself, most often we only store the optimal state required
* For example, for a typical knapsack problem:&#x20;
  * dp\[i]\[w] represents the state iterating till item i for weight w.&#x20;
  * We can also use only dp\[w] to represent the max/min value for weight w, we still iterating through all n items, but for each iteration, we start from the right (biggest）down to the left&#x20;
  * where dp\[w] = max(dp\[w], dp\[w - w\[i]] + p\[i])
  * If we do left to right then the same item's value could be duplicated in calculating the bigger part

for problems where the item price is the same as the item weight, and we want to find the max weight / specific weight is possible

* we can compress the dp from 2-d to 1-d
* or we just use a set to store all possible states up to item i - 1, and iterate through the possible states for new possible state with i&#x20;



## Derivations of the problem

### Finding the number of ways to reach certain profits

In addition to the traditional knapsack, we will need to store the specific profit reached as one of the states.&#x20;

* For example, dp\[p]\[w] represents the number of ways to reach profit p with the weight of w
  * The last p will store all ways to reach profit >= p
  * Transition function will be, dp\[p]\[w] = dp\[p]\[w] + dp\[p - p\[i]]\[w - w\[i]] for each item
  * We will need to iterate from largest value down to smaller value

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
