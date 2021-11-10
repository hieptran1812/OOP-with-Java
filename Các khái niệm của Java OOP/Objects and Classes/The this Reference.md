# The this Reference

The keyword this refers to the object itself. It can also be used inside a constructor to
invoke another constructor of the same class.

The this keyword is the name of a reference that an object can use to refer to itself. You can
use the this keyword to reference the object’s instance members. For example, the following
code in (a) uses this to reference the object’s radius and invokes its getArea() method
explicitly. The this reference is normally omitted for brevity as shown in (b). However, the
this reference is needed to reference a data field hidden by a method or constructor parameter,
or to invoke an overloaded constructor

![image](https://user-images.githubusercontent.com/44777689/141033629-0243caea-87a1-4772-9715-048630a9d960.png)

## Using this to Reference Data Fields

It is a good practice to use the data field as the parameter name in a setter method or a constructor to make the code easy to read and to avoid creating unnecessary names. In this case,
you need to use the this keyword to reference the data field in the setter method. For example, the setRadius method can be implemented as shown in (a). It would be wrong if it is
implemented as shown in (b).

![image](https://user-images.githubusercontent.com/44777689/141033672-2c28de66-2cd4-405d-9d12-dae3dd4c9d77.png)

The data field radius is hidden by the parameter radius in the setter method. You need to
reference the data field name in the method using the syntax this.radius. A hidden static
variable can be accessed simply by using the ClassName.staticVariable reference. A
hidden instance variable can be accessed by using the keyword this, as shown in Figure

![image](https://user-images.githubusercontent.com/44777689/141033701-39c3a9fe-4dd8-472b-80d4-1c3e1b882be1.png)

The this keyword gives us a way to reference the object that invokes an instance method.
To invoke f1.setI(10), this.i = i is executed, which assigns the value of parameter i to
the data field i of this calling object f1. The keyword this refers to the object that invokes the
instance method setI, as shown in Figure 9.21b. The line F.k = k means the value in parameter
k is assigned to the static data field k of the class, which is shared by all the objects of the class.

## Using this to Invoke a Constructor

The this keyword can be used to invoke another constructor of the same class. For example,
you can rewrite the Circle class as follows:

![image](https://user-images.githubusercontent.com/44777689/141033739-f20a2877-6c71-4048-9023-f35d0db16bca.png)

The line this(1.0) in the second constructor invokes the first constructor with a double
value argument.

**Note**

Java requires that the this(arg-list) statement appear first in the constructor before
any other executable statements.

**Tip**

If a class has multiple constructors, it is better to implement them using this(arg-list)
as much as possible. In general, a constructor with no or fewer arguments can invoke a
constructor with more arguments using this(arg-list). This syntax often simplifies
coding and makes the class easier to read and to maintain.
