Little Tanya decided to present her dad a postcard on his Birthday. She has already created a message — string s of length n, consisting of uppercase and lowercase English letters. Tanya can't write yet, so she found a newspaper and decided to cut out the letters and glue them into the postcard to achieve string s. The newspaper contains string t, consisting of uppercase and lowercase English letters. We know that the length of string t greater or equal to the length of the string s.

The newspaper may possibly have too few of some letters needed to make the text and too many of some other letters. That's why Tanya wants to cut some n letters out of the newspaper and make a message of length exactly n, so that it looked as much as possible like s. If the letter in some position has correct value and correct letter case (in the string s and in the string that Tanya will make), then she shouts joyfully "YAY!", and if the letter in the given position has only the correct value but it is in the wrong case, then the girl says "WHOOPS".

Tanya wants to make such message that lets her shout "YAY!" as much as possible. If there are multiple ways to do this, then her second priority is to maximize the number of times she says "WHOOPS". Your task is to help Tanya make the message.

##Input

The first line contains line s (1 ≤ |s| ≤ 2·10^5), consisting of uppercase and lowercase English letters — the text of Tanya's message.

The second line contains line t (|s| ≤ |t| ≤ 2·10^5), consisting of uppercase and lowercase English letters — the text written in the newspaper.

Here |a| means the length of the string a.

##Output

Print two integers separated by a space:

the first number is the number of times Tanya shouts "YAY!" while making the message,
the second number is the number of times Tanya says "WHOOPS" while making the message.

##Example

```
Input
-----
AbC
DCbA

Output
------
3 0

######

Input
-----
ABC
abc

Output
------
0 3

######

Input
-----
abacaba
AbaCaBA

Output
------
3 4
```

##Solution

###Idea

* Count the number of each character appear in the message and store in a hash map. For example: "abacaba" => {"a": 4, "b": 2, "c": 1}. Do the same with the newspaper text.
* For each key in message hash map, compare its count number to the same key's in newspaper text hash map. Minus both to the smallet one and add it to the "YAY!" number.
* After counting all "YAY!" number, for each key in message hash map, compare its count number to the its case-reverse key in newspaper text hash map. Minus both to the smallet one and add it to the "WHOOPS!" number.
* Return "YAY!" and "WHOOPS!" number.

###Implement
