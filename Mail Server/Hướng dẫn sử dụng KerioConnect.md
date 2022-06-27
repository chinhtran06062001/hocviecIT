## Hướng dẫn sử dụng 

1. Hướng dẫn add domain mới

Domain : ngonmame.com

Nhu cầu: domain cho 10 tài khoản

Bước 1: Vào configuration -> domain -> add -> local domain
Domain : Tên domain cần đưa vào

Description : Miêu tả  thông tin liên quan

User count : Giới hạn số user cho domain

Bước 2 : Tab Security
Chọn theo như trong hình : 2 thông số trên nhằm đảm bảo vấn đề liên quan đến password.

Bước 3: Tab Mesages
Giới hạn dung lượng mail gửi ra : 50MB

Ngoài ra bạn có thể cấu hình thêm phần Items mục địch nhằm tối ưu hệ thống dung lượng của user.

Bước 4: Tab Directory Service
Ở phần này nếu bạn có sử dụng Microsoft Active Directory thì bạn cấu hình tại đây. Ở phần này mình không có sử dụng AD nên mình không cấu hình, bạn nào muốn cấu hình thì commend phía dưới bài viết mình sẽ hỗ trợ riêng.

Bước 5: Tab Custom Logo
Ở đây nếu bạn có công ty logo riêng thì bạn có thể upload lên đây : Kích thước đề nghi 142×45

Cài đặt thành công cho 1 domain !

Bước 6 : Set domain ngonmame.com thành domain chính để quản lý.
Chuột phải vào domain ngonmame.com

2. Hướng dẫn tạo user cho domain ngonmame.com vừa tạo

Bước 1: Login vào account -> User -> chọn domain

Bước 2: Add user vào domain trên
Chọn add -> điền thông tin user

Bước 3: Tại tab General Điền đầy đủ thông tin

Bước 4: Tab contact
Ở phần này bạn có thể điền tùy ý thông tin hoặc không điền cũng không có vấn đề gì

Bước 5: Nếu bạn có group riêng thì bạn vào phần group để cấu hình
Ví dụ : Group IT, group Nhân sự, group kinh doanh … nếu không có thì không cần cấu hình

Bước 6: Tab Rights
Ở tab này là phần gán quyền cho user trên, nếu là admin thì cần quyền gì, user thì quyền gì

ví dụ admin có toàn quyền trên domain ngonmame.com , cái này như phần quyền cho admin cấp thấp hơn quản lý.

Nếu không bạn có thể cho admin có toàn quyền trên server.

Bước 6: Tab Quota
Để giới hạn dung lượng cho mỏi user thì bạn vào đây để cấu hình

Ở đây mình giới hạn user admin 500 MB

Bước 7: Tab mesages
Ở phần này tương tự như phần cấu hình chính sách tại phần cấu hình domain, tuy nhiên nếu bạn là admin thì và bạn muốn cấu hình riêng cho từng user thì bạn cấu hình tại đây. Nếu không thì tất cả các user sẽ được cấu hình chính sách theo domain chính.

Ví dụ : domain chính là ngonmame.com giới hạn gửi mail là 50Mb thì tất cả user đều bị giới hạn, nhưng bạn muốn sếp có quyền hạn gởi mail 100MB thì bạn sẽ cấu hình tại đây để sếp được ngoại lệ.

Bước 8: Kiểm tra lại domain vừa tạo có hoạt động hay không
https://IP_Server_mail:4040/admin

Như vậy là bạn đã login thành công. (Đây là trang admin quản trị của user admin)

Tóm lại : Bạn đã add một domain ngonmame.com vào hệ thống, và tạo một user admin quản trị domain này. Nếu bạn muốn add thêm user cho domain ngon mà mẹ này thì bạn cứ thực hiện add user là được.

Lưu ý : Bước kiểm tra là ta kiểm tra bằng IP, bây giờ bạn muốn trỏ login vào bằng domain thì bạn chỉ cần tạo một record mail.ngonmame.com trỏ về địa chỉ IP trên là được.

Ví dụ : mail.ngonmame.com A 103.27.62.9 

Mình cần lưu ý 2 thông tin sau :

Lưu ý : tùy vào từng công cụ quản trị domain thì có hình ảnh khác nhau và quản trị khác nhau nhưng các record thì giống nhau.

Kiểm tra lại hệ vấn đề trên bằng cách Ping và Kiểm tra mx record

Kiểm tra record MX

Như vậy bạn đã login thành công ! Có thể gửi mail được rồi! (Đây là trang webmail cho client)
Kiểm tra truy cập bằng domain
