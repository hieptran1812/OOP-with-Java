# Numeric Data Types and Operations

Java has six numeric types for integers and floating-point numbers with operators +,-, *, /, and %.

## Numeric Types


Every data type has a range of values. The compiler allocates memory space for each
variable or constant according to its data type. Java provides eight primitive data types
for numeric values, characters, and Boolean values. This section introduces numeric data
types and operators.

![image](https://user-images.githubusercontent.com/44777689/152993769-d9b2a239-3d6d-467f-8193-bd7993b5c0e1.png)

## Reading Numbers from the Keyboard

![image](https://user-images.githubusercontent.com/44777689/152993955-1190f652-873b-4b3e-b4d5-837f5213d314.png)

Here are examples for reading values of various types from the keyboard:

```java
Scanner input = new Scanner(System.in);
System.out.print("Enter a byte value: ");
byte byteValue = input.nextByte();
System.out.print("Enter a short value: ");
short shortValue = input.nextShort();
System.out.print("Enter an int value: ");
int intValue = input.nextInt();
System.out.print("Enter a long value: ");
long longValue = input.nextLong();
System.out.print("Enter a float value: ");
float floatValue = input.nextFloat();
```

If you enter a value with an incorrect range or format, a runtime error would occur.

## Numeric Operators

![image](https://user-images.githubusercontent.com/44777689/152994319-2335c3cb-58a4-43af-9998-fc12fa5fa60b.png)

When both operands of a division are integers, the result of the division is the quotient and
the fractional part is truncated. For example, 5 / 2 yields 2, not 2.5, and –5 / 2 yields –2,
not –2.5. To perform a floating-point division, one of the operands must be a floating-point
number. For example, 5.0 / 2 yields 2.5.

## Exponent Operations

The Math.pow(a, b) method can be used to compute ab. The pow method is defined in the
Math class in the Java API. You invoke the method using the syntax Math.pow(a, b) (e.g.,
Math.pow(2, 3)), which returns the result of ab (23). Here, a and b are parameters for the
pow method and the numbers 2 and 3 are actual values used to invoke the method. For
example.

```java
System.out.println(Math.pow(2, 3)); // Displays 8.0
System.out.println(Math.pow(4, 0.5)); // Displays 2.0
System.out.println(Math.pow(2.5, 2)); // Displays 6.25
System.out.println(Math.pow(2.5, –2)); // Displays 0.16
```

