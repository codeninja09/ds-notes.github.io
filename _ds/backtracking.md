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

## Permutations

### Permutations with out duplicates

```
46

Given an array nums of distinct integers, return all the possible permutations. You can return the answer in any order.

Example 1:

Input: nums = [1,2,3]
Output: [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]
```

```java
class Solution {
    public List<List<Integer>> permute(int[] nums) {
        List<List<Integer>> result = new ArrayList<>();
        boolean[] included = new boolean[nums.length];
        permute(nums, new ArrayList<>(),result, included);
        return result;
    }
    
    public void permute(int[] nums, List<Integer> temp, List<List<Integer>> result, boolean[] included){
        if(temp.size() == nums.length){
            result.add(new ArrayList(temp));
            return;
        }
        for(int i =0 ; i< nums.length ; i++){
            if(included[i]){
                continue;
            }
            included[i] = true;
            temp.add(nums[i]);
            permute(nums,temp,result, included);
            included[i] = false;
            temp.remove(temp.size() - 1);
            
        }
    }
}
```

### Permutations with duplicates

```
47
Given a collection of numbers, nums, that might contain duplicates, return all possible unique permutations in any order.

Example 1:

Input: nums = [1,1,2]
Output:
[[1,1,2],
 [1,2,1],
 [2,1,1]]
Example 2:

Input: nums = [1,2,3]
Output: [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]
```

```java
class Solution {
    public List<List<Integer>> permuteUnique(int[] nums) {
        List<List<Integer>> result = new ArrayList<>();
        if(nums.length == 0){
            result.add(new ArrayList<>());
            return result;
        }
        Arrays.sort(nums);
        permutations(nums,0, new boolean[nums.length],result,new ArrayList<>());
        return result;
    }
    
    public void permutations(int[] nums, int index, boolean[] used, List<List<Integer>> combinations, List<Integer> combination){
        if(index == nums.length){
            combinations.add(new ArrayList<>(combination));
            return;
        }
        for(int i = 0; i< nums.length ; i++){
            if(i > 0 && nums[i] == nums[i-1] && used[i-1] == false){
                continue;
            }
            if(used[i] == false){
                combination.add(nums[i]);
                used[i] = true;
                permutations(nums, index+1, used, combinations, combination);
                used[i] = false;
                combination.remove(combination.size() - 1);
            }
        }
    }
}
```

## Combinations

```
77
Given two integers n and k, return all possible combinations of k numbers out of the range [1, n].

You may return the answer in any order.

 

Example 1:

Input: n = 4, k = 2
Output:
[
  [2,4],
  [3,4],
  [2,3],
  [1,2],
  [1,3],
  [1,4],
]
Example 2:

Input: n = 1, k = 1
Output: [[1]]
```

```java
    public static List<List<Integer>> combine(int n, int k) {
        List<List<Integer>> combs = new ArrayList<List<Integer>>();
        combine(combs, new ArrayList<Integer>(), 1, n, k);
        return combs;
    }
    public static void combine(List<List<Integer>> combs, List<Integer> comb, int start, int n, int k) {
        if(k==0) {
            combs.add(new ArrayList<Integer>(comb));
            return;
        }
        for(int i=start;i<=n;i++) {
            comb.add(i);
            combine(combs, comb, i+1, n, k-1);
            comb.remove(comb.size()-1);
        }
    }
```

### Combination Sum

```
39
Given an array of distinct integers candidates and a target integer target, return a list of all unique combinations of candidates where the chosen numbers sum to target. You may return the combinations in any order.

The same number may be chosen from candidates an unlimited number of times. Two combinations are unique if the frequency of at least one of the chosen numbers is different.

It is guaranteed that the number of unique combinations that sum up to target is less than 150 combinations for the given input.

 

Example 1:

Input: candidates = [2,3,6,7], target = 7
Output: [[2,2,3],[7]]
Explanation:
2 and 3 are candidates, and 2 + 2 + 3 = 7. Note that 2 can be used multiple times.
7 is a candidate, and 7 = 7.
These are the only two combinations.
Example 2:

Input: candidates = [2,3,5], target = 8
Output: [[2,2,2,2],[2,3,3],[3,5]]
Example 3:

Input: candidates = [2], target = 1
Output: []
```

```java
class Solution {
    public List<List<Integer>> combinationSum(int[] candidates, int target) {
        List<List<Integer>> result = new ArrayList<>();
        if(null == candidates || candidates.length == 0){
            return result;
        }
        combinationSum(candidates,target,result,new ArrayList<>(),0);
        return result;
    }
    
    private void combinationSum(int[] candidates, int target,List<List<Integer>> result, List<Integer> combination, int index){
        if(target < 0){
            return;
        }
        if(target == 0){
            result.add(new ArrayList<>(combination));
        }
        for(int i = index; i< candidates.length;i++ ){
            combination.add(candidates[i]);
            combinationSum(candidates,target - candidates[i] ,result,combination,i);
            combination.remove(combination.size() - 1);
        }
    }
}
```

### Letter Combinations of a Phone Number

[leetcode-17](https://leetcode.com/problems/letter-combinations-of-a-phone-number/discuss/2021106/Java-4-Approaches%3A-BF-4-Loops-Backtracking-BFS-Queue-with-Image-Explaination)

```
Given a string containing digits from 2-9 inclusive, return all possible letter combinations that the number could represent. Return the answer in any order.

A mapping of digits to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.

Example 1:

Input: digits = "23"
Output: ["ad","ae","af","bd","be","bf","cd","ce","cf"]
Example 2:

Input: digits = ""
Output: []
Example 3:

Input: digits = "2"
Output: ["a","b","c"]
```

```java
class Solution {
    
    final char[][] letters = { {},{},{'a','b','c'},{'d','e','f'},{'g','h','i'},{'j','k','l'}, {'m','n','o'},{'p','q','r','s'},{'t','u','v'},{'w','x','y','z'} };
    
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