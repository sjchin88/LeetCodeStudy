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

&#x20;
