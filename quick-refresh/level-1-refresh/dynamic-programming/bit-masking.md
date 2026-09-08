# Bit Masking

Good reference: [https://www.hackerearth.com/practice/algorithms/dynamic-programming/bit-masking/tutorial/](https://www.hackerearth.com/practice/algorithms/dynamic-programming/bit-masking/tutorial/)

Good for&#x20;

* Assignment problems, assiging X people to Y tasks

Useful property of bitmasking that make this possible

* Bitmask is a good represent of subset elements for a set. Consider set A = {1, 2, 3, 4, 5}. When each ith (0 <= i <= 4) is set it menas ith element is present in subset.&#x20;
* Setting new element of ith position:
  * b | (1 << i)
* Unset element of ith position:
  * 1 << i to get the target bit
  * \~( 1 << i ) get all bit except i , eg: 11101 when i == 1
  * b & \~( 1 << i ) unset only ith&#x20;
* Check if ith bit is set&#x20;
  * b & (1 << i)

### Example walkthrough Hats to Peoples

1434 [https://leetcode.com/problems/number-of-ways-to-wear-different-hats-to-each-other/description/](https://leetcode.com/problems/number-of-ways-to-wear-different-hats-to-each-other/description/)

```python
class Solution:
    def numberWays(self, hats: List[List[int]]) -> int:
        n = len(hats)
        MOD = 10**9 + 7
        target_mask = (1 << n) - 1

        hats_to_people = defaultdict(list)
        for person, liked_hats in enumerate(hats):
            for hat in liked_hats:
                hats_to_people[hat].append(person)

        # dp[hat][mask]: ways to cover `mask` using a subset of hats in range [1..hat]
        dp = [[0] * (target_mask + 1) for _ in range(41)]
        
        # Base case: 0 hats considered covers mask 0 in exactly 1 way (nobody gets a hat)
        dp[0][0] = 1

        for hat in range(1, 41):
            for mask in range(target_mask + 1):
                # Choice 1: Don't use this hat
                total = dp[hat - 1][mask]

                # Choice 2: Assign this hat to person p
                for p in hats_to_people[hat]:
                    # If this person in the mask
                    if mask & (1 << p):
                        # add previous subset where the person is not in the mask
                        total = (total + dp[hat - 1][mask ^ (1 << p)]) % MOD

                dp[hat][mask] = total

        return dp[40][target_mask]
```

Example 2

1799 [https://leetcode.com/problems/maximize-score-after-n-operations/description/](https://leetcode.com/problems/maximize-score-after-n-operations/description/)

```python
class Solution:
    def maxScore(self, n: List[int]) -> int:
        @cache
        def dfs(i: int, mask: int) -> int:
            if i > len(n) // 2:
                return 0;
            res = 0
            for j in range(len(n)):
                for k in range(j + 1, len(n)):
                    # combination of j + k new pair.
                    new_mask = (1 << j) + (1 << k)
                    # check if already covered by mask, if not
                    if not mask & new_mask:
                        res = max(res, i * gcd(n[j], n[k]) + dfs(i + 1, mask + new_mask))
            return res
        return dfs(1, 0)
```
