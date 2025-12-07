# Prime

## Sieve of Eratosthenes

```
# get primes
def get_primes(n:int)->list[int]:
    if n < 2:
        return []
    is_prime = [True] * (n + 1)
    is_prime[0] = False
    is_prime[1] = False
    num = 2
    primes = []
    for i in range(2, n + 1):
        if is_prime[i]:
            for j in range(i*i, n + 1, i):
                is_prime[j] = False
            primes.append(i)
    
    return primes
```
