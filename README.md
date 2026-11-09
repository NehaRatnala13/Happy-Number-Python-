# LeetCode 202: Happy Number (Python)

Solution for **[LeetCode 202 - Happy Number](https://algo.monster/liteproblems/202)** using a hash set for cycle detection in Python 3.

## Problem Summary
Determine if a positive integer `n` is a happy number. A happy number is defined by the following process:
- Starting with any positive integer, replace the number by the sum of the squares of its digits.
- Repeat the process until the number equals `1` (where it stays), or it loops endlessly in a cycle which does not include `1`.
- Those numbers for which this process ends in `1` are happy.

## Python Solution

```python
class Solution:

  def isHappy(self, n: int) -> bool:

    def get_next(number: int) -> int:
      total_sum = 0
      while number > 0:
        number, digit = divmod(number, 10)
        total_sum += digit**2
      return total_sum

    seen = set()
    # Loop until n becomes 1 or we detect a cycle
    while n != 1 and n not in seen:
      seen.add(n)
      n = get_next(n)
    return n == 1
```

## Complexity Analysis

* **Time Complexity:** $\mathcal{O}(\log n)$ — The sum of squares transformation reduces numbers rapidly, bounding the number of iterations.
* **Space Complexity:** $\mathcal{O}(\log n)$ — Storage required for the `seen` hash set to track previously visited sequence values.
