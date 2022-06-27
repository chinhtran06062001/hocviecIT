## Hướng dẫn sử dụng 

1. Hướng dẫn add domain mới

Domain : xn--chnhtrn-8ya8069d.vn

Nhu cầu: domain cho 10 tài khoản

Bước 1: Vào configuration -> domain -> add -> local domain

Domain : Tên domain cần đưa vào

Description : Miêu tả  thông tin liên quan

User count : Giới hạn số user cho domain

![image](https://user-images.githubusercontent.com/97047640/175846928-0d89aa09-b13d-40b7-8dd8-29e9f1c22075.png)

![image](https://user-images.githubusercontent.com/97047640/175848711-db60af2d-8272-4474-8141-a1698e3f2c50.png)

Bước 2 : Tab Security

Chọn theo như trong hình : 2 thông số trên nhằm đảm bảo vấn đề liên quan đến password.

![image](https://user-images.githubusercontent.com/97047640/175848766-068dad17-1706-41ce-ac37-bdf8be768019.png)

Bước 3: Tab Mesages

Giới hạn dung lượng mail gửi ra : 50MB

Ngoài ra bạn có thể cấu hình thêm phần Items mục địch nhằm tối ưu hệ thống dung lượng của user.

![image](https://user-images.githubusercontent.com/97047640/175849447-5ee61525-6a15-4b80-846f-cd5f5dbefb8d.png)

Bước 4: Tab Directory Service

Ở phần này nếu bạn có sử dụng Microsoft Active Directory thì bạn cấu hình tại đây. Ở phần này mình không có sử dụng AD nên mình không cấu hình.

![image](https://user-images.githubusercontent.com/97047640/175849528-7788b838-3afd-4d81-8178-0c023d33383a.png)

Bước 5: Tab Custom Logo

Ở đây nếu bạn có công ty logo riêng thì bạn có thể upload lên đây : Kích thước đề nghi 142×45

Cài đặt thành công cho 1 domain !

![image](https://user-images.githubusercontent.com/97047640/175849606-6c940ddf-f340-44d5-a88d-5ebca727e46e.png)

Bước 6 : Set domain xn--chnhtrn-8ya8069d.vn thành domain chính để quản lý.

Chuột phải vào domain xn--chnhtrn-8ya8069d.vn

![image](https://user-images.githubusercontent.com/97047640/175850484-8b3f8c24-a441-4970-81b3-0bf5b52bb2de.png)

![image](https://user-images.githubusercontent.com/97047640/175850509-13f63d48-d6d0-44b2-977b-7df30c9262f6.png)

2. Hướng dẫn tạo user cho domain xn--chnhtrn-8ya8069d.vn vừa tạo

Bước 1: Login vào account -> User -> chọn domain

![image](https://user-images.githubusercontent.com/97047640/175851362-7117a040-12e1-4b97-8676-2c2ac8ad77e6.png)

Bước 2: Add user vào domain trên

Chọn add -> điền thông tin user

Bước 3: Tại tab General Điền đầy đủ thông tin

![image](https://user-images.githubusercontent.com/97047640/175851552-969598e2-f3d7-4cab-9ef8-ecb10ad5f8a7.png)

Bước 4: Tab contact
Ở phần này bạn có thể điền tùy ý thông tin hoặc không điền cũng không có vấn đề gì

![image](https://user-images.githubusercontent.com/97047640/175851871-a18c7473-56e5-41ac-9e73-3521b6324820.png)

Bước 5: Nếu bạn có group riêng thì bạn vào phần group để cấu hình

Ví dụ : Group IT, group Nhân sự, group kinh doanh … nếu không có thì không cần cấu hình

Bước 6: Tab Rights

Ở tab này là phần gán quyền cho user trên, nếu là admin thì cần quyền gì, user thì quyền gì

ví dụ admin có toàn quyền trên domain xn--chnhtrn-8ya8069d.vn , cái này như phần quyền cho admin cấp thấp hơn quản lý.

Nếu không bạn có thể cho admin có toàn quyền trên server.

![image](https://user-images.githubusercontent.com/97047640/175851980-a4c40e24-e9f2-4a76-aff3-2759ee85d7f9.png)

Bước 6: Tab Quota

Để giới hạn dung lượng cho mỏi user thì bạn vào đây để cấu hình

Ở đây mình giới hạn user 500 MB

![image](https://user-images.githubusercontent.com/97047640/175852034-5986082b-45a4-4782-86f4-f0a1dc3407c1.png)

Bước 7: Tab mesages

Ở phần này tương tự như phần cấu hình chính sách tại phần cấu hình domain, tuy nhiên nếu bạn là admin thì và bạn muốn cấu hình riêng cho từng user thì bạn cấu hình tại đây. Nếu không thì tất cả các user sẽ được cấu hình chính sách theo domain chính.

Ví dụ : domain chính là xn--chnhtrn-8ya8069d.vn giới hạn gửi mail là 50Mb thì tất cả user đều bị giới hạn, nhưng bạn muốn sếp có quyền hạn gởi mail 100MB thì bạn sẽ cấu hình tại đây để sếp được ngoại lệ.

![image](https://user-images.githubusercontent.com/97047640/175852138-c8794d97-1fab-4ebd-b17f-fc7834d4662e.png)

Bước 8: Kiểm tra lại domain vừa tạo có hoạt động hay không
https://IP_Server_mail:4040/admin

![image](https://user-images.githubusercontent.com/97047640/175852242-6032d0c7-bdd5-496c-9ec5-190f2b5d966b.png)

![image](https://user-images.githubusercontent.com/97047640/175852298-0fd15448-c5d6-4f04-ba74-14082ff0a925.png)

![image](https://user-images.githubusercontent.com/97047640/175852342-3fc6ffc2-8402-4827-bdc9-1553b74b59a9.png)

Như vậy là bạn đã login thành công. (Đây là trang admin quản trị của user admin)

Tóm lại : Bạn đã add một domain ngonmame.com vào hệ thống, và tạo một user admin quản trị domain này. Nếu bạn muốn add thêm user cho domain ngon mà mẹ này thì bạn cứ thực hiện add user là được.

Lưu ý : Bước kiểm tra là ta kiểm tra bằng IP, bây giờ bạn muốn trỏ login vào bằng domain thì bạn chỉ cần tạo một record mail.xn--chnhtrn-8ya8069d.vn trỏ về địa chỉ IP trên là được.

Mình cần lưu ý 2 thông tin sau :

Lưu ý : tùy vào từng công cụ quản trị domain thì có hình ảnh khác nhau và quản trị khác nhau nhưng các record thì giống nhau.

![image](https://user-images.githubusercontent.com/97047640/175852500-0f06196b-f766-48e2-b524-f42bfe2dba9b.png)

Kiểm tra lại hệ vấn đề trên bằng cách Ping và Kiểm tra mx record

![image](https://user-images.githubusercontent.com/97047640/175852651-5eedbc88-932d-45d9-8185-0646fdad7ef5.png)

Kiểm tra record MX

![image](https://user-images.githubusercontent.com/97047640/175852951-6fe4791b-42dc-47e5-8a6c-eaa0ff77046c.png)

Như vậy bạn đã login thành công ! Có thể gửi mail được rồi! (Đây là trang webmail cho client)
Kiểm tra truy cập bằng domain

![image](https://user-images.githubusercontent.com/97047640/175853000-5e924c79-e234-4be1-a74f-afa76fb93bf5.png)

