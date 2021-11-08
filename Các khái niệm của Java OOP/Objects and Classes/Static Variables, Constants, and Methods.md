# Static Variables, Constants, and Methods

A static variable is shared by all objects of the class. A static method cannot access
instance members (i.e., instance data fields and methods) of the class.

The data field radius in the circle class is known as an instance variable. An instance variable
is tied to a specific instance of the class; it is not shared among objects of the same class. For
example, suppose that you create the following objects:

```java
Circle circle1 = new Circle();
Circle circle2 = new Circle(5);
```

The radius in circle1 is independent of the radius in circle2 and is stored in a different
memory location. Changes made to circle1’s radius do not affect circle2’s radius, and
vice versa.

If you want all the instances of a class to share data, use *static variables*, also known as
*class variables*. Static variables store values for the variables in a common memory location.
Because of this common location, if one object changes the value of a static variable, all objects
of the same class are affected. Java supports static methods as well as static variables. *Static
methods* can be called without creating an instance of the class.

Let’s modify the Circle class by adding a static variable numberOfObjects to
count the number of circle objects created. When the first object of this class is created,
numberOfObjects is 1. When the second object is created, numberOfObjects becomes
2. The UML of the new circle class is shown in Figure. The Circle class defines the
instance variable radius and the static variable numberOfObjects, the instance methods
getRadius, setRadius, and getArea, and the static method getNumberOfObjects. (Note
static variables and methods are underlined in the UML class diagram.)

![image](https://user-images.githubusercontent.com/44777689/140677770-914aa30f-e6a9-46ee-9a32-34958e35da12.png)

Instance variables belong to the instances and have memory storage independent of one another. Static
variables are shared by all the instances of the same class.

To declare a static variable or define a static method, put the modifier static in the variable or method declaration. The static variable numberOfObjects and the static method
getNumberOfObjects() can be declared as follows:

```java
static int numberOfObjects;
static int getNumberObjects() {
  return numberOfObjects;
}
```

Constants in a class are shared by all objects of the class. Thus, constants should be declared
as final static. For example, the constant PI in the Math class is defined as follows:

```java
final static double PI = 3.14159265358979323846;
```

```java
public class Circle {
    /** The radius of the circle */
    double radius;
    /** The number of objects created */
    static int numberOfObjects = 0;
    /** Construct a circle with radius 1 */
    Circle() {
        radius = 1;
        numberOfObjects++;
    }
    /** Construct a circle with a specified radius */
    Circle(double newRadius) {
        radius = newRadius;
        numberOfObjects++;
    }
    /** Return numberOfObjects */
    static int getNumberOfObjects() {
        return numberOfObjects;
    }
    /** Return the area of this circle */
    double getArea() {
        return radius * radius * Math.PI;
    }
}
```

Method getNumberOfObjects() in Circle is a static method. All the methods in the Math
class are static. The main method is static, too.

Instance methods (e.g., getArea()) and instance data (e.g., radius) belong to instances
and can be used only after the instances are created. They are accessed via a reference variable.
Static methods (e.g., getNumberOfObjects()) and static data (e.g., numberOfObjects) can
be accessed from a reference variable or from their class name.

The program below demonstrates how to use instance and static variables and methods and illustrates the effects of using them.

```java
public class TestCircleWithStaticMembers {
    /** Main method */
    public static void main(String[] args) {
        System.out.println("Before creating objects");
        System.out.println("The number of Circle objects is " +
                Circle.numberOfObjects);
// Create c1
        Circle c1 = new Circle(); // Use the Circle class in Listing 9.6
// Display c1 BEFORE c2 is created
        System.out.println("\nAfter creating c1");
        System.out.println("c1: radius (" + c1.radius +
                ") and number of Circle objects (" +
                c1.numberOfObjects + ")");
// Create c2
        Circle c2 = new Circle(5);
// Modify c1
        c1.radius = 9;
// Display c1 and c2 AFTER c2 was created
        System.out.println("\nAfter creating c2 and modifying c1");
        System.out.println("c1: radius (" + c1.radius +
                ") and number of Circle objects (" +
                c1.numberOfObjects + ")");
        System.out.println("c2: radius (" + c2.radius +
                ") and number of Circle objects (" +
                c2.numberOfObjects + ")");
    }
}
```

When you compile TestCircleWithStaticMembers.java, the Java compiler automatically compiles Circle.java if it has not been compiled since the last change.

Static variables and methods can be accessed without creating objects. Line 6 displays the
number of objects, which is 0, since no objects have been created.

The main method creates two circles, c1 and c2 (lines 9 and18). The instance variable
radius in c1 is modified to become 9 (line 21). This change does not affect the instance
variable radius in c2, since these two instance variables are independent. The static variable numberOfObjects becomes 1 after c1 is created (line 9), and it becomes 2 after c2
is created (line 18).

Note PI is a constant defined in Math and Math.PI references the constant. c1.numberOfObjects (line 27) and c2.numberOfObjects (line 30) are better replaced by Circle.
numberOfObjects. This improves readability because other programmers can easily recognize the static variable. You can also replace Circle.numberOfObjects with Circle.
getNumberOfObjects().

**Tip**:

Use ClassName.methodName(arguments) to invoke a static method and ClassName.staticVariable to access a static variable. This improves readability because
this makes static methods and data easy to spot.

An instance method can invoke an instance or static method, and access an instance or static
data field. A static method can invoke a static method and access a static data field. However,
a static method cannot invoke an instance method or access an instance data field, since static
methods and static data fields don’t belong to a particular object. The relationship between
static and instance members is summarized in the following diagram:

![image](https://user-images.githubusercontent.com/44777689/140678287-72dd2306-959a-4b34-a1cf-532cb43526d5.png)

For example, the following code is wrong.

```java
public class A {
    int i = 5;
    static int k = 2;
    public static void main(String[] args) {
        int j = i; // Wrong because i is an instance variable
        m1(); // Wrong because m1() is an instance method
    }
    public void m1() {
// Correct since instance and static variables and methods
// can be used in an instance method
        i = i + k + m2(i, k);
    }
    public static int m2(int i, int j) {
        return (int)(Math.pow(i, j));
    }
}
```

Note if you replace the preceding code with the following new code, the program would be
fine, because the instance data field i and method m1 are now accessed from an object a
(lines 7 and 8):

```java
public class A {
    int i = 5;
    static int k = 2;
    public static void main(String[] args) {
        A a = new A();
        int j = a.i; // OK, a.i accesses the object's instance variable
        a.m1(); // OK, a.m1() invokes the object's instance method
    }
    public void m1() {
        i = i + k + m2(i, k);
    }
    public static int m2(int i, int j) {
        return (int)(Math.pow(i, j));
    }
}
```

**Design Guide**

How do you decide whether a variable or a method should be instance or static? A
variable or a method that is dependent on a specific instance of the class should be an
instance variable or method. A variable or a method that is not dependent on a specific
instance of the class should be a static variable or method. For example, every circle has
its own radius, so the radius is dependent on a specific circle. Therefore, radius is an
instance variable of the Circle class. Since the getArea method is dependent on a
specific circle, it is an instance method. None of the methods in the Math class, such
as random, pow, sin, and cos, is dependent on a specific instance. Therefore, these
methods are static methods. The main method is static and can be invoked directly
from a class.

**Caution**

It is a common design error to define an instance method that should have been defined
as static. For example, the method factorial(int n) should be defined as static,
as shown next, because it is independent of any specific instance.

![image](https://user-images.githubusercontent.com/44777689/140678482-f885b248-0f29-4f89-8fb8-bfcabf0b583f.png)
