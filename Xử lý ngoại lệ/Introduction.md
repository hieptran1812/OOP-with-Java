# Exception Handling

## Giới thiệu

Một exception (hoặc exceptional event) là một vấn đề phát sinh trong quá trình thực hiện một chương trình. Khi một exception xảy ra, quy trình bình thường của chương trình bị gián đoạn và chương trình/ứng dụng kết thúc bất thường, do đó, các exception này phải được xử lý.

Một exception có thể xảy ra vì nhiều lý do khác nhau. Sau đây là một số trường hợp xảy ra exception:

* Người dùng nhập vào dữ liệu không hợp lệ (ví dụ như ô năm sinh lại nhập vào kí tự chữ cái,...).
* Một file cần được mở nhưng lại không được tìm thấy.
* Truy cập tới một giá trị của mảng mà chỉ số lại nằm ngoài giới hạn của mảng (ví dụ mảng có 5 giá trị thì truy cập vào giá trị có chỉ số là 6,...)

Một số trường hợp ngoại lệ này là do lỗi người dùng, một số trường hợp khác do lỗi của lập trình viên và các trường hợp khác do tài nguyên vật lý bị lỗi theo một cách nào đó.

## Tổng quan về xử lý Exception

*Exception được ném từ một method. Việc gọi đến method có thể bắt và xử lý exception.*

Để trình bày cách xử lý exception, bao gồm việc exception object được tạo và ném ra như nào, hãy bắt đầu với ví dụ dưới đây, chương trình sẽ thực hiện in ra thương của 2 số nguyên:

```java
import java.ulti.Scanner;

public class Quotient{
  public class void main(String[] args){
    Scanner sc = new Scanner(System.in);
    
    System.out.println("Nhap 2 so nguyen);
    int number1 = sc.nextInt();
    int number2 = input.nextInt();
    
    System.out.println(number1 + " / " + number2 + " = " + (number1+ " / " + number2 + " is " + (number1 / number2));
  }
}
```

![image](https://user-images.githubusercontent.com/44777689/144582939-54a0f930-79ba-4317-b758-e3ce8ce3a873.png)

If you entered 0 for the second number, a runtime error would occur, because you cannot
divide an integer by 0. (Note a floating-point number divided by 0 does not raise an exception.)
A simple way to fix this error is to add an if statement to test the second number.

```java
import java.util.Scanner;

  public class QuotientWithIf {
    public static void main(String[] args) {
      Scanner input = new Scanner(System.in);

      // Prompt the user to enter two integers
      System.out.print("Enter two integers: ");
      int number1 = input.nextInt();
      int number2 = input.nextInt();

      if (number2 != 0)
        System.out.println(number1 + " / " + number2 + " is " + (number1 / number2));
      else
        System.out.println("Divisor cannot be zero ");
     }
  }
```
How can a method notify its caller an exception has occurred? Java enables a method to throw an exception that can be caught and handled by the caller. 

```java
import java.util.Scanner;

  public class QuotientWithException {
    public static int quotient(int number1, int number2) {
    if (number2 == 0)
      throw new ArithmeticException("Divisor cannot be zero");
      return number1 / number2;
    }

    public static void main(String[] args) {
      Scanner input = new Scanner(System.in);
  
      // Prompt the user to enter two integers
      System.out.print("Enter two integers: ");
      int number1 = input.nextInt();
      int number2 = input.nextInt();

      try {
        int result = quotient(number1, number2);
        System.out.println(number1 + " / " + number2 + " is " + result);
      }
      catch (ArithmeticException ex) {
        System.out.println("Exception: an integer " + "cannot be divided by zero ");
      }

      System.out.println("Execution continues ...");
     }
   }
```


