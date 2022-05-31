# Các bước cài đặt Wordpress (LAMP)

## Bước 1 : Cấu hình MySQL

Truy cập vào MariaDB bằng tài khoản root:

`# mysql -u root -p`

Tạo database cho WordPress, với wordpress là tên database:

`CREATE DATABASE wordpress;`

Tạo user và password cho việc truy cập database vừa tạo, với wordpressuser là tên tài khoản, password là mật khẩu cần tạo và cấp quyền truy cập cho user vừa tạo:

`GRANT ALL PRIVILEGES ON wordpress.* TO 'wordpressuser'@'localhost' IDENTIFIED BY ‘password’;`

Cập nhật thay đổi và thoát:

`FLUSH PRIVILEGES;`

`exit`

## Bước 2 : Cài WordPress trên CentOS 7

Cài thêm gói php-gd (thư viện xử lý ảnh của PHP) để tránh các lỗi không mong muốn khi sửa ảnh với WordPress:

`# yum install php-gd`

Khởi động lại Apache:

`# service httpd restart`

Về thư mục home (root) và tải bản WordPress mới nhất, sau đó giải nén:

`# cd ~`

`# wget http://wordpress.org/latest.tar.gz`

`# tar xzvf latest.tar.gz`

Chuyển thư mục WordPress đã giải nén về thư mục mặc định của web bằng rsync (nếu chưa có rsync thì cài với lệnh yum install rsync):

`# rsync -avP ~/wordpress/ /var/www/html/`

Tạo thư mục để WordPress lưu trữ các file upload lên:

`# mkdir /var/www/html/wp-content/uploads`

Cấp quyền cho nhóm người dùng Apache:

`# sudo chown -R apache:apache /var/www/html/*`

## Bước 3 : Cấu hình WordPress

Di chuyển đến thư mục html và chỉnh sửa file cấu hình của WordPress:

`# cd /var/www/html`

`# cp wp-config-sample.php wp-config.php`

`# vi wp-config.php`

Chỉnh sửa tên, user, password database phù hợp:

```

// ** MySQL settings – You can get this info from your web host ** //

/** The name of the database for WordPress */

define( ‘DB_NAME’, ‘database_name_here’ );

/** MySQL database username */

define( ‘DB_USER’, ‘username_here’ );

/** MySQL database password */

define( ‘DB_PASSWORD’, ‘password_here’ );

```

Truy cập vào IP (hoặc domain nếu đã trỏ trước đó) để cấu hình ban đầu WordPress:

![image](https://user-images.githubusercontent.com/97047640/171110803-4e1857ff-a560-49fe-94b7-a4c572772548.png)

chọn ngôn ngữ

![image](https://user-images.githubusercontent.com/97047640/171110883-854b7dd2-e69d-4ddd-ba4e-a093c566356b.png)

tạo tài khoản đăng nhập wordpress

![image](https://user-images.githubusercontent.com/97047640/171110965-b3f87a94-eebc-4869-9574-3ea434726e6c.png)

Cài đặt thành công

![image](https://user-images.githubusercontent.com/97047640/171115309-152c328d-0c16-4ec7-be03-5f18dfeb0949.png)

