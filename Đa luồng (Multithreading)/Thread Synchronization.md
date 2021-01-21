# Thread Synchronization

*Thread Synchronization là điều phối việc thực thi các luồng phụ thuộc.*

Tài nguyên được chia sẻ có thể bị hỏng nếu nó được truy cập đồng thời bởi nhiều thread.
Hãy thử tìm hiểu ví dụ sau:

Giả sử rằng bạn tạo và khởi chạy 100 thread, mỗi thread sẽ thêm một xu vào tài khoản.
Định nghĩa một class có tên **Account** để thể hiện object tài khoản, một class có tên **AddAPennyTask** 
để thêm một xu vào tài khoản và một lmain class tạo và khởi chạy các thread. Các mối quan hệ
của các class này được thể hiện như hình dưới.

<p align = "center"><img src = "https://github.com/hieptran1812/OOP-with-Java-PTIT/blob/main/Image/synchronization_intro.PNG"></p>

```java
import java.util.concurrent.*;

public class AccountWithoutSync {
    private static Account account = new Account();
    public static void main(String[] args) {
      ExecutorService executor = Executors.newCachedThreadPool();
      // Create and launch 100 threads
      for (int i = 0; i < 100; i++) {
        executor.execute(new AddAPennyTask());
      }
      executor.shutdown();

      // Wait until all tasks are finished
      while (!executor.isTerminated()) {
      }

      System.out.println("What is balance? " + account.getBalance());
   }

 // A thread for adding a penny to the account
 private static class AddAPennyTask implements Runnable {
     public void run() {
        account.deposit(1);
     }
   }
  
   // An inner class for account
  private static class Account {
    private int balance = 0;
  
    public int getBalance() {
      return balance;
    }
  
    public void deposit(int amount) {
      int newBalance = balance + amount;
  
      // This delay is deliberately added to magnify the
      // data-corruption problem and make it easy to see.
      try {
        Thread.sleep(5);
      }
      catch (InterruptedException ex) {
      }
  
      balance = newBalance;
    }
  }
}
```
Okay! Output là gì :)) Đáng ra nó phải là 100 vì mình đã nạp 100 xu vào nhưng không phải, kết quả có thể là một sô bất kì nào nhỏ hơn 100.
Điều này chứng tỏ sự cố hỏng dữ liệu (data-corruption) xảy ra khi tất cả các thread có quyền truy cập đồng thời vào cùng một nguồn dữ liệu.

| Step        | Balance     | Task 1    |Task 2   |
| :---:        |    :----:   | :----:   |  :---: |
| 1       |    0   | newBalance = balance + 1;   |   |
| 2        |    0   |    |  newBalance = balance + 1; |
| 3       |    1   |   balance = newBalance; |   |
| 4        |    1   |    |  balance = newBalance; |

Tại bước 1, Task 1 có nhiệm vụ nhận số dư từ tài khoản. Tại bước 2, Task 2 nhận số dư giống như từ tài khoản.
Trong bước 3, Task 1 ghi số dư mới vào tài khoản. Tại bước 4, Task 2 ghi số dư mới vào tài khoản.

Vấn đề ở đây là, Task 1 không làm cái gì cả bởi vì trong bước 4, Task 2 ghi đè lên kết quả của Task 1.
Đây là một vấn đề phổ biến do Task 1 và Task 2 đang cùng truy cập một tài nguyên chung do đó sẽ gây ra
xung đột. Vấn đề này còn được gọi là [*race condition*](https://bizflycloud.vn/tin-tuc/race-condition-la-gi-lam-sao-de-khai-thac-20180116193609705.htm) trong chương trình đa luồng. Một class được gọi là
một *luồng an toàn (thread-safe) nếu một object của class không gây ra tình trạng race condition khi
đang có nhiều luồng. Như code trên thì lớp **Account** không phải thread-safe.

## Synchronized keyword

Để tránh race conditions, ta cần ngăn nhiều thread cùng truy cập đồng thời vào một phần quan trọng 
của chương trình, gọi là *critical region*. 
Critical region trong code trên là toàn bộ phương thức **deposit**. 
Bạn có thể sử dụng từ khóa **synchronized** để đồng bộ hóa method sao cho chỉ một thread có thể truy cập method tại một thời điểm. 
Có một số cách để khắc phục sự cố trong code trên. 
Một cách tiếp cận là làm cho **Account** thread-safe bằng cách thêm từ khóa **synchronized** trong phương thức 
**deposit** ở dòng 38, như sau:

```Java
public synchronized void deposit(double amount)
```

Quan sát hình dưới,

<p align = "center"><img src = "https://github.com/hieptran1812/OOP-with-Java-PTIT/blob/main/Image/sync_2.PNG"></p>

Một synchronized method có được một khóa trước khi nó thực thi. 
Khóa là một cơ chế sử dụng riêng một tài nguyên. Trong trường hợp là method, 
khóa nằm trên object mà method được gọi. 
Trong trường hợp là một static method, khóa nằm trên class. 
Nếu một thread gọi một synchronized method (hoặc static method) 
trên một object, thì khóa của object (hoặc class) đó sẽ được lấy trước,
sau đó method được thực thi và cuối cùng khóa được giải phóng. 
Một thread khác gọi cùng một method của object (hoặc class) đó bị chặn cho đến khi khóa được giải phóng. 
Với method **deposit** được đồng bộ hóa, kịch bản trước đó không thể xảy ra. Nếu Task 1 truy cập method, 
Task 2 sẽ bị chặn cho đến khi Tsk 1 kết thúc method.

## Synchronizing Statements


