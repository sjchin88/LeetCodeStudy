# Bit Operation



<figure><img src="../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

a ^ b = c implies a = b ^ c or b = a ^ c

So if we have a set of prefix\_xor where prefix\_xor\[i] = 0 ^ nums\[1] ^ nums\[2] ^... ^ nums\[i - 1]

We can find the xor results of numbers between i and j by prefix\_xor\[j + 1] ^ prefix\_xor\[i]&#x20;

Quick Practise:

* [https://leetcode.com/problems/bitwise-ors-of-subarrays/description/](https://leetcode.com/problems/bitwise-ors-of-subarrays/description/)&#x20;
* (a ^ b) & (a ^ c) = a & (b ^ c) [https://leetcode.com/problems/find-xor-sum-of-all-pairs-bitwise-and/description/](https://leetcode.com/problems/find-xor-sum-of-all-pairs-bitwise-and/description/)

Trick to find right most 1 -bit&#x20;

```python
diff = x & (-x)
```

## Use of XOR Properties

Rules:

1. For an array, if we calculate xor of all elements and an element appear twice, its effect to the final xor is 0.&#x20;
2.

136 [https://leetcode.com/problems/single-number/description/](https://leetcode.com/problems/single-number/description/)

137 Combo of XOR and not [https://leetcode.com/problems/single-number-ii/](https://leetcode.com/problems/single-number-ii/)

260 Combo of XOR, right most 1 - bit [https://leetcode.com/problems/single-number-iii/description/](https://leetcode.com/problems/single-number-iii/description/)
