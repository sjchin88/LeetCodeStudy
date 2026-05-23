# Digit DP

* Digit DP is a technique used to solve problems that asks you to find the number of integers within a range that satisfies some property based on the digits of the integers.&#x20;
* Typically, the ranges are between large integers (such as between $$1$$ to 10^18) so looping through each integer and checking if it satisfies the given property is too slow.&#x20;
* Digit DP uses the digits of the integers to quickly count the number of integers with the given property in the range of integers.

## Core concept

* G(a - b) can be given by G(b) - G(a-1)  , if a and b are inclusive, a = lower bound, b = upper bound.&#x20;
* If the answer for digit = 0 (first digit/right most digit/least significant digit) is calculated, for next iteration of digit = 1, the sum can be reused&#x20;
* Usually need two states for same digit level, **tight or not tight**&#x20;
  * tight - current digits range is restricted from 0 to digit\[idx] inclusively
  * not tight, current digits range is not restricted, span from 0 to 9.&#x20;
  * Example, we want to count sum of digits for upper bound 3245.&#x20;
    * If we at 31XX, the next digit is not **tight**, as we can sum from 310X till 319X.&#x20;
    * If we at 32XX, the next digit is tight, we can only sum from 320X till 324X.&#x20;
  * Useful formula to detemine tight

```
# Assuming top-down/dp with memoization, starting from left/most significant digit
# target_digit is the digit chosen/we want to count
# digit[idx] is the limiting integer at current idx
# previousTight is the tight value from previous state
newTight = previousTight & (target_digit==digit[idx])

# Example, we at 32XX, we want to sum up result at idx = 2 (third digit from left)
# previousTight = 1, at target_digit (2) == digit[1] (2) , newTight will be 1
# thus we can sum up to the digit[2] which is 4 only instead of 9
```

* DP states, usually consists of dp\[idx]\[tight]\[substate],&#x20;
  * idx is the index from the left(most significant) / right (least significant)
  * tight as explained early
  * substate depends, for calculating sum of digits, it will be range of possible sum for single number (0 -180 if 20 digits max).&#x20;
  * The return value is total number meeting certain conditions.
* Time complexity O(idx \* tight \* state)

## Example Problem & Code

```python
# Problem: https://leetcode.com/problems/number-of-digit-one/description/
class Solution:
    def countDigitOne(self, n: int) -> int:
        n_str = str(n)
        digits = [int(ch) for ch in n_str]

        # cache do memoization (dp)
        # the Time & space complexity are decided by number of states involved, 
        # which in this case will be n(digit) * n(tight), roughtly equals to 10 * 2 etc
        @cache
        def count(digit, tight) -> tuple[int, int]:
            if digit == len(digits):
                return 0, 1
            
            upper_limit = 9
            if tight:
                upper_limit = digits[digit]
            
            cnt_one = 0
            cnt_num = 0
            for i in range(upper_limit + 1):
                t1, tn = count(digit+1, tight & (i==digits[digit]))
                cnt_one += t1
                cnt_num += tn
                if i == 1:
                    cnt_one += tn
            return cnt_one, cnt_num

        cnt_one, cnt_num = count(0, 1)
        return cnt_one
```

### Practise Problem:



## Template Formula

Example solution for [https://leetcode.com/problems/number-of-digit-one/description/](https://leetcode.com/problems/number-of-digit-one/description/)

````python


class Solution:
    def countDigitOne(self, n: int) -> int:
        n_str = str(n)
        digits = [int(ch) for ch in n_str]

        # State is omitted here, as we dont need to stored the state
        @cache
        def count(digit, tight) -> tuple[int, int]:
            if digit == len(digits):
                return 0, 1
            
            upper_limit = 9
            if tight:
                upper_limit = digits[digit]
            
            cnt_one = 0
            cnt_num = 0
            for i in range(upper_limit + 1):
                t1, tn = count(digit+1, tight and (i==digits[digit]))
                cnt_one += t1
                cnt_num += tn
                if i == 1:
                    cnt_one += tn
            return cnt_one, cnt_num

        cnt_one, cnt_num = count(0, 1)
        return cnt_one
```
````

Another case for [https://leetcode.com/problems/count-beautiful-numbers/description/](https://leetcode.com/problems/count-beautiful-numbers/description/)

````python
class Solution:
    def beautifulNumbers(self, l: int, r: int) -> int:
        def count_up_to(x):
            num = str(x)
            digits = [int(ch) for ch in num]

            @cache
            def count(idx, tight, nsum, nprod):
                
                total = 0
                if idx == len(digits):
                    if nsum == 0:
                        return 0
                    if nprod % nsum == 0:
                        return 1
                    return 0
                limit = 9 if not tight else digits[idx]
                for i in range(limit + 1):
                    new_sum = nsum + i
                    # Keep new_prod at 1 if we are at leading zeros (like 0000XX)
                    new_prod = 1 if new_sum == 0 else nprod * i
                    total += count(idx+1, tight and (i==limit), new_sum, new_prod)
                return total
            return count(0, True, 0, 1)

        return count_up_to(r) - count_up_to(l - 1)
```
````
