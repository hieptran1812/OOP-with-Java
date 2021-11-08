# Constructing Objects Using Constructors

## Example
Classes are definitions for objects and objects are created from classes.

This section gives two examples of defining classes and uses the classes to create objects.
Code below is a program that defines the Circle class and uses it to create objects. The program constructs three circle objects with radius 1, 25, and 125 and displays the radius and
area of each of the three circles. It then changes the radius of the second object to 100 and
displays its new radius and area.

```java
public class test {
    public static void main(String[] args) {
        // Create a circle with radius 1
        Circle circle1 = new Circle();
        System.out.println("The area of the circle of radius "
                + circle1.radius + " is " + circle1.getArea());

        // Create a circle with radius 25
        Circle circle2 = new Circle(25);
        System.out.println("The area of the circle of radius "
                + circle2.radius + " is " + circle2.getArea());

        // Create a circle with radius 125
        Circle circle3 = new Circle(125);
        System.out.println("The area of the circle of radius "
                + circle3.radius + " is " + circle3.getArea());

        // Modify circle radius
        circle2.radius = 100; // or circle2.setRadius(100)
        System.out.println("The area of the circle of radius "
                + circle2.radius + " is " + circle2.getArea());
    }
}

// Define the circle class with two constructors
class Circle {
    double radius;

    /** Construct a circle with radius 1 */
    Circle() {
        radius = 1;
    }

    /** Construct a circle with a specified radius */
    Circle(double newRadius) {
        radius = newRadius;
    }

    /** Return the area of this circle */
    double getArea() {
        return radius * radius * Math.PI;
    }

    /** Return the perimeter of this circle */
    double getPerimeter() {
        return 2 * radius * Math.PI;
    }

    /** Set a new radius for this circle */
    void setRadius(double newRadius) {
        radius = newRadius;
    }
}
```

The program contains two classes. The first of these, TestCircle, is the main class. Its sole
purpose is to test the second class, Circle. Such a program that uses the class is often referred
to as a *client* of the class. When you run the program, the Java runtime system invokes the
main method in the main class.

You can put the two classes into one file, but only one class in the file can be a public class.
Furthermore, the public class must have the same name as the file name. Therefore, the file
name is TestCircle.java, since TestCircle is public. Each class in the source code is compiled into a .class file. When you compile TestCircle.java, two class files TestCircle.class
and Circle.class are generated.

![image](https://user-images.githubusercontent.com/44777689/140675153-c344fc99-bbbb-4235-b257-a58d71fa9e82.png)

There are many ways to write Java programs. For instance, you can combine the two classes
in the preceding example into one.

```java
public class test {
    public static void main(String[] args) {
        // Create a circle with radius 1
        Circle circle1 = new Circle();
        System.out.println("The area of the circle of radius "
                + circle1.radius + " is " + circle1.getArea());

        // Create a circle with radius 25
        Circle circle2 = new Circle(25);
        System.out.println("The area of the circle of radius "
                + circle2.radius + " is " + circle2.getArea());

        // Create a circle with radius 125
        Circle circle3 = new Circle(125);
        System.out.println("The area of the circle of radius "
                + circle3.radius + " is " + circle3.getArea());

        // Modify circle radius
        circle2.radius = 100; // or circle2.setRadius(100)
        System.out.println("The area of the circle of radius "
                + circle2.radius + " is " + circle2.getArea());
    }
    
    double radius;
    /** Construct a circle with radius 1 */
    Circle() {
        radius = 1;
    }

    /** Construct a circle with a specified radius */
    Circle(double newRadius) {
        radius = newRadius;
    }

    /** Return the area of this circle */
    double getArea() {
        return radius * radius * Math.PI;
    }

    /** Return the perimeter of this circle */
    double getPerimeter() {
        return 2 * radius * Math.PI;
    }

    /** Set a new radius for this circle */
    void setRadius(double newRadius) {
        radius = newRadius;
    }
}
```


## Constructor
A constructor is invoked to create an object using the new operator.

Constructors are a special kind of method. They have three peculiarities:
- A constructor must have the same name as the class itself.
- Constructors do not have a return type—not even **void**.
- Constructors are invoked using the **new** operator when an object is created. Constructors play the role of initializing objects.

The constructor has exactly the same name as its defining class. Like regular methods, constructors can be overloaded (i.e., multiple constructors can have the same name but different signatures), making it easy to construct objects with different initial data values.

It is a common mistake to put the **void** keyword in front of a constructor. For example,

```java
public void Circle() {
}
```

In this case, **Circle()** is a method, not a constructor.

Constructors are used to construct objects. To construct an object from a class, invoke a
constructor of the class using the **new** operator, as follows:

```java
new ClassName(arguments);
```

For example, new Circle() creates an object of the Circle class using the first constructor defined in the Circle class, and new Circle(25) creates an object using the second
constructor defined in the Circle class.

A class normally provides a constructor without arguments (e.g., Circle()). Such a constructor is referred to as a *no-arg* or *no-argument* constructor.

A class may be defined without constructors. In this case, a public no-arg constructor with
an empty body is implicitly defined in the class. This constructor, called a *default constructor*,
is provided automatically *only if no constructors are explicitly defined in the class*.

