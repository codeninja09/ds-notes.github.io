---
layout: default
title: Inputs
parent: java
has_children: false
---

# Ways to take input from console

{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---
## BufferedReader
- Input is buffered for efficient reading

```java
        // Enter data using BufferReader
        BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));

        // Reading data using readLine
        String name = reader.readLine();
```

## Scanner 
- Convenient methods for parsing primitives (nextInt(), nextFloat(), …) from the tokenized input.
- Regular expressions can be used to find tokens.


```java
        // Using Scanner for Getting Input from User
        Scanner in = new Scanner(System.in);
 
        String s = in.nextLine();
        System.out.println("You entered string " + s);
 
        int a = in.nextInt();
        System.out.println("You entered integer " + a);
 
        float b = in.nextFloat();
        System.out.println("You entered float " + b);
```

## Console Class 
- Reading password without echoing the entered characters.
- Reading methods are synchronized.
- Format string syntax can be used.
- Does not work in non-interactive environment (such as in an IDE).

```java
        // Using Console to input data from user
        String name = System.console().readLine();
 
        System.out.println("You entered string " + name);
```

## Using Command line argument 

```java
        public static void main(String[] args) {
                // check if length of args array is
                // greater than 0
                if (args.length > 0) {
                    System.out.println("The command line arguments are:");

                    // iterating the args array and printing
                    // the command line arguments
                    for (String val : args)
                        System.out.println(val);
                } else
                    System.out.println("No command line arguments found.");
          }
```


reference links
- https://www.geeksforgeeks.org/ways-to-read-input-from-console-in-java/
