# Common Errors and Pitfalls

*Common elementary programming errors often involve undeclared variables, uninitialized
variables, integer overflow, unintended integer division, and round-off errors.*

**Common Error 1:** Undeclared/Uninitialized Variables and Unused Variables

A variable must be declared with a type and assigned a value before using it. A common error
is not declaring a variable or initializing a variable. Consider the following code:
```java
double interestRate = 0.05;
double interest = interestrate * 45;
```
This code is wrong, because interestRate is assigned a value 0.05; but interestrate
has not been declared and initialized. Java is case sensitive, so it considers interestRate
and interestrate to be two different variables.
If a variable is declared, but not used in the program, it might be a potential programming
error. Therefore, you should remove the unused variable from your program. For example, in
the following code, taxRate is never used. It should be removed from the code.
```java
double interestRate = 0.05;
double taxRate = 0.05;
double interest = interestRate * 45;
System.out.println("Interest is " + interest);
```
If you use an IDE such as Eclipse and NetBeans, you will receive a warning on unused
variables.

**Common Error 2:** Integer Overflow

Numbers are stored with a limited numbers of digits. When a variable is assigned a value that
is too large (in size) to be stored, it causes overflow. For example, executing the following
statement causes overflow, because the largest value that can be stored in a variable of the int
type is 2147483647. 2147483648 will be too large for an int value:

```java
int value = 2147483647 + 1; // value will actually be -2147483648
```
Likewise, executing the following statement also causes overflow, because the smallest value
that can be stored in a variable of the int type is -2147483648. -2147483649 is too large
in size to be stored in an int variable.

```java
int value = –2147483648 – 1; // value will actually be 2147483647
```

Java does not report warnings or errors on overflow, so be careful when working with integers
close to the maximum or minimum range of a given type.

When a floating-point number is too small (i.e., too close to zero) to be stored, it causes
underflow. Java approximates it to zero, so normally you don’t need to be concerned about
underflow.

**Common Error 3:** Round-off Errors

A round-off error, also called a rounding error, is the difference between the calculated
approximation of a number and its exact mathematical value. For example, 1/3 is approximately 0.333 if you keep three decimal places, and is 0.3333333 if you keep seven decimal
places. Since the number of digits that can be stored in a variable is limited, round-off errors
are inevitable. Calculations involving floating-point numbers are approximated because these
numbers are not stored with complete accuracy. For example,

```java
System.out.println(1.0 - 0.1 - 0.1 - 0.1 - 0.1 - 0.1);
```

displays 0.5000000000000001, not 0.5, and
```java
System.out.println(1.0 - 0.9);
```

displays 0.09999999999999998, not 0.1. Integers are stored precisely. Therefore, calculations with integers yield a precise integer result.

**Common Error 4:** Unintended Integer Division

Java uses the same divide operator, namely /, to perform both integer and floating-point division. When two operands are integers, the / operator performs an integer division. The result
of the operation is an integer. The fractional part is truncated. To force two integers to perform
a floating-point division, make one of the integers into a floating-point number. For example,
the code in (a) displays that average as 1 and the code in (b) displays that average as 1.5.

![image](https://user-images.githubusercontent.com/44777689/152997837-ce434d56-9730-4590-b2f5-27879b256b46.png)

Common Pitfall 1: Redundant Input Objects
New programmers often write the code to create multiple input objects for each input. For
example, the following code reads an integer and a double value:

![image](https://user-images.githubusercontent.com/44777689/152997905-d8df68e0-dd1e-4df2-9767-ad3780519fe1.png)

The code is not good. It creates two input objects unnecessarily and may lead to some subtle
errors. You should rewrite the code as follows:

![image](https://user-images.githubusercontent.com/44777689/152997970-45defa37-ad72-485e-a22c-69b9c27fe252.png)
