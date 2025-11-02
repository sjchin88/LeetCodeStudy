# Common Mechanism

## Tiny Url

```python
import random
class Solution:
    
    def __init__(self):
        self.alphabet = "0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ";
        self._tiny2url = {}

    def get_rand(self):
        return ''.join(self.alphabet[random.randint(0, 61)] for i in range(6))

    def encode(self, longUrl):
        # Encodes a URL to a shortened URL.
        key = self.get_rand()
        while key in self.tiny2url:
            key = self.get_rand()
        self._tiny2url[key] = longUrl
        return f"http://tinyurl.com/{key}"

    def decode(self, shortUrl):
        # Decodes a shortened URL to its original URL.
        key = shortUrl[-6:]
        return self._tiny2url[key]
```
