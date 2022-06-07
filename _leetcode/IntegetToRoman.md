---
layout: default
title: Integer To Roman
has_children: false
---

# Conversion between Integer and Roman

{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Integer to Roman

This problem is most easily solved using a lookup table  for the conversion between digit and numeral. In this case, we can easily deal with the values in descending order and insert the appropriate numeral (or numerals) as many times as we can while reducing our target number (N) by the same amount.  
Once N runs out, we can return the answer.

```java
class Solution {
    final static int[] val = {1000,900,500,400,100,90,50,40,10,9,5,4,1};
    final static String[] rom = {"M","CM","D","CD","C","XC","L","XL","X","IX","V","IV","I"};

    public String intToRoman(int N) {
        StringBuilder ans = new StringBuilder();
        for (int i = 0; N > 0; i++)
            while (N >= val[i]) {
                ans.append(rom[i]);
                N -= val[i];
            }
        return ans.toString();
    }
}
```

## Roman to Integer

The only really tricky thing about counting in roman numerals is when a numeral is used as a subtractive value rather than an additive value.  In "IV" for example, the value of "I", 1, is subtracted from the value of "V", 5. Otherwise, you're simply just adding the values of all the numerals.

The one thing we should realize about subtractive numerals is that they're identifiable because they appear before a larger number. This means that the easier way to iterate through roman numerals is from right to left, to aid in the identifying process.

So then the easy thing to do here would be to iterate backward through S, look up the value for each letter, and then add it to our answer (ans). If we come across a letter value that's smaller than the largest one seen so far, it should be subtracted rather than added.

The standard approach would be to use a separate variable to keep track of the highest value seen, but there's an easier trick here.  Since numbers generally increase in a roman numeral notation from right to left, any subtractive number must also be smaller than our current ans.

So we can avoid the need for an extra variable here. We do run into the case of repeated numerals causing an issue (ie, "III"), but we can clear that by multiplying num by any number between 2 and 4 before comparing it to ans, since the numerals jump in value by increments of at least 5x.

```java
class Solution {
    public int romanToInt(String S) {
        int ans = 0, num = 0;
        for (int i = S.length()-1; i >= 0; i--) {
            switch(S.charAt(i)) {
                case 'I': num = 1; break;
                case 'V': num = 5; break;
                case 'X': num = 10; break;
                case 'L': num = 50; break;
                case 'C': num = 100; break;
                case 'D': num = 500; break;
                case 'M': num = 1000; break;
            }
            if (4 * num < ans) ans -= num;
            else ans += num;
        }
        return ans;
    }
}
```
