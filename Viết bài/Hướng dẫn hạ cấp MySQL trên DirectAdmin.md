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

Hình dưới đây là kết quả của mình, với phiên bản đang cài hiện tại là 8.0.20.

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

Lệnh 1: Tắt tự động khởi động MySQL theo hệ điều hành.

Lệnh 2: Tắt dịch vụ MySQL.
Lệnh 3: Sao lưu thư mục /var/lib/mysql thành thư mục /var/lib/mysql.old.
Screen Shot 2020 07 24 at 1.47.58 PM

Lệnh 4: Di chuyển vào thư mục custombuild.
Screen Shot 2020 07 24 at 1.50.43 PM

Lệnh 5: Điều chỉnh cấu hình phiên bản MySQL lên bản 5.6 (Bạn có thể thay đổi thành phiên bản khác nếu muốn).
Screen Shot 2020 07 24 at 1.51.43 PM

Lệnh 6: Sử dụng hệ quản trị cơ sở dữ liệu là MySQL.
Screen Shot 2020 07 24 at 1.52.25 PM

Lệnh 7: Tắt sao lưu database tự động vì hiện tại MySQL đã không còn hoạt động.
Screen Shot 2020 07 24 at 1.56.04 PM

Lệnh 8: Cập nhật lại custombuild script.
Screen Shot 2020 07 24 at 1.57.42 PM

Lệnh 9: Bắt đầu quá trình cài lại MySQL.

Quá trình cài lại MySQL cũng không mất quá nhiều thời gian. Sau khi cài xong chúng ta sử dung tiếp lệnh mysqld -V để xem phiên bản mới vừa được cài đặt nhé.

Như vậy là VPS của mình đã được hạ cấp MySQL từ bản 8.0.20 về bản MySQL 5.6.48.

# Tổng kết

Thông qua bài này các bạn đã nắm được cách hạ cấp MySQL trên DirectAdmin nhanh gọn. Tuy nhiên mình không khuyến khích làm như vậy trừ trường hợp bất khả kháng như dịch vụ MySQL của bạn đã chết hoàn toàn hoặc một vài lý do khác.

Chúc các bạn thực hiện thành công.
