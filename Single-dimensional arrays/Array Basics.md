# Array Basics

## 1. Declaring Array Variables

To use an array in a program, you must declare a variable to reference the array and specify the array’s element type. Here is the syntax for declaring an array variable:

```java
elementType[] arrayRefVar;

elementType arrayRefVar[]; // Allowed, but not preferred
```
The **elementType** can be any data type, and all elements in the array will have the same data type. For example, the following code declares a variable **myList** that references an array of double elements.

```java
double[] myList;

double myList[]; // Allowed, but not preferred
```

## 2. Creating Arrays

Unlike declarations for primitive data type variables, the declaration of an array variable does not allocate any space in memory for the array. It creates only a storage location for the reference to an array. If a variable does not contain a reference to an array, the value of the variable is **null**. You cannot assign elements to an array unless it has already been created. After an array variable is declared, you can create an array by using the **new** operator and assign its reference to the variable with the following syntax:

```java
arrayRefVar = new elementType[arraySize];
```
This statement does two things: (1) it creates an array using new **elementType[arraySize]** and (2) it assigns the reference of the newly created array to the variable **arrayRefVar**. Declaring an array variable, creating an array, and assigning the reference of the array to the variable can be combined in one statement as

```java
elementType[] arrayRefVar = new elementType[arraySize];

elementType arrayRefVar[] = new elementType[arraySize];
```
Here is an example of such a statement:

```java
double[] myList = new double[10];
```
This statement declares an array variable, myList, creates an array of 10 elements of double type, and assigns its reference to myList. To assign values to the elements, use the syntax

```java
arrayRefVar[index] = value;
```
For example, the following code initializes the array:

```java
myList[0] = 5.6;
myList[1] = 4.5;
myList[2] = 3.3;
myList[3] = 13.2;
myList[4] = 4.0;
myList[5] = 34.33;
myList[6] = 34.0;
myList[7] = 45.45;
myList[8] = 99.993;
myList[9] = 11123;
```
![image](https://user-images.githubusercontent.com/44777689/140594484-acbc45d0-d3e0-4dac-ae82-8a8be78e2bc2.png)

## 3. Array Size and Default Values

When space for an array is allocated, the array size must be given, specifying the number of elements that can be stored in it. The size of an array cannot be changed after the array is created.
Size can be obtained using **arrayRefVar.length**. For example, **myList.length** is **10**.
When an array is created, its elements are assigned the default value of **0** for the numeric
primitive data types, **\u0000** for char types, and **false** for boolean types.

## 4. Accessing Array Elements

The array elements are accessed through the index. Array indices are **0** based; that is, they
range from **0** to **arrayRefVar.length − 1**. In the example, **myList** holds 10
**double** values, and the indices are from **0** to **9**.
Each element in the array is represented using the following syntax, known as an *indexed
variable*:

```java
arrayRefVar[index];
```

For example, **myList[9]** represents the last element in the array **myList**

An indexed variable can be used in the same way as a regular variable. For example, the
following code adds the values in **myList[0]** and **myList[1]** to **myList[2]**:

```java
myList[2] = myList[0] + myList[1];
```

The following loop assigns **0** to **myList[0]**, **1** to **myList[1]**, . . . , and **9** to **myList[9]**:

```java
for (int i = 0; i < myList.length; i++) {
  myList[i] = i;
}
```

## 5. Array Initializers

When processing array elements, you will often use a **for** loop for one of two reasons:

1. All of the elements in an array are of the same type. They are evenly processed in the
same fashion repeatedly using a loop.

2. Since the size of the array is known, it is natural to use a for loop.

Assume that the array is created as follows:

```java
double[] myList = new double[10];
```

The following are some examples of processing arrays:

1. *Initializing arrays with input values*: The following loop initializes the array myList with user input values:
```java
java.util.Scanner input = new java.util.Scanner(System.in);
System.out.print("Enter " + myList.length + " values: ");
for (int i = 0; i < myList.length; i++)
  myList[i] = input.nextDouble();
```

2. *Initializing arrays with random values*: The following loop initializes the array myList
with random values between 0.0 and 100.0, but less than 100.0:
```java
for (int i = 0; i < myList.length; i++) {
  myList[i] = Math.random() * 100;
}
```

3. *Displaying arrays*: To print an array, you have to print each element in the array using
a loop such as the following:
```java
for (int i = 0; i < myList.length; i++) {
  System.out.print(myList[i] + " ");
}
```

**Tips:** For an array of the char[] type, it can be printed using one print statement. For
example, the following code displays Dallas:
```java
char[] city = {'D', 'a', 'l', 'l', 'a', 's'};
System.out.println(city);
```

4. *Summing all elements*: Use a variable named total to store the sum. Initially total is 0. Add each element in the array to total using a loop such as the following:
```java
double total = 0;
for (int i = 0; i < myList.length; i++) {
  total += myList[i];
}
```

5. *Finding the largest element*: Use a variable named max to store the largest element.
Initially max is myList[0]. To find the largest element in the array myList, compare
each element with max, and update max if the element is greater than max.
```java
double max = myList[0];
for (int i = 1; i < myList.length; i++) {
  if (myList[i] > max) max = myList[i];
}
```

6. *Finding the smallest index of the largest element*: Often you need to locate the largest
element in an array. If an array has multiple elements with the same largest value, find the
smallest index of such an element. Suppose that the array myList is {1, 5, 3, 4, 5, 5}. The
largest element is 5, and the smallest index for 5 is 1. Use a variable named max to store
the largest element, and a variable named indexOfMax to denote the index of the largest
element. Initially max is myList[0] and indexOfMax is 0. Compare each element in
myList with max and update max and indexOfMax if the element is greater than max.

```java
double max = myList[0];
int indexOfMax = 0;
for (int i = 1; i < myList.length; i++) {
  if (myList[i] > max) {
    max = myList[i];
    indexOfMax = i;
  }
}
```

7. *Random shuffling*: In many applications, you need to randomly reorder the elements in
an array. This is called shuffling. To accomplish this, for each element myList[i],
randomly generate an index j and swap myList[i] with myList[j], as follows:
```java
for (int i = 0; i < myList.length – 1; i++) {
// Generate an index j randomly
int j = (int)(Math.random() * myList.length);
// Swap myList[i] with myList[j]
double temp = myList[i];
myList[i] = myList[j];
myList[j] = temp;
}
```

8. *Shifting elements*: Sometimes you need to shift the elements left or right. Here is an
example of shifting the elements one position to the left and filling the last element with
the first element:
```java
double temp = myList[0]; // Retain the first element
// Shift elements left
for (int i = 1; i < myList.length; i++) {
myList[i - 1] = myList[i];
}
// Move the FIrst element to fill in the last position
myList[myList.length - 1] = temp;
```

## 6. Foreach Loops

Java supports a convenient for loop, known as a foreach loop, which enables you to traverse
the array sequentially without using an index variable. For example, the following code displays all the elements in the array myList:
```java
for (double e: myList) {
  System.out.println(e);
}
```

You can read the code as “for each element e in myList, do the following.” Note that the
variable, e, must be declared as the same type as the elements in myList.
In general, the syntax for a foreach loop is

```java
for (elementType element: arrayRefVar) {
// Process the element
}
```

You still have to use an index variable if you wish to traverse the array in a different order or
change the elements in the array.

**Caution**

Accessing an array out of bounds is a common programming error that throws a runtime
**ArrayIndexOutOfBoundsException**. To avoid it, make sure you do not use
an index beyond **arrayRefVar.length − 1** or simply using a foreach loop if
possible.
Programmers often mistakenly reference the first element in an array with index 1, but
it should be 0. This is called the off-by-one error. Another common off-by-one error in
a loop is using <= where < should be used. For example, the following loop is wrong:
```java
for (int i = 0; i <= list.length; i++)
  System.out.print(list[i] + " ");
```
The <= should be replaced by <. Using a foreach loop can avoid the off-by-one error in
this case.



