---
layout: default
title: Breadth First Search (Tree)
parent: Tree
---

# Breadth First Search

{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

Any problem involving the traversal of a tree in a level-by-level order can be efficiently solved using this approach. We will use a **Queue** to keep track of all the nodes of a level before we jump onto the next level. This also means that the space complexity of the algorithm will be O(W), where ‘W’ is the maximum number of nodes on any level.


## Binary Tree Level Order Traversal
[102](https://leetcode.com/problems/binary-tree-level-order-traversal)

<img width="335" alt="image" src="https://user-images.githubusercontent.com/3500791/180861146-c821b444-f646-4e30-b966-f91b322c62d6.png">

```
Given the root of a binary tree, return the level order traversal of its nodes' values. (i.e., from left to right, level by level).

Example 1:
Input: root = [3,9,20,null,null,15,7]
Output: [[3],[9,20],[15,7]]

Example 2:
Input: root = [1]
Output: [[1]]

Example 3:
Input: root = []
Output: []
```

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public List<List<Integer>> levelOrder(TreeNode root) {
        List<List<Integer>> result = new ArrayList<>();
        if(null == root){
            return result;
        }
        Queue<TreeNode> queue = new LinkedList<>();
        queue.add(root);
        while(!queue.isEmpty()){
            int size = queue.size();
            List<Integer> list = new ArrayList<>();
            while(size > 0){
                TreeNode current = queue.remove();
                list.add(current.val);
                if(null != current.left){
                    queue.add(current.left);
                }
                if(null != current.right){
                    queue.add(current.right);
                }
                size--;
            }
            result.add(list);
        }
        return result;
    }
}
```


## Binary Tree Level Order Traversal II
[107](https://leetcode.com/problems/binary-tree-level-order-traversal-ii/)

<img width="335" alt="image" src="https://user-images.githubusercontent.com/3500791/180861146-c821b444-f646-4e30-b966-f91b322c62d6.png">

```
Given the root of a binary tree, return the bottom-up level order traversal of its nodes' values. (i.e., from left to right, level by level from leaf to root).

Example 1:
Input: root = [3,9,20,null,null,15,7]
Output: [[15,7],[9,20],[3]]

Example 2:
Input: root = [1]
Output: [[1]]

Example 3:
Input: root = []
Output: []
```

```java
class Solution {
    public List<List<Integer>> levelOrderBottom(TreeNode root) {
        List<List<Integer>> result = new ArrayList<>();
        Queue<TreeNode> queue = new LinkedList<>();
        if(root == null){
            return result;
        }
        queue.add(root);
        while(!queue.isEmpty()){
            int size = queue.size();
            List<Integer> levelNodes = new ArrayList<>(); 
            for(int i =0 ; i < size ; i++){
                TreeNode node = queue.remove();
                levelNodes.add(node.val);
                if(null != node.left){
                    queue.add(node.left);
                }
                if(null != node.right){
                    queue.add(node.right);
                }
            }
            result.add(0,levelNodes);
        }
        return result;
    }
}
```

## Average of Levels in Binary Tree
[637](https://leetcode.com/problems/average-of-levels-in-binary-tree/)

<img width="335" alt="image" src="https://user-images.githubusercontent.com/3500791/180861146-c821b444-f646-4e30-b966-f91b322c62d6.png">

```
Given the root of a binary tree, return the average value of the nodes on each level in the form of an array. Answers within 10-5 of the actual answer will be accepted.

Input: root = [3,9,20,null,null,15,7]
Output: [3.00000,14.50000,11.00000]
Explanation: The average value of nodes on level 0 is 3, on level 1 is 14.5, and on level 2 is 11.
Hence return [3, 14.5, 11].

```

```java
class Solution {
    public List<Double> averageOfLevels(TreeNode root) {
        List<Double> result = new ArrayList<>();
        Queue<TreeNode> queue = new LinkedList<>();
        if(null == root){
            return result;
        }
        queue.offer(root);
        while(!queue.isEmpty()){
            int size = queue.size();
            double temp = 0;
            for(int i= 0 ; i < size ; i++){
                TreeNode current = queue.poll();
                temp += current.val;
                if(null != current.left){
                    queue.add(current.left);    
                }
                if(null != current.right){
                    queue.add(current.right);    
                }
            }
            result.add(temp/size);
        }
        return result;
    }
}
```

## 
[103](Binary Tree Zigzag Level Order Traversal)

```
Given the root of a binary tree, return the zigzag level order traversal of its nodes' values. (i.e., from left to right, then right to left for the next level and alternate between).

Example 1:
Input: root = [3,9,20,null,null,15,7]
Output: [[3],[20,9],[15,7]]

Example 2:
Input: root = [1]
Output: [[1]]

Example 3:
Input: root = []
Output: []
```

```java
class Solution {
    public List<List<Integer>> zigzagLevelOrder(TreeNode root) {
        List<List<Integer>> result = new ArrayList<>();
        if(null == root){
            return result;
        }
        Queue<TreeNode> queue = new LinkedList<>();
        queue.add(root);
        boolean leftToRight = true;
        while(!queue.isEmpty()){
            int size = queue.size();
            List<Integer> levelData = new ArrayList<>();
            for(int i =0; i < size ; i++){
                TreeNode node = queue.remove();
                
                if(leftToRight){
                    levelData.add(node.val);
                }else{
                    levelData.add(0,node.val);
                }
                
                if(null != node.left){
                    queue.add(node.left);
                }
                
                if(null != node.right){
                    queue.add(node.right);
                }
            }
            leftToRight = !leftToRight;
            result.add(levelData);
        }
        
        return result;
    }
}
```

## Depth

### Max Depth

[104](https://leetcode.com/problems/maximum-depth-of-binary-tree/)

```java
// DFS
class Solution {
    public int maxDepth(TreeNode root) {
        if(root == null){
            return 0;
        }
        return 1 + Math.max(maxDepth(root.right),maxDepth(root.left));
    }    
}

// BFS
class Solution {
    public int maxDepth(TreeNode root) {
        int depth = 0;
        if(null == root){
            return depth;
        }
        Queue<TreeNode> queue = new LinkedList<>();
        queue.add(root);
        while(!queue.isEmpty()){
            int size = queue.size();
            depth++;
            while(size > 0){
                size--;
                TreeNode node = queue.remove();
                if(null != node.left){
                    queue.add(node.left);
                }
                if(null != node.right){
                    queue.add(node.right);
                }
            }
        }
        return depth;
    }
}
```

### Min Depth

[111](https://leetcode.com/problems/minimum-depth-of-binary-tree/)

```java
// DFS
class Solution {
    public int minDepth(TreeNode root) {
        if(null == root){
            return 0;
        }
        
        if(null != root.left && null != root.right){
            return 1 + Math.min(minDepth(root.left), minDepth(root.right));
        }else{
            return 1 + Math.max(minDepth(root.left), minDepth(root.right));    
        }
    }
}

// BFS
class Solution {
    public int minDepth(TreeNode root) {
        if(null == root){
            return 0;
        }
        
        int depth = 0;
        Queue<TreeNode> queue = new LinkedList<>();
        queue.add(root);
        while(!queue.isEmpty()){
            depth++;
            int size = queue.size();
            for(int i = 0; i< size ; i++){
                TreeNode node = queue.remove();
                if(null == node.left && null == node.right){
                    return depth;
                }
                
                if(null != node.left){
                    queue.add(node.left);
                }
                
                if(null != node.right){
                    queue.add(node.right);
                }
            }            
        }
        return depth;
    }
}
```