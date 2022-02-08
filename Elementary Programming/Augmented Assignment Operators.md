# Augmented Assignment Operators

The operators +, -, *, /, and % can be combined with the assignment operator to form
augmented operators.

Very often, the current value of a variable is used, modified, then reassigned back to the same
variable. For example, the following statement increases the variable count by 1:

```java
count = count + 1;
```

Java allows you to combine assignment and addition operators using an augmented (or
compound) assignment operator. For example, the preceding statement can be written as

```java
count += 1;
```

The += is called the addition assignment operator. 

![image](https://user-images.githubusercontent.com/44777689/152995395-252a8c15-4d1a-4610-919b-ebc26f96081f.png)

The augmented assignment operator is performed last after all the other operators in the
expression are evaluated. For example,

```java
x /= 4 + 5.5 * 1.5;
```
is same as
```java
x = x / (4 + 5.5 * 1.5);
```

**Caution**
There are no spaces in the augmented assignment operators. For example, + = should
be +=.

**Note**

Like the assignment operator (=), the operators (+=, -=, *=, /=, and %=) can be used
to form an assignment statement as well as an expression. For example, in the following code, x += 2 is a statement in the first line, and an expression in the second line:
```java
x += 2; // Statement
System.out.println(x += 2); // Expression
```
