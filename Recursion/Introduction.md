# Introducion

Recursion is a technique that leads to elegant solutions to problems that are difficult
to program using simple loops. 

To use recursion is to program using recursive methods—that is, to use methods that invoke themselves. Recursion is a useful programming technique. In some cases, it enables you to develop a natural, straightforward, simple solution to an otherwise difficult problem. 

## Case study: Computing Factorials

A recursive method is one that invokes itself directly or indirectly.

Many mathematical functions are defined using recursion. Let’s begin with a simple example.

The factorial of a number n can be recursively defined as follows:
```
0! = 1;
n! = n × (n − 1)!; n > 0
```

How do you find n! for a given n? To find 1! is easy because you know that 0! is 1 and 1!
is 1 × 0!. Assuming that you know (n − 1)!, you can obtain n! immediately by using
n × (n − 1)!. Thus, the problem of computing n! is reduced to computing (n − 1)!. When
computing (n − 1)!, you can apply the same idea recursively until n is reduced to 0.

Let factorial(n) be the method for computing n!. If you call the method with n = 0,
it immediately returns the result. The method knows how to solve the simplest case, which is
referred to as the *base case* or the *stopping condition*. If you call the method with n > 0, it
reduces the problem into a subproblem for computing the factorial of n − 1. The *subproblem*
is essentially the same as the original problem, but it is simpler or smaller. Because the subproblem has the same property as the original problem, you can call the method with a different
argument, which is referred to as a *recursive call*.

The recursive algorithm for computing factorial(n) can be simply described as follows:
```java
if (n == 0)
  return 1;
else
  return n * factorial(n − 1);
```

A recursive call can result in many more recursive calls because the method keeps on dividing
a subproblem into new subproblems. For a recursive method to terminate, the problem must
eventually be reduced to a stopping case, at which point the method returns a result to its caller.

The caller then performs a computation and returns the result to its own caller. This process
continues until the result is passed back to the original caller. The original problem can now
be solved by multiplying n by the result of factorial(n − 1).

```java
import java.util.Scanner;
  public class ComputeFactorial {
  /** Main method */
    public static void main(String[] args) {
      // Create a Scanner
      Scanner input = new Scanner(System.in);
      System.out.print("Enter a nonnegative integer: ");
      int n = input.nextInt();
      
      // Display factorial
      System.out.println("Factorial of " + n + " is " + factorial(n));
    }

  /** Return the factorial for the specified number */
  public static long factorial(int n) {
    if (n == 0) // Base case
      return 1;
    else
      return n * factorial(n − 1); // Recursive call
    }
  }
```

##  Case Study: Computing Fibonacci Numbers
In some cases, recursion enables you to create an intuitive, straightforward, simple
solution to a problem.

The factorial method in the preceding section could easily be rewritten without using recursion. In this section, we show an example for creating an intuitive solution to a problem using
recursion. Consider the well-known Fibonacci-series problem:

The series: 0 1 1 2 3 5 8 13 21 34 55 89 . . .

indexes: 0 1 2 3 4 5 6 7 8 9 10 11

The Fibonacci series begins with 0 and 1, and each subsequent number is the sum of the preceding two. The series can be recursively defined as:

```
fib(0) = 0;
fib(1) = 1;
fib(index) = fib(index − 2) + fib(index − 1); index >= 2
```

The Fibonacci series was named for Leonardo Fibonacci, a medieval mathematician, who
originated it to model the growth of the rabbit population. It can be applied in numeric optimization and in various other areas.

How do you find fib(index) for a given index? It is easy to find fib(2) because you
know fib(0) and fib(1). Assuming you know fib(index − 2) and fib(index − 1),
you can obtain fib(index) immediately. Thus, the problem of computing fib(index) is
reduced to computing fib(index − 2) and fib(index − 1). When doing so, you apply
the idea recursively until index is reduced to 0 or 1.

The base case is index = 0 or index = 1. If you call the method with index = 0 or
index = 1, it immediately returns the result. If you call the method with index >= 2, it divides
the problem into two subproblems for computing fib(index − 1) and fib(index − 2)
using recursive calls. The recursive algorithm for computing fib(index) can be simply
described as follows:

```java
if (index == 0)
  return 0;
else if (index == 1)
  return 1;
else
  return fib(index − 1) + fib(index − 2);
```

![image](https://user-images.githubusercontent.com/44777689/144581407-71c4e483-24ea-4625-99af-c2d78bc4aea7.png)

