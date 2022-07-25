---
layout: default
title: Tree
has_children: true
---

# Tree Data Structure

{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

Tree is a nonlinear hierarchical data structure that consists of nodes connected by edges.

## Why Tree Data Structure?
Other data structures such as arrays, linked list, stack, and queue are linear data structures that store data sequentially. In order to perform any operation in a linear data structure, the time complexity increases with the increase in the data size. But, it is not acceptable in today's computational world.

Different tree data structures allow quicker and easier access to the data as it is a non-linear data structure.

## Tree Terminologies

### Node
A node is an entity that contains a key or value and pointers to its child nodes.

The last nodes of each path are called leaf nodes or external nodes that do not contain a link/pointer to child nodes.

The node having at least a child node is called an internal node.

### Edge
It is the link between any two nodes.

### Root
It is the topmost node of a tree.

### Height of a Node
The height of a node is the number of edges from the node to the deepest leaf (ie. the longest path from the node to a leaf node).

### Depth of a Node
The depth of a node is the number of edges from the root to the node.

### Height of a Tree
The height of a Tree is the height of the root node or the depth of the deepest node.

![image](https://user-images.githubusercontent.com/3500791/166079676-58aa546a-d030-4cb2-a251-881b5ccc9117.png)

Degree of a Node
The degree of a node is the total number of branches of that node.

Forest
A collection of disjoint trees is called a forest.
![image](https://user-images.githubusercontent.com/3500791/166079792-bc1b5d67-8d6a-47c6-ad43-69847e14633c.png)

You can create a forest by cutting the root of a tree.

## Tree Applications
- Binary Search Trees(BSTs) are used to quickly check whether an element is present in a set or not.
- Heap is a kind of tree that is used for heap sort.
- A modified version of a tree called Tries is used in modern routers to store routing information.
- Most popular databases use B-Trees and T-Trees, which are variants of the tree structure we learned above to store their data
- Compilers use a syntax tree to validate the syntax of every program you write.

## Binary Tree
A binary tree is a tree data structure in which each parent node can have at most two children. Each node of a binary tree consists of three items:

data item

address of left child

address of right child

![image](https://user-images.githubusercontent.com/3500791/166121700-91a4356a-8ed7-4c0b-9e34-22e32e13bdea.png)

## Types of Binary Tree

1. Full Binary Tree
A full Binary tree is a special type of binary tree in which every parent node/internal node has either two or no children.

![image](https://user-images.githubusercontent.com/3500791/166121717-a2843aa2-bf70-43d2-babf-1d63501e9623.png)

## Traversal 

![image](https://user-images.githubusercontent.com/3500791/166345988-5574a620-eee9-445e-9a47-9072e9fa879d.png)

- Depth First Traversal
  - InOrder (Left Root Right)
  - PreOrder (Root Left Right)
  - PostOrder (Left Right Root)
- Breadth First Traversal

```java
  // Inorder
  void printInorder(Node node)
    {
        if (node == null)
            return;
 
        /* first recur on left child */
        printInorder(node.left);
 
        /* then print the data of node */
        System.out.print(node.key + " ");
 
        /* now recur on right child */
        printInorder(node.right);
    }
  // Pre order
  void printPreorder(Node node)
    {
        if (node == null)
            return;
 
        /* first print data of node */
        System.out.print(node.key + " ");
 
        /* then recur on left subtree */
        printPreorder(node.left);
 
        /* now recur on right subtree */
        printPreorder(node.right);
    }
  // Post Order
    void printPostorder(Node node)
    {
        if (node == null)
            return;
 
        // first recur on left subtree
        printPostorder(node.left);
 
        // then recur on right subtree
        printPostorder(node.right);
 
        // now deal with the node
        System.out.print(node.key + " ");
    }
  // Breadth First 

```
