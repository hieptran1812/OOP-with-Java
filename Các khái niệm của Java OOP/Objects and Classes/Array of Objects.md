# Array of Objects

An array can hold objects as well as primitive-type values.

Single-Dimensional Arrays, described how to create arrays of primitive-type elements. You can also create arrays of objects. For example, the following statement declares
and creates an array of 10 Circle objects:

```java
Circle[] circleArray = new Circle[10];
```

To initialize circleArray, you can use a for loop as follows:

```java
for (int i = 0; i < circleArray.length; i++) {
  circleArray[i] = new Circle();
}
```

An array of objects is actually an array of reference variables. Thus, invoking circleArray[1]
.getArea() involves two levels of referencing, as shown in Figure. circleArray
references the entire array, and circleArray[1] references a Circle object.

![image](https://user-images.githubusercontent.com/44777689/141033364-025bffcb-7d92-4754-87f4-169e60fd4262.png)

In an array of objects, an element of the array contains a reference to an
object.

Program gives an example that demonstrates how to use an array of objects. The program summarizes the areas of an array of circles. The program creates circleArray, an
array composed of five Circle objects; it then initializes circle radii with random values and
displays the total area of the circles in the array.

```java
public class TotalArea {
    /** Main method */
    public static void main(String[] args) {
// Declare circleArray
        Circle[] circleArray;
// Create circleArray
        circleArray = createCircleArray();
// Print circleArray and total areas of the circles
        printCircleArray(circleArray);
    }
    /** Create an array of Circle objects */
    public static Circle[] createCircleArray() {
        Circle[] circleArray = new Circle[5];
        for (int i = 0; i < circleArray.length; i++) {
            circleArray[i] = new Circle(Math.random() * 100);
        }
// Return Circle array
        return circleArray;
    }
    /** Print an array of circles and their total area */
    public static void printCircleArray(Circle[] circleArray) {
        System.out.printf("%–30s%–15s\n", "Radius", "Area");
        for (int i = 0; i < circleArray.length; i++) {
            System.out.printf("%–30f%–15f\n", circleArray[i].getRadius(),
                    circleArray[i].getArea());
        }
        System.out.println("— — — — — — — — — — — — — — — — — — — — — — — — — — — — ");
// Compute and display the result
                System.out.printf("%–30s%–15f\n", "The total area of circles is",
                        sum(circleArray));
    }
    /** Add circle areas */
    public static double sum(Circle[] circleArray) {
// Initialize sum
        double sum = 0;
// Add areas to sum
        for (int i = 0; i < circleArray.length; i++)
            sum += circleArray[i].getArea();
        return sum;
    }
}
```

The program invokes createCircleArray() (line 8) to create an array of five circle objects.
Several circle classes were introduced in this chapter. This example uses the Circle class
introduced in Section 9.9, Data Field Encapsulation.

The circle radii are randomly generated using the Math.random() method (line 19). The
createCircleArray method returns an array of Circle objects (line 23). The array is
passed to the printCircleArray method, which displays the radius and area of each circle
and the total area of the circles.

The sum of the circle areas is computed by invoking the sum method (line 38), which takes
the array of Circle objects as the argument and returns a double value for the total area.



