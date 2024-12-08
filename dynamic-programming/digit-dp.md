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
# target_disit is the digit chosen/we want to count
# digit[idx] is the limiting integer at current idx
# previousTight is the tight value from previous state
newTight = previousTight & (target_digit==digit[idx])

# Example, we at 32XX, we want to look at idx = 1 (sec digit from left)
# previousTight = 1, at target_digit (4) == digit[1] (4) , newTight will be 1
```

* DP states, usually consists of dp\[idx]\[tight]\[substate],&#x20;
  * idx is the index from the right (least significant)
  * tight as explained early
  * substate depends, for calculating sum of digits, it will be range of possible sum for single number (0 -180 if 20 digits max).&#x20;
* Time complexity O(idx \* tight \* state)
