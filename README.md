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

  - note
        String a = new String("Hello");
        String b = new String("Hello");
        String c = a;
        System.out.println(a==b); //false vì tạo hai Object mới
        System.out.println(a==c); //true vì cùng trá trị và a,c cùng Object khác vị trí ô nhớ;


    
