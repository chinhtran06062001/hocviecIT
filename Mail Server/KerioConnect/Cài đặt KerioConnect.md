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

![image](https://user-images.githubusercontent.com/97047640/175811418-10707a20-e03b-4a96-8541-d4909d9219be.png)

Bước 6 : Điền hostname và domain

![image](https://user-images.githubusercontent.com/97047640/175811319-8ecb84d5-11d1-4852-a8ce-3b2b51ecbee8.png)

Bước 7 : Đặt Password cho administrator

*Lưu ý : Pass phải nhiều hơn 8 ký tự có ký tự hoa, và ký tự số 

![image](https://user-images.githubusercontent.com/97047640/175811458-93c1a567-0f23-4baa-9ac7-1a775fc789de.png)

Bước 8 : Chọn thư mục lưu trũ mail

![image](https://user-images.githubusercontent.com/97047640/175811483-d624c4b0-6af4-4fb9-ba4e-b1d4b90c71bd.png)

Bước 9 : Nhập key nếu bạn có mua license hoặc bạn có thể sử dụng bản trial

![image](https://user-images.githubusercontent.com/97047640/175811494-df9cdc75-668e-4b45-b65e-112c4661681c.png)

Bước 10 : Nhập Key

![image](https://user-images.githubusercontent.com/97047640/175811508-17305066-c27d-4642-967f-d9bb4774a93c.png)

![image](https://user-images.githubusercontent.com/97047640/175811522-dfa48203-545e-4a1a-bc69-0cc97a3eb1a7.png)

Bước 11 : Để mặc định và chọn Next 

![image](https://user-images.githubusercontent.com/97047640/175811532-3b357728-e1a7-44ab-b4c6-d4ff8a4e4247.png)

Bước 12 : Kết thúc việc cài đặt 

![image](https://user-images.githubusercontent.com/97047640/175811540-8dcbcffa-dab8-4ef3-827b-03a76cc45702.png)

Bước 13 : Truy cập control quản trị 

![image](https://user-images.githubusercontent.com/97047640/175811642-795db9cf-5a14-48f2-8a22-f7fbc60f1503.png)

Bước 14 : Thay đổi ngôn ngữ 

![image](https://user-images.githubusercontent.com/97047640/175811714-fe4bbb5f-48b5-4337-80aa-dc05e2e934e7.png)

Quá trình cài đặt hoàn tất ..! 
