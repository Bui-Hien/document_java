- Packge:
    + cung lop cac kieu du lieu co the su dung: public, mac dinh, private.
    + cuong goi cac kieu du lieu co the su dung: public, mac ding (private khong the su dung).
    + khac goi cac kieu du lieu dung duoc: public (mac dinh, private khong dung duov).
      
- Trong lập trình hướng đối tượng:
  + Các thành viên bình thường là thành viên thuộc về đối tượng.
  + Các thành viên tĩnh (static) là thành viện thuộc về lớp.

- final trong java:
  + khong the thay doi o nho trong ram khi tao bien.
 
- lớp bao:
  + các lớp bao không thể thay đổi được.
  + các lớp bao là final.
  + tất cả các phương thức của lớp bao đều là static.
  + tất cả các lớp bào trừ lớp Character và Boolean là kế thừa từ lớp Number.
  + Boolean và Character là kế thừa trực tiếp từ lớp Object.
  
- Java không có lạp trồng toán tử.

- Quản lý bộ nhớ trong java:
  + trong Java có hai loại bộ nhớ chính:
     + Bộ nhớ heap: lưu trữ các dữ liệu được cấp phát cho các tham chiếu.
     + Bộ nhớ stack: lưu trữ các tham chiếu ( ~địa chỉ các con trỏ) và cá dữ liệu nguyên thủy.
    + ví dụ:
          + String s= new String("Hello"); // chuỗi "Hello" được lưu trên bộ nhớ "heap",  s được lưu bên "stack" và lưu địa chỉ trỏ đến chuỗi "Hello".
          
      

    
