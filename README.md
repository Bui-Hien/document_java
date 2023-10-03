- Packge:
    + cung lop cac kieu du lieu co the su dung: public, mac dinh, private.
    + cuong goi cac kieu du lieu co the su dung: public, mac ding (private khong the su dung).
    + khac goi cac kieu du lieu dung duoc: public (mac dinh, private khong dung duov).
      
- Trong lập trình hướng đối tượng:
  + Các thành viên bình thường là thành viên thuộc về đối tượng.
  + Các thành viên tĩnh (static) là thành viện thuộc về lớp.

- final trong java:
  + khong the thay doi o nho trong ram khi tao bien.
  + trong class khong ke thua.
  + trong bien la constant.
 
- Wrapper class:
  + các lớp bao không thể thay đổi được(Immutable class).
  + các lớp bao là final.
  + tất cả các phương thức của lớp bao đều là static.
  + tất cả các lớp bào trừ lớp Character và Boolean là kế thừa từ lớp Number.
  + Boolean và Character là kế thừa trực tiếp từ lớp Object.
  
- Java không có lạp trồng toán tử.

- String:
  + String là một immutable, sau khi tạo ra chỉ có thể dùng và không thể thay đổi giá trị được.
  + Các hàm thay đổi gía trị trong String bản chất là tạo ra các String mới.
- String Pool: khi khởi tạo giá trị trong 'string pool' thì hàm khởi tạo sẽ xo sánh nếu trong 'string pool' đã có giá trị khởi tạo thì sẽ tham chiếu đến gía trị đó trong 'string pool', nếu không có sẽ khởi tạo giá trị mới.
  + String s1 = "Fresher";
  + String s2 = "Fresher";
  + String s3 = "Academy";
  + String s4 = new String("Fresher");
    + s1, s2, s3 được lưu trong String Pool;
    + s4 được lưu trong heap.
- Quản lý bộ nhớ trong java:
  + trong Java có hai loại bộ nhớ chính:
    + Bộ nhớ heap: lưu trữ các dữ liệu được cấp phát cho các tham chiếu.
    + Bộ nhớ stack: lưu trữ các tham chiếu ( ~địa chỉ các con trỏ) và cá dữ liệu nguyên thủy.
  + ví dụ:
    + String s = new String("Hello"); // chuỗi "Hello" được lưu trên bộ nhớ "heap",  s được lưu bên "stack" và lưu địa chỉ trỏ đến chuỗi "Hello".
    + String x = new String("Hello"); // chuỗi "Hello" được lưu trên bộ nhớ "heap" và khác địa chỉ với chuỗi "Hello" của đối tượng "s".
    + String x1 = x; // x1 được tham chiếu đến địa chỉ x không tạo ra đối tượng mới.
    + s==x; //false
    + x1=x; // true
    + x1=x; // false vì x1 = "Hello"; cấp phát bộ nhớ mới và tạo đối tượng mới.


- Trong java chỉ có tham trị.
  + ví dụ:
  + public static void swap(Integer integer1, Integer integer2)
  + {
    + Integer temp = integer1;
    + integer1 = integer2;
    + integer2 = temp;
  + }
    + befor:
      + temp, integer1 -> 'giá trị x';
      + integer2 -> 'giá trị y';
    + after:
      + temp, integer2 -> 'giá trị x';
      +  integer1 -> 'giá trị y';
     
- Interface:
  + các phương thúc trong interface đều là public, abstract;
  + các thuộc tính trong interface đều là final;
  + nếu một lớp implements lại interface mà không override thì lớp đó thành abstract;
- Collection:
  	- List:
  		+List cho phép lưu trữ dữ liệu trùng lặp, truy cập dữ liệu dựa theo chỉ số là vị trí mà chúng ta cần cúng được coi như 'Array' có các API phong phú hơn vào không bị fixsize như 'Array'.
		+ List là 1 interface có 3 class con của Líst là Vector, ArrayLít, LinkedList:
  		+ Vector và ArrayList có thể hình dung như các Arry thuần túy có thẻ thay đổi kích thước, truy xuất phần tử dễ ràng, khi khi khởi tạo được set 1 số lượng phần tử nhất định khi đầy thì Vector sẽ được 'double' kích thước, ArrayList thì chỉ được tăng 50% kích thước.
  	 	+ LinkedList: addg , remove tốt hơn như các thao tác 'get' dữ liệu tệ rất là nhiều.
  	- Set không có thứ tự và không thể trùng lặp, có 3 class con là HashSet, TreeSet, LinkedHashSet:
  	- Map ánh xạ (key and value).
 
- Thead:
  	+ start: bắt đầu luồng.
  	+ stop: kết thúc luồng (không thể sart lại luồng phải khởi tạo lại luồng).
  	+ sleep(value): tạm dừng luồng với value mini giây.
  	+ join: sửa lý tuần tự khi gặp join thì thực hiện xong hàm mới xử lý tiếp.
