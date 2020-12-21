# Abstract Classes

**Một abstract class không thể được sử dụng để tạo một objects. Một abstract class bao gồm các abstract method được cài đặt tại các subclass cụ thể.**

Trong hệ thống phân cấp kế thừa (inheritance hierarchy), class trở nên cụ thể (specific) hơn với mỗi subclass mới. Ví dụ class cha *hình học* có 2 class con là class *hình
chữ nhật* và class *hình tam giác*, class *hình tam giác* lại có 2 class con là class *tam giác cân* và class *tam giác vuông*,... chúng ngày càng cụ thể hơn. Nếu ta 
di chuyển từ một class con ngược trở lại superclass, class trở nên tổng quát (general) và ít cụ thể hơn. Việc thiết kế class nên đảm bảo một superclass phải bao gồm
các đặc trưng phổ biến (common feature) cho các subclass của nó. Đôi khi, một superclass quá trừu tượng nên không thể được sử dụng để tạo một trường hợp cụ thể
nào cả (specific instances). Những class như vậy được gọi là *abstract class*.



