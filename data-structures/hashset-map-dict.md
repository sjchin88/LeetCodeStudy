# HashSet/Map/Dict

## Time Complexities

Insert/Search/Delete - O(1) in most cases

## Collisions

When two items have the same hash value (or more items than hash slot - pigeonhole)

Resolution

* Chaining with doubly linked list&#x20;
  * worst case O(n)
  * load factor alpha = n / m   (n = number of elements, m = size of table)
  * avg time complexity = O(1 + alpha)
* Open Addressing
  * Linear probing : h(k, i) = (h'(k) + i) % m
    * Example k = 38, m = 7, then the probe sequence will be&#x20;
    * h'(38) = 3 = h(k, 0), h(k, 1) = (3 + 1) % 7 = 4
  * Quadratic Probing: h(k, i) = (h'(k) + c1i + c2i^2) % m
  * Double hashing : h(k, i) = (h1(k) + i \* h2(k)) % m
    * Normally, h1(k) = k % m, h2(k) = 1 + (k % (m - 1))

## Hash function

* Dividision Method : h(k) = k % m&#x20;
  * avoid power of 2 for m
  * prime is usually good, but avoid prime too close to exact power of 2
* Multiplication method&#x20;
  * h(k) = lower (m(kA - lower(kA))
* Universal hashing
