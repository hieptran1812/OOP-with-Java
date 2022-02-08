# Reading Input from the Console

Reading input from the console enables the program to accept input from the user.

Java uses **System.out** to refer to the standard output device, and **System.in** to the
standard input device. By default, the output device is the display monitor, and the input
device is the keyboard. To perform console output, you simply use the println method to
display a primitive value or a string to the console. To perform console input, you need to use
the **Scanner** class to create an object to read input from **System.in**, as follows:

```java
Scanner input = new Scanner(System.in);
```

The syntax **new Scanner(System.in)** creates an object of the **Scanner** type. The syntax
**Scanner** input declares that input is a variable whose type is **Scanner**. The whole line
**Scanner input = new Scanner(System.in)** creates a **Scanner** object and assigns its
reference to the variable input. An object may invoke its methods. To invoke a method on
an object is to ask the object to perform a task. You can invoke the **nextDouble(**) method
to read a double value as follows:

```java
double radius = input.nextDouble();
```

