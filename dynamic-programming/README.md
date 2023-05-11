# Dynamic Programming

Common Problems for DP

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

1. Calculate how many possible ways to divide an array
2. To minimize the max sum of subarray by dividing an array with max k portions (note binary search of potential solution could be faster)

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

1. For 2-D matrix dp, if the new row value only depends on the previous row value
2. For 1-D dp, if the new position value only depends on the previous position(s)
