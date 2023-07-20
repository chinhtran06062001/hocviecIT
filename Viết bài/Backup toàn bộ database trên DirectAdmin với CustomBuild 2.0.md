# 1. Tổng quan

Trong một vài trường hợp nhất định bạn sẽ muốn backup toàn bộ database trên DirectAdmin, trong đó có thể kể đến như là chuẩn bị nâng cấp/hạ cấp phiên bản MySQL/MariaDB, sao lưu định kỳ và một vài trường hợp khác nữa.

Và trong bài hôm nay mình sẽ hướng dẫ các bạn có thể backup toàn bộ database trên DirectAdmin với CustomBuild 2.0 chỉ với một vài thao tác đơn giản.

Lưu ý: Bắt buộc các hệ quản trị cơ sở dữ liệu MySQL/MariaDB vẫn còn hoạt động bình thường.

# 2. Hướng dẫn backup toàn bộ database trên DirectAdmin với CustomBuild 2.0

Để backup toàn bộ database trên DirectAdmin chúng ta thực hiện theo X bước sau.

### Bước 1: SSH vào hệ thống DirectAdmin của bạn

Để backup toàn bộ database trên DirectAdmin, đầu tiên chúng ta cần làm là SSH hoặc truy cập VPS hoặc máy chủ của bạn với quyền root trước.

Sau khi đã SSH thành công chúng ta tiếp tục với bước 2 để bắt đầu quá trình backup toàn bộ database trên DirectAdmin với CustomBuild 2.0.

### Bước 2: Backup toàn bộ database trên DirectAdmin với CustomBuild 2.0

Đầu tiên chúng ta cần xem phiên bản CustomBuild đang sử dụng có phải là 2.0 hay không.

Trong trường hợp phiên bản CustomBuild của bạn thấp hơn 2.0 thì bạn cần nâng cấp CustomBuild 1.x lên 2.0

Sau khi kiểm tra đã có CustomBuild 2.0 chúng ta thực hiện một số lệnh sau:

```sh
cd /usr/local/directadmin/custombuild
./build set mysql_backup yes
./build mysql_backup
```

Giải thích các lệnh trên:

Lệnh 1: Di chuyển để thư mục custombuild.
Lệnh 2: Điều chỉnh cấu hình bật tính năng sao lưu database.
Lệnh 3: Khởi chạy quá trình sao lưu database.

Nếu các bạn chưa biết thư mục mysql_backup chứa các database nằm ở đâu thì có thể sử dụng lệnh sau:

```sh
cat /usr/local/directadmin/custombuild/options.conf | grep mysql_backup_dir
```

Dưới đây là kết quả của mình:

Vậy là thư mục chứa các database được backup ra sẽ là /usr/local/directadmin/custombuild/mysql_backups. Có thể ở trên VPS/Server của bạn sẽ khác, tùy vào cấu hình ở tệp tin /usr/local/directadmin/custombuild/options.conf.

Hoặc bạn cũng có thể thay đổi đường dẫn này bằng cách sử lại cấu hình của tệp tin options.conf nếu muốn.

Vì mình chỉ có một user demo2 với 1 database demo2_test thôi nên khi chạy lệnh ./build mysql_backup thì quá trình này rất nhanh, và chỉ có 2 database được sinh ra, trong đó có một database mặc định.

Kiểm tra danh sách tệp tin tại thư mục này cũng thấy 2 database tương tự log trên.

Trong trường hợp thư mục mysql_backups của bạn đã tồn tại dữ liệu rồi và bạn không muốn bị ghi đè thì có thể thay đổi tên thư mục hiện tại với lệnh sau:

Sau khi chạy lệnh này tên thư mục mysql_backups sẽ được đổi thành tên mới dạng mysql_backups.YYYY-mm-dd như hình sau:

Vậy là hoàn tất quá trình backup toàn bộ database trên DirectAdmin.

# 3. Tổng kết

Qua bài viết này bạn đã nắm được cách thức thực hiện việc backup toàn bộ database trên DirectAdmin cũng như thay đổi đường dẫn database sẽ được sao lưu ra. Hy vọng bài viết này sẽ thật sự hữu ích với các bạn.

Chúc các bạn thực hiện thành công.
