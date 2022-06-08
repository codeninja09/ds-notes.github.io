---
layout: default
title: Backtracking
has_children: false
---

# Backtracking

{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

17. Letter Combinations of a Phone Number

Given a string containing digits from 2-9 inclusive, return all possible letter combinations that the number could represent. Return the answer in any order.

A mapping of digit to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.

```
Example 1:

Input: digits = "23"
Output: ["ad","ae","af","bd","be","bf","cd","ce","cf"]
```

```java
class Solution {
    
    final char[][] letters = {{},{},{'a','b','c'},{'d','e','f'},{'g','h','i'},{'j','k','l'}, {'m','n','o'},{'p','q','r','s'},{'t','u','v'},{'w','x','y','z'}};
    
    public List<String> letterCombinations(String digits) {
        int len = digits.length();
        List<String> result = new ArrayList<>();
        if(len == 0){
            return result;
        }
        letterCombinations(digits,0,len, new StringBuilder(), result);
        return result;
    }
    
    public void letterCombinations(String digits, int pos, int len, StringBuilder sb, List<String> result) {
        if(pos == len){
            result.add(sb.toString());
        }else{
            char[] arr = letters[Character.getNumericValue(digits.charAt(pos))];
            for(char c : arr){
               letterCombinations(digits,pos+1,len, new StringBuilder(sb).append(c), result); 
            }                                                    
        }
        
    }
}
```