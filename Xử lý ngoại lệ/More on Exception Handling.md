# More on Exception Handling

A handler for an exception is found by propagating the exception backward through a
chain of method calls, starting from the current method.

Java’s exception-handling model is based on three operations: *declaring an exception,
throwing an exception, and catching an exception*.

![image](https://user-images.githubusercontent.com/44777689/144744780-44b41685-c657-4571-b948-aa2dcc150b45.png)

## Declaring Exceptions

In Java, the statement currently being executed belongs to a method. The Java interpreter
invokes the main method to start executing a program. Every method must state the types of
checked exceptions it might throw. This is known as declaring exceptions. Because system
errors and runtime errors can happen to any code, Java does not require that you declare Error
and RuntimeException (unchecked exceptions) explicitly in the method. However, all other
exceptions thrown by the method must be explicitly declared in the method header so the caller
of the method is informed of the exception.

To declare an exception in a method, use the throws keyword in the method header, as in
this example:

```java
public void myMethod() throws IOException
```

- The **throws** keyword indicates myMethod might throw an **IOException**. If the method
might throw multiple exceptions, add a list of the exceptions, separated by commas, after
**throws**:

```java
public void myMethod()
  throws Exception1, Exception2, ..., ExceptionN
```

**Note**

If a method does not declare exceptions in the superclass, you cannot override it to
declare exceptions in the subclass.

## Throwing Exceptions

A program that detects an error can create an instance of an appropriate exception type and
throw it. This is known as throwing an exception. Here is an example: Suppose the program
detects that an argument passed to the method violates the method contract (e.g., the argument must be nonnegative, but a negative argument is passed); the program can create an instance
of IllegalArgumentException and throw it, as follows:

```java
IllegalArgumentException ex = new IllegalArgumentException("Wrong Argument");
throw ex;
```

Or, if you prefer, you can use the following:

```java
throw new IllegalArgumentException("Wrong Argument");
```

**Note**

**IllegalArgumentException** is an exception class in the Java API. In general,
each exception class in the Java API has at least two constructors: a no-arg constructor and a constructor with a **String** argument that describes the exception.
This argument is called the exception message, which can be obtained by invoking
**getMessage()** from an exception object.

**Tip**

The keyword to **declare** an exception is **throws**, and the keyword to **throw** an exception
is **throw**.

## Catching Exceptions

You now know how to declare an exception and how to throw an exception. When an exception is thrown, it can be caught and handled in a **try-catch** block, as follows:

```java
try {
  statements; // Statements that may throw exceptions
}
catch (Exception1 exVar1) {
  handler for exception1;
}
catch (Exception2 exVar2) {
  handler for exception2;
}
...
catch (ExceptionN exVarN) {
  handler for exceptionN;
}
```

If no exceptions arise during the execution of the **try** block, the **catch** blocks are skipped.

If one of the statements inside the try block throws an exception, Java skips the remaining
statements in the try block and starts the process of finding the code to handle the exception.
The code that handles the exception is called the exception handler; it is found by propagating
the exception backward through a chain of method calls, starting from the current method.
Each catch block is examined in turn, from first to last, to see whether the type of the exception object is an instance of the exception class in the catch block. If so, the exception object
is assigned to the variable declared and the code in the catch block is executed. If no handler
is found, Java exits this method, passes the exception to the method’s caller, and continues the
same process to find a handler. If no handler is found in the chain of methods being invoked,
the program terminates and prints an error message on the console. The process of finding a
handler is called catching an exception.

Suppose the main method invokes method1, method1 invokes method2, method2
invokes method3, and method3 throws an exception, as shown in Figure 12.3. Consider the
following scenario:

- If the exception type is Exception3, it is caught by the catch block for handling
exception ex3 in method2. statement5 is skipped and statement6 is executed.
- If the exception type is Exception2, method2 is aborted, the control is returned to
method1, and the exception is caught by the catch block for handling exception ex2
in method1. statement3 is skipped and statement4 is executed.
- If the exception type is Exception1, method1 is aborted, the control is returned
to the main method, and the exception is caught by the catch block for handling
exception ex1 in the main method. statement1 is skipped and statement2 is
executed.
- If the exception type is not caught in method2, method1, or main, the program
terminates and statement1 and statement2 are not executed.

![image](https://user-images.githubusercontent.com/44777689/144745103-c10b10b1-4200-4913-8312-851a8597ab0e.png)

## Example: Declaring, Throwing, and Catching Exceptions

```java
public class CircleWithException {
    /** The radius of the circle */
    private double radius;
    /** The number of the objects created */
    private static int numberOfObjects = 0;
    /** Construct a circle with radius 1 */
    public CircleWithException() {
        this(1.0);
    }
    /** Construct a circle with a specified radius
     public CircleWithException(double newRadius) {
     setRadius(newRadius);
     numberOfObjects++;
     }
     /** Return radius */
    public double getRadius() {
        return radius;
    }
    /** Set a new radius */
    public void setRadius(double newRadius)
            throws IllegalArgumentException {
        if (newRadius >= 0)
            radius = newRadius;
        else
            throw new IllegalArgumentException(
                    "Radius cannot be negative");
    }
    /** Return numberOfObjects */
    public static int getNumberOfObjects() {
        return numberOfObjects;
    }
    /** Return the area of this circle */
    public double findArea() {
        return radius * radius * 3.14159;
    }
}
```

```java
public class TestCircleWithException {
    public static void main(String[] args) {
        try {
            CircleWithException c1 = new CircleWithException(5);
            CircleWithException c2 = new CircleWithException(−5);
            CircleWithException c3 = new CircleWithException(0);
        }
        catch (IllegalArgumentException ex) {
            System.out.println(ex);
        }
        System.out.println("Number of objects created: " +
                CircleWithException.getNumberOfObjects());
    }
}
```

![image](https://user-images.githubusercontent.com/44777689/144745544-28d8f6d8-9f73-4896-bd85-9e3865016352.png)


The original Circle class remains intact except that the class name is changed to
CircleWithException, a new constructor CircleWithException(newRadius) is added,
and the setRadius method now declares an exception and throws it if the radius is negative.

The setRadius method declares to throw IllegalArgumentException in the method
header (lines 25–32 in Listing 12.7 CircleWithException.java). The CircleWithException
class would still compile if the throws IllegalArgumentException clause (line 26) were
removed from the method declaration, since it is a subclass of RuntimeException and every
method can throw RuntimeException (an unchecked exception) regardless of whether it is
declared in the method header.

The test program creates three CircleWithException objects—c1, c2, and
c3—to test how to handle exceptions. Invoking new CircleWithException(−5)
(line 5 in Listing 12.8) causes the setRadius method to be invoked, which throws an
IllegalArgumentException, because the radius is negative. In the catch block, the
type of the object ex is IllegalArgumentException, which matches the exception object
thrown by the setRadius method, so this exception is caught by the catch block.

The exception handler prints a short message, ex.toString() (line 9 in Listing 12.8),
about the exception, using System.out.println(ex).

Note that the execution continues in the event of the exception. If the handlers had not
caught the exception, the program would have abruptly terminated.

The test program would still compile if the try statement were not used, because the method
throws an instance of IllegalArgumentException, a subclass of RuntimeException (an
unchecked exception).

## The finally Clause

The finally clause is always executed regardless of whether an exception occurred or not.

Occasionally, you may want some code to be executed regardless of whether an exception
occurs or is caught. Java has a finally clause that can be used to accomplish this objective.
The syntax for the finally clause might look like this:

```java
try {
    statements;
}
catch (TheException ex) {
    handling ex;
}
finally {
    finalStatements;
}
```

The code in the finally block is executed under all circumstances, regardless of whether an
exception occurs in the try block or is caught. Consider three possible cases:

1. If no exception arises in the try block, finalStatements is executed and the next
statement after the try statement is executed.
2. If a statement causes an exception in the try block that is caught in a catch block, the
rest of the statements in the try block are skipped, the catch block is executed, and
the finally clause is executed. The next statement after the try statement is executed.
3. If one of the statements causes an exception that is not caught in any catch block,
the other statements in the try block are skipped, the finally clause is executed,
and the exception is passed to the caller of this method.

The finally block executes even if there is a return statement prior to reaching the
finally block.

## When to Use Exceptions

A method should throw an exception if the error needs to be handled by its caller.

The try block contains the code that is executed in normal circumstances. The catch block
contains the code that is executed in exceptional circumstances. Exception handling separates error-handling code from normal programming tasks, thus making programs easier
to read and to modify. Be aware, however, that exception handling usually requires more
time and resources, because it requires instantiating a new exception object, rolling back
the call stack, and propagating the exception through the chain of method calls to search
for the handler.

An exception occurs in a method. If you want the exception to be processed by its caller, you
should create an exception object and throw it. If you can handle the exception in the method
where it occurs, there is no need to throw or use exceptions.

In general, common exceptions that may occur in multiple classes in a project are candidates
for exception classes. Simple errors that may occur in individual methods are best handled
without throwing exceptions. This can be done by using if statements to check for errors.

When should you use a try-catch block in the code? Use it when you have to deal with
unexpected error conditions. Do not use a try-catch block to deal with simple, expected
situations. For example, the following code:

```java
try {
  System.out.println(refVar.toString());
}
catch (NullPointerException ex) {
  System.out.println("refVar is null");
}
```

is better replaced by

```java
if (refVar != null)
  System.out.println(refVar.toString());
else
  System.out.println("refVar is null");
```

Which situations are exceptional and which are expected is sometimes difficult to decide. The
point is not to abuse exception handling as a way to deal with a simple logic test.
