---
layout: default
title: Array
parent: ds
---

## LinkedList using Array
https://www.geeksforgeeks.org/create-linked-list-from-a-given-array/
```java
```

## Stack using Array

```java
  public class StackUsingArray {
    int MAX = 1000;
    int[] arr = new int[MAX];
    int top = -1;

    public boolean push(int data) {
        if (isFull()) {
            return false;
        }
        arr[++top] = data;
        return true;
    }

    public int pop() {
        if (isEmpty()) {
            return Integer.MIN_VALUE;
        }
        return arr[top--];
    }

    public int peek() {
        if (isEmpty()) {
            return Integer.MIN_VALUE;
        }
        return arr[top];
    }

    public boolean isFull() {
        if (top >= MAX - 1) {
            return true;
        }
        return false;
    }


    public boolean isEmpty() {
        if (top < 0) {
            return true;
        }
        return false;
    }

    public static void main(String[] args) {
        StackUsingArray stack = new StackUsingArray();
        stack.push(1);
        stack.push(2);
        stack.push(3);
        System.out.println(stack.pop());
        System.out.println(stack.pop());
        System.out.println(stack.pop());
    }

}
```

## Stack using Linked List

```java
class StackNode {
    int data;
    StackNode next;

    public StackNode(int data) {
        this.data = data;
    }
}

public class StackUsingLinkedList {
    StackNode top = null;

    public static void main(String[] args) {
        StackUsingLinkedList stack = new StackUsingLinkedList();
        stack.push(1);
        stack.push(2);
        stack.push(3);
        System.out.println(stack.pop().data);
        System.out.println(stack.pop().data);
        System.out.println(stack.pop().data);
    }

    public StackNode push(int data) {
        StackNode newNode = new StackNode(data);
        if (top == null) {
            top = newNode;
            return top;
        }
        newNode.next = top;
        top = newNode;
        return top;
    }

    public StackNode pop() {
        StackNode deletedNode = top;
        top = top.next;
        return deletedNode;
    }
}
```

## Stack using Queue
  ### Two Queue's
  ``` java
  // by making push operation as costly
  import java.util.LinkedList;
  import java.util.Queue;

  public class StackUsingQueue {
    Queue<Integer> q1 = new LinkedList<>();
    Queue<Integer> q2 = new LinkedList<>();

    // adding the new data to the Q2 and then add the remaining elements from Q1 to Q2
    // then swap the queues for the next push
    public void push(int data) {
        q2.add(data);

        while (!q1.isEmpty()) {
            q2.add(q1.remove());
        }

        Queue<Integer> temp = q2;
        q2 = q1;
        q1 = temp;
    }

    public int pop() throws Exception {
        if (q1.isEmpty()) {
            throw new Exception("Stack is empty");
        }
        return q1.remove();
    }


    public static void main(String[] args) throws Exception {
        StackUsingQueue stack = new StackUsingQueue();
        stack.push(1);
        stack.push(2);
        stack.push(3);
        System.out.println(stack.pop());
        System.out.println(stack.pop());
        System.out.println(stack.pop());
    }

}
  
  
  // by making pop operation as costly
  import java.util.LinkedList;
  import java.util.Queue;

  public class StackUsingQueue {
    Queue<Integer> q1 = new LinkedList<>();
    Queue<Integer> q2 = new LinkedList<>();


    public void push(int data) {
        q1.add(data);
    }

    public int pop() throws Exception {
        if (q1.isEmpty()) {
            throw new Exception("Stack is empty");
        }
        while (q1.size() > 1) {
            q2.add(q1.remove());
        }
        int deletedElement = q1.remove();
        Queue<Integer> temp = q2;
        q2 = q1;
        q1 = temp;
        return deletedElement;
    }
    
    public static void main(String[] args) throws Exception {
        StackUsingQueue stack = new StackUsingQueue();
        stack.push(1);
        stack.push(2);
        stack.push(3);
        System.out.println(stack.pop());
        System.out.println(stack.pop());
        System.out.println(stack.pop());
    }

}

  
  ```
  
  ### Single Queue
  ``` java
  public class StackUsingQueue {
    Queue<Integer> q = new LinkedList<>();

    public void push(int data) {
        q.add(data);
        int size = q.size();
        while (size > 1) {
            q.add(q.remove());
            size--;
        }
    }

    public int pop() {
        if (q.isEmpty()) {
            return Integer.MIN_VALUE;
        }
        return q.remove();
    }

    public static void main(String[] args) throws Exception {
        StackUsingQueue stack = new StackUsingQueue();
        stack.push(1);
        stack.push(2);
        stack.push(3);
        System.out.println(stack.pop());
        System.out.println(stack.pop());
        System.out.println(stack.pop());
    }
  }

  ```

## Queue using Array
https://www.geeksforgeeks.org/array-implementation-of-queue-simple/
## Queue using LinkedList
https://www.geeksforgeeks.org/queue-linked-list-implementation/
## Queue using Stack
https://www.geeksforgeeks.org/queue-using-stacks/
