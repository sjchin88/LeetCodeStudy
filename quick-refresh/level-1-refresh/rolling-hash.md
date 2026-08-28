# Rolling Hash

```python
def rolling_hash(s: str, window_size: int, base: int = 26, mod: int = 10**9 + 7) -> List[int]:
    """
    Calculates the rolling hash values of all substrings of length window_size in string s.
    Uses the polynomial rolling hash algorithm with base and mod as constants.

    :param s: the input string
    :param window_size: the size of the rolling window
    :param base: the base for the polynomial hash function
    :param mod: the modulus for the polynomial hash function
    :return: a list of hash values of all substrings of length window_size in s
    """
    n = len(s)
    power = [1] * (n + 1)
    hash_values = [0] * (n - window_size + 1)

    # Precompute the powers of the
    # base modulo the mod
    for i in range(1, n + 1):
        power[i] = (power[i - 1] * base) % mod

    # Compute the hash value of
    # the first window
    current_hash = 0
    for i in range(window_size):
        current_hash = (current_hash * base + ord(s[i])) % mod

    hash_values[0] = current_hash

    # Compute the hash values of the
    # rest of the substrings
    for i in range(1, n - window_size + 1):

        # Remove the contribution of the
        # first character in the window
        current_hash = (
            current_hash - power[window_size - 1] * ord(s[i - 1])) % mod

        # Shift the window by one character
        # and add the new character
        # to the hash
        current_hash = (current_hash * base + ord(s[i + window_size - 1])) % mod

        hash_values[i] = current_hash

    return hash_values
```

## Rabin Karp

<figure><img src="../../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

```python
# Function to search for all occurrences of 'pat' in 'txt' using Rabin-Karp
def search(pat, txt):

    # Number of characters in the input alphabet (ASCII)
    d = 256

    # A prime number for modulo operations to reduce collisions
    q = 101

    # Length of the pattern
    m = len(pat)

    # Length of the text
    n = len(txt)

    # Hash value for pattern
    p = 0

    # Hash value for current window of text
    t = 0

    # High-order digit multiplier
    h = 1

    ans = []

    # Precompute h = pow(d, m-1) % q
    for i in range(m - 1):
        h = (h * d) % q

    # Compute initial hash values for pattern and first window of text
    for i in range(m):
        p = (d * p + ord(pat[i])) % q
        t = (d * t + ord(txt[i])) % q

    # Slide the pattern over text one by one
    for i in range(n - m + 1):

        # If hash values match, check characters one by one
        if p == t:
            match = True
            for j in range(m):
                if txt[i + j] != pat[j]:
                    match = False
                    break
            if match:
                ans.append(i)

        # Calculate hash value for the next window
        if i < n - m:
            t = (d * (t - ord(txt[i]) * h) + ord(txt[i + m])) % q
            if t < 0:
                t += q

    return ans
```
