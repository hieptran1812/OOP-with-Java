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
    
    System.out.println(number1 + " / " + number2 + " = " + (number1
  }
}
```

## Các chủ điểm kiến thức

1. Tổng quan về exception
2. Lợi ích của việc xử lý exception
3. Phân biệt 2 loại exception: **Error** (fatal) với **Exception** (nonfatal) và checked với unchecked
