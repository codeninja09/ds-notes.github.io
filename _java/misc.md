---
layout: default
title: Misc
has_children: false
---

### clear the console
clears the console statements
```java
    public static void clearScreen() {
        System.out.print("\033[H\033[2J");
        System.out.flush();
    }
```
