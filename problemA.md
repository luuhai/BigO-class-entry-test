ZS the Coder and Chris the Baboon are travelling to Udayland! To get there, they have to get on the special IOI bus. The IOI bus has n rows of seats. There are 4 seats in each row, and the seats are separated into pairs by a walkway. When ZS and Chris came, some places in the bus was already occupied.

ZS and Chris are good friends. They insist to get a pair of neighbouring empty seats. Two seats are considered neighbouring if they are in the same row and in the same pair. Given the configuration of the bus, can you help ZS and Chris determine where they should sit?

##Input

The first line of the input contains a single integer n (1 ≤ n ≤ 1000) — the number of rows of seats in the bus.

Then, n lines follow. Each line contains exactly 5 characters, the first two of them denote the first pair of seats in the row, the third character denotes the walkway (it always equals '|') and the last two of them denote the second pair of seats in the row.

Each character, except the walkway, equals to 'O' or to 'X'. 'O' denotes an empty seat, 'X' denotes an occupied seat. See the sample cases for more details.

##Output

If it is possible for Chris and ZS to sit at neighbouring empty seats, print "YES" (without quotes) in the first line. In the next n lines print the bus configuration, where the characters in the pair of seats for Chris and ZS is changed with characters '+'. Thus the configuration should differ from the input one by exactly two charaters (they should be equal to 'O' in the input and to '+' in the output).

If there is no pair of seats for Chris and ZS, print "NO" (without quotes) in a single line.

If there are multiple solutions, you may print any of them.

##Example
```
Input
-----
6
OO|OX
XO|XX
OX|OO
XX|OX
OO|OO
OO|XX

Output
------
YES
++|OX
XO|XX
OX|OO
XX|OX
OO|OO
OO|XX

#####

Input
-----
4
XO|OX
XO|XX
OX|OX
XX|OX

Output
------
NO
```

##Solution

###Idea

* Load the bus configuration into an array of string, each element is a row of seat.
* Loop over the array to compare each element to see whether it is equal to one of the following string:

    ```
    ["OO|OO", "OO|OX", "OO|XO", "OO|XX", "OX|OO", "XO|OO", "XX|OO"]
    ```

  If true, print "YES", replace this element with new string with the "++" characters in place of the first "OO" characters, print the array and return.
* If none of the elements satisfy previous condition, print "NO" and return.

###Implement
