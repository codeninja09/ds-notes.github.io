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

### 46. Permutations

```
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

