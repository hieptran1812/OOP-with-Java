# Increment and Decrement Operators

*The increment operator (++) and decrement operator (--) are for incrementing and
decrementing a variable by 1.*

The ++ and — — are two shorthand operators for incrementing and decrementing a variable by 1.
These are handy because that’s often how much the value needs to be changed in many programming tasks. For example, the following code increments i by 1 and decrements j by 1.

```java
int i = 3, j = 3;
i++; // i becomes 4
j——; // j becomes 2
```

i++ is pronounced as "i plus plus" and i—— as "i minus minus." These operators are known
as postfix increment (or postincrement) and postfix decrement (or postdecrement), because the
operators ++ and —— are placed after the variable. These operators can also be placed before
the variable. For example,

```java
int i = 3, j = 3;
++i; // i becomes 4
——j; // j becomes 2
```

++i increments i by 1 and ——j decrements j by 1. These operators are known as prefix
increment (or preincrement) and prefix decrement (or predecrement).

As you see, the effect of i++ and ++i or i—— and ——i are the same in the preceding examples. However, their effects are different when they are used in statements that do more than
just increment and decrement.

![image](https://user-images.githubusercontent.com/44777689/152996110-ab18ffb6-b347-4eb9-b838-b417224b2490.png)

Here are additional examples to illustrate the differences between the prefix form of ++ (or
——) and the postfix form of ++ (or ——). Consider the following code:
```java
int i = 10;
int newNum = 10 * i++;
```
Same
```java
System.out.print("i is " + i + ", newNum is " + newNum);
```

In this case, i is incremented by 1, then the old value of i is used in the multiplication. Thus,
newNum becomes 100. If i++ is replaced by ++i, then it becomes as follows:
```java
int i = 10;
int newNum = 10 * ++i;
```
Same
```java
System.out.print("i is " + i + ", newNum is " + newNum);
```

Here is another example:
```java
double x = 1.0;
double y = 5.0;
double z = x–– + (++y);
```

After all three lines are executed, y becomes 6.0, z becomes 7.0, and x becomes 0.0.
Operands are evaluated from left to right in Java. The left-hand operand of a binary operator
is evaluated before any part of the right-hand operand is evaluated. This rule takes precedence
over any other rules that govern expressions. Here is an example:

```java
int i = 1;
int k = ++i + i * 3;
```

++i is evaluated and returns 2. When evaluating i * 3, i is now 2. Therefore, k
becomes 8.

**Tip**
Using increment and decrement operators makes expressions short, but it also makes
them complex and difficult to read. Avoid using these operators in expressions that
modify multiple variables or the same variable multiple times, such as this one: 

```java
int k = ++i + i * 3
```
