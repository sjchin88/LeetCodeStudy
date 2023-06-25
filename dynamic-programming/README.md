# Dynamic Programming

## Common Problems for DP

Finding if certain combinations is possible for the solution

dp\[] value is true / false

dp\[big problem] = dp\[small problem 1] or dp\[small problem2]

Find the total number of combinations (not concern about specific solution, which mostly use backtracking (dfs)

dp\[big problem] = sum ( dp\[small problem 1] .... dp\[small problem n])

Find the max/min&#x20;

dp\[big problem] = min / max { dp\[small problem 1] .... dp\[small problem n] }

## General Steps

1. Find the state representation and optimal subproblem&#x20;
2. Determine the state transition function
3. Check the initial condition and boundary rules
4. Determine the order of calculations for the states

## Coordinate Type DP

1. The state corresponds to each coordinates&#x20;

Practise:

115 [https://www.lintcode.com/problem/115/](https://www.lintcode.com/problem/115/)

## Sequence Type

1. Similar to coordinate type, except that f(i) record the states up to i - 1
2. Useful to initialize f(0) as 0 (or other initial conditions required) to minimize/eliminate boundary checking&#x20;

Practise:

515 [https://www.lintcode.com/problem/515/](https://www.lintcode.com/problem/515/)

## Dividing Type

1.

Common:

dp\[i]\[j] represents the max/min results obtained by performing operations on elements i to j&#x20;

We need to start iterating from length of 2 to the entire length of the array,&#x20;

for each length and each starting point, iterate the divider (k) from i till j

```python
//
for length in range(2, n):
    for i in range(n - length + 1):
        j = i + length - 1
        for k in range(i, j):
            dp[i][j] = min/max (dp[i][j], dp[i][k] + dp[k + 1][j] etc)
```

Practise

87 (very hard) Scrambling String [https://leetcode.com/problems/scramble-string/submissions/](https://leetcode.com/problems/scramble-string/submissions/)

312 Burst Ballon [https://leetcode.com/problems/burst-balloons/submissions/](https://leetcode.com/problems/burst-balloons/submissions/)

410 Split Array Largest Sum [https://leetcode.com/problems/split-array-largest-sum/](https://leetcode.com/problems/split-array-largest-sum/)

512 [https://www.lintcode.com/problem/512/](https://www.lintcode.com/problem/515/)

## Game Type

Often involved two players playing a game, trying to determine the optimum strategy

The outcome of optimum strategy is often  f(n) = gain - f(n - 1) , gain = gain at this step,&#x20;

f(n - 1) = optimum strategy minus off the step&#x20;

Practise

396 [https://www.lintcode.com/problem/396/](https://www.lintcode.com/problem/396/)

## Potential Space Optimization

1. For 2-D matrix dp, if the new row value only depends on the previous row value, we can use only two rows to store the results (use old and new to represent row value, and interchange old and new value during iterations of each row)
2. For 1-D dp, if the new position value only depends on the previous position(s)
