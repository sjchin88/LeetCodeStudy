# KnapSack Problem

{% embed url="https://www.geeksforgeeks.org/0-1-knapsack-problem-dp-10/" %}
Explanation
{% endembed %}

## Derivations of the problem&#x20;

### All Stone mashing problems

#### Intuition

consider stones list of \[a , b , c , d]

if we smash a & b, c & d, then a - b with c - d, the final weight is&#x20;

( a - b) - (c - d) = a - b - c + d = (a + d) - (b + c)&#x20;

which essentially divides the stones into two bags.&#x20;

We can use this property to solve some problems, like minimum weight left after optimizing smashing (which is total - 2 \* maximum weight of the smallest bag)

#### Practise Questions:

1049  Last Stone Weight II [https://leetcode.com/problems/last-stone-weight-ii/](https://leetcode.com/problems/last-stone-weight-ii/)
