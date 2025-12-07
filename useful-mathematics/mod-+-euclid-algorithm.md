# Mod + Euclid Algorithm

## Theorems

(A \* B) mod C = (A mod C \* B mod C) mod C

## Practise Problems

{% embed url="https://leetcode.com/problems/concatenate-non-zero-digits-and-multiply-by-sum-ii/description/" %}



## GCD & LCM

```
# GCD
def gcd(a, b):
    if a < b:
        return gcd(b, a)
    if b == 0:
        return a
    return gcd(b, a%b)

# LCM
def lcm(a, b):
    return (a * b) / gcd(a, b)
```
