# TÌM HIỂU NGINX VÀ CÀI ĐẶT

## I. Tìm hiểu nginx

## 1. Tổng quan

- Nginx là một máy chủ reverse proxy mã nguồn mửo cho các giao thức HTTP, HTTPS, SMTP, POP3 và IPMAP,
cũng như 1 máy chủ cân bằng tải (load balancer), HTTP cacche và web. DỰ án NginX được bắt đầu với 
việc tập trung vào tính đồng thời cao, hiệu năng cao và sử dụng tài nguyên thấp và được phát triển
bởi Igor Sysoev vào năm 2002, được phân phối ra công chúng lần đầu vào năm 2004.

- Không giống với các máy chủ web truyền thống, Nginx không dựa trên luồng (Thread) để xử lý yêu cầu.
Thay vào đó, nó sử dụng 1 kiến trúc bất đồng bộ hướng sự kiện linh hoạt.Kiến trúc này sử dụng ít,
nhưng quan trọng hơn là lượng bộ nhớ có thể dự đoán khi hoạt động. Đây chính là điểm mấu chốt khiến
Nginx là một trong số ít những máy chủ được viết để giải quyết vấn đề C10K.

- Một số người sẽ không hiểu vấn đề C10K là gì? Hiểu đơn giản thì nó do các máy chủ web truyền thống 
xử lý các yêu cầu dựa trên luồng (thread), tức là mỗi khi máy chủ web nhận được một yêu cầu mới, nó 
sẽ tạo ra 1 luồng mới để xử lý yêu cầu này, và cứ thế khi số lượng các yêu cầu gửi đến máy chủ web ngày 
càng nhiều thì số lượng các luồn xử lý này trong máy chủ sẽ ngày càng tăng. Và điều này dẫn đến việc thiếu 
hụt tài nguyên cấp cho các luồn xử lý trên ... (Các bạn có thể tìm hiểu rõ hơn tại đây)

- Hiện nay, có khoảng 14,72 % (hơn 137 triệu) các website trên Internet đang sử dụng Nginx là máy chủ web.

![image](https://user-images.githubusercontent.com/97047640/169438819-0600820f-4837-4c17-999e-1d96dd3ff54b.png)

## 2. Kiến trúc của Nginx

- Khi được khởi chạy service, nginx khởi tạo mọt tiến trình chủ và cũng là tiến trình duy nhất tồn tại
trong bộ nhớ Master Process. Tiến trình này không chịu trách nhiệm tự xử lý bất kỳ request nào từ phía 
client mà thay vào đó nó sinh ra các tiến trình con gọi là Worker Process để xử lý các request này.

![image](https://user-images.githubusercontent.com/97047640/169438968-21ec8e03-0ac3-4805-85a5-c3b98e6bde7f.png)

- Để định nghĩa cho các Worker Process này, chúng ta cần sử dụng tệp tin cấu hình để xác định số tiến trình,
số lượng kết nối , tài khoản và nhóm tài khoản mà mỗi Worker Process chạy.

## 3. Cấu hình HTTP trong Nginx

- Module HTTP Core là thành phần chứa tất cả các khối, chỉ thị và các biến cơ bản của máy chủ HTTP. Mặc định 
module này được cài đặt trong khi biên dịch, nhưng không được bật lên khi Nginx chạy, việc sử dụng module 
này là không bắt buộc

- Module này là 1 trong những module tiêu chuẩn lớn nhất của Nginx – nó cung cấp 1 số lượng lớn các chỉ thị 
và biến. Để có thể hiểu được tất cả các yếu tố này và vai trò của chúng, chúng ta sẽ bắt tay vào tìm hiểu 
3 khối chỉ thị chính – ``http``, ``server`` và ``location``.

- ``http`` : được khai báo ở phần đầu của tập tin cấu hình. Nó cho phép chúng ta định nghĩa các chỉ thị và các 
khối từ tất cả các module liên quan đến khía cạnh HTTP của Nginx. Khối chỉ thị này có thể được khai báo 
nhiều lần trong tập tin cấu hình, và các giá trị chỉ thị được chèn trong khối http sau sẽ ghi đè lên các 
chỉ thị nằm trong khối http trước đó

- ``server`` : khối này cho phép chúng ta khai báo 1 website. Nói cách khác, 1 website cụ thể (được nhận diện 
bởi 1 hoặc nhiều hostname) được thừa nhận bới Nginx và nhận cấu hình của chính nó. Khối này chỉ có thể 
được dùng bên trong khối http.

- ``location`` : cho phép chúng ta định nghĩa 1 nhóm các thiết lập được áp dụng cho 1 vị trí cụ thể trên 
website (thể hiện qua URL của website đó). Khối location có thể được dùng bên trong 1 khối server hoặc 
nằm chồng bên trong 1 khối location khác.

![image](https://user-images.githubusercontent.com/97047640/169439386-f1c40972-3382-463a-ae01-169f76c0b4db.png)

## II. Cài đặt NginX trên hệ điều hành Linux

Bước 1 : Dừng SELinux nhằm tránh trường hợp nó chặn Nginx

Truy cập SELinux bằng câu lệnh :

`` nano /etc/sysconfig/selinux `` 

![image](https://user-images.githubusercontent.com/97047640/169443161-d06e7b0a-cc62-4274-9e22-d2613297af18.png)

Thay đổi `enforcing` thành `disabled` như hình trên

Sau đó dùng lệnh `reboot` để khởi động lại hệ thống

Tiếp theo dùng lệnh `sestatus` để kiểm tra selinux đã dừng chưa (Nếu như hình dưới là đã thành công)

![image](https://user-images.githubusercontent.com/97047640/169443410-4fbef4be-b0f5-4c2d-88a2-951d921ec0fe.png)

Bước 2 : Cài đặt các gói cần thiết hỗ trợ NginX

Để cài Nginx trên CentOS, chúng ta sẽ cần thêm EPEL repository giúp tạo, duy trì và quản lý các gói bổ sung.

`sudo yum install epel-release -y`

![image](https://user-images.githubusercontent.com/97047640/169443698-1a8a301e-23a3-425a-a268-ab6cd57ef8b4.png)



Bước 3 : Tiến hành cài đặt NginX

Chúng ta cài đặt nginx với câu lệnh :

`yum install nginx -y`

![image](https://user-images.githubusercontent.com/97047640/169444431-1df31b7c-6918-48f7-9c42-7a603c687c7b.png)

Bước 4 : Khởi động Nginx

- `systemctl enable nginx` : Câu lệnh đặt mặc định khỏi động Nginx cùng với hệ thống
- `systemctl start nginx` : Câu lệnh khởi chạy Nginx
- `systemctl status nginx` : Câu lệnh kiểm tra trạng thái Nginx

![image](https://user-images.githubusercontent.com/97047640/169445542-e76e5456-12f2-4c17-bcd2-75c3d9705f32.png)

Sau đó truy cập IP/Domain hệ thống nếu ra như hình dưới là đã cài đặt thành công

![image](https://user-images.githubusercontent.com/97047640/169446837-70f4fb5c-0014-4f3e-9b6d-fa4c19ddbe9b.png)

Bước 5 : Cấu hình Firewall (Nếu có) 
 
 Nếu các bạn sử dụng Firewalld để có thể truy cập được website các bạn sẽ cần mở port bằng các lệnh sau đây

    firewall-cmd --permanent --zone=public --add-service=http
    firewall-cmd --permanent --zone=public --add-service=https
    firewall-cmd --reload

![image](https://user-images.githubusercontent.com/97047640/169445765-ae107b15-a724-4bf2-b01c-e285b3bf9899.png)

Bước 6 : Tạo Virtual host (vhost)

Virtual Host là file cấu hình cho phép nhiều domain cùng chạy trên một máy chủ. Tất cả các file vhost sẽ nằm trong thư mục /etc/nginx/conf.d/. Để tiện quản lý mỗi website nên có một vhost riêng, ví dụ: chinhtran.com.conf

Ở đây chúng ta sẽ tạo website chinhtran.com với vhost tương ứng là /etc/nginx/conf.d/chinhtran.com.conf bằng câu lệnh sau:

`nano /etc/nginx/conf.d/hostvn.net.conf`

Dán nội dung dưới dây vào

    server {
       listen 80;
       listen [::]:80;
       server_name www.chinhtran.com chinhtran.com;
       access_log /home/chinhtran.com/logs/access.log;
       error_log /home/chinhtran.com/logs/.error.log;
       root /home/chinhtran.com/public_html;
       index index.html index.htm index.php;
       location / {
        try_files $uri $uri/ =404;
       }
    }
    
  Tiếp theo các bạn cần tạo thư mục chứa mã nguồn website và thư mục chứa file log bằng các lệnh sau:
  
`mkdir -p /home/chinhtran.com/public_html`

`mkdir -p /home/chinhtran.com/logs`

`chown -R nginx:nginx /home/chinhtran.com`

`chmod -R 755 /home` (gán quyền)

`nano /etc/hosts` (Gán tên miền với Domain)

Sau khi cấu hình hoàn tất các bạn trỏ tên miền về vps sau đó tạo file /home/hostvn.net/public_html/index.html

`nano /home/chinhtran.com/public_html/index.html`

Dán nội dung sau vào

     <!DOCTYPE html>
     <html lang="en">
     <head>
	     <meta charset="UTF-8">
	     <title>TRANCHINH.COM - Hướng dẫn cài đặt Nginx trên CentOS 7</title>
     </head>
     <body>
	     <p><center>Hello World</center></p>
     </body>
     </html>

Reload lại Nginx để load cấu hình

`systemctl reload nginx`

Cuối cùng truy cập tên miền của bạn bằng trình duyệt để kiểm tra

![image](https://user-images.githubusercontent.com/97047640/169449133-389e6b01-8e68-47bf-a972-78cf918fef80.png)
