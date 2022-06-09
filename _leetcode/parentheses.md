---
layout: default
title: Parentheses
has_children: false
---

# Parentheses

{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

20. Valid Parentheses
```
Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:

- Open brackets must be closed by the same type of brackets.
- Open brackets must be closed in the correct order.

 

Example 1:

Input: s = "()"
Output: true

Example 2:

Input: s = "()[]{}"
Output: true

Example 3:

Input: s = "(]"     s= "]"
Output: false

```

```java
class Solution {
    public boolean isValid(String s) {
        Stack<Character> stack = new Stack<>();
        for (char c : s.toCharArray()) {
            if (c == '(' || c == '[' || c == '{')
                stack.push(c);
            else {
                if (stack.isEmpty()) // this condition is needed if the input string has closed parentheses as starting. s= "]"
                    return false;
                if (c == ')') {
                    if ('(' != stack.pop())
                        return false;
                } else if (c == ']') {
                    if ('[' != stack.pop())
                        return false;
                } else if (c == '}') {
                    if ('{' != stack.pop())
                        return false;
                }
            }
        }
        return stack.isEmpty();
    }
}
```

Time Complexity - O(n)  
We are looping through the string once to cover all the characters

Space Complexity - O(n)  
We are storing all the characters in to a stack, In wrost case scenario if all the parentheses are open one's then they will be stored in the stack.

