# Assignment Statements and Assignment Expressions

*An assignment statement designates a value for a variable. An assignment statement can be used as an expression in Java.*

After a variable is declared, you can assign a value to it by using an assignment statement. In
Java, the equal sign (=) is used as the assignment operator. The syntax for assignment statements is as follows:

```
variable = expression;
```

An expression represents a computation involving values, variables, and operators that,
taking them together, evaluates to a value. For example, consider the following code:

```java
int y = 1; // Assign 1 to variable y
double radius = 1.0; // Assign 1.0 to variable radius
int x = 5 * (3 / 2); // Assign the value of the expression to x
x = y + 1; // Assign the addition of y and 1 to x
double area = radius * radius * 3.14159; // Compute area
```

You can use a variable in an expression. A variable can also be used in both sides of the =
operator. For example,

```java
x = x + 1;
```

In this assignment statement, the result of x + 1 is assigned to x. If x is 1 before the
statement is executed, then it becomes 2 after the statement is executed.

To assign a value to a variable, you must place the variable name to the left of the assignment operator. Thus, the following statement is wrong:

```java
1 = x; // Wrong
```

**Note**

In mathematics, x = 2 * x + 1 denotes an equation. However, in Java, x = 2 * x + 1 is an assignment statement that evaluates the expression 2 * x + 1 and assigns the
result to x.

In Java, an assignment statement is essentially an expression that evaluates to the value to
be assigned to the variable on the left side of the assignment operator. For this reason, an
assignment statement is also known as an assignment expression. For example, the following
statement is correct:

```java
System.out.println(x = 1);
```

which is equivalent to

```java
x = 1;
System.out.println(x);
```

If a value is assigned to multiple variables, you can use the following syntax:

```java
i = j = k = 1;
```

which is equivalent to

```java
k = 1;
j = k;
i = j;
```

**Note**

In an assignment statement,** the data type of the variable on the left must be compatible
with the data type of the value on the right**. For example, int x = 1.0 would be illegal, because the data type of x is int. You cannot assign a double value (1.0) to an
int variable without using type casting. 
