# Exception Type

Exceptions are objects, and objects are defined using classes. The root class for
exceptions is java.lang.Throwable.

![image](https://user-images.githubusercontent.com/44777689/144744402-b7c890a8-413e-4ee7-be26-78a87d9ef8fd.png)

The Throwable class is the root of exception classes. All Java exception classes inherit
directly or indirectly from Throwable. You can create your own exception classes by
extending Exception or a subclass of Exception.

The exception classes can be classified into three major types: system errors, exceptions,
and runtime exceptions.

**System errors** are thrown by the JVM and are represented in the Error class. The
Error class describes internal system errors, though such errors rarely occur. If
one does, there is little you can do beyond notifying the user and trying to terminate
the program gracefully.

![image](https://user-images.githubusercontent.com/44777689/144744430-4e2a2155-4df2-43b6-8e0b-73674a037e2f.png)

Exceptions are represented in the Exception class, which describes errors caused by
your program and by external circumstances. These errors can be caught and handled
by your program. 

![image](https://user-images.githubusercontent.com/44777689/144744448-b89bfb48-487c-4404-a2cb-f2f6648058e3.png)

Runtime exceptions are represented in the RuntimeException class, which describes
programming errors, such as bad casting, accessing an out-of-bounds array, and
numeric errors. Runtime exceptions normally indicate programming errors.

![image](https://user-images.githubusercontent.com/44777689/144744456-f6692247-89a4-43ef-b662-7c498bfbf362.png)

RuntimeException, Error, and their subclasses are known as unchecked exceptions. All
other exceptions are known as checked exceptions, meaning the compiler forces the programmer to check and deal with them in a try-catch block or declare it in the method header.

In most cases, unchecked exceptions reflect programming logic errors that are unrecoverable. For example, a NullPointerException is thrown if you access an object through a
reference variable before an object is assigned to it; an IndexOutOfBoundsException is
thrown if you access an element in an array outside the bounds of the array. These are logic
errors that should be corrected in the program. Unchecked exceptions can occur anywhere in
a program. To avoid cumbersome overuse of try-catch blocks, Java does not mandate that
you write code to catch or declare unchecked exceptions.

