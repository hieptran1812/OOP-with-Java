# Variables

*Variables are used to represent values that may be changed in the program.*

Variables are used to store values to be used later in a program. They are called variables because their values can be changed.

Variables are for representing data of a certain type. To use a variable, you declare it by
telling the compiler its name as well as what type of data it can store. The variable declaration
tells the compiler to allocate appropriate memory space for the variable based on its data type.
The syntax for declaring a variable is:

```
datatype variableName;
```

Here are some examples of variable declarations:

```java
int count; // Declare count to be an integer variable
double radius; // Declare radius to be a double variable
double interestRate; // Declare interestRate to be a double variable
```

These examples use the data types **int** and **double**. Later you will be introduced to
additional data types, such as **byte**, **short**, **long**, **float**, **char**, and **boolean**.

If variables are of the same type, they can be declared together, as follows:

```
datatype variable1, variable2, ..., variablen;
```

The variables are separated by commas. For example,

```java
int i, j, k; // Declare i, j, and k as int variables
```

Variables often have initial values. You can declare a variable and initialize it in one step.
Consider, for instance, the following code:

```java
int count = 1;
```

This is equivalent to the next two statements:

```java
int count;
count = 1;
```

You can also use a shorthand form to declare and initialize variables of the same type
together. For example,

```java
int i = 1, j = 2;
```

**Tip**

A variable must be declared before it can be assigned a value. A variable declared in a
method must be assigned a value before it can be used.

Whenever possible, declare a variable and assign its initial value in one step. This will
make the program easy to read and avoid programming errors.

Every variable has a scope. **The scope of a variable** is the part of the program where the
variable can be referenced. 
