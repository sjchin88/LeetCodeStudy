# String Matching / Edit

Practise

LeetCode 10 explanation:

### Core Logic Behind the Branches

At any state `dp(i, j)` where $$ $i$ $$ is the index in `text` and $$ $j$ $$ is the index in `pattern`:

1. Base Case: If $$ $j = \text{len}(pattern)$ $$, return `True` only if $$ $i = \text{len}(text)$ $$.
2. `*` Branching (`pattern[j+1] == '*'`): You have two choices:
   * Skip zero occurrences: `dp(i, j + 2)`
   * Consume one more character at pattern\[j] (if `first_match` holds): `dp(i + 1, j)`
3. Standard Match: If no `*` follows, require `first_match` and move both pointers: `dp(i + 1, j + 1)`.



44 . [https://leetcode.com/problems/wildcard-matching/](https://leetcode.com/problems/wildcard-matching/)

72 . [https://leetcode.com/problems/edit-distance/description/](https://leetcode.com/problems/edit-distance/description/)
