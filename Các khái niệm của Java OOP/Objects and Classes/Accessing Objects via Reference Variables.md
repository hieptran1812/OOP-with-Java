# Accessing Objects via Reference Variables

An object’s data and methods can be accessed through the dot (.) operator via the
object’s reference variable.

Newly created objects are allocated in the memory. They can be accessed via reference
variables.

## Reference Variables and Reference Types

Objects are accessed via the object’s reference variables, which contain references to the
objects. Such variables are declared using the following syntax:

```java
ClassName objectRefVar;
```

A class is essentially a programmer-defined type. A class is a reference type, which means that
a variable of the class type can reference an instance of the class. The following statement
declares the variable myCircle to be of the Circle type:

```java
Circle myCircle;
```

The variable myCircle can reference a Circle object. The next statement creates an object
and assigns its reference to myCircle:

```java
myCircle = new Circle();
```

You can write a single statement that combines the declaration of an object reference variable,
the creation of an object, and the assigning of an object reference to the variable with the following syntax:

```java
ClassName objectRefVar = new ClassName();
```

Here is an example:

```java
Circle myCircle = new Circle();
```

The variable myCircle holds a reference to a Circle object.

**Note**:

An object reference variable that appears to hold an object actually contains a reference
to that object. Strictly speaking, an object reference variable and an object are different,
but most of the time the distinction can be ignored. Therefore, it is fine, for simplicity,
to say that myCircle is a Circle object rather than use the long-winded description
that myCircle is a variable that contains a reference to a Circle object.

**Note**:

Arrays are treated as objects in Java. Arrays are created using the **new** operator. An array
variable is actually a variable that contains a reference to an array.

## Accessing an Object’s Data and Methods

In OOP terminology, an object’s member refers to its data fields and methods. After an object
is created, its data can be accessed and its methods can be invoked using the *dot operator (.)*,
also known as the *object member access operator*:

- objectRefVar.dataField references a data field in the object.
- objectRefVar.method(arguments) invokes a method on the object.

For example, myCircle.radius references the radius in myCircle and myCircle
.getArea() invokes the getArea method on myCircle. Methods are invoked as operations
on objects.

The data field radius is referred to as an *instance variable* because it is dependent on a
specific instance. For the same reason, the method getArea is referred to as an instance
method because you can invoke it only on a specific instance. The object on which an instance
method is invoked is called a *calling object*.

**Caution**:

Recall that you use Math.methodName(arguments) (e.g., Math.pow(3, 2.5))
to invoke a method in the Math class. Can you invoke getArea() using Circle.
getArea()? The answer is no. All the methods in the Math class are static methods,
which are defined using the static keyword. However, getArea() is an instance
method, and thus nonstatic. It must be invoked from an object using objectRefVar.
methodName(arguments) (e.g., myCircle.getArea())

**Note**:

Usually you create an object and assign it to a variable, then later you can use the
variable to reference the object. Occasionally, an object does not need to be referenced
later. In this case, you can create an object without explicitly assigning it to a variable
using the syntax:

```java
new Circle();
```
or
```java
System.out.println("Area is " + new Circle(5).getArea());
```

The former statement creates a Circle object. The latter creates a Circle object and
invokes its getArea method to return its area. An object created in this way is known
as an *anonymous object*.

## Reference Data Fields and the null Value

The data fields can be of reference types. For example, the following Student class contains
a data field name of the String type. String is a predefined Java class.

```java
class Student {
    String name; // name has the default value null
    int age; // age has the default value 0
    boolean isScienceMajor; // isScienceMajor has default value false
    char gender; // gender has default value '\u0000'
}
```

If a data field of a reference type does not reference any object, the data field holds a special
Java value, null. null is a literal just like true and false. While true and false are
Boolean literals, null is a literal for a reference type.

The default value of a data field is null for a reference type, 0 for a numeric type, false
for a boolean type, and \u0000 for a char type. However, Java assigns no default value to
a local variable inside a method. The following code displays the default values of the data
fields name, age, isScienceMajor, and gender for a Student object:

```java
class TestStudent {
    public static void main(String[] args) {
        Student student = new Student();
        System.out.println("name? " + student.name);
        System.out.println("age? " + student.age);
        System.out.println("isScienceMajor? " + student.isScienceMajor);
        System.out.println("gender? " + student.gender);
    }
}
```

The following code has a compile error, because the local variables x and y are not initialized:

```java
class TestLocalVariables {
    public static void main(String[] args) {
        int x; // x has no default value
        String y; // y has no default value
        System.out.println("x is " + x);
        System.out.println("y is " + y);
    }
}
```

## Differences between Variables of Primitive Types and Reference Types

Every variable represents a memory location that holds a value. When you declare a variable,
you are telling the compiler what type of value the variable can hold. For a variable of a primitive type, the value is of the primitive type. For a variable of a reference type, the value is a
reference to where an object is located. For example, the value of int
variable i is int value 1, and the value of Circle object c holds a reference to where the
contents of the Circle object are stored in memory.

![image](https://user-images.githubusercontent.com/44777689/140677128-679981cc-f10f-48b8-9081-2c21504738f9.png)

A variable of a primitive type holds a value of the primitive type, and a variable
of a reference type holds a reference to where an object is stored in memory.

When you assign one variable to another, the other variable is set to the same value. For
a variable of a primitive type, the real value of one variable is assigned to the other variable.
For a variable of a reference type, the reference of one variable is assigned to the other variable. As shown in figure, the assignment statement i = j copies the contents of j into i

![image](https://user-images.githubusercontent.com/44777689/140677289-07ed4a5c-8ca1-465f-9326-55296e36bde5.png)

for primitive variables. As shown in Figure 9.9, the assignment statement c1 = c2 copies
the reference of c2 into c1 for reference variables. After the assignment, variables c1 and c2
refer to the same object.

![image](https://user-images.githubusercontent.com/44777689/140677321-2edca50f-afd0-41ff-8b58-6c57680f3a08.png)







