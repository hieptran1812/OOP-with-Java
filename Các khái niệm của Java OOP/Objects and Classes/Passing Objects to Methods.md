#  Passing Objects to Methods

Passing an object to a method is to pass the reference of the object.

You can pass objects to methods. Like passing an array, passing an object is actually passing
the reference of the object. The following code passes the myCircle object as an argument to
the printCircle method:

```java
public class Test {
    public static void main(String[] args) {
// Circle is defined in Listing 9.8
        Circle myCircle = new Circle(5.0);
        printCircle(myCircle);
    }
    public static void printCircle(Circle c) {
        System.out.println("The area of the circle of radius "
                + c.getRadius() + " is " + c.getArea());
    }
}
```

Java uses exactly one mode of passing arguments: pass-by-value. In the preceding code,
the value of myCircle is passed to the printCircle method. This value is a reference to a
Circle object.

The program in program demonstrates the difference between passing a primitive-type
value and passing a reference value.

```java
public class TestPassObject {
    /** Main method */
    public static void main(String[] args) {
// Create a Circle object with radius 1
        Circle myCircle =
                new Circle(1); // Use the Circle class in Listing 9.8
// Print areas for radius 1, 2, 3, 4, and 5.
        int n = 5;
        printAreas(myCircle, n);
// See myCircle.radius and times
        System.out.println("\n" + "Radius is " + myCircle.getRadius());
        System.out.println("n is " + n);
    }
    /** Print a table of areas for radius */
    public static void printAreas(Circle c, int times) {
        System.out.println("Radius \t\tArea");
        while (times >= 1) {
            System.out.println(c.getRadius() + "\t\t" + c.getArea());
            c.setRadius(c.getRadius() + 1);
            times——;
        }
    }
}
```

The Circle class is defined in Listing 9.8. The program passes a Circle object myCircle
and an integer value from n to invoke printAreas(myCircle, n) (line 10), which prints a
table of areas for radii 1, 2, 3, 4, and 5, as presented in the sample output.
Figure 9.18 shows the call stack for executing the methods in the program. Note the objects
are stored in a heap.

When passing an argument of a primitive data type, the value of the argument is passed. In
this case, the value of n (5) is passed to times. Inside the printAreas method, the content
of times is changed; this does not affect the content of n.

When passing an argument of a reference type, the reference of the object is passed. In this
case, c contains a reference for the object that is also referenced via myCircle. Therefore,
changing the properties of the object through c inside the printAreas method has the same
effect as doing so outside the method through the variable myCircle. Pass-by-value on references can be best described semantically as pass-by-sharing; that is, the object referenced in
the method is the same as the object being passed.

![image](https://user-images.githubusercontent.com/44777689/141033165-6013d884-089e-483c-9f17-d032885601f4.png)

The value of n is passed to times, and the reference to myCircle is passed to
c in the printAreas method.



