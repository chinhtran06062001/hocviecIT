# 1. Tổng quan

Trong bài này mình sẽ hướng dẫn hạ cấp hạ cấp MariaDB trên DirectAdmin một các đơn giản và nhanh chóng nhất. Tuy nhiên việc hạ cấp là một việc không nên làm trừ khi bạn bắt buộc phải làm như vậy.

Mình có thấy rất nhiều bài viết hướng dẫn hạ cấp ở trên Google, tuy nhiên đa số đều không phải hướng dẫn chính thống từ DirectAdmin và một số nhiều trong đó không hoạt động được. Và bài này mình sẽ dựa theo các bài viết chính thống của DirecAdmin, đường dẫn bài viết này mình sẽ để ở cuối bài viết.

Lưu ý quan trọng: Trong trường hợp bài viết này là bạn đã sao lưu toàn bộ database của mình rồi hoặc bạn không còn gì để mất nữa.

# 2. Hướng dẫn hạ cấp MySQL trên DirectAdmin

Vì MariaDB sử dụng chung nhân MySQL nên đa số các lệnh khá tương đồng nhau. Để hạ cấp MariaDB trên DirectAdmin chúng ta cần thực hiện 3 bước sau.

### Bước 1: SSH vào hệ thống DirectAdmin của bạn

Để hạ cấp MariaDB trên DirectAdmin, đầu tiên chúng ta cần làm là SSH hoặc truy cập VPS hoặc máy chủ của bạn với quyền root trước.

Sau khi đã SSH thành công chúng ta tiếp tục với bước 2 để bắt đầu quá trình hạ cấp MariaDB trên DirectAdmin.

### Bước 2: Kiểm tra phiên bản MariaDB đang sử dụng hiện tại

Để kiểm tra phiên bản MariaDB hiện tại chúng ta sử dụng 1 lệnh sau.

```sh
mysqld -V
```

Hình dưới đây là kết quả của mình, với phiên bản đang cài hiện tại là 10.5.9.

![image](https://github.com/chinhtran06062001/hocviecIT/assets/97047640/a092a27c-9d74-458b-ab85-83375d7e2197)

Vậy là xong bước kiểm tra phiên bản MariaDB đang sử dụng hiện tại. Chúng ta tiếp tục với bước 3 để hạ cấp MariaDB trên DirectAdmin.

### Bước 3: Hạ cấp MariaDB trên DirectAdmin với Custombild 2.0

Đầu tiên chúng ta cần xem phiên bản CustomBuild đang sử dụng có phải là 2.0 hay không

Trong trường hợp phiên bản CustomBuild của bạn thấp hơn 2.0 thì bạn cần nâng cấp CustomBuild 1.x lên 2.0

Trong bước này bạn sẽ xóa hoàn toàn phiên bản MariaDB đang cài đi, tuy nhiên cũng đừng quá lo lắng vì chúng ta đã có bước sao lưu trước thư mục /var/lib/mysql để tránh mất dữ liệu database.

Dưới đây là các lệnh mà chúng ta cần thực hiện:

```sh
perl -pi -e 's/mysqld=ON/mysqld=OFF/' /usr/local/directadmin/data/admin/services.status
service mariadb stop 
mv /var/lib/mysql /var/lib/mysql.old
cd /usr/local/directadmin/custombuild
./build set mariadb 10.4
./build set mysql_inst mariadb
./build set mysql_backup no
./build update
./build mariadb
```

Giải thích các lệnh trên:

Lệnh 1: Tắt tự động khởi động MariaDB theo hệ điều hành.(Lưu ý: Khi copy lệnh này không được để dư khoảng trắng ở cuối lệnh).
Lệnh 2: Tắt dịch vụ MariaDB .
Lệnh 3: Sao lưu thư mục /var/lib/mysql thành thư mục /var/lib/mysql.old.
Lệnh 4: Di chuyển vào thư mục custombuild.
Lệnh 5: Điều chỉnh cấu hình phiên bản MariaDB lên bản 10.4 (Bạn có thể thay đổi thành phiên bản khác nếu muốn như 5.5, 10.0, 10.1, 10.2, 10.3 hoặc 10.4)
Lệnh 6: Sử dụng hệ quản trị cơ sở dữ liệu là MariaDB.
Lệnh 7: Tắt sao lưu database tự động vì hiện tại MariaDB đã không còn hoạt động.
Lệnh 8: Cập nhật lại custombuild script.
Lệnh 9: Bắt đầu quá trình cài lại MariaDB.

Dưới đây là một số hình ảnh trong quá trình hạ cấp của mình:

![image](https://github.com/chinhtran06062001/hocviecIT/assets/97047640/9bcc7a5b-6634-4a19-a1be-28d8c61bc05b)

Lệnh 1: Tắt tự động khởi động MariaDB theo hệ điều hành.

![image](https://github.com/chinhtran06062001/hocviecIT/assets/97047640/3c8f7f80-09af-4606-b3bf-8dac977cbf1a)

Lệnh 2: Tắt dịch vụ MariaDB.

![image](https://github.com/chinhtran06062001/hocviecIT/assets/97047640/31fbfcea-492e-4607-8d51-bb88048b5378)

Lệnh 3: Sao lưu thư mục /var/lib/mysql thành thư mục /var/lib/mysql.old (hoặc bạn có thể đặt tên khác nếu muốn).

![image](https://github.com/chinhtran06062001/hocviecIT/assets/97047640/6de9e86f-bae4-4531-a6f5-7403918ba8f7)

Lệnh 4: Di chuyển vào thư mục custombuild.

![image](https://github.com/chinhtran06062001/hocviecIT/assets/97047640/a210a385-d333-46f8-a3b2-4e264f6c5e1f)

Lệnh 5: Điều chỉnh cấu hình phiên bản MariaDB sang bản 10.4 (Bạn có thể thay đổi thành phiên bản khác nếu muốn).

![image](https://github.com/chinhtran06062001/hocviecIT/assets/97047640/8bce6f72-2d01-452a-bf8f-ae7190c47e39)

Lệnh 6: Sử dụng hệ quản trị cơ sở dữ liệu là MariaDB.

![image](https://github.com/chinhtran06062001/hocviecIT/assets/97047640/683bceab-42ea-4af0-b052-ba1748a51551)

Lệnh 7: Tắt sao lưu database tự động vì hiện tại MariaDB đã không còn hoạt động.

![image](https://github.com/chinhtran06062001/hocviecIT/assets/97047640/c4e6a0ee-ed64-4ae4-93de-318e078e8ba1)

Lệnh 8: Cập nhật lại custombuild script.

![image](https://github.com/chinhtran06062001/hocviecIT/assets/97047640/9abdacf4-8b9f-4af7-9a3c-2788fb579905)

Lệnh 9: Bắt đầu quá trình cài lại MariaDB.

Quá trình cài lại MariaDB cũng không mất quá nhiều thời gian. Sau khi cài xong chúng ta sử dung tiếp lệnh mariadb -V hoặc mysqld -V để xem phiên bản mới vừa được cài đặt nhé.

Phiên bản MariaDB được cài đặt là 10.4.13.

![image](https://github.com/chinhtran06062001/hocviecIT/assets/97047640/897cf092-984e-4d73-b057-25af570d855b)

Như vậy là VPS của mình đã được hạ cấp MariaDB từ bản 10.5.9 về bản MariaDB 10.4.26.

# Tổng kết

Thông qua bài này các bạn đã nắm được cách hạ cấp MariaDB trên DirectAdmin nhanh gọn. Tuy nhiên mình không khuyến khích làm như vậy trừ trường hợp bất khả kháng như dịch vụ MariaDB của bạn đã chết hoàn toàn hoặc một vài lý do khác.

Chúc các bạn thực hiện thành công.
