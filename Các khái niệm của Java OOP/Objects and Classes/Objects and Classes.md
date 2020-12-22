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
Ngoài ra một class cung cấp các method thuộc loại đặc biệt, gọi là *constructors*, được gọi để khởi tạo một object mới.
