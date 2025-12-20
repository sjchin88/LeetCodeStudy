# Fenwick Tree

Good article - [https://medium.com/carpanese/a-visual-introduction-to-fenwick-tree-89b82cac5b3c](https://medium.com/carpanese/a-visual-introduction-to-fenwick-tree-89b82cac5b3c)



Key Note

* 1 - index array -> bit index tree
* The value of a more significant bit is the sum of the values of the immediate less significant bit. Eg - 2(bit - 10) is the sum of 1 (bit 01) and 2, 6 (bit - 110 ) is the sum of 5 (bit -101), 8 (1000) is the sum of 4 (0100) and 5-8 .&#x20;

<figure><img src="../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

```python
class FenwickTree:
    def __init__(self, size):
        self.tree = [0] * (size + 1)

    # Update operation
    def add(self, i, delta):
        while i < len(self.tree):
            self.tree[i] += delta
            # add the least significant bit (i & (-i)), if we start from 9 (bit 1001)
            # it will become bit 1010 (number 10) then bit 1100 (number 12) 
            # then bit 10000 (number 16) then <<1 (32 , 64, etc)
            i += i & (-i)

    def query(self, i):
        s = 0
        while i > 0:
            # result of current number is the sum of all bits by removing 
            # the least significant bit 1 by 1 . ie 
            # if we start from 15 (bit 1111) then it is 15 + 14 (bit 1110) + 
            # 12 (bit 1100) + 8 (bit 1000)
            s += self.tree[i]
            i -= i & (-i)
        return s
```

practise question - [https://leetcode.com/problems/minimum-deletions-to-make-alternating-substring/description/](https://leetcode.com/problems/minimum-deletions-to-make-alternating-substring/description/)
