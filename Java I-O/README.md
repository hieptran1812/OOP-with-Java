# Java I/O

## Giới thiệu

*Java cung cấp các class để thực hiện text I/O và binary I/O*.

Files được phân loại dưới dạng text hoặc binary. Một file có thể được xử lý (đọc, tạo mới hoặc sửa) bằng cách sử dụng text editor như Notepad trên Windows hoặc vi trên UNIX được gọi là *text file*. Tất cả những file còn lại được gọi là *binary file*. Bạn không thể đọc binary file sử dụng text editor do chúng được thiết kế để đọc bởi chương trình. Ví dụ, chương trình mã nguồn Java là text file và được đọc bởi text editor, nhưng Java class file là binary file và được đọc bởi JVM.

Java cung cấp các class để thực hiện file input và output. Ta có thể phân loại thành: *text I/O classes* và *binary I/O classes*.

## Kiến thức

Qua phần này bạn sẽ tìm hiểu được:

1. Nhập xuất được xử lý như nào trong Java.
2. Phân biệt text I/O và binary I/O.
3. Đọc và ghi byte sử dụng **FileInputStream* và **FileOutputStream**.
4. Lọc dữ liệu sử dụng base classes **FilterInputStream** và **FilterOutputStream**.
5. Cải thiện hiệu suất I/O sử dụng **BufferedInputStream** và **BufferedOutputStream**.
6. Cách viết một chương trình copy một file.
7. Lưu trữ và khôi phục object sử dụng **ObjectOutputStream** và **ObjectInputStream**.
8. Cài đặt **Serializable** interface để làm cho object được tuần tự hóa (serializable).
9. Tuần tự hóa các mảng (serialize arrays).
10. Đọc và ghi file sử dụng **RandomAccessFile** class.
