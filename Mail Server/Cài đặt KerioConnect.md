Bước 1 : Kiểm tra và cập nhật hệ thống
Bước đầu tiên bạn cần kiểm tra SELINUX xem có đang bật không, nếu đang bật thì bạn tắt đi.

![image](https://user-images.githubusercontent.com/97047640/173772917-efb3bc0a-9c22-4f03-bfcf-0aaf3055335e.png)

```
# vi /etc/selinux/config
SELINUX=disabled
```
```
[root@mail ~]# sestatus
SELinux status: disabled
```

Thực hiện stop postfix và remove postfix.

Postfix là một phầm mềm nguồn mở được dùng để gửi mail (Mail Transfer Agent-MTA). Được phát hành bởi IBM với mục tiêu thay thế trình gửi mail phổ biến là sendmail. Nó được trang bị trên hệ điều hành do đó bạn hãy xoá bỏ để sử dụng dịch vụ riêng của Zimbra.

```
[root@mail ~]# systemctl stop postfix
[root@mail ~]# yum remove postfix -y
```
![image](https://user-images.githubusercontent.com/97047640/173773176-ad9e4e54-a96c-4ce3-b2c0-a149961c6901.png)

Sau đó bạn cập nhật hệ thống bằng lệnh sau và reboot lại máy chủ để áp dụng

`[root@mail ~]# yum update -y ; reboot`

Bước 2 : Tiến hành download file rpm Kerio-Connect về VPS bằng cách sử dụng câu lệnh :

```
wget http://cdn.kerio.com/dwn/connect/connect-9.2.9-4540/kerio-connect-9.2.9-4540-p1-linux-x86_64.rpm
```

![image](https://user-images.githubusercontent.com/97047640/175810134-2b673d65-bfea-4777-b9b9-f44bb3926bab.png)

Bước 3 : Tiến hành rpm file kerio-connect.rpm

```
rpm -i kerio-connect-9.2.9-4540-p1-linux-x86_64.rpm
```

![image](https://user-images.githubusercontent.com/97047640/175810168-89967761-f8f2-4354-a70f-41e3edfeea2c.png)

Kiểm tra xem kerio-connect đã cài đặt thành công chưa bằng cách sử dụng câu lệnh `systemctl status kerio-connect`

![image](https://user-images.githubusercontent.com/97047640/175810224-9427bba1-d08c-4876-b936-555a9e65626d.png)

Bước 4 : Đăng nhập mail server trên trình duyệt 

https://IP_server:4040/admin

![image](https://user-images.githubusercontent.com/97047640/175810812-11c742d4-d609-42c3-b469-9f2d146d63c9.png)

Nhấn Next

Bước 5 : Chấp nhận license

Bước 6 : Điền hostname và domain

Bước 7 : Đặt Password cho administrator

*Lưu ý : Pass phải nhiều hơn 8 ký tự có ký tự hoa, và ký tự số 

Bước 8 : Chọn thư mục lưu trũ mail

Bước 9 : Nhập key nếu bạn có mua license hoặc bạn có thể sử dụng bản trial

Bước 10 : Nhập Key

Bước 11 : Để mặc định và chọn Next 

Bước 12 : Kết thúc việc cài đặt 

Bước 13 : Truy cập control quản trị 

Bước 14 : Thay đổi ngôn ngữ 

Quá trình cài đặt hoàn tất ..! 
