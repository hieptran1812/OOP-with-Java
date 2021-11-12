# Visibility Modifiers

Visibility modifiers can be used to specify the visibility of a class and its members.

You can use the public visibility modifier for classes, methods, and data fields to denote they
can be accessed from any other classes. If no visibility modifier is used, then by default the
classes, methods, and data fields are accessible by any class in the same package. This is known
as package-private or package-access.

In addition to the public and default visibility modifiers, Java provides the private and
protected modifiers for class members. This section introduces the private modifier. 

The private modifier makes methods and data fields accessible only from within its own
class. Figure illustrates how a public, default, and private data field or method in class C1
can be accessed from a class C2 in the same package, and from a class C3 in a different package.

![image](https://user-images.githubusercontent.com/44777689/141444701-91879a70-fe7f-47d4-9fdb-0324b34ff79e.png)

The private modifier restricts access to its defining class, the default modifier restricts access to a package,
and the public modifier enables unrestricted access.

If a class is not defined as public, it can be accessed only within the same package. As shown
in Figure, C1 can be accessed from C2, but not from C3.

![image](https://user-images.githubusercontent.com/44777689/141444776-02b7727c-d435-42d6-bec7-0a436a74fa9c.png)

A nonpublic class has package access.

A visibility modifier specifies how data fields and methods in a class can be accessed from
outside the class. There is no restriction on accessing data fields and methods from inside the
class. As shown in b, an object c of class C cannot access its private members,
because c is in the Test class. As shown in a, an object c of class C can access its
private members, because c is defined inside its own class.

![image](https://user-images.githubusercontent.com/44777689/141444861-74b48c1c-5923-45b9-a78e-3860ecf54db8.png)

An object can access its private members if it is defined in its own class.

**Caution**

The private modifier applies only to the members of a class. The public modifier
can apply to a class or members of a class. Using the modifiers public and private
on local variables would cause a compile error.

**Note**

In most cases, the constructor should be public. However, if you want to prohibit the
user from creating an instance of a class, use a private constructor. For example, there
is no reason to create an instance from the Math class, because all of its data fields and
methods are static. To prevent the user from creating objects from the Math class, the
constructor in java.lang.Math is defined as follows:

```java
private Math() {
}
```
