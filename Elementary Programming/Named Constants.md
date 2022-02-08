# Named Constants

*A named constant is an identifier that represents a permanent value.*

The value of a variable may change during the execution of a program, but a named constant,
or simply constant, represents permanent data that never changes. A constant is also known as
a final variable in Java. Here is the
syntax for declaring a constant:

```java
final datatype CONSTANTNAME = value;
```

A constant must be declared and initialized in the same statement. The word final is a
Java keyword for declaring a constant. By convention, all letters in a constant are in uppercase.

```java
final double PI = 3.14159; // Declare a constant
```
There are three benefits of using constants: (1) you don’t have to repeatedly type the same
value if it is used multiple times; (2) if you have to change the constant value (e.g., from 3.14
to 3.14159 for PI), you need to change it only in a single location in the source code; and (3)
a descriptive name for a constant makes the program easy to read.
