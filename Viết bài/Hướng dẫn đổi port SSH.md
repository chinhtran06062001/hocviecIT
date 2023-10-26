Đổi port SSH mặc định để bảo mật hệ thống, làm khó khăn hơn cho các script độc hại hoặc kẻ xấu cố gắng để đăng nhập vào máy chủ CentOS của bạn. Từ CentOS 7 việc đổi port SSH có đôi chút khác biệt với các hệ điều hành cũ, để thực hiện đổi port SSH trên CentOS 7 bạn thực hiện như sau:

##1 - Update các bản vá cho hệ thống:

```sh
[root@localhost ~]# yum update -y​
````

2- Cấu hình SSH đổi port mong muốn

```sh
[root@localhost ~]# vi /etc/ssh/sshd_config
```

Mặc định là port 22 bạn sửa thành port mong muốn:

VD: ở đây muốn mở port 2220 cho dịch vụ SSH

![image](https://github.com/chinhtran06062001/hocviecIT/assets/97047640/401833df-54a3-4d40-a5b5-ade915218fe3)

Lưu lại cấu hình và khởi động lại dịch vụ SSH để nhận port mới.

```sh
[root@localhost ~]# systemctl restart sshd.service
```

Bạn có thể kiểm tra lại dịch vụ SSH đã nhận chính xác port mới chưa, bằng công cụ netstat. Nếu chưa có Netstat bạn có thể cài đặt bằng lệnh:

```sh
[root@localhost ~]# yum install net-tools -y
```

Sau đó kiểm tra các cổng đang mở.

```sh
[root@localhost ~]# netstat -tupln
```

![image](https://github.com/chinhtran06062001/hocviecIT/assets/97047640/fb6e31c8-39a7-4eca-ac3b-098e13d825a4)

Bây giờ cho phép kiểm tra xem CentOS của bạn đang lắng nghe dịch vụ SSH trên cổng mới. Gõ lệnh lệnh netstat để kiểm tra:

```sh
[root@localhost ~]# netstat -tupln
```

Cuối cùng mở port mới cho dịch vụ SSH trên Firewall

```sh
[root@localhost ~]# firewall-cmd –permanent –add-port=2220/tcp
```

Khởi động lại Firewall để có hiệu lực

```sh
[root@localhost ~]# firewall-cmd –reload
```

Bây giờ bạn thử SSH xem kết quả, chúc bạn thực hiện thành công !
