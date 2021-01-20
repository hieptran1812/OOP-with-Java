## Creating Tasks and Threads

*Một task class phải implement **Runnable** interface. Một task phải được chạy từ một thread.*

Một task là một object. Để tạo task, bạn phải định nghĩa một class cho task, 
lớp này sẽ implement interface **Runnable**. Inferace **Runnable** khá đơn giản. 
Tất cả những gì nó chứa là phương thức run ().
Bạn cần implement phương thức này để cho hệ thống biết luồng của bạn sẽ chạy như thế nào.

<p align = "center"><img src = "https://github.com/hieptran1812/OOP-with-Java-PTIT/blob/main/Image/runnable%20interface.PNG"></p>

Ảnh trên minh họa việc phát triển một task class.

Sau khi định nghĩa một **TaskClass**, bạn có thể tạo một task như sau:

```Java
TaskClass task = new TaskClass(...);
```

Một task phải được thực thi trong một thread. **Thread** class bao gồm constructors để tạo thread và nhiều phương thức hữu ích để điều khiển thread. Để tạo thread cho một task, sử dụng:

```Java
Thread thread = new Thread(task);
```

Sau đó bạn có thể gọi phương thức **start()** để nói với JVM rằng thread đã sẵn sàng để chạy:

```Java
thread.start();
```

JVM sẽ thực thi task bằng cách gọi phương thức **run()** của task. 

Tớ sẽ thực hiện demo để các bạn hiểu rõ hơn với yêu cầu như sau: 

Tạo một chương trình tạo 3 task và 3 thread để chạy các nhiệm vụ 
* Task đầu in chữ a 100 lần
* Task thứ 2 in chữ b 100 lần
* Task thứ 3 in số từ 1 tới 100

Code như sau:

```Java
public class TaskThreadDemo {
  public static void main(String[] args) {
    // Create tasks
    Runnable printA = new PrintChar('a', 100);
    Runnable printB = new PrintChar('b', 100);
    Runnable print100 = new PrintNum(100);

    // Create threads
    Thread thread1 = new Thread(printA);
    Thread thread2 = new Thread(printB);
    Thread thread3 = new Thread(print100);

    // Start threads
    thread1.start();
    thread2.start();
    thread3.start();
  }
}

// The task for printing a character a specified number of times
class PrintChar implements Runnable {
  private char charToPrint; // The character to print
  private int times; // The number of times to repeat
  /** Construct a task with a specified character and number of
  * times to print the character
  */
  public PrintChar(char c, int t) {
    charToPrint = c;
    times = t;
  }
  
  @Override /** Override the run() method to tell the system
  * what task to perform
  */
  public void run() {
    for (int i = 0; i < times; i++) {
      System.out.print(charToPrint);
    }
  }
}

// The task class for printing numbers from 1 to n for a given n
class PrintNum implements Runnable {
  private int lastNum;
  /** Construct a task for printing 1, 2, ..., n */
  public PrintNum(int n) {
    lastNum = n;
  }
  @Override /** Tell the thread how to run */
  public void run() {
    for (int i = 1; i <= lastNum; i++) {
      System.out.print(" " + i);
    }
  }
}
```

Khi chạy chương trình này, 3 thread sẽ chia sẻ tài nguyên CPU và thực hiện task. Kết quả như sau:

<p align = "center"><img src = "https://github.com/hieptran1812/OOP-with-Java-PTIT/blob/main/Image/Capture.PNG"></p>

## Thread Class

* **Thread** class bao gồm constructor để tạo thread cho task và các phương thức để điều khiển thread.

<p align = "center"><img src = "https://github.com/hieptran1812/OOP-with-Java-PTIT/blob/main/Image/thread%20extend.PNG"></p>

**Note**: 

Vì **Thread** class đã implement **Runnable**, bạn có thể định nghĩa 1 class kế thừa (extend) **Thread** và implement phương thức **run** như hình dưới, sau đó tạo một object từ class và gọi phương thức **start** của nó trong client program để chạy thread.

<p align = "center"><img src = "https://github.com/hieptran1812/OOP-with-Java-PTIT/blob/main/Image/define%20thread.PNG"></p>

Tuy nhiên, cách tiếp cận này không được khuyến khích vì nó **trộn lẫn** task và cơ chế của việc chạy task. Tách task từ thread được khuyến khích hơn trong thiết kế.

## Thread class và Runnable Interface

1. Nếu chúng ta extend lớp Thread, lớp của chúng ta không thể extend bất kỳ lớp nào khác vì Java không hỗ trợ đa kế thừa. Nhưng nếu chúng ta implement interface Runnable, lớp của chúng ta vẫn có thể extend các lớp cơ sở khác. 

2. Chúng ta có thể có được chức năng cơ bản của một thread bằng cách extend thread vì nó cung cấp một số phương thức có sẵn như yield(), interrupt(), v.v. không có sẵn trong interface Runnable.
