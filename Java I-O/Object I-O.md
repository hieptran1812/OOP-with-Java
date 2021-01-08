# Object I/O

***ObjectInputStream/ObjectOutputStream** classes được dùng để đọc/ghi object một cách tuần tự.*

**DataInputStream/DataOutputStream** cho phép thực hiện I/O với dữ liệu nguyên thủy. **ObjectInputStream/ObjectOutputStream** cho phép thực hiện I/O cho object không chỉ dữ liệu nguyên thủy như trên. Vì **ObjectInputStream/ObjectOutputStream** bao gồm tất cả các chức năng của **DataInputStream/DataOutputStream** nên ta có thể thay thế hoàn toàn **DataInputStream/DataOutputStream** bằng **ObjectInputStream/ObjectOutputStream**.

## Serializable Interface

Không phải mọi object đều có thể ghi vào một luồng đầu ra (output stream). Object mà được ghi được như vậy được gọi là *tuần tự hóa (serializable)*. Một serializable object là một instance của **java.io.Serializable** interface, do đó class của object phải implement **Serializable**.

Ví dụ cho dễ hiểu nhé :)) Giả sử mình tạo một class Person như dưới

```java
package Serializable;

/**
 *
 * @author hiept
 */
import java.io.File;
import java.io.FileOutputStream;
import java.io.IOException;
import java.io.ObjectOutputStream;

/**
 *
 * @author hiept
 */
public class Person {
    private int id;

    public int getId() {
        return id;
    }

    public void setId(int id) {
        this.id = id;
    }

    public Person(int id) {
        this.id = id;
    }

    public static void main(String[] args) throws IOException {
        Person p = new Person(1);
        
        File file = new File("demo.txt");
        if(!file.exists()){
            file.createNewFile();
        }
        
        FileOutputStream fileOutputStream = new FileOutputStream(file); //Luu xuong file
        
        ObjectOutputStream objectOutputStream = new ObjectOutputStream(fileOutputStream); //Luu doi tuong xuong file
        
        objectOutputStream.writeObject(p);
        fileOutputStream.close();
    }
}

//Chạy code này bạn sẽ bị lỗi như sau:
/* Exception in thread "main" java.io.NotSerializableException: Serializable.Person
	at java.base/java.io.ObjectOutputStream.writeObject0(ObjectOutputStream.java:1185)
	at java.base/java.io.ObjectOutputStream.writeObject(ObjectOutputStream.java:349)
	at Serializable.Person.main(Person.java:49)
D:\Synthetic\TAI_LIEU_TREN_LOP\Junior\LTHDT\Test_Knowledge\nbproject\build-impl.xml:1341: The following error occurred while executing this line:
D:\Synthetic\TAI_LIEU_TREN_LOP\Junior\LTHDT\Test_Knowledge\nbproject\build-impl.xml:936: Java returned: 1
BUILD FAILED (total time: 0 seconds) */
```

Để fix lỗi, bạn cần implements **Serializable** interface vào class Person. Tưởng tượng như này, khi 
