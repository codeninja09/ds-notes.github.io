---
layout: default
title: Deque
parent: Queue
---

# Deque

{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Here are a few reasons why Deque is better than Stack:

Object oriented design - Inheritance, abstraction, classes and interfaces: Stack is a class, Deque is an interface. Only one class can be extended, whereas any number of interfaces can be implemented by a single class in Java (multiple inheritance of type). Using the Deque interface removes the dependency on the concrete Stack class and its ancestors and gives you more flexibility, e.g. the freedom to extend a different class or swap out different implementations of Deque (like LinkedList, ArrayDeque).

Inconsistency: Stack extends the Vector class, which allows you to access element by index. This is inconsistent with what a Stack should actually do, which is why the Deque interface is preferred (it does not allow such operations)--its allowed operations are consistent with what a FIFO or LIFO data structure should allow.

Performance: The Vector class that Stack extends is basically the "thread-safe" version of an ArrayList. The synchronizations can potentially cause a significant performance hit to your application. Also, extending other classes with unneeded functionality (as mentioned in #2) bloat your objects, potentially costing a lot of extra memory and performance overhead.

Stack and Deque have reverse iteration orders:

```java
Stack<Integer> stack = new Stack<>();
stack.push(1);
stack.push(2);
stack.push(3);
System.out.println(new ArrayList<>(stack)); // prints 1, 2, 3


Deque<Integer> deque = new ArrayDeque<>();
deque.push(1);
deque.push(2);
deque.push(3);
System.out.println(new ArrayList<>(deque)); // prints 3, 2, 1

Deque returns an iterator over the elements in this deque in proper sequence. The elements will be returned in order from first (head) to last (tail).
```