# Dynamic Programming

## When to apply

* Searching for optimum combination
* Overlapping subproblems  (if no overlapping, have to use dfs with recursion, with time complexity often O(2 ^n)
* Local optimal is not necessary equal to global optimal (if it is equal, use Greedy)

## Prerequisites for DP

If you are working with arrays,&#x20;

* then you have to work with either subarrays （contiguous part of array) or subsequences ( non contiguous, but maintain relative order of elements). By breaking down the problem into smaller subproblem (like 0 to i for  0 < i <= n)
* Cannot work with subset (Random order), as the subproblems cannot guarantee overlap



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

1. The state corresponds to each coordinates (dimension of the problem)
2. Example:&#x20;
   1. KnapSack problem, usually is two state dp\[i]\[w]
   2. Longest Palindrome subsequence -> two state dp\[i]\[j], i = idx on str 1, j = idx on str 2

Practise:

115 [https://www.lintcode.com/problem/115/](https://www.lintcode.com/problem/115/)

When going from topleft to bottom right is difficult, consider working backward from bottom right to topleft.&#x20;

Example question: [https://leetcode.com/problems/dungeon-game/description/](https://leetcode.com/problems/dungeon-game/description/)

## Sequence Type

1. Similar to coordinate type, except that f(i) record the states up to i - 1
2. Useful to initialize f(0) as 0 (or other initial conditions required) to minimize/eliminate boundary checking&#x20;

Practise:

515 [https://www.lintcode.com/problem/515/](https://www.lintcode.com/problem/515/)

Another sequence type needs some thinking,&#x20;

If we can enumerate the states in certain orders, so that when we reach dp\[state] , all the previous state leading to dp\[state] has been calculated and final .

Practise&#x20;

LintCode; [https://www.lintcode.com/problem/398/description?fromId=178&\_from=collection](https://www.lintcode.com/problem/398/description?fromId=178&_from=collection)

## Dividing Type

See Popular DP questions





## Game Type

Often involved two players playing a game, trying to determine the optimum strategy

The outcome of optimum strategy is often  f(n) = gain - f(n - 1) ,&#x20;

gain = gain at this step,&#x20;

f(n - 1) = optimum strategy minus off the step&#x20;

we will need to iterate from the last step&#x20;

Practise

396 [https://www.lintcode.com/problem/396/](https://www.lintcode.com/problem/396/)

395 [https://www.lintcode.com/problem/395/description?fromId=178&\_from=collection](https://www.lintcode.com/problem/395/description?fromId=178&_from=collection)

## Potential Space Optimization

1. For 2-D matrix dp, if the new row value only depends on the previous row value, we can use only two rows to store the results (use old and new to represent row value, and interchange old and new value during iterations of each row)
2. For 1-D dp, if the new position value only depends on the previous position(s)
