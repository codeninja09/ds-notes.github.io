---
layout: default
title: Random
has_children: false
---

# Random

{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

1700. Number of Students Unable to Eat Lunch
```
The school cafeteria offers circular and square sandwiches at lunch break, referred to by numbers 0 and 1 respectively. All students stand in a queue. Each student either prefers square or circular sandwiches.

The number of sandwiches in the cafeteria is equal to the number of students. The sandwiches are placed in a stack. At each step:

    If the student at the front of the queue prefers the sandwich on the top of the stack, they will take it and leave the queue.
    Otherwise, they will leave it and go to the queue's end.

This continues until none of the queue students want to take the top sandwich and are thus unable to eat.

You are given two integer arrays students and sandwiches where sandwiches[i] is the type of the i​​​​​​th sandwich in the stack (i = 0 is the top of the stack) and students[j] is the preference of the j​​​​​​th student in the initial queue (j = 0 is the front of the queue). Return the number of students that are unable to eat.

 

Example 1:

Input: students = [1,1,0,0], sandwiches = [0,1,0,1]
Output: 0 
Explanation:
- Front student leaves the top sandwich and returns to the end of the line making students = [1,0,0,1].
- Front student leaves the top sandwich and returns to the end of the line making students = [0,0,1,1].
- Front student takes the top sandwich and leaves the line making students = [0,1,1] and sandwiches = [1,0,1].
- Front student leaves the top sandwich and returns to the end of the line making students = [1,1,0].
- Front student takes the top sandwich and leaves the line making students = [1,0] and sandwiches = [0,1].
- Front student leaves the top sandwich and returns to the end of the line making students = [0,1].
- Front student takes the top sandwich and leaves the line making students = [1] and sandwiches = [1].
- Front student takes the top sandwich and leaves the line making students = [] and sandwiches = [].
Hence all students are able to eat.

Example 2:

Input: students = [1,1,1,0,0,1], sandwiches = [1,0,0,0,1,1]
Output: 3

```


```java
// option 1
class Solution {
    public int countStudents(int[] students, int[] sandwiches) {
        int len = students.length;
        Queue<Integer> q = new LinkedList<>();
        for(int i = 0 ; i< len ; i++){
            q.add(students[i]);
        }
        int counter = 0;
        int temp = 0;
        while(!q.isEmpty()){
            if(q.peek() == sandwiches[counter]){
                q.remove();
                counter++;
                temp = 0;
            }else{
                q.add(q.remove());
                temp++;
            }
            
            if(temp == q.size()){
                return q.size();
            }
        }
        return 0;
    }
}

// option 2
class Solution {
    public int countStudents(int[] students, int[] sandwiches) {
        int ones = 0; //count of students who prefer type1
        int zeros = 0; //count of students who prefer type0
		
        for(int stud : students){
            if(stud == 0) zeros++;
            else ones++;
        }
        
        // for each sandwich in sandwiches
        for(int sandwich : sandwiches){
            if(sandwich == 0){  // if sandwich is of type0
                if(zeros == 0){ // if no student want a type0 sandwich
                    return ones;
                }
                zeros--;
            }
            else{  // if sandwich is of type1
                if(ones == 0){  // if no student want a type1 sandwich 
                    return zeros;
                }
                ones--;
            }
        }
        return 0;
    }
}

```

2073. Time Needed to Buy Tickets

```
There are n people in a line queuing to buy tickets, where the 0th person is at the front of the line and the (n - 1)th person is at the back of the line.

You are given a 0-indexed integer array tickets of length n where the number of tickets that the ith person would like to buy is tickets[i].

Each person takes exactly 1 second to buy a ticket. A person can only buy 1 ticket at a time and has to go back to the end of the line (which happens instantaneously) in order to buy more tickets. If a person does not have any tickets left to buy, the person will leave the line.

Return the time taken for the person at position k (0-indexed) to finish buying tickets.

 

Example 1:

Input: tickets = [2,3,2], k = 2
Output: 6
Explanation: 
- In the first pass, everyone in the line buys a ticket and the line becomes [1, 2, 1].
- In the second pass, everyone in the line buys a ticket and the line becomes [0, 1, 0].
The person at position 2 has successfully bought 2 tickets and it took 3 + 3 = 6 seconds.

Example 2:

Input: tickets = [5,1,1,1], k = 0
Output: 8
Explanation:
- In the first pass, everyone in the line buys a ticket and the line becomes [4, 0, 0, 0].
- In the next 4 passes, only the person in position 0 is buying tickets.
The person at position 0 has successfully bought 5 tickets and it took 4 + 1 + 1 + 1 + 1 = 8 seconds.

```

```java
class Solution {
    public int timeRequiredToBuy(int[] tickets, int k) {
        int sub = tickets[k];
        int total = 0;
        
        for(int i = 0; i < tickets.length; i++) {
            if(i <= k) total += Math.min(sub,tickets[i]);
            else total += Math.min(sub - 1, tickets[i]);
        }
        return total;
        
    }
}
```

405. Convert a Number to Hexadecimal

```
Given an integer num, return a string representing its hexadecimal representation. For negative integers, two’s complement method is used.

All the letters in the answer string should be lowercase characters, and there should not be any leading zeros in the answer except for the zero itself.

Note: You are not allowed to use any built-in library method to directly solve this problem.

 

Example 1:

Input: num = 26
Output: "1a"

Example 2:

Input: num = -1
Output: "ffffffff"

```


```java
class Solution {
    public String toHex(int num) {
        if(num == 0){
            return "0";
        }
        char[] c = {'0', '1', '2' ,'3','4','5','6','7','8','9','a','b','c','d','e','f'};
        StringBuilder s = new StringBuilder();
        while(num != 0){
            s.append(c[num & 15]);
            num = num >>> 4;
        }
        return s.reverse().toString();
    }
}
```

1047. Remove All Adjacent Duplicates In String

```
You are given a string s consisting of lowercase English letters. A duplicate removal consists of choosing two adjacent and equal letters and removing them.

We repeatedly make duplicate removals on s until we no longer can.

Return the final string after all such duplicate removals have been made. It can be proven that the answer is unique.

 

Example 1:

Input: s = "abbaca"
Output: "ca"
Explanation: 
For example, in "abbaca" we could remove "bb" since the letters are adjacent and equal, and this is the only possible move.  The result of this move is that the string is "aaca", of which only "aa" is possible, so the final string is "ca".

Example 2:

Input: s = "azxxzy"
Output: "ay"

```

```java
// ArrayDeque

public String removeDuplicates(String S) {
        Deque<Character> dq = new ArrayDeque<>();
        for (char c : S.toCharArray()) {
            if (!dq.isEmpty() && dq.peekLast() == c) { 
                dq.pollLast();
            }else {
                dq.offer(c);
            }
        }
        StringBuilder sb = new StringBuilder();
        for (char c : dq) { sb.append(c); }
        return sb.toString();
    }

// String Builder  
 public String removeDuplicates(String S) {
        StringBuilder sb = new StringBuilder();
        for (char c : S.toCharArray()) {
            int size = sb.length();
            if (size > 0 && sb.charAt(size - 1) == c) { 
                sb.deleteCharAt(size - 1); 
            }else { 
                sb.append(c); 
            }
        }
        return sb.toString();
    }  

```

1209. Remove All Adjacent Duplicates in String II

```
You are given a string s and an integer k, a k duplicate removal consists of choosing k adjacent and equal letters from s and removing them, causing the left and the right side of the deleted substring to concatenate together.

We repeatedly make k duplicate removals on s until we no longer can.

Return the final string after all such duplicate removals have been made. It is guaranteed that the answer is unique.

 

Example 1:

Input: s = "abcd", k = 2
Output: "abcd"
Explanation: There's nothing to delete.

Example 2:

Input: s = "deeedbbcccbdaa", k = 3
Output: "aa"
Explanation: 
First delete "eee" and "ccc", get "ddbbbdaa"
Then delete "bbb", get "dddaa"
Finally delete "ddd", get "aa"

Example 3:

Input: s = "pbbcggttciiippooaais", k = 2
Output: "ps"

```

```java
public String removeDuplicates(String S, int k) {
        Deque<Character> charStk = new ArrayDeque<>();
        Deque<Integer> cntStk = new ArrayDeque<>();
        for (int i = 0; i < S.length(); ++i) {
            char c = S.charAt(i);
            if (charStk.isEmpty() || charStk.peek() != c) { // no char in stack yet, or top char is different from the current.
                charStk.push(c);
                cntStk.push(1);
            }else if (cntStk.peek() + 1 < k) { // top char is same as the current, but less than k after appending the current.
                cntStk.push(cntStk.pop() + 1);
            }else { // found k-in-a-row duplicates, remove them.
                charStk.pop();
                cntStk.pop();
            }
        }
        StringBuilder sb = new StringBuilder();
        for (char c : charStk) {
            int cnt = cntStk.pop();
            while (cnt-- > 0) {
                sb.append(c);
            }
        }
        return sb.reverse().toString(); // Do NOT forget reverse().
    }

```