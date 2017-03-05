Let’s consider K-based numbers, containing exactly N digits. We define a number to be valid if its K-based notation doesn’t contain two successive zeros. For example:

```
1010230 is a valid 7-digit number;
1000198 is not a valid number;
0001235 is not a 7-digit number, it is a 4-digit number.
```

Given two numbers N and K, you are to calculate an amount of valid K based numbers, containing N digits.
You may assume that 2 ≤ K ≤ 10; N ≥ 2; N + K ≤ 18.

##Input
The numbers N and K in decimal notation separated by the line break.

##Output
The result in decimal notation.

##Example

```
Input
-----
2
10

Output
------
90
```

##Solution

###Idea

* If `n = 1`, number of valid numbers is k
* If `n = 2`, number of valid numbers is (k - 1) * k
* With `n > 2` the number of valid numbers is a sum of:
  + With each of valid (n - 1) digits number, we can add a a digit from 1 to k at the start to get a valid n digits number.
  + With each of valid (n - 2) digits number, we can add a a digit from 1 to k and 0 at the start to get a valid n digits number. But if `n = 3`, we must subtract this number to (k - 1) because 0 is a valid 1 digit number but x00 (with x from 1 to (k - 1)) is not a valid 3 digits number.

###Implement

```python
def valid_number(n, k):
    if n == 1:
        return k
    elif n == 2:
        return (k -1) * k
    elif n == 3:
        return ((k - 1) * valid_number(n - 1, k)) + ((k-1) * (valid_number(n-2, k) - 1))
    else:
        return ((k - 1) * valid_number(n - 1, k)) + ((k-1) * valid_number(n-2, k))
```
