# Binary Jumping / Lifting

## Reference

Ref1 : [https://codeforces.com/blog/entry/100826](https://codeforces.com/blog/entry/100826)

Ref2 : [https://usaco.guide/plat/binary-jump?lang=cpp](https://usaco.guide/plat/binary-jump?lang=cpp)

## Key Idea

Common Application

"Let G be a **graph** (can be tree or several tree) with N nodes. For Q queries of the form (K,V) we want to find the **K-th node** of **V** as travel in the graph. "

The Brute force solution will start from every node in the graph, and travel (following the edges) in K step. This will have time complexities of O (NK) -> if N and K become very large, the time spent will become unacceptable.&#x20;

However, notice that there will be repeated traversal given the nodes are within the graph.&#x20;

For example, if node A  travel to node B in one step, node B travel to node C in one step, then node A will travel to node C in two steps.&#x20;

Similarly, f node A  travel to node C in two steps, node C travel to node D in two steps, then node A will travel to node D in four steps.

For every k-th steps of power of two, say k = 2^i

we can reuse the computation from  2^(i - 1) steps for all the nodes

Thus this can solve the problem in O(N log2K) time.&#x20;

With space complexity of O(N log2K)

## Practise

Leetcode 2836: [https://leetcode.com/problems/maximize-value-of-function-in-a-ball-passing-game/](https://leetcode.com/problems/maximize-value-of-function-in-a-ball-passing-game/)
