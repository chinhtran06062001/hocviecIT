# PHPMyAdmin là gì?

PhpMyAdmin là phần mềm mã nguồn mở được viết bằng ngôn ngữ PHP giúp quản trị cở sở dữ liệu MySQL thông qua giao diện web. Tính đến nay, phpMyAdmin đã có đến hàng triệu lượt sử dụng và vẫn không ngừng tăng. Vậy tính năng hữu ích mà phpMyAdmin mang lại là gì?



*phpMyAdmin được viết bằng ngôn ngữ PHP*


## Các tính năng của phpMyAdmin là gì?

![image](https://user-images.githubusercontent.com/62273292/160774929-f549f0eb-5649-4d5e-aa60-a152f3c76740.png)

Một số tính năng chung thường được sử dụng trên phpMyAdmin:

- Quản lý user(người dùng): thêm, xóa, sửa(phân quyền).

- Quản lý cơ sở dữ liệu: tạo mới, xóa, sửa, thêm bảng, hàng, trường, tìm kiếm đối tượng.
 
- Nhập xuất dữ liệu(Import/Export): hỗ trợ các định dạng SQL, XML và CSV.

- Thực hiện các truy vấn MySQL, giám sát quá trình và theo dõi.

- Sao lưu và khôi phục(Backup/Restore): Thao tác thủ công.

Điểm yếu trong việc sao lưu dữ liệu của phpMyAdmin là gì?

 
 Dù có nhiều ưu điểm song phpMyAdmin vẫn khó tránh khỏi một vài điểm yếu cố hữu. Đặc biệt, trong việc sao lưu dữ liệu thủ công sẽ không có một vài tính năng cần thiết.

Scheduling(sao lưu tự động theo lịch đặt trước): Một tính năng khá phổ biến ở những công cụ quản trị cơ sở dữ liệu.

Storage media support(hỗ trợ lưu trữ các phương tiện truyền thông): phpMyAdmin chỉ cho phép lưu các bản sao lưu vào các local drive có sẵn trên hệ thống, qua hộp thoại Save as của trình duyệt.
 
 ## Cách sử dụng PHPMyAdmin
 
- Truy cập vào phpMyAdmin

- Quản lý cơ sở dữ liệu

Bước 1 : Chọn thanh tab Databases, sau đó điền tên , chọn kiểu mã hoá.

![image](https://user-images.githubusercontent.com/97047640/173489584-ff687c50-8168-495d-9c5c-06a97e070a81.png)


Bước 2 : Nhấn vào Create sẽ cho kết quả hiện thị tại một database ở cột bên trái.

![image](https://user-images.githubusercontent.com/97047640/173489603-7d089b31-0122-42b6-af6e-9fd203084830.png)


- Quản lý table (bảng dữ liệu)

Bước 1: Sau khi tạo thành công một CSDL ở cột bên trái, bạn nhấn vào tên dữ liệu.

![image](https://user-images.githubusercontent.com/97047640/173489676-25bb5376-4f8e-4090-8f0c-1aa7668283db.png)

Bước 2: Tìm đến dòng Create Table để điền tên, trường của bảng mà bạn muốn tạo, cuối cùng nhấn GO.

![image](https://user-images.githubusercontent.com/97047640/173489918-a7cb635c-62e5-4ccd-9cf4-985afcce6c27.png)


- Sao lưu cơ sở dữ liệu

Bước 1 : Xuất Data ra khỏi hệ thống bằng cú pháp của cơ sở dữ liệu MySQL.


Bước 2 : Nếu sao lưu từ cột bên trái thì chọn Database, tab Export với định dạng là SQL, kiểu sao lưu là Quick.

- Phục hồi CSDL

Bước 1 : Tạo một cơ sở dữ liệu mới

Bước 2 : Từ cột bên trái các bạn chọn tên data rồi truy cập vào tav Import, chọn tên để tìm các file data, file chuẩn là file có đuôi .sql

Bước 3 : Bấm GO.
 
Chèn dữ liệu trong bảng
![image](https://user-images.githubusercontent.com/97047640/173491121-b9351b60-14ee-4a89-bf1b-dc3e1a03dc79.png)

![image](https://user-images.githubusercontent.com/97047640/173491163-69ea29f9-7a41-4319-9b38-4fb3eee418f4.png)


- Thực hiện truy vấn

Bước 1 : Chọn các bảng data từ bên trái để tìm xem câu lệnh SQL là gì.

Bước 2 : Bạn chọn CSDL rồi chèn câu lệnh vào, cuối cùng nhấn nút GO.

 ![image](https://user-images.githubusercontent.com/97047640/173491303-b3b8c37d-3beb-4eaa-8a88-693afb7b2172.png)

 Kết quả
 
![image](https://user-images.githubusercontent.com/97047640/173491337-a3de3bbe-a1f9-438f-afac-79196292b151.png)

 
 Ưu điểm của phpMyAdmin là gì?
 
- Tăng hiệu quả công tác quản lý cơ sở dữ liệu

-Cộng đồng hỗ trợ rộng lớn

-Đa ngôn ngữ

-Chi phí
 
 
 **Tăng hiệu quả công tác quản lý cơ sở dữ liệu**
 
 phpMyAdmin mang đến giao diện xử lý các thao tác trên cơ sở dữ liệu một cách trực quan. Từ đó, tiết kiệm thời gian, thao tác so với việc thực hiện bằng dòng lệnh trên command line.

Là công cụ đa năng có thể vừa làm việc với một đối tượng vừa xử lý lỗi hoặc các tính huống bất ngờ.

**Cộng đồng hỗ trợ rộng lớn**

phpMyAdmin có tính chất là một mã nguồn mở, được phát triển bởi rất nhiều lập trình viên trên toàn thế giới. Nhờ đó, người dùng sẽ nhận được sử hỗ trợ rất lớn từ cộng đồng.

**Đa ngôn ngữ**

Được duy trì bởi The phpMyAdmin Project hiện có sẵn đến 64 ngôn ngữ khác nhau.

**Chi phí**

Dù có nhiều ưu điểm và mang đến nhiều lợi ích vượt bậc, phpMyAdmin vẫn là công cụ hoàn toàn miễn phí.

## Nhược điểm của phpMyAdmin là gì?
 
 
 – Bảo mật
 
 Hạn chế lớn nhất của các mã nguồn mở chắc chắn là vấn đề bảo mật. Hạn chế truy cập vào URL của phpMyAdmin từ những địa chỉ IP cố định.
 
 – Sao lưu
 
 Như đã chia sẻ, thao tác sao lưu và phục hồi dữ liệu thủ công trên phpMyAdmin vẫn còn một số nhược điểm:

Không thể tự xuất database.

Chỉ có thể kết nối thông qua trình duyệt tức chỉ lưu được các bản sao lưu vào các local drive có sẵn trên hệ thống.

Định dạng file xuất bằng phpMyAdmin không được mã hóa(thiếu an toàn) và chiếm dung lượng đĩa lớn.
