# Centros là gì ?
Centos là một hệ điều hành miễn phí được xây dựng và phát triển dựa trên hệ điều hành mã nguồn mở Linux. Centos là chữ viết tắt của “Community Enterprise Operating System”. CentOS ra mắt vào tháng 5/2004 và được phát triển dựa trên bản phân phối của Red Hat Enterprise Linux (RHEL).
# Cài Đặt centos 7

Bước 1: Khởi động máy ảo VMware > File > New Virtual Machine.

![image](https://user-images.githubusercontent.com/101684058/158751797-fed10714-dd3a-44f0-b885-6e6d63c774fb.png)

Bước 2: Chọn Custom > Next.

![image](https://user-images.githubusercontent.com/101684058/158751881-93419d62-c866-482a-b2b3-197a2ed80b42.png)

Bước 3:  check vào ô I will install the operating system later. > Next

![image](https://user-images.githubusercontent.com/101684058/158753579-47e7eec2-6372-4103-bce8-f890f12a2ed7.png)

Bước 4:  Chọn Linux > Version: Centos 7 64-bit (ở đây, máy của mình là 64bit nên mình sẽ chọn là centos 7 64-bit).

![image](https://user-images.githubusercontent.com/101684058/158753793-567afd2b-8106-4888-bd72-49f381585dbf.png)

Bước 5:  Đặt tên và chọn nơi lưu file (đây là file đĩa ảo, file này khá nặng nên lưu ở ổ đĩa nào còn trống nhiều dung lượng để tránh gặp lỗi khi cài đặt).

![image](https://user-images.githubusercontent.com/101684058/158753921-0eccb0e3-9022-4ee2-86f4-36a72cf68b49.png)

Bước 6: Chọn tốc độ xử lý của máy ảo

![image](https://user-images.githubusercontent.com/101684058/158753984-1599ce41-cee9-4e23-8990-b2b404ce698c.png)

Bước 7: Chọn RAM,  nếu ram bạn nhiều thì có thể để lên cao hơn nữa.

![image](https://user-images.githubusercontent.com/101684058/158755451-5a6e2ff8-fcac-426f-aaab-3930290e72ff.png)

Bước 8: Thiết lập card mạng cho máy ảo ( bạn có thể chọn card nat hoặc bried)

![image](https://user-images.githubusercontent.com/101684058/158755747-9fa43f70-bcb1-4b56-a800-054ac312472f.png)

Bước 9:  Thiết lập chế độ nhập xuất

![image](https://user-images.githubusercontent.com/101684058/158755851-3689c8c1-f615-4455-ac0c-ef23037ed5c5.png)

Bước 10: tiếp click Next

![image](https://user-images.githubusercontent.com/101684058/158755939-a50cd4cb-ec2c-406c-9e36-fda9d9deaf7a.png)

Bước 11:  Tạo một ổ đĩa ảo mới. Chọn Create a new virtual disk > Next

![image](https://user-images.githubusercontent.com/101684058/158756015-fe7b88a1-6600-4350-9ee4-73fd365af560.png)

Bước 12: Chọn dung lượng cho ổ đĩa đó, mình để mặc định là 40GB. NHỚ CHỌN Store virtual disk as a single file

![image](https://user-images.githubusercontent.com/101684058/158756117-eba81de8-84dd-40d3-afc6-39e558abdcab.png)

Bước 13: Chọn đường dẫn lưu file ổ đĩa ảo, sau này có thể copy và chuyển qua máy tính khác mã vẫn dùng được máy ảo.

![image](https://user-images.githubusercontent.com/101684058/158756309-0088fd3d-5dd8-4f17-b8d9-33fbfe3c88ed.png)

Bước 14: Chọn Customize Hardware để kiếm tra lại các thiếp lập.

![image](https://user-images.githubusercontent.com/101684058/158756421-9aae4c79-9347-49f1-8220-113a68c037cf.png)

Bước 15:  New CD/DVD  (IDE) > Use ISO image file và chọn đến đường dẫn file ISO centos 7 đã tải về ở trên. Sau đó ấn Close

![image](https://user-images.githubusercontent.com/101684058/158756643-d795129d-9b5f-4a2f-b8c4-bd0bed36c5c5.png)

Bước 16: Chọn Finish

![image](https://user-images.githubusercontent.com/101684058/158756812-228f25ea-fc7b-4352-bfed-3dbe14f4d619.png)

Bước 17: Khởi động centos bằng Power on this virtual machine

![image](https://user-images.githubusercontent.com/101684058/158757020-26054bfc-ff69-4b7b-a786-365b40b8a1ed.png)

Bước 18: Chọn Install centos 7

![image](https://user-images.githubusercontent.com/101684058/158757722-a925a373-bcc5-41ac-b787-43beddc3a30d.png)

Bước 19: Thiết lập ngôn ngữ > Continue (english khuyến cáo).

![image](https://user-images.githubusercontent.com/101684058/158758101-ce16f717-4fee-4deb-a107-81eec621986c.png)

Bước 20: Thiết lập ngày, giờ. DATE & TIME > Done (set giờ việt nam nhé, cứ trỏ chuột vào bản đồ việt nam)

![image](https://user-images.githubusercontent.com/101684058/158758815-1fdbca9f-c661-4e97-8799-9d71125b2077.png)

Bước 21: Ở mục SOFTWATE SELECTION, chọn giao diện đồ hoạ (GUI) để dễ dàng thao tác:


Server with GUI > KDE > Done

![image](https://user-images.githubusercontent.com/101684058/158759116-879e493c-39e1-43c5-8949-eb44cf20bb48.png)

Bước 22: Mục INSTALLATION DESTINATION, chọn ổ đĩa ảo mình đã tạo lúc nãy > Done

![image](https://user-images.githubusercontent.com/101684058/158759337-caa417e3-d78c-42a4-8530-1e8447752204.png)

Bước 23: Mục NETWORK & HOST NAME, chọn ON > Done

![image](https://user-images.githubusercontent.com/101684058/158759483-2be395bf-27c1-4c5f-ba9c-a940fe095e85.png)

Bước 24: Chọn Begin Installation

![image](https://user-images.githubusercontent.com/101684058/158759583-decd030d-f683-451d-87c2-71307e5dd4e7.png)

Bước 25: Thiết lập tài khoản ROOT, tài khoản này rất quan trọng nên cần phải ghi nhớ mật khẩu

![image](https://user-images.githubusercontent.com/101684058/158762032-63b5c691-5af3-4fff-8e7c-ce0a63420dc7.png)

Bước 26:  Chờ máy tự động cài đặt, bạn chờ khoảng 3 đến 5 phút tuỳ vào cấu hình của máy tính. Click Reboot

![image](https://user-images.githubusercontent.com/101684058/158762751-5f551661-f5ce-4c72-89c5-b5e0d1948b45.png)


Bước 27: Tạo tài khoản để đăng nhập hệ thống

![image](https://user-images.githubusercontent.com/101684058/158763196-0847b90b-4f38-4912-ab71-13f5d84d7626.png)

Bước 28: Set mật khẩu cho tài khoản của bạn vừa tạo lúc nãy. LƯU Ý 2 MẬT KHẨU ROOT VÀ USER KHÁC NHAU

![image](https://user-images.githubusercontent.com/101684058/158763541-0250058d-df5f-461f-96fa-95706e7aa95a.png)

Bước 29: Giờ ta đã có thể chạy được Centos trên máy ảo VMware.

![image](https://user-images.githubusercontent.com/101684058/158763795-79ce3953-6071-490e-98d7-6e5dfe9a0ee2.png)
