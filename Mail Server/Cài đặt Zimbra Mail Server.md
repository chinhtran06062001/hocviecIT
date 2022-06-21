# I. Tổng quan

1. Zimbra mail server là gì? 

Zimbra Mail (Zimbra Collaboration Suite)  là phần mềm mã nguồn mở với hai phần là máy chủ mail và máy khách website và được phát triển với mục tiêu ngoài dùng làm mail ra thì còn là một giải pháp có thể giải quyết được nhiều vấn đề như bảo mật, kết nối các thành viên(chat) cũng như quản lý và chia sẽ công việc một cách nhanh chóng, hiệu quả cho các doanh nghiệp lớn – nhỏ.

2. Chức năng của Zimbra mail

Các chức năng trên zimbra mail:

- Thư điện tử: Hệ thống thư điện tử hoàn hảo, Với hai phần là Mail Server (SMTP, POP3, IMAP, Backup, Antivirus… Bên cạnh đó có đủ các tính năng như: tự động trả lời, chuyển tiếp…) và Mail Client (Zimbra Desktop và Zimbra Web Client).
- Sổ địa chỉ (Contacts): Quản lý sổ cá nhân của từng thành viên(Địa chỉ, số điện thoại, thông tin cá nhân,…) và sổ chung của đội nhóm.
- Danh mục công việc (Tasks): Danh sách các công việc, giúp theo dõi tiến độ, và việc quản lý được tối ưu hơn, cũng như có phân chia độ ưu tiên công việc và khối lượng công việc đã hoàn thành của mỗi cá nhân hoặc đội nhóm.
- Tài liệu (Documents): Dễ dàng soạn thảo văn bản tài liệu dưới dạng Wiki của mỗi cá nhân hoặc đội nhóm. Cho phép người dùng in trực tiếp văn bản soạn thảo xong hoặc trao đổi(gửi – nhận) qua Email.
- Cặp tài liệu hồ sơ (Briefcase): Với công cụ này có thể lưu trữ tài liệu, tập tin cho việc dùng cá nhân hoặc chia sẻ với nhóm hoặc cá nhân khác dùng chung.
- Chat: Chat nội bộ với nhau trong mạng LAN hoặc trên Internet.
- Lịch công tác (Calendar): Thông tin về lịch cá nhân và lịch nhóm, hỗ trợ cho phép tạo cuộc hẹn, tự động gửi mail theo lịch trình(Như thời gian hợp được lên lịch trước)…
- Preferences: Chỉnh sửa nâng cao với Zimbra, Gồm thay đổi Theme, phông chữ, ngôn ngữ, phím tắt, chữ ký, bộ lọc mail….

3. Cấu hình tối thiếu để cài đặt Zimbra?

Disk: Trên 20GB
Ram: 6GB
IP(VPS hoặc máy chủ), domain, mail domain

## Cài đặt Zimbra Mail Server

Bước 1: Cập nhật bản ghi mail

Để phục vụ cho việc cài đặt. Bạn hãy trỏ bản ghi mail như sau trước nhé. Bên dưới là 2 bản ghi và mẫu của mình.

Bước 2:  Kiểm tra và cập nhật hệ thống
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

Bước 3: Kiểm tra và set hostname
Bạn thực hiện kiểm tra hostname và set lại hostname tương ứng

`[root@mail ~]# hostnamectl set-hostname mail.chinhtran.site
[root@mail ~]# exec bash`

Sau khi set hostname xong bạn thêm dòng sau vào file hosts bạn nhớ thay đổi IP bằng IP của bạn nha.

`[root@mail ~]# vi /etc/hosts`

```
127.0.0.1 localhost localhost.localdomain localhost4 localhost4.localdomain4
::1 localhost localhost.localdomain localhost6 localhost6.localdomain6
192.168.126.161 mail.chinhtran.site
```

![image](https://user-images.githubusercontent.com/97047640/173776357-87c7e371-bdf7-408b-896f-a3a35ed0dd58.png)

Bước 4: Cài đặt Zimbra
Bạn thực hiệ chạy lệnh sau để install Zimbra & ZCS dependencies
```
[root@mail ~]# yum install unzip net-tools sysstat openssh-clients perl-core libaio nmap-ncat libstdc++.so.6 wget -y
```

![image](https://user-images.githubusercontent.com/97047640/174704856-ed2ab3e6-9c5b-4a9c-85c0-375060f7cb2e.png)

Bước tiếp theo bạn cần Download Zimbra và cài đặt. Và bạn cần tạo một thư mục zimbra để cài vào đó. Bạn cũng có thể xem các phiên bản Zimbra ở trang chủ để download nhé.
```
[root@mail ~]# mkdir zimbra && cd zimbra
[root@mail zimbra]# wget https://files.zimbra.com/downloads/8.8.15_GA/zcs-8.8.15_GA_3869.RHEL7_64.20190918004220.tgz --no-check-certificate
```

![image](https://user-images.githubusercontent.com/97047640/174704922-717f0c8f-ed0f-431d-8b6e-a30cea539200.png)

Sau khi download về hoàn tất bạn tiến hành giải nén file ra

`[root@mail zimbra]# tar zxpvf zcs*.tgz`

Truy cập vào thư mục vừa giải nén và chạy lệnh ./install

`[root@mail zimbra]# cd zcs* && ./install.sh`

![image](https://user-images.githubusercontent.com/97047640/174704980-bfe54989-1112-4178-8f60-9578db00f018.png)


Bước 5: Khai báo Domain 

![image](https://user-images.githubusercontent.com/97047640/174705375-70118e3e-c184-4c21-9574-15cdb81d1f4f.png)

Nhập Domain như hình trên, sau đó nhân Enter để tiếp tục

![image](https://user-images.githubusercontent.com/97047640/174705531-999741d3-2b35-4896-ae7f-8ce6c5ff736d.png)

Chọn 7 sau đó chọn 4 để thiết lập tài khoản Admin

![image](https://user-images.githubusercontent.com/97047640/174705790-6b875892-4d42-4c7b-9eb2-3f6e4a7a5c72.png)

Nhập password và ấn r để lưu thay đổi, tiếp theo nhấn a để cập nhật thay đổi

![image](https://user-images.githubusercontent.com/97047640/174706057-b1c23a2c-c51d-4d72-a201-42623a8a0e5f.png)

![image](https://user-images.githubusercontent.com/97047640/174706161-789b36cb-d5a2-4f70-a9b0-9c990b75d591.png)

Bước 6: Sau khi cài đặt xong khởi động lại dịch vụ zimbar bằng lệnh :

```
[root@mail ~]# su zimbra
[zimbra@mail root]$ zmcontrol restart
```

Bước 7: Mở port firewall :

```
firewall-cmd --permanent --add-port={25,80,110,143,443,465,587,993,995,5222,5223,9071,7071}/tcp
firewall-cmd --reload
```

Sau đó truy cập bằng zimbar bằng IP : 192.168.126.167

![image](https://user-images.githubusercontent.com/97047640/174734916-46d1aa77-610c-41a2-9f18-1b5f50baa100.png)

Kết quả 

![image](https://user-images.githubusercontent.com/97047640/174735348-23e18faf-c2db-402d-bb29-fed0bf831c81.png)

