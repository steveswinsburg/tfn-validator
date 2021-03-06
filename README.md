# TFN Validator
A tool to validate Tax File Numbers (TFN) as provided by the Australian Taxation Office.

### Why?
I needed to validate a TFN before entering it into a document, and couldn't find one online. The format is well known, so I made a validator. Now you too can validate TFNs, even just for fun if you like, make a day of it.

## Usage
[Open the validator](https://cdn.rawgit.com/steveswinsburg/tfn-validator/master/tfn-validator.html)

Enter the TFN, click <kbd>Validate</kbd> and wait for the magic!

## Privacy concerns?
Privacy is guaranteed. You only need to enter the TFN, which is useless on its own, as its just a number in a certain format. There is absolutely no way that anyone's details can be leaked at all since they arent there to start with.

In addition, the validator stores nothing, it doesn't even make a web request so nothing is sent to any server at all. You can check the source :)

## The maths
The TFN validation algorithm is based on simple modulo 11 arithmetic just like many other digit checksum schemes. The weighting algorithm for the TFN is well known[1],[2], with each digit multiplied by the corresponding weighting number.

Therefore, the example TFN '123456782' can be checked by the following process:
<pre>
1   2   3   4    5    6    7    8    2
×   ×   ×   ×    ×    ×    ×    ×    ×
1   4   3   7    5    8    6    9    10
=   =   =   =    =    =    =    =    =
1 + 8 + 9 + 28 + 25 + 48 + 42 + 72 + 20 = 253
</pre>

The sum of the numbers is 253 (1 + 8 + 9 + 28 + 25 + 48 + 42 + 72 + 20 = 253). 253 is a multiple of 11 (11 × 23 = 253). Therefore the number is valid.

[1] Management of Tax File Numbers, ANAO, 1999 (ISBN 0 644 38866 8) http://www.anao.gov.au/%7E/media/Uploads/Documents/1998%2099_audit_report_37.pdf

[2] Tax file number, Wikipedia, http://en.wikipedia.org/wiki/Tax_file_number
