# Multithreading in Java

## Giới thiệu

Đa luồng (multithreading) là một tính năng của Java cho phép thực hiện đồng thời hai hoặc nhiều phần của một chương trình để sử dụng tối đa tài nguyên CPU. Mỗi phần của chương trình như vậy được gọi là một luồng (thread). Thread là một đơn vị nhỏ nhất của tiến trình.

Như ta đã biết, một chương trình bao gồm rất nhiều task cần phải chạy đồng thời (điều này rất dễ thấy trong các game). Một *thread* cung cấp cơ chế để chạy một task. Để mường tượng rõ hơn quá trình này, hãy xem hình dưới :)))

<p align = "center"><img src = "https://github.com/hieptran1812/OOP-with-Java-PTIT/blob/main/Image/Thread.PNG"></p>

Trong các hệ thống một bộ xử lý (single - processor systems), như trong hình 32.1b, nhiều luồng chia sẻ thời gian sử dụng CPU, được gọi là *time sharing* và hệ điều hành chịu trách nhiệm lập lịch (scheduling) và phân bổ tài nguyên (allocating resources) cho chúng. Sự sắp xếp này là thực tế vì hầu hết thời gian CPU ở chế độ nhàn rỗi :v Ví dụ, nó không làm gì trong khi chờ người dùng nhập dữ liệu. 

Đa luồng làm cho chương trình của bạn phản hồi và tương tác tốt hơn cũng như nâng cao hiệu suất. Ví dụ: một trình xử lý văn bản tốt cho phép bạn in hoặc lưu một tệp trong khi bạn đang nhập văn bản. Trong một số trường hợp, các chương trình đa luồng chạy nhanh hơn các chương trình đơn luồng ngay cả trên các hệ thống xử lý đơn. Java cung cấp hỗ trợ đặc biệt tốt cho việc tạo và chạy các luồng cũng như khóa tài nguyên (locking resources) để tránh xung đột. 

Bạn có thể tạo các luồng bổ sung để chạy các tác vụ đồng thời trong chương trình. Trong Java, mỗi tác vụ là một thể hiện (instance) của giao diện (interface) **Runnable**, còn được gọi là *Runnable object*. Một luồng về cơ bản là một đối tượng tạo điều kiện cho việc thực hiện một tác vụ.

## Ưu điểm của đa luồng trong Java

1. Nó không chặn người sử dụng vì các luồng là độc lập và bạn có thể thực hiện nhiều công việc cùng một lúc.
2. Bạn có thể thực hiện nhiều hoạt động với nhau để tiết kiệm thời gian.
3. Luồng là độc lập vì vậy nó không ảnh hưởng đến luồng khác nếu ngoại lệ xảy ra trong một luồng duy nhất.

## Qua phần này bạn sẽ học được

1. Có cái nhìn tổng quát về multithreading
2. Phát triển các task class bằng cách implementing **Runnable** Interface
3. 


