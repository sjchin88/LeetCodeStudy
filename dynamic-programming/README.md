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

Practise

512 [https://www.lintcode.com/problem/512/](https://www.lintcode.com/problem/515/)
