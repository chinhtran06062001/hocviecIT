# Cài đặt IIS trên Windows Server 2019

1. Chạy Powershell với quyền admin và cài đặt IIS.

![image](https://user-images.githubusercontent.com/97047640/169728950-e86214d7-30ba-466d-ad3d-a7314665841f.png)


2. Chạy Server Manager và nhấp vào Add roles and features.

![image](https://user-images.githubusercontent.com/62273292/158933760-7b52d094-f73e-464c-af9a-93107c241686.png)


3. Nhấp vào nút Next.

![image](https://user-images.githubusercontent.com/62273292/158933777-34fe646e-274a-4640-807b-611b3d3d9235.png)


4. Chọn Role-based or feature-based installation.

![image](https://user-images.githubusercontent.com/62273292/158933795-c6c6476e-a6ef-4034-904a-4cdd840f8281.png)


5. Chọn host bạn muốn thêm các service.

![image](https://user-images.githubusercontent.com/97047640/169729030-304acbc9-f947-4e26-a388-5a035a560978.png)


6. Tích vào hộp Web Server (IIS).

![image](https://user-images.githubusercontent.com/62273292/158933833-bf5a1e9a-6bc9-41a6-b29d-ca47a10f6c28.png)


7. Các tính năng bổ sung được yêu cầu để thêm IIS Server. Nhấp vào nút Add Features > Next.

![image](https://user-images.githubusercontent.com/62273292/158933855-04a5e530-933d-4c42-a5e3-2bfbd5d83424.png)


8. Nhấp vào nút Next.

![image](https://user-images.githubusercontent.com/62273292/158933873-e5cb9915-a818-46ce-9e5b-18a4d72b2103.png)


9. Nhấp vào nút Next.

![image](https://user-images.githubusercontent.com/62273292/158933884-88f0f708-ec0e-41c0-b4a4-b847ad825498.png)


10. Đây là phần chọn các tính năng của Web Server. Hãy chọn những tính năng mà bạn muốn thêm. Trong ví dụ này, các tùy chọn mặc định được giữ nguyên. Tất nhiên, bạn có thể thêm các tính năng này sau khi cài đặt IIS.

![image](https://user-images.githubusercontent.com/62273292/158933903-289fa707-e06c-4f25-b009-3567a755ab81.png)


11. Nhấp vào nút Install.

![image](https://user-images.githubusercontent.com/62273292/158933920-c5b6dbf5-5a4d-4068-be25-4d54142c3dbc.png)


12. Sau khi kết thúc cài đặt, nhấp vào nút Close.

![image](https://user-images.githubusercontent.com/62273292/158933941-7c655fd2-637d-450f-94f1-e72ea2d68b3d.png)


13. Chạy trình duyệt web và truy cập vào localhost, sau đó bạn có thể xác minh IIS có đang chạy bình thường không.

![image](https://user-images.githubusercontent.com/62273292/158933959-6bf3577b-d982-4dab-8f8d-7ca764d4b1bb.png)





# IIS với ASP Classic và ASP.net

![image](https://user-images.githubusercontent.com/62273292/160034648-6a5993a1-62f5-46a4-890a-750419c8b98d.png)

Chuột phải vào Site-> Add Website

![image](https://user-images.githubusercontent.com/62273292/160034679-aff86192-ab91-4b7d-bbf4-97ec415fc31c.png)


 Tiến hành cấu hình:
 
 Đặt tên site name, chọn đến Application Pool, ở đây mình chọn .NET v4.5, sau đó OK
(Ở đây các bạn có thể tạo Application pool, hướng dẫn tạo Application pool tại đây)

![image](https://user-images.githubusercontent.com/62273292/160034722-897dafef-60d9-45af-9354-b361274331ca.png)


Tiếp đến Physical Path: chọn đến đường dẫn thư mục có chứa file web config

Sau đó chọn Connect as => Specific user => Set tài khoản Microsoft bạn đang sử dụng trên máy, điền Username & Password => OK

![image](https://user-images.githubusercontent.com/62273292/160034768-435991d9-f666-422e-8a1d-fd52f5275c6c.png)

 Tiếp đến ô IP Address gõ đúng cái địa chỉ IP của localhost (ở đây là 127.0.0.1), Port 80 là mặc định, Host name: tùy ý. Sau đó nhấn OK
 
 ![image](https://user-images.githubusercontent.com/62273292/160034785-9ff6b55f-98ea-4c34-9af6-87c7658b4a47.png)


 Lúc này đã tạo thành công Site
 
 ![image](https://user-images.githubusercontent.com/62273292/160034819-73df15ee-51f4-4117-b089-db630f051c9b.png)


Lúc này vẫn chưa chạy được, chúng ta phải tiến hành chỉnh sửa file host:

Vào đường dẫn: C:\Windows\System32\drivers\etc, mở file hosts lên và làm như sau: Thêm dòng bôi vàng trong hình vào 127.0.0.1 test.lv.com (127.0.0.1: IP localhost, test.lv.com: Host name chúng ta đã thêm trong quá trình tạo Site), Lưu lại là OK

![image](https://user-images.githubusercontent.com/62273292/160034878-8530b6b6-8e95-4bcd-97cd-750298de8559.png)


 Mở trình duyệt gõ Host name chúng ta đã tạo, thì sẽ chạy được project Web của chùng ta mà không cần mở code lên chạy thủ công nữa.
 
 ![image](https://user-images.githubusercontent.com/62273292/160034915-e61a40ef-43df-4628-8225-6dcc91c43609.png)







## Kết quả

![image](https://user-images.githubusercontent.com/97047640/169738275-3a8c60d4-dc87-47e2-bd0e-7684df0311e4.png)


![image](https://user-images.githubusercontent.com/62273292/160043972-b70a311e-0fb0-4c33-946f-c90fca9b7038.png)

![image](https://user-images.githubusercontent.com/97047640/169738238-e507ef9c-8d40-4bb5-a58e-71516fcf5dc6.png)




