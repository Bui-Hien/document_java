# Hướng Dẫn Sử Dụng Các Lệnh Cơ Bản

## Để cập nhật các gói trên Ubuntu, bạn có thể sử dụng các lệnh dưới đây:
### 1. Cập nhật danh sách gói
```bash
sudo apt update
```
### 2. Nâng cấp các gói hiện có
```bash
sudo apt upgrade
```

## Lệnh `ls` được sử dụng để liệt kê các tệp và thư mục trong hệ điều hành Linux. Dưới đây là một số tùy chọn phổ biến khi sử dụng lệnh này
```bash
ls
```
### Các tùy chọn phổ biến:

- `ls`: Hiển thị danh sách các tệp và thư mục trong thư mục hiện tại.
  
- `ls -l`: Hiển thị danh sách dưới dạng chi tiết (bao gồm quyền truy cập, chủ sở hữu, kích thước, ngày sửa đổi, v.v.).

- `ls -a`: Hiển thị tất cả các tệp, bao gồm cả tệp ẩn (những tệp bắt đầu bằng dấu chấm `.` như `.bashrc`).

- `ls -lh`: Hiển thị danh sách chi tiết và hiển thị kích thước tệp ở định dạng dễ đọc hơn (KB, MB, GB).

## Lệnh `cd` (change directory) được sử dụng để thay đổi thư mục làm việc hiện tại.
```bash
cd [path]
```
### Các tùy chọn phổ biến:

- `cd` /home/user/Documents: Di chuyển đến thư mục /home/user/Documents.
  
- `cd ..`: Quay trở lại thư mục cha của thư mục hiện tại.v.v.).

- `cd ~`: Di chuyển về thư mục gốc của người dùng hiện tại (thường là /home/username).

- `cd -`: Quay lại thư mục trước đó.


## Lệnh `clear` được sử dụng để xóa màn hình terminal, giúp người dùng làm việc dễ dàng hơn mà không bị rối bởi các dòng lệnh cũ.
```bash
clear
```

## Lệnh `mkdir` (make directory) được sử dụng để tạo thư mục mới.
```bash
mkdir [tùy chọn] tên_thư_mục
```
### Các tùy chọn phổ biến:

- `mkdir tên_thư_mục`: Tạo một thư mục mới có tên là tên_thư_mục.
  
- `mkdir -p đường_dẫn/thư_mục`: Tạo thư mục cùng với các thư mục cha (nếu chưa tồn tại).


## Lệnh `touch` được sử dụng để tạo tệp mới hoặc cập nhật thời gian sửa đổi của tệp hiện có.
```bash
touch tên_tệp
```

## Lệnh `cat` (concatenate) được sử dụng để hiển thị nội dung của một hoặc nhiều tệp, cũng như để kết hợp tệp.
```bash
cat [tùy chọn] [tên_tệp]
```
### Các tùy chọn phổ biến:

- `cat tên_tệp`: Hiển thị nội dung của tên_tệp trên màn hình.

- `cat tệp1 tệp2`: Kết hợp nội dung của tệp1 và tệp2 và hiển thị.
  
- `cat > tên_tệp`: Tạo một tệp mới và cho phép nhập nội dung vào tệp (nhấn Ctrl + D để lưu và thoát).
  
- `cat >> tên_tệp`: Thêm nội dung vào cuối tệp hiện có.

## Lệnh `echo` được sử dụng để hiển thị một chuỗi văn bản ra màn hình hoặc ghi vào tệp.
```bash
echo [tùy chọn] [chuỗi]
```
### Các tùy chọn phổ biến:

- `echo "chuỗi"`: Hiển thị chuỗi văn bản.

- `echo -n "chuỗi"`: Hiển thị chuỗi mà không xuống dòng ở cuối.
  
- `echo "chuỗi" > tên_tệp`: Ghi chuỗi vào tệp (tạo mới hoặc ghi đè).
  
- `echo "chuỗi" >> tên_tệp`: Ghi chuỗi vào cuối tệp hiện có.

## Lệnh `tail` được sử dụng để hiển thị các dòng cuối cùng của một tệp. Mặc định, tail hiển thị 10 dòng cuối cùng.
```bash
tail [tùy chọn] [tên_tệp]
```
### Các tùy chọn phổ biến:

- `tail tên_tệp`: Hiển thị 10 dòng cuối cùng của tệp tên_tệp.

- `tail -n số_dòng tên_tệp`: Hiển thị số_dòng dòng cuối cùng của tệp.
  
- `tail -f tên_tệp`: Theo dõi tệp theo thời gian thực (sử dụng cho các tệp log).


## Lệnh `grep` được sử dụng để tìm kiếm chuỗi trong tệp và hiển thị các dòng chứa chuỗi đó.
```bash
grep [tùy chọn] "chuỗi" [tên_tệp]
```
### Các tùy chọn phổ biến:

- `grep "chuỗi" tên_tệp`: Tìm kiếm chuỗi trong tên_tệp.

- `grep -i "chuỗi" tên_tệp`: Tìm kiếm không phân biệt chữ hoa chữ thường.
  
- `grep -r "chuỗi" thư_mục`: Tìm kiếm chuỗi trong tất cả các tệp trong thư mục (đệ quy).
  
- `grep -v "chuỗi" tên_tệp`: Hiển thị các dòng không chứa chuỗi.

## Lệnh `cp` được sử dụng để sao chép tệp và thư mục.
```bash
cp [tùy chọn] nguồn đích
```
### Các tùy chọn phổ biến:

- `cp tệp_nguồn tệp_đích`: Sao chép tệp_nguồn sang tệp_đích.

- `cp -r thư_mục_nguồn thư_mục_đích`: Sao chép thư mục và tất cả nội dung của nó (đệ quy).

- `cp -i tệp_nguồn tệp_đích`: Cảnh báo trước khi ghi đè lên tệp_đích nếu nó đã tồn tại.

- `cp -u tệp_nguồn tệp_đích`: Sao chép chỉ khi tệp_nguồn mới hơn tệp_đích hoặc nếu tệp_đích không tồn tại.

## Lệnh `mv` được sử dụng để di chuyển hoặc đổi tên tệp và thư mục.
```bash
mv [tùy chọn] nguồn đích
```
### Các tùy chọn phổ biến:

- `mv tệp_nguồn tệp_đích`: Di chuyển hoặc đổi tên tệp_nguồn thành tệp_đích.

- `mv thư_mục_nguồn thư_mục_đích`: Di chuyển thư_mục_nguồn đến thư_mục_đích.

- `mv -i tệp_nguồn tệp_đích`: Cảnh báo trước khi ghi đè lên tệp_đích nếu nó đã tồn tại.

- `mv -u tệp_nguồn tệp_đích`: Di chuyển chỉ khi tệp_nguồn mới hơn tệp_đích hoặc nếu tệp_đích không tồn tại.

## Lệnh `rm` được sử dụng để xóa tệp.
```bash
rm [tùy chọn] tệp
```
### Các tùy chọn phổ biến:

- `rm tệp`: Xóa tệp.

- `rm -i tệp`: Cảnh báo trước khi xóa tệp.

- `rm -r thư_mục`: Xóa thư mục và tất cả nội dung của nó (đệ quy).

- `rm -f tệp`: Xóa tệp mà không cần hỏi xác nhận, ngay cả khi tệp không tồn tại.

## Lệnh `rmdir` được sử dụng để xóa thư mục rỗng.
```bash
rmdir [tùy chọn] thư_mục
```
### Các tùy chọn phổ biến:

- `rmdir thư_mục`: Xóa thư mục thư_mục nếu nó rỗng.

- `rmdir -p thư_mục`: Xóa thư mục thư_mục và các thư mục cha của nó nếu chúng rỗng.

- `rmdir -i thư_mục`: Cảnh báo trước khi xóa thư_mục.

## Lệnh `sudo` (SuperUser DO) được sử dụng để thực thi một lệnh với quyền của người dùng khác, thường là người dùng root.
```bash
sudo [tùy chọn] lệnh
```
### Các tùy chọn phổ biến:

- `sudo lệnh`: Thực thi lệnh với quyền root.

- `sudo -i`: Mở một shell mới với quyền root.

- `sudo -u người_dùng lệnh`: Thực thi lệnh với quyền của người_dùng khác.

## Lệnh `chmod` (change mode) được sử dụng để thay đổi quyền truy cập cho tệp và thư mục.
```bash
chmod [tùy chọn] quyền tệp
```
### Các quyền:

- `r`: Quyền đọc (read)

- `w`: Quyền ghi (write)

- `x`: Quyền thực thi (execute)


## Lệnh `chown` (change owner) được sử dụng để thay đổi chủ sở hữu và nhóm của tệp hoặc thư mục.
```bash
chown [tùy chọn] chủ_sở_hữu[:nhóm] tệp
```
### Các tùy chọn phổ biến:

- `chown user tệp`: Đổi chủ sở hữu của tệp thành user.

- `chown user:group tệp`: Đổi chủ sở hữu của tệp thành user và nhóm thành group.

- `chown -R user tệp`: Đổi chủ sở hữu của tệp và tất cả nội dung bên trong (đệ quy).


## Lệnh `man` (manual) được sử dụng để hiển thị tài liệu hướng dẫn sử dụng cho các lệnh và chương trình trên Linux.
```bash
man [tùy chọn] lệnh
```
### Các tùy chọn phổ biến:

- `man lệnh`: Hiển thị tài liệu hướng dẫn cho lệnh.

- `man -k từ_khóa`: Tìm kiếm các lệnh có chứa từ_khóa trong mô tả.

- `man -f lệnh`: Hiển thị thông tin ngắn về lệnh.


## Lệnh `wget` được sử dụng để tải xuống tệp từ internet qua HTTP, HTTPS, và FTP.

```bash
wget [tùy chọn] [URL]
```
### Các tùy chọn phổ biến:

- `wget URL`: Tải xuống tệp từ URL.

- `wget -O tệp`: Ghi tệp đã tải xuống vào tệp chỉ định.

- `wget -c URL`: Tiếp tục tải xuống tệp đã bị gián đoạn.

- `wget -r URL`: Tải xuống một trang web cùng với các tài nguyên liên quan (đệ quy).

## Lệnh `apt` được sử dụng để quản lý gói phần mềm trong các hệ thống dựa trên Debian, bao gồm Ubuntu.
```bash
apt [tùy chọn] [lệnh]
```
### Các tùy chọn phổ biến:

- `apt update`: Cập nhật danh sách các gói có sẵn từ kho lưu trữ.

- `apt upgrade`: Nâng cấp tất cả các gói đã cài đặt lên phiên bản mới nhất.

- `apt install gói`: Cài đặt gói phần mềm gói.

- `apt remove gói`: Xóa gói phần mềm gói.

- `apt search từ_khóa`: Tìm kiếm gói phần mềm có chứa từ_khóa.

## Lệnh `kill` được sử dụng để gửi tín hiệu đến một hoặc nhiều tiến trình đang chạy, thường là để kết thúc một tiến trình.
```bash
kill [tùy chọn] PID
```
### Các tùy chọn phổ biến:

- `kill PID`: Gửi tín hiệu TERM (terminate) đến tiến trình có PID là PID.

- `kill -9 PID`: Gửi tín hiệu KILL đến tiến trình, buộc kết thúc tiến trình ngay lập tức.

- `killall tên_tiến_trình`: Gửi tín hiệu đến tất cả các tiến trình có tên là tên_tiến_trình.

## Lệnh `ping` được sử dụng để kiểm tra kết nối mạng giữa máy tính của bạn và một địa chỉ IP hoặc tên miền.
```bash
ping [tùy chọn] địa_chỉ
```
### Các tùy chọn phổ biến:

- `ping địa_chỉ`: Gửi gói tin ICMP đến địa chỉ IP hoặc tên miền để kiểm tra kết nối.

- `ping -c số_lần địa_chỉ`: Gửi chỉ số_lần gói tin ICMP và sau đó dừng.

- `ping -i khoảng_thời_gian địa_chỉ`: Đặt khoảng thời gian giữa các gói tin


## Lệnh `passwd` được sử dụng để thay đổi mật khẩu của người dùng hiện tại hoặc của một người dùng khác.
```bash
passwd [tùy chọn] [người_dùng]
```
### Các tùy chọn phổ biến:

- `passwd`: Thay đổi mật khẩu cho người dùng hiện tại.

- `passwd người_dùng`: Thay đổi mật khẩu cho người_dùng được chỉ định (cần quyền root).

- `passwd -l người_dùng`:Khóa tài khoản của người_dùng.


## Lệnh `top` được sử dụng để hiển thị thông tin về các tiến trình đang chạy trong hệ thống theo thời gian thực.
```bash
top
```
### Các phím tắt hữu ích trong giao diện top:

- `h`: Hiển thị hướng dẫn sử dụng.

- `q`: Thoát khỏi giao diện top.

- `P`: Sắp xếp theo mức sử dụng CPU.

- `M`: Sắp xếp theo mức sử dụng bộ nhớ.


## Lệnh `df` (disk free) được sử dụng để hiển thị thông tin về dung lượng ổ đĩa.

```bash
df [tùy chọn]
```
### Các tùy chọn phổ biến:

- `df`: Hiển thị dung lượng ổ đĩa cho tất cả các hệ thống tập tin.

- `df -h`: Hiển thị dung lượng ổ đĩa trong định dạng dễ đọc hơn (KB, MB, GB).

- `df-T`: Hiển thị loại hệ thống tập tin cho mỗi hệ thống tập tin.

## Lệnh `free` được sử dụng để hiển thị thông tin về bộ nhớ hệ thống, bao gồm bộ nhớ đã sử dụng, bộ nhớ tự do và bộ nhớ swap.
```bash
free [tùy chọn]
```
### Các tùy chọn phổ biến:

- `free`: Hiển thị thông tin bộ nhớ.

- `free -h`: Hiển thị thông tin bộ nhớ theo định dạng dễ đọc hơn (KB, MB, GB).

- `free -m`: Hiển thị thông tin bộ nhớ tính bằng MB.

- `free -s giây`: Cập nhật thông tin sau mỗi giây chỉ định.


## `vi` là một trình soạn thảo văn bản mạnh mẽ và linh hoạt, thường được sử dụng trong môi trường Unix/Linux để chỉnh sửa tệp. Nó có hai chế độ chính: chế độ lệnh (command mode) và chế độ chèn (insert mode).
```bash
vi tên_tệp
```
### Các lệnh lưu và thoát VIM:
- `:q`: Thoát khỏi Vim
- `:q!`: Bắt buộc thoát không cần lưu
- `:w`: Lưu file
- `:w!`: Bắt buộc ghi file (ghi đè)
- `:wq`: Lưu xong thoát
### Các Lệnh Cơ Bản Trong Chế Độ Lệnh

- `h`: Di chuyển con trỏ sang trái.
- `j`: Di chuyển con trỏ xuống dưới.
- `k`: Di chuyển con trỏ lên trên.
- `l`: Di chuyển con trỏ sang phải.
- `x`: Xóa ký tự dưới con trỏ.
- `dd`: Xóa toàn bộ dòng hiện tại.
- `yy`: Sao chép dòng hiện tại.
- `p`: Dán nội dung đã sao chép.
