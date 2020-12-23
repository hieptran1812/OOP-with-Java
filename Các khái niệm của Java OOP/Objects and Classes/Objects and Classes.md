## Introduction

*Lập trình hướng đối tượng cho phép ta phát triển phần mềm quy mô lớn (large-scale software) và GUIs hiệu quả hơn.*

Lập trình hướng đối tượng là một kĩ thuật cần thiết để phát triển phần mềm có khả năng tái sử dụng (reusable software).

## Định nghĩa Classes

*Một class định nghĩa thuộc tính (properties) và hành vi (behaviors) cho đối tượng (objects).*

Lập trình hướng đối tượng (OOP) liên quan đến việc lập trình sử dụng các đối tượng. Một đối tượng đại diện cho một thực thể (entity) trong thế giới thực có thể được xác định rõ ràng. Ví dụ, một học sinh, một cái bàn,
một vòng tròn, một nút và thậm chí một khoản vay đều có thể được xem như các đối tượng. Một đối tượng có một danh tính duy nhất (unique identity), trạng thái (state) và hành vi (behavior).

* *State* của một object (còn được gọi là *properties* hoặc *attributes*) được biểu diễn bằng những trường dữ liệu (data field) cùng với giá trị hiện tại của chúng. Ví dụ: một object hình tròn có trường dữ liệu là bán kính (radius) - 
thuộc tính đặc trưng cho một hình tròn. Một object hình chữ nhật gồm 2 data field là chiều rộng (width) và chiều dài (height), đó là thuộc tính đặc trưng cho mỗi hình chữ nhật.

* *Behavior* của một object định nghĩa bởi phương thức (method). Khi gọi một method trong object là ta yêu cầu object thực hiện một hành động (action).
Ví dụ, ta định nghĩa method có tên getArea() và getPerimeter() cho object hình tròn. Object hình tròn có thể gọi getArea() để trả về giá trị diện tích hình tròn và
getPerimeter() để trả về chu vi hình tròn. Ngoài ra, ta có thể định nghĩa thêm method setRadius(radius). Một object hình tròn có thể gọi object này để thay đổi bán kính hình tròn.

Một class là một nhóm object có các thuộc tính chung. Một object là một thể hiện (instance) của một class. Ta có thể tạo nhiều instance của một class. Một lớp Java sử dụng biến (variable) để xác định data field và method để xác định behavior.
Ngoài ra một class cung cấp các method thuộc loại đặc biệt, gọi là *constructors*, được gọi để khởi tạo một object mới. Một constructor có thể thực hiện bất kì action nào, nhưng constructor được thiết kể để khởi tạo actions, chẳng hạn như khởi tạo data fields cho objects. Ảnh dưới là ví dụ về định nghĩa class cho circle objects.

<p align = "center"><img src = "https://github.com/hieptran1812/OOP-with-Java-PTIT/blob/main/Image/object.PNG"></p>

```Java

class Circle{
  /** The radius of this circle */
  double radius = 1;
  
  /** Construct a circle object */
  Circle(){
  }
  
  /** Contruct a circle object */
  Circle(double newRadius){
    radius = newRadius;
  }
  
  /** Return the area of this circle */
  double getArea(){
    return radius * radius * Math.PI;
  }
  
  /** Return the perimeter of this circle */
  double getPerimeter(){
    return 2 * radius * Math.PI;
  }
  
  /** Set a new radius for this circle */
  void setRadius(double newRadius){
    radius = newRadius;
  }
}

```

## Ví dụ: Định nghĩa Classes và tạo Object

Chương trình dưới là một chương trình định nghĩa class Circle và sử dụng nó để tạo các object. Chương trình xây dựng ba object Circle có bán kính 1, 25 và 125 và hiển thị bán kính và diện tích của mỗi hình tròn. Sau đó, nó thay đổi bán kính của object thứ hai thành 100 và hiển thị bán kính và diện tích mới của nó.

```Java
public class TestCircle {
   /** Main method */
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

Chương trình gồm 2 class. Class đầu tiên, TestCircle, là main class. Vai trò duy nhất của lớp này là kiểm tra lớp thứ 2, Circle. Khi chạy chương trình, Java runtime system gọi main method trong main class.

Bạn có thể đặt 2 class vào trong 1 file, nhưng chỉ 1 class trong file là *public class*. Hơn nữa, public class phải có cùng tên với tên file. Vì vậy, tên file là **TestCircle.java** vì TestCircle là public. Mỗi class trong code được compile thành **.class** file. Khi compile **TestCircle.java**, 2 class **TestCircle.class** và **Circle.class** được sinh ra.

<p align = "center"><img src = "https://github.com/hieptran1812/OOP-with-Java-PTIT/blob/main/Image/public%20class.PNG"></p>

Ngoài ra ta có thể gộp 2 class thành 1 class như sau:

```Java
public class Circle {
    /** Main method */
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
        circle2.radius = 100;
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
