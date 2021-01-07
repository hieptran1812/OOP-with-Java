## Text I/O được xử lý như nào trong Java

*Dữ liệu text được đọc sử dụng **Scanner** class và viết sử dụng **PrintWriter** class.*

Ta đã biết rằng một **File** object đóng gói các thuộc tính hoặc đường dẫn của file nhưng không bao gồm 
các method đọc/ghi dữ liệu từ/đến file. Để thực hiện nhập/xuất, bạn cần tạo một object sử dụng Java I/O class
thích hợp. Object bao gồm các method để đọc/ghi dữ liệu từ/đến file. Ví dụ, để ghi text vào một file tên
**temp.txt**, bạn có thể tạo một object sử dụng **PrintWriter** class như dưới đây:

```java
PrintWriter output = new PrintWriter("temp.txt");
```

Okay! Giờ bạn có thể gọi **print** method của object để ghi một string nào đó vào file. Ví dụ, để viết
**Hiepdz** vào file ta làm như sau:

```java
output.print("Hiepdz");
```

Sau đó ta đóng file:
```java
output.close;
```

Có nhiều I/O class cho nhiều mục đích khác nhau. Nói chung, ta có thể phân loại thành input classes và 
output classes. Một *input class* bao gồm phương thức để đọc dữ liệu, và một *output class* bao gồm các
phương thức để ghi dữ liệu. **PrintWriter** là một ví dụ về output class, và **Scanner** là một ví dụ về
input class. Đoạn code dưới đây tạo một input object cho file **temp.txt** và đọc dữ liệu từ file.

```java
Scanner input = new Scanner(new File("temp.txt"));
System.out.println(input.nextLine());
```

Nếu **temp.txt** chứa đoạn text **Hiepdz**, **input.nextLine()** trả về string **Hiepdz**.

Hình bên dưới minh họa Java I/O. Một input object đọc một *stream* của dữ liệu từ một file, và một 
output object ghi một stream của dữ liệu đến một file. Một input object còn được gọi là *input stream*
và một output object là *output stream*.

<p align = "center"><img src = "https://github.com/hieptran1812/OOP-with-Java-PTIT/blob/main/Image/iostream.PNG"></p>

## Text I/O và Binary I/O

*Binary I/O không liên quan đến việc mã hóa (encoding) và giải mã (decoding) nên do đó chúng hiệu quả 
hơn text I/O.*

<p align = "center"><img src = "https://github.com/hieptran1812/OOP-with-Java-PTIT/blob/main/Image/text%20and%20binary%20IO.PNG"></p>

## Binary I/O Classes



