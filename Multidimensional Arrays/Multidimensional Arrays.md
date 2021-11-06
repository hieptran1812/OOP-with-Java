# Multidimensional Arrays

## Introduction

Data in a table or a matrix can be represented using a two-dimensional array.

```java
double[][] distances = {
  {0, 983, 787, 714, 1375, 967, 1087},
  {983, 0, 214, 1102, 1763, 1723, 1842},
  {787, 214, 0, 888, 1549, 1548, 1627},
  {714, 1102, 888, 0, 661, 781, 810},
  {1375, 1763, 1549, 661, 0, 1426, 1187},
  {967, 1723, 1548, 781, 1426, 0, 239},
  {1087, 1842, 1627, 810, 1187, 239, 0},
};
```
## Two-Dimensional Array Basics

An element in a two-dimensional array is accessed through a row and a column index.

### Declaring Variables of Two-Dimensional Arrays and Creating Two-Dimensional Arrays

The syntax for declaring a two-dimensional array is as follows:
```java
elementType[][] arrayRefVar;
```

or
```java
elementType arrayRefVar[][]; // Allowed, but not preferred
```

As an example, here is how you would declare a two-dimensional array variable matrix
of int values:
```java
int[][] matrix;
```

You can create a two-dimensional array of 5-by-5 int values and assign it to matrix using
this syntax:
```java
matrix = new int[5][5];
```

![image](https://user-images.githubusercontent.com/44777689/140604655-b07b312c-fd88-439e-a9f2-07bb6839f86f.png)

![image](https://user-images.githubusercontent.com/44777689/140604660-586e455c-4f51-48cf-aee1-45ed1beea3ad.png)

### Obtaining the Lengths of Two-Dimensional Arrays

A two-dimensional array is actually an array in which each element is a one-dimensional array.
The length of an array x is the number of elements in the array, which can be obtained using x.
length. x[0], x[1], . . . , and x[x.length − 1] are arrays. Their lengths can be obtained
using x[0].length, x[1].length, . . . , and x[x.length − 1].length.

For example, suppose that x = new int[3][4], x[0], x[1], and x[2] are onedimensional arrays and each contains four elements, as shown in Figure 8.2. x.length is 3,
and x[0].length, x[1].length, and x[2].length are 4.

![image](https://user-images.githubusercontent.com/44777689/140604700-ba53df6e-bdad-4611-9591-81357e389f71.png)

### Ragged Arrays

Each row in a two-dimensional array is itself an array. Thus, the rows can have different lengths. An array of this kind is known as a ragged array. Here is an example of creating a ragged array:

![image](https://user-images.githubusercontent.com/44777689/140605224-27759a1b-7be2-45b9-b600-81bd1afaa9c6.png)

As you can see, triangleArray[0].length is 5, triangleArray[1].length is 4,
triangleArray[2].length is 3, triangleArray[3].length is 2, and triangle−
Array[4].length is 1.

If you don’t know the values in a ragged array in advance, but do know the sizes—say, the
same as in the preceding figure—you can create a ragged array using the following syntax:

![image](https://user-images.githubusercontent.com/44777689/140605254-feb1645c-2107-4397-8f85-b1eefba1abff.png)

You can now assign values to the array. For example:

![image](https://user-images.githubusercontent.com/44777689/140605267-74742657-d0ae-40d1-9fce-c5fd67829544.png)

## Passing Two-Dimensional Arrays to Methods

When passing a two-dimensional array to a method, the reference of the array is
passed to the method. You can pass a two-dimensional array to a method just as you pass a one-dimensional array.
You can also return an array from a method.

## Multidimensional Arrays

A two-dimensional array is an array of one-dimensional arrays, and a three-dimensional array is an array of two-dimensional arrays.

In the preceding section, you used a two-dimensional array to represent a matrix or a table.
Occasionally, you will need to represent n-dimensional data structures. In Java, you can create
n-dimensional arrays for any positive integer n.

The way to declare two-dimensional array variables and create two-dimensional arrays can
be generalized to declare n-dimensional array variables and create n-dimensional arrays for
n >= 3. For example, you may use a three-dimensional array to store exam scores for a class
of six students with five exams, and each exam has two parts (multiple-choice and essay type
questions). The following syntax declares a three-dimensional array variable scores, creates
an array, and assigns its reference to scores.

```java
double[][][] scores = new double[6][5][2];
```

You can also use the array initializer to create and initialize the array as follows:

```java
double[][][] scores = {
{{7.5, 20.5}, {9.0, 22.5}, {15, 33.5}, {13, 21.5}, {15, 2.5}},
{{4.5, 21.5}, {9.0, 22.5}, {15, 34.5}, {12, 20.5}, {14, 9.5}},
{{6.5, 30.5}, {9.4, 10.5}, {11, 33.5}, {11, 23.5}, {10, 2.5}},
{{6.5, 23.5}, {9.4, 32.5}, {13, 34.5}, {11, 20.5}, {16, 7.5}},
{{8.5, 26.5}, {9.4, 52.5}, {13, 36.5}, {13, 24.5}, {16, 2.5}},
{{9.5, 20.5}, {9.4, 42.5}, {13, 31.5}, {12, 20.5}, {16, 6.5}}};
```

scores[0][1][0] refers to the multiple-choice score for the first student’s second exam,
which is 9.0. scores[0][1][1] refers to the essay score for the first student’s second exam,
which is 22.5. This is depicted in the following figure:

![image](https://user-images.githubusercontent.com/44777689/140605402-88fd0364-a5ac-48fb-9a9f-a1292ed5bf76.png)

A multidimensional array is actually an array in which each element is another array. A threedimensional array is an array of two-dimensional arrays. A two-dimensional array is an array
of one-dimensional arrays. For example, suppose that x = new int[2][2][5] and x[0]
and x[1] are two-dimensional arrays. x[0][0], x[0][1], x[1][0], and x[1][1] are onedimensional arrays and each contains five elements. x.length is 2, x[0].length and x[1].
length are 2, and x[0][0].length, x[0][1].length, x[1][0].length, and x[1][1].
length are 5.







