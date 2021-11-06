# Copy arrays

To copy the contents of one array into another, you have to copy the array’s individual elements into the other array.
Often, in a program, you need to duplicate an array or a part of an array. In such cases you
could attempt to use the assignment statement (=), as follows:

```java
list2 = list1;
```

However, this statement does not copy the contents of the array referenced by list1 to list2,
but instead merely copies the reference value from list1 to list2.

![image](https://user-images.githubusercontent.com/44777689/140601308-8c593552-9641-4429-8e95-7d02ab87e34f.png)

Before the assignment statement, list1 and list2 point to separate memory
locations. After the assignment, the reference of the list1 array is passed to list2

```java
public class test {
    public static void main(String[] args) {
        char[] city = {'D', 'a', 'l', 'l', 'a', 's'};
        char[] list2 = city;
        System.out.println(list2);
    }
}
```

Another approach is to use the arraycopy method in the java.lang.System class to copy
arrays instead of using a loop. The syntax for arraycopy is:

```java
arraycopy(sourceArray, srcPos, targetArray, tarPos, length);
```

The parameters srcPos and tarPos indicate the starting positions in sourceArray and
targetArray, respectively. The number of elements copied from sourceArray to
targetArray is indicated by length. For example, you can rewrite the loop using the
following statement:
```java
System.arraycopy(sourceArray, 0, targetArray, 0, sourceArray.length);
```

The arraycopy method does not allocate memory space for the target array. The target array
must have already been created with its memory space allocated. After the copying takes place,
targetArray and sourceArray have the same content but independent memory locations.

# Passing Arrays to Methods

When passing an array to a method, the reference of the array is passed to the method.
Just as you can pass primitive type values to methods, you can also pass arrays to methods.
For example, the following method displays the elements in an int array:

```java
public static void printArray(int[] array) {
  for (int i = 0; i < array.length; i++) {
    System.out.print(array[i] + " ");
  }
}
```

You can invoke it by passing an array. For example, the following statement invokes the
printArray method to display 3, 1, 2, 6, 4, and 2.

```java
printArray(new int[]{3, 1, 2, 6, 4, 2});
```

Java uses pass-by-value to pass arguments to a method. There are important differences
between passing the values of variables of primitive data types and passing arrays.

- For an argument of a primitive type, the argument’s value is passed.
- For an argument of an array type, the value of the argument is a reference to an array;
this reference value is passed to the method. Semantically, it can be best described as
pass-by-sharing, that is, the array in the method is the same as the array being passed.
Thus, if you change the array in the method, you will see the change outside the method

```java
public class test {
    public static void main(String[] args) {
        int x = 1; // x represents an int value
        int[] y = new int[10]; // y represents an array of int values
        m(x, y); // Invoke m with arguments x and y
        System.out.println("x is " + x);
        System.out.println("y[0] is " + y[0]);
    }
    public static void m(int number, int[] numbers) {
        number = 1001; // Assign a new value to number
        numbers[0] = 5555; // Assign a new value to numbers[0]
    }
}
```
You may wonder why after m is invoked, x remains 1, but y[0] becomes 5555. This is because y and numbers, although they are independent variables, reference the same array. When m(x, y) is invoked, the values of x and y are passed to number and numbers. Since y contains the reference value to the array, numbers now contains the same reference value to the same array.
![image](https://user-images.githubusercontent.com/44777689/140601758-9ef416c8-20a3-4717-8e18-8dbcd0057f4f.png)

The primitive type value in x is passed to number, and the reference value in y is passed to numbers

program below shows the difference between passing a primitive data
type value and an array reference variable to a method.
The program contains two methods for swapping elements in an array. The first method,
named swap, fails to swap two int arguments. The second method, named swapFirstTwoInArray, successfully swaps the first two elements in the array argument.

```java
public class test {
 /** Main method */
        public static void main(String[] args) {
        int[] a = {1, 2};
        // Swap elements using the swap method
        System.out.println("Before invoking swap");
        System.out.println("array is {" + a[0] + ", " + a[1] + "}");
        swap(a[0], a[1]);
        System.out.println("After invoking swap");
        System.out.println("array is {" + a[0] + ", " + a[1] + "}");
        // Swap elements using the swapFirstTwoInArray method
        System.out.println("Before invoking swapFirstTwoInArray");
        System.out.println("array is {" + a[0] + ", " + a[1] + "}");
        swapFirstTwoInArray(a);
        System.out.println("After invoking swapFirstTwoInArray");
        System.out.println("array is {" + a[0] + ", " + a[1] + "}");
        }
        /** Swap two variables */
        public static void swap(int n1, int n2) {
            int temp = n1;
            n1 = n2;
            n2 = temp;
        }

        /** Swap the first two elements in the array */
        public static void swapFirstTwoInArray(int[] array) {
            int temp = array[0];
            array[0] = array[1];
            array[1] = temp;
        }
}
```

# Returning an Array from a Method

When a method returns an array, the reference of the array is returned.

You can pass arrays when invoking a method. A method may also return an array. For example,
Point the following method returns an array that is the reversal of another array.

```java
public class test {
    public static void main(String[] args) {
        int[] a = new int[10];
        for(int i = 0; i < a.length; i++){
            a[i] = i;
        }
        int [] result = reverse(a);
        for(int i = 0; i < result.length; i++){
            System.out.print(result[i]);
        }
    }
    public static int[] reverse(int[] list) {
        int[] result = new int[list.length];
        for (int i = 0, j = result.length - 1; i < list.length; i++, j--) {
            result[j] = list[i];
        }
        return result;
    }
}
```







