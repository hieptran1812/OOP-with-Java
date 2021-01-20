## Creating Tasks and Threads

*Một task class phải implement **Runnable** interface. Một task phải được chạy từ một thread.*

Một task là một object. Để tạo task, bạn phải định nghĩa một class cho task, 
lớp này sẽ implement interface **Runnable**. Inferace Runnable khá đơn giản. 
Tất cả những gì nó chứa là phương thức run ().
Bạn cần implement phương thức này để cho hệ thống biết luồng của bạn sẽ chạy như thế nào.

