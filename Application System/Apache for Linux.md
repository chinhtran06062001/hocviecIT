# CÁC BƯỚC CÀI ĐẶT APACHE CHO CenOS 7

1. Truy cập Teminal CenOS 7 với quyền root với câu lệnh 

   `` sudo -i ``
   
   ![image](https://user-images.githubusercontent.com/97047640/168954554-5bcb3eb6-9767-4ceb-b37e-a57caa94cba8.png)

2. Do Apache đã có sẵn trong kho lưu trữ CentOS mặc định nên việc cài đặt khá đơn giản. Để cài đặt Apache hãy chạy lệnh sau:

   `` yum install httpd -y ``
   
   ![image](https://user-images.githubusercontent.com/97047640/168954874-024db8a4-8a23-48c7-8cba-2e1949a36607.png)

3. Sau khi cài đặt hoàn tất, tiến hành khởi động Apache bằng cách khởi động lại nó bằng các lệnh sau :

   `` systemctl enable httpd ``

   `` systemctl start httpd ``
   
   ![image](https://user-images.githubusercontent.com/97047640/168955130-cecdd341-7d5b-4309-91ef-99cb8c281859.png)

   **Để kiểm tra trạng thái apache chúng ta sử dụng câu lệnh `` systemctl status httpd ``**
   
   ![image](https://user-images.githubusercontent.com/97047640/168955368-5d983a40-c2b4-4ac7-a6c1-7b20cb431fd8.png)

4. Cấu hình firewall (nếu có)

   Nếu các bạn sử dụng Firewalld để có thể truy cập được website các bạn sẽ cần mở port bằng các lệnh sau đây

   `` firewall-cmd --permanent --zone=public --add-service=http ``

   `` firewall-cmd --permanent --zone=public --add-service=https ``

   `` firewall-cmd --reload ``

![image](https://user-images.githubusercontent.com/97047640/168955960-5a8af638-7368-49b2-9869-04fcf0d75b33.png)

*Các câu lệnh quản lý apache với systemctl :
   
   - Để dừng apache dùng lệnh : `` systemctl stop httpd ``
   - Để khởi động apache dùng lệnh : `` systemctl start httpd ``
   - Lệnh khởi động lại apache `` systemctl restart httpd
   - Tải lại dịch vụ apache sau khi thay đổi cấu hình : `` systemctl reload httpd ``
   - Nếu không muốn Apache tự động chạy mỗi khi khởi động lại VPS sử dụng lệnh sau: ``systemctl disable httpd ``
   - Nếu muốn Apache tự động chạy mỗi khi khởi động lại VPS sử dụng lệnh sau: ``systemctl enable httpd``

*Các file cấu hình :

   - Tất cả các file cấu hình của Apache đều nằm trong thư mục /etc/httpd.
   - File cấu hình chính của Apache là /etc/httpd/conf/httpd.conf.
   - Tất cả các tệp cấu hình đều phải kết thúc bằng .conf và nằm trong thư mục /etc/httpd/conf.d.
   - Các tệp cấu hình chịu trách nhiệm tải các modules Apache được đặt trong thư mục /etc/httpd/conf.modules.d.
   - Để quản lý tốt hơn, nên tạo một tệp cấu hình riêng (vhost) cho mỗi tên miền.
   - Các tệp vhost Apache phải kết thúc bằng .conf và được lưu trữ trong thư mục /etc/httpd/conf.d. Ví dụ: nếu tên miền của bạn là mydomain.com thì tệp cấu hình sẽ được đặt tên /etc/httpd/conf.d/mydomain.com.conf
   - Các file log của Apache (access_log và error_log) nằm trong thư mục /var/log/httpd/. Bạn nên có file log riêng cho mỗi vhost.

5. Tạo Virtualhost (Vhost)

5.1 Bật userdir bằng lệnh : ``nano /etc/httpd/conf.d/userdir.conf``

![image](https://user-images.githubusercontent.com/97047640/168957776-ee84a24f-1778-41b1-a450-b5722458d57a.png)

5.2 Tại đây, chúng ta cần sửa bằng cách nhập ``#UserDir public_html``

![image](https://user-images.githubusercontent.com/97047640/168958008-1a7ea1c8-8ae4-4c33-8f7f-d6e6ff35338c.png)

5.3 Tiếp theo tìm đoạn rule 

![image](https://user-images.githubusercontent.com/97047640/168958415-f0d9a167-9bd7-4bde-b8b7-f2a24d423905.png)

Sửa thành 

![image](https://user-images.githubusercontent.com/97047640/168958554-b0fb0403-a35f-42d1-8dfe-1fd638f7cac5.png)

5.4 Chặn truy cập IP VPS tự động 

Theo mặc định thì khi truy cập IP của VPS hoặc khi trỏ một tên miền về VPS mà tên miền này không được cấu hình vhost thì bạn sẽ được redirect tới một website bất kỳ trên VPS, điều này là không nên và để hạn chế điều này các bạn mở file /etc/httpd/conf/httpd.conf

   `` nano /etc/httpd/conf/httpd.conf ``

Thêm phía trên dòng IncludeOptional conf.d/*.conf rules sau:
   
``<VirtualHost *:80>

	DocumentRoot /var/www/html
  
	ServerName www.example.com
  
	<Directory "/var/www/html">
  
		AllowOverride All
    
    Options None
    
    Require method GET POST OPTIONS
    
	</Directory>
  
</VirtualHost>
Screenshot_113``

5.5 Tạo virtual host (vhost) cho website

Virtual Host là file cấu hình trong Apache để cho phép nhiều domain cùng chạy trên một máy chủ. Có một khái niệm khác được đề cập tới trong Nginx cũng có chức năng tương tự như Virtual Host được gọi là Server Block.

Tất cả các file vhost sẽ nằm trong thư mục /etc/httpd/conf.d/. Để tiện quản lý mỗi website nên có một vhost riêng, ví dụ: hostvn.net.conf

Trong ví dụ này sẽ tạo website tranchinh.com với vhost tương ứng là /etc/httpd/conf.d/tranchinh.com.conf

`nano /etc/httpd/conf.d/tranchinh.com.conf`

Dán nội dung sau vào

```
<VirtualHost *:80>
ServerAdmin chinhtran06062001@gmail.com
ServerName chinhtran.vn
ServerAlias www.chinhtran.vn
DocumentRoot /home/chinhtran.vn/public_html
ErrorLog logs/error
CustomLog logs/access combined
</VirtualHost>
```

Tiếp theo các bạn cần tạo thư mục chứa mã nguồn website và thư mục chứa file log bằng các lệnh sau

`mkdir -p /home/tranchinh.com/public_html`

`mkdir -p /home/tranchinh.com/logs`

`chown -R apache:apache /home/tranchinh.com`

Reload lại Apache để cập nhật cấu hình

`systemctl reload httpd`

Sau khi cấu hình hoàn tất các bạn trỏ tên miền về vps sau đó tạo file /home/hostvn.net/public_html/index.html

`nano /home/tranchinh.com/public_html/index.html`

Dán nội dung sau vào

```
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>TRANCHINH.COM - Hướng dẫn cài đặt Apache trên CentOS 7</title>
</head>
<body>
	<p><center><?= "Hello World" ?></center></p>
</body>
</html>
```

Truy cập tên miền của bạn bằng trình duyệt để kiểm tra
    

 


