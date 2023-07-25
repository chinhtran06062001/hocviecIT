# 1. Tổng quan

Trong bài này mình sẽ hướng dẫn hạ cấp MySQL trên DirectAdmin một các đơn giản và nhanh chóng nhất. Tuy nhiên việc hạ cấp là một việc không nên làm trừ khi bạn bắt buộc phải làm như vậy.

Mình có thấy rất nhiều bài viết hướng dẫn hạ cấp ở trên Google, tuy nhiên đa số đều không phải hướng dẫn chính thống từ DirectAdmin và một số nhiều trong đó không hoạt động được. Và bài này mình sẽ dựa theo các bài viết chính thống của DirecAdmin, đường dẫn bài viết này mình sẽ để ở cuối bài viết.

Lưu ý quan trọng: Trong trường hợp bài viết này là bạn đã sao lưu toàn bộ database của mình rồi hoặc bạn không còn gì để mất nữa. Nếu bạn chưa biết cách để sao lưu database các bạn có thể tham khảo bài viết bên dưới.

# 2. Hướng dẫn hạ cấp MySQL trên DirectAdmin

Để hạ cấp MySQL trên DirectAdmin chúng ta cần thực hiện 3 bước sau.

### Bước 1: SSH vào hệ thống DirectAdmin của bạn

Để hạ cấp MySQL trên DirectAdmin, đầu tiên chúng ta cần làm là SSH hoặc truy cập VPS hoặc máy chủ của bạn với quyền root trước.

Sau khi đã SSH thành công chúng ta tiếp tục với bước 2 để bắt đầu quá trình hạ cấp MySQL trên DirectAdmin.

### Bước 2: Kiểm tra phiên bản MySQL đang sử dụng hiện tại

Để kiểm tra phiên bản MySQL hiện tại chúng ta sử dụng 1 lệnh sau.

```sh
mysqld -V
```

Hình dưới đây là kết quả của mình, với phiên bản đang cài hiện tại là 15.1 .

![image](https://github.com/chinhtran06062001/hocviecIT/assets/97047640/738b699b-8fcc-4954-832b-d762bfb5d7e3)

Vậy là xong bước kiểm tra phiên bản MySQL đang sử dụng hiện tại. Chúng ta tiếp tục với bước 3 để hạ cấp MySQL trên DirectAdmin.

### Bước 3: Hạ cấp MySQL trên DirectAdmin với Custombild 2.0

Đầu tiên chúng ta cần xem phiên bản CustomBuild đang sử dụng có phải là 2.0 hay không

Trong trường hợp phiên bản CustomBuild của bạn thấp hơn 2.0 thì bạn cần nâng cấp CustomBuild 1.x lên 2.0

Trong bước này bạn sẽ xóa hoàn toàn phiên bản MySQL đang cài đi, tuy nhiên cũng đừng quá lo lắng vì chúng ta đã có bước sao lưu trước thư mục /var/lib/mysql để tránh mất dữ liệu database.

Dưới đây là các lệnh mà chúng ta cần thực hiện:

```sh
perl -pi -e 's/mysqld=ON/mysqld=OFF/' /usr/local/directadmin/data/admin/services.status
service mysqld stop
mv /var/lib/mysql /var/lib/mysql.old
cd /usr/local/directadmin/custombuild
./build set mysql 5.6
./build set mysql_inst mysql
./build set mysql_backup no
./build update
./build mysql
```

Giải thích các lệnh trên:

Lệnh 1: Tắt tự động khởi động MySQL theo hệ điều hành.(Lưu ý: Khi copy lệnh này không được để dư khoảng trắng ở cuối lệnh).
Lệnh 2: Tắt dịch vụ MySQL.
Lệnh 3: Sao lưu thư mục /var/lib/mysql thành thư mục /var/lib/mysql.old.
Lệnh 4: Di chuyển vào thư mục custombuild.
Lệnh 5: Điều chỉnh cấu hình phiên bản MySQL lên bản 5.6 (Bạn có thể thay đổi thành phiên bản khác nếu muốn).
Lệnh 6: Sử dụng hệ quản trị cơ sở dữ liệu là MySQL.
Lệnh 7: Tắt sao lưu database tự động vì hiện tại MySQL đã không còn hoạt động.
Lệnh 8: Cập nhật lại custombuild script.
Lệnh 9: Bắt đầu quá trình cài lại MySQL.

Dưới đây là một số hình ảnh trong quá trình hạ cấp của mình:

![image](https://github.com/chinhtran06062001/hocviecIT/assets/97047640/92da3fc7-0c20-4ab1-88d6-0d2bf6c45db5)

Lệnh 1: Tắt tự động khởi động MySQL theo hệ điều hành.

![image](https://github.com/chinhtran06062001/hocviecIT/assets/97047640/7db58099-3615-4f78-92c9-832bc68b9acd)

Lệnh 2: Tắt dịch vụ MySQL.

![image](https://github.com/chinhtran06062001/hocviecIT/assets/97047640/2c859cf8-1621-40c8-91a3-c0d1b63ad5fe)

Lệnh 3: Sao lưu thư mục /var/lib/mysql thành thư mục /var/lib/mysql.old.

![image](https://github.com/chinhtran06062001/hocviecIT/assets/97047640/6583ef82-b90a-471b-9ac3-dcef4791c17d)

Lệnh 4: Di chuyển vào thư mục custombuild.

![image](https://github.com/chinhtran06062001/hocviecIT/assets/97047640/e4c6a06d-48cd-4e5f-99e7-1bd17c68abdb)

Lệnh 5: Điều chỉnh cấu hình phiên bản MySQL thành bản 5.6 (Bạn có thể thay đổi thành phiên bản khác nếu muốn).

![image](https://github.com/chinhtran06062001/hocviecIT/assets/97047640/d83f0e30-36c2-4c06-a4d0-9c56f31fc1e6)

Lệnh 6: Sử dụng hệ quản trị cơ sở dữ liệu là MySQL.

![image](https://github.com/chinhtran06062001/hocviecIT/assets/97047640/ece5caf1-683c-480f-96c3-07ef56edeacf)

Lệnh 7: Tắt sao lưu database tự động vì hiện tại MySQL đã không còn hoạt động.

![image](https://github.com/chinhtran06062001/hocviecIT/assets/97047640/7d225a7b-aa87-430e-b1ce-c4c30502c832)

Lệnh 8: Cập nhật lại custombuild script.

![image](https://github.com/chinhtran06062001/hocviecIT/assets/97047640/43cd9276-223e-4b58-b22a-cf314b6de347)

Lệnh 9: Bắt đầu quá trình cài lại MySQL.

Quá trình cài lại MySQL cũng không mất quá nhiều thời gian. Sau khi cài xong chúng ta sử dung tiếp lệnh mysqld -V để xem phiên bản mới vừa được cài đặt nhé.

Như vậy là VPS của mình đã được hạ cấp MySQL từ bản 8.0.20 về bản MySQL 5.6.48.

# Tổng kết

Thông qua bài này các bạn đã nắm được cách hạ cấp MySQL trên DirectAdmin nhanh gọn. Tuy nhiên mình không khuyến khích làm như vậy trừ trường hợp bất khả kháng như dịch vụ MySQL của bạn đã chết hoàn toàn hoặc một vài lý do khác.

Chúc các bạn thực hiện thành công.
