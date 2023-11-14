
# [JAVA] - BUỔI 4: MỌI THỨ ĐỀU LÀ ĐỐI TƯỢNG
- [\[JAVA\] - BUỔI 4: MỌI THỨ ĐỀU LÀ ĐỐI TƯỢNG](#java---buổi-4-mọi-thứ-đều-là-đối-tượng)
  - [Tính đóng gói trong Java](#tính-đóng-gói-trong-java)
  - [Tính kế thừa trong Java](#tính-kế-thừa-trong-java)
    - [Tại sao nên sử dụng tính kế thừa trong Java](#tại-sao-nên-sử-dụng-tính-kế-thừa-trong-java)
    - [Các thuật ngữ](#các-thuật-ngữ)
    - [Cú pháp](#cú-pháp)
    - [Các kiểu kế thừa trong Java](#các-kiểu-kế-thừa-trong-java)
      - [Ví dụ về đơn kế thừa](#ví-dụ-về-đơn-kế-thừa)
      - [Ví dụ về kế thừa nhiều cấp](#ví-dụ-về-kế-thừa-nhiều-cấp)
      - [Ví dụ về kế thừa thứ bậc](#ví-dụ-về-kế-thừa-thứ-bậc)
  - [Tính đa hình trong Java](#tính-đa-hình-trong-java)
    - [Đa hình lúc runtime trong java](#đa-hình-lúc-runtime-trong-java)
      - [Upcasting là gì?](#upcasting-là-gì)
      - [Ví dụ về đa hình lúc runtime trong java](#ví-dụ-về-đa-hình-lúc-runtime-trong-java)
      - [Đa hình lúc runtime trong Java với thành viên dữ liệu](#đa-hình-lúc-runtime-trong-java-với-thành-viên-dữ-liệu)
      - [Đa hình lúc runtime trong Java với kế thừa nhiều tầng](#đa-hình-lúc-runtime-trong-java-với-kế-thừa-nhiều-tầng)

## Tính đóng gói trong Java
Tính đóng gói hay tính bao đóng (Encapsulation) là một trong bốn tính chất cơ bản của lập trình hướng đối tượng trong Java.

Tính đóng gói là kỹ thuật ẩn giấu thông tin không liên quan và hiện thị ra thông liên quan. Mục đích chính của đóng gói trong java là giảm thiểu mức độ phức tạp phát triển phần mềm.
![Markdown](https://gpcoder.com/wp-content/uploads/2017/11/encapsulation.png)

Tính bao đóng trong Java là một tiến trình đóng gói code và dữ liệu lại với nhau vào trong một đơn vị unit đơn. Chúng ta có thể tạo một lớp được bao đóng hoàn toàn trong Java bằng việc tạo tất cả thành viên dữ liệu của lớp là private. Bây giờ, chúng ta sử dụng phương thức setter và getter để thiết lập và lấy dữ liệu trong nó.

Tính bao đóng là kỹ thuật tạo một trường của lớp private và cung cấp khả năng truy cập trường này qua các phương thức pullic. Nếu một trường được khai báo là private, nó không thể được truy cập bởi bên ngoài lớp, do đó có thể che dấu các trường có lớp này. Vì lý do này, tính bao đóng được ám chỉ như việc dấu dữ liệu (data hiding).

**Để đạt được đóng gói trong Java chúng ta cần:**
* Khai báo các biến của một lớp là private.
* Cung cấp phương thức setter và getter là public để có thể sửa đổi và xem các giá trị biến.

Ví dụ:

```java
public class Sach {
    private String tieuDe;
    private String tacGia;
    private String theLoai;
    private String ngayXuatban;
    public void setTieuDe(String tieuDe) {
        this.tieuDe = tieuDe;
    }

    public void setTacGia(String tacGia) {
        this.tacGia = tacGia;
    }

    public void setTheLoai(String theLoai) {
        this.theLoai = theLoai;
    }

    public void setNgayXuatban(String ngayXuatban) {
        this.ngayXuatban = ngayXuatban;
    }
    public String getTieuDe() {
        return tieuDe;
    }

    public String getTacGia() {
        return tacGia;
    }

    public String getTheLoai() {
        return theLoai;
    }

    public String getNgayXuatban() {
        return ngayXuatban;
    }
}
```
**Lưu ý Quy ước đặt tên:**

Quy ước đặt tên biến trong Java: từ đầu tiên là viết thường, từ thứ hai trở đi viết hoa chữ cái đầu tiên ở mỗi từ. 

Quy ước đặt tên phương thức getter và setter như sau:
* **Getter**: bắt đầu bằng chữ get + viết hoa chữ đầu tiên tất cả các từ (viết hoa chữ đầu tiên của tên biến).
* **Setter**: bắt đầu bằng chữ set + viết hoa chữ đầu tiên tất cả các từ (viết hoa chữ đầu tiên của tên biến).
**Lợi ích của đóng gói trong java**

* Tất cả các trường (field) của lớp có có chế độ chỉ đọc (read-only) hoặc chỉ ghi (write-only), tức là chỉ có hàm getter hoặc setter.
* Một lớp có thể có toàn bộ điều khiển thông qua những gì được lưu giữ trong các trường (field) của nó.
* Người sử dụng của class không biết cách các class lưu trữ dữ liệu. Một class có thể thay đổi kiểu dữ liệu của một trường và người dùng class không cần sự thay đổi trong code.
## Tính kế thừa trong Java
Tính kế thừa trong Java là một cơ chế trong đó một đối tượng có được tất cả các thuộc tính và hành vi của một đối tượng cha. Đây là một phần quan trọng của OOPs (Hệ thống lập trình hướng đối tượng).

Ý tưởng đằng sau tính kế thừa trong Java là việc bạn có thể tạo các class mới được dựa trên các class đã có sẵn. Khi bạn kế thừa từ một class có sẵn, bạn có thể tái sử dụng các phương thức và trường của class cha. Hơn nữa, bạn có thể thêm các phương thức và trường mới trong class hiện tại.

Tính kế thừa thể hiện quan hệ IS-A, còn gọi là quan hệ cha-con.
### Tại sao nên sử dụng tính kế thừa trong Java
* Để thực hiện Ghi đè phương thức (nhờ thế mà có thể đạt được tính đa hình trong runtime).
* Để tái sử dụng code.
### Các thuật ngữ
* Class: Class là một tập hợp các đối tượng có chung tính chất. Nó là một bản mẫu hay một bản thiết kế mà từ đó các đối tượng được tạo ra.
* Class con (Sub class/Child class): Class con là một class kế thừa từ class khác. Một số thuật ngữ khác để gọi class con trong tiếng Anh là “derived class”, “extended class”, hay “child class”.
* Class cha (Super class/Parent class): Class cha là class được class con kế thừa. Một số thuật ngữ khác để gọi class cha trong tiếng Anh là “base class” hay “parent class”.
* Tính tái sử dụng: Như tên gọi, tính tái sử dụng là cơ thế cho phép bạn sử dụng lại các trường và phương thức của class hiện tại khi bạn tạo một class mới. Bạn có thể sử dụng cùng trường và phương thức đã được định nghĩa ở class cha.
### Cú pháp
```java
class Subclass-name extends Superclass-name  
{  
   //methods and fields  
}  
```
Từ khoá extends chỉ ra rằng bạn đang tạo một class mới từ một class có sẵn. “extends” nghĩa là mở rộng các chức năng.

Trong thuật ngữ của Java, class được kế thừa gọi là class cha (parent class/super class), và class mới được gọi là class con (child class/subclass).

Ví dụ:
```java
class Employee {  
   float salary = 40000;  
}  


class Programmer extends Employee {  
   int bonus = 10000;
   public static void main(String args[]) {  
      Programmer p = new Programmer();
      System.out.println("Programmer salary is:" + p.salary);  
      System.out.println("Bonus of Programmer is:" + p.bonus);  
   }
}
```
Kết quả:
> Programmer salary is:40000.0
> 
> Bonus of programmer is:10000

Ở ví dụ trên, đối tượng Programmer có thể truy cập trường của class của nó cũng như của Employee class, đây là tái sử dụng code.
### Các kiểu kế thừa trong Java

Trên cơ sở class, có ba kiểu kế thừa trong Java: đơn kế thừa, kế thừa nhiều cấp, kế thừa thứ bậc.

![Markdown](https://media.techmaster.vn/api/static/c6gsfifk0cmj7hbgjgeg/EBBRcItv)

Chú ý: Đa kế thừa trong Java không được hỗ trợ thông qua class.

#### Ví dụ về đơn kế thừa

Đơn kế thừa là khi một class kế thừa một class khác. Ở ví dụ dưới đây, Dog class thừa kế Animal class vì thế đây là đơn kế thừa

```java
class Animal {  
   void eat() {System.out.println("eating...");}  
} 


class Dog extends Animal {  
   void bark() {System.out.println("barking...");}  
}  


class TestInheritance {  
   public static void main(String args[]) {  
      Dog d = new Dog();
      d.bark();  
      d.eat();  
   }
}

```
Kết quả:
```
barking...
eating...
```
#### Ví dụ về kế thừa nhiều cấp
Kế thừa nhiều cấp là khi có một chuỗi kế thừa. Ở ví dụ dưới đây, BabyDog class kế thừa Dog class mà class này lại kế thừa Animal class, vì thế đây là kế thừa nhiều cấp.

```java
class Animal {  
   void eat() {System.out.println("eating...");}  
} 


class Dog extends Animal {  
   void bark() {System.out.println("barking...");}  
}


class BabyDog extends Dog {  
   void weep() {System.out.println("weeping...");}  
}  


class TestInheritance2 {  
   public static void main(String args[]) {  
      BabyDog d = new BabyDog();
      d.weep();
      d.bark();  
      d.eat();  
   }
}
```
Kết quả:
```
weeping...
barking...
eating...
```
#### Ví dụ về kế thừa thứ bậc
Kế thừa thứ bậc là khi có từ hai class trở lên kế thừa một class. Ở ví dụ dưới đây, các class Dog và Cat kế thừa Animal class, vì thế đây là kế thừa thứ bậc.

```java
class Animal {  
   void eat() {System.out.println("eating...");}  
} 


class Dog extends Animal {  
   void bark() {System.out.println("barking...");}  
}


class Cat extends Animal {  
   void meow() {System.out.println("meowing...");}  
}


class TestInheritance3 {  
   public static void main(String args[]) {  
      Cat c=new Cat();  
      c.meow();  
      c.eat();
   }
}
```
Kết quả:
```
meowing...
eating…
```
## Tính đa hình trong Java
**Tính đa hình** là khả năng một đối tượng có thể thực hiện một tác vụ theo nhiều cách khác nhau.

Đối với tính chất này, nó được thể hiện rõ nhất qua việc gọi phương thức của đối tượng. Các phương thức hoàn toàn có thể giống nhau, nhưng việc xử lý luồng có thể khác nhau. Nói cách khác: Tính đa hình cung cấp khả năng cho phép người lập trình gọi trước một phương thức của đối tượng, tuy chưa xác định đối tượng có phương thức muốn gọi hay không. Đến khi thực hiện **(run-time)**, chương trình mới xác định được đối tượng và gọi phương thức tương ứng của đối tượng đó. Kết nối trễ giúp chương trình được uyển chuyển hơn, chỉ yêu cầu đối tượng cung cấp đúng phương thức cần thiết là đủ.
Trong Java, chúng ta sử dụng nạp chồng phương thức (method **overloading**) và ghi đè phương thức (method **overriding**) để có tính đa hình.

**Nạp chồng (Overloading)**: Đây là khả năng cho phép một lớp có nhiều thuộc tính, phương thức cùng tên nhưng với các tham số khác nhau về loại cũng như về số lượng. Khi được gọi, dựa vào tham số truyền vào, phương thức tương ứng sẽ được thực hiện.

**Ghi đè (Overriding)**: là hai phương thức cùng tên, cùng tham số, cùng kiểu trả về nhưng thằng con viết lại và dùng theo cách của nó, và xuất hiện ở lớp cha và tiếp tục xuất hiện ở lớp con. Khi dùng override, lúc thực thi, nếu lớp Con không có phương thức riêng, phương thức của lớp Cha sẽ được gọi, ngược lại nếu có, phương thức của lớp Con được gọi.
### Đa hình lúc runtime trong java
**Đa hình lúc runtime** là quá trình gọi phương thức đã được ghi đè trong thời gian thực thi chương trình. Trong quá trình này, một phương thức được ghi đè được gọi thông qua biến tham chiếu của một lớp cha.

#### Upcasting là gì?
Khi biến tham chiếu của lớp cha tham chiếu tới đối tượng của lớp con, thì đó là Upcasting. Ví dụ:
```java
class A{} 
class B extends A{} 
A a=new B();//upcasting  
```
#### Ví dụ về đa hình lúc runtime trong java
Chúng ta tạo hai lớp Bike và Splendar. Lớp Splendar kế thừa lớp Bike và ghi đè phương thức run() của nó. Chúng ta gọi phương thức run bởi biến tham chiếu của lớp cha. Khi nó tham chiếu tới đối tượng của lớp con và phương thức lớp con ghi đè phương thức của lớp cha, phương thức lớp con được gọi lúc runtime.
Khi việc gọi phương thức được quyết định bởi JVM chứ không phải Compiler, vì thế đó là đa hình lúc runtime.
```java
class Bike {
    void run() {
        System.out.println("running");
    }
}
 
public class Splender extends Bike {
    void run() {
        System.out.println("running safely with 60km");
    }
 
    public static void main(String args[]) {
        Bike b = new Splender();// upcasting
        b.run();
    }
}
```
Kết quả:
> running safely with 60km
#### Đa hình lúc runtime trong Java với thành viên dữ liệu
Phương thức bị ghi đè không là thành viên dữ liệu, vì thế đa hình tại runtime không thể có được bởi thành viên dữ liệu. Trong ví dụ sau đây, cả hai lớp có một thành viên dữ liệu là speedlimit, chúng ta truy cập thành viên dữ liệu bởi biến tham chiếu của lớp cha mà tham chiếu tới đối tượng lớp con. Khi chúng ta truy cập thành viên dữ liệu mà không bị ghi đè, thì nó sẽ luôn luôn truy cập thành viên dữ liệu của lớp cha.

***Quy tắc: Đa hình lúc runtime không thể xảy ra với thành viên dữ liệu.***
```java
class Bike{ 
 int speedlimit=90; 
} 
class Honda3 extends Bike{ 
 int speedlimit=150; 
   
 public static void main(String args[]){ 
  Bike obj=new Honda3(); 
  System.out.println(obj.speedlimit);//90 
} 
```
Kết quả:
>90
#### Đa hình lúc runtime trong Java với kế thừa nhiều tầng
Ví dụ 1:
```java
class Animal {
    void eat() {
        System.out.println("eating");
    }
}
 
class Dog extends Animal {
    void eat() {
        System.out.println("eating fruits");
    }
}
 
class BabyDog extends Dog {
    void eat() {
        System.out.println("drinking milk");
    }
 
    public static void main(String args[]) {
        Animal a1, a2, a3;
        a1 = new Animal();
        a2 = new Dog();
        a3 = new BabyDog();
        a1.eat();
        a2.eat();
        a3.eat();
    }
}
```
Kết quả:
```
eating
eating fruits
drinking Milk
```
Ví dụ 2:
```java
class Animal {
    void eat() {
        System.out.println("animal is eating...");
    }
}
 
class Dog extends Animal {
    void eat() {
        System.out.println("dog is eating...");
    }
}
 
class BabyDog1 extends Dog {
    public static void main(String args[]) {
        Animal a = new BabyDog1();
        a.eat();
    }
}
```
Kết quả:
>Dog is eating

Vì BabyDog1 không ghi đè phương thức eat(), nên phương thức eat() của lớp Dog được gọi.



