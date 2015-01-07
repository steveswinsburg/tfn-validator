# TFN Validator
A tool to validate Tax File Numbers (TFN) as provided by the Australian Taxation Office

### Why?
I needed to validate a tax file number before entering it into a document, and couldn't find one online. The format is well known, so I made a validator. Now you too can validate TFNs, even just for fun if you like :)

## Usage


## The maths

Every TFN includes a check digit for detecting erroneous numbers. The algorithm is based on simple modulo 11 arithmetic just like many other digit checksum schemes. The weighting algorithm for the TFN is well known, with each digit multiplied by the corresponding weighting number.

Therefore, the example TFN '123456782' can be checked by the following process:
<pre>
1   2   3   4    5    6    7    8    2
×   ×   ×   ×    ×    ×    ×    ×    ×
1   4   3   7    5    8    6    9    10
=   =   =   =    =    =    =    =    =
1 + 8 + 9 + 28 + 25 + 48 + 42 + 72 + 20 = 253
</pre>

The sum of the numbers is 253 (1 + 8 + 9 + 28 + 25 + 48 + 42 + 72 + 20 = 253). 253 is a multiple of 11 (11 × 23 = 253). Therefore the number is valid.
