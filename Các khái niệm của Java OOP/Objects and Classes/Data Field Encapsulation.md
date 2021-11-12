# Data Field Encapsulation

Making data fields private protects data and makes the class easy to maintain.
The data fields radius and numberOfObjects in the Circle class in program can be
modified directly (e.g., c1.radius = 5 or Circle.numberOfObjects = 10). This is not
a good practice—for two reasons:

1. Data may be tampered with. For example, numberOfObjects is to count the number
of objects created, but it may be mistakenly set to an arbitrary value (e.g., Circle.
numberOfObjects = 10).

2. The class becomes difficult to maintain and vulnerable to bugs. Suppose that you
want to modify the Circle class to ensure that the radius is nonnegative after other
programs have already used the class. You have to change not only the Circle class
but also the programs that use it because the clients may have modified the radius
directly (e.g., c1.radius = –5).

To prevent direct modifications of data fields, you should declare the data fields private,
using the private modifier. This is known as *data field encapsulation*.

A private data field cannot be accessed by an object from outside the class that defines the
private field. However, a client often needs to retrieve and modify a data field. To make a
private data field accessible, provide a getter method to return its value. To enable a private
data field to be updated, provide a setter method to set a new value. A getter method is also
referred to as an accessor and a setter to a mutator. A getter method has the following
signature:

```java
public returnType getPropertyName()
```
If the returnType is boolean, the getter method should be defined as follows by convention:

```java
public boolean isPropertyName()
```

A setter method has the following signature:

```java
public void setPropertyName(dataType propertyValue)
```

Let’s create a new circle class with a private data-field radius and its associated accessor and
mutator methods. The class diagram is shown in Figure

![image](https://user-images.githubusercontent.com/44777689/141448539-15b6132d-de2f-4c18-a9c8-843ca8994357.png)

The Circle class encapsulates circle properties and provides getter/setter and other methods.

```java
public class Circle {
    /** The radius of the circle */
    private double radius = 1;
    /** The number of objects created */
    private static int numberOfObjects = 0;
    /** Construct a circle with radius 1 */
    public Circle() {
        numberOfObjects++;
    }
    /** Construct a circle with a specified radius */
    public Circle(double newRadius) {
        radius = newRadius;
        numberOfObjects++;
    }
    /** Return radius */
    public double getRadius() {
        return radius;
    }
    /** Set a new radius */
    public void setRadius(double newRadius) {
        radius = (newRadius >= 0) ? newRadius : 0;
    }
    /** Return numberOfObjects */
    public static int getNumberOfObjects() {
        return numberOfObjects;
    }
    /** Return the area of this circle */
    public double getArea() {
        return radius * radius * Math.PI;
    }
}
```

The getRadius() method (lines 20–22) returns the radius and the setRadius(newRadius)
method (lines 25–27) sets a new radius for the object. If the new radius is negative, 0 is set as
the radius for the object. Since these methods are the only ways to read and modify the radius,
you have total control over how the radius property is accessed. If you have to change the
implementation of these methods, you don’t need to change the client programs. This makes
the class easy to maintain.
Program below gives a client program that uses the Circle class to create a Circle object,
and modifies the radius using the setRadius method.

```java
public class TestCircleWithPrivateDataFields {
    /** Main method */
    public static void main(String[] args) {
// Create a circle with radius 5.0
        Circle myCircle = new Circle(5.0);
        System.out.println("The area of the circle of radius "
                + myCircle.getRadius() + " is " + myCircle.getArea());
// Increase myCircle's radius by 10%
        myCircle.setRadius(myCircle.getRadius() * 1.1);
        System.out.println("The area of the circle of radius "
                + myCircle.getRadius() + " is " + myCircle.getArea());
        System.out.println("The number of objects created is "
                + Circle.getNumberOfObjects());
    }
}
```

The data field radius is declared private. Private data can be accessed only within their defining class, so you cannot use myCircle.radius in the client program. A compile error would
occur if you attempted to access private data from a client.

Since numberOfObjects is private, it cannot be modified. This prevents tampering. For
example, the user cannot set numberOfObjects to 100. The only way to make it 100 is to
create 100 objects of the Circle class.



