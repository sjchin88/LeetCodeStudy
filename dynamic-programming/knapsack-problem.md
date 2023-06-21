# KnapSack Problem

{% embed url="https://www.geeksforgeeks.org/0-1-knapsack-problem-dp-10/" %}
Explanation
{% endembed %}

Key Summary

0 / 1 as for each item, we have the option of not including / including it into the knapsack

Brute forces will result in O(2^n)&#x20;

DP can often reduce the time complexity into O(n ^ 2). dp\[i]\[w] represents the state iterating till item i for weight w.&#x20;

for problems where the item price is the same as the item weight, and we want to find the max weight / specific weight is possible

* we can compressed the dp from 2-d to 1-d
* or we just use a set to store all possible states up to item i - 1, and iterate through the possible states for new possible state with i&#x20;



## Derivations of the problem&#x20;

### All Stone mashing problems

#### Intuition

consider stones list of \[a , b , c , d]

if we smash a & b, c & d, then a - b with c - d, the final weight is&#x20;

( a - b) - (c - d) = a - b - c + d = (a + d) - (b + c)&#x20;

which essentially divides the stones into two bags.&#x20;

We can use this property to solve some problems like minimum weight left after optimizing smashing (which is a total - 2 \* maximum weight of the smallest bag)

#### Practise Questions:

1049  Last Stone Weight II [https://leetcode.com/problems/last-stone-weight-ii/](https://leetcode.com/problems/last-stone-weight-ii/)
