# Giải pháp tăng cường bảo mật cho dịch vụ Email Server

**Sử dụng riêng biệt**

Đối với dịch vụ Email Server Riêng, chỉ 1 mình Quý khách sử dụng 1 server, thay vì sử dụng chung server với nhiều khách hàng khác (Email Pro) sẽ đảm bảo được tính ổn định, bảo mật, không bị ảnh hưởng, chia sẻ tốc độ, băng thông với nhau, đảm bảo hiệu suất hoạt động tốt nhất. Khi sử dụng riêng Quý khách cũng sẽ dễ dàng yêu cầu tùy chỉnh các cấu hình server theo chính sách của công ty mình mà các dịch vụ share không làm được.

**Mua chứng chỉ SSL**

Mua thêm chứng chỉ SSL cho tên miền mail.tenmien để đảm bảo mã hóa các thông tin truyền tải giữa client & server. Bắt buộc users phải sử dụng giao thức SSL khi sử dụng email.

**Sử dụng VPN**

Xây dựng VPN Server tại văn phòng để quản lý việc sử dụng của users nhằm bảo mật hơn thông tin tài khoản email, giới hạn chỉ sử dụng từ IP tĩnh công ty hoặc IP VPN để tránh bị lợi dụng khi mất thông tin, bị scan password khi sử dụng ngoài công ty.

**Chữ ký số**

Sử dụng chữ ký số trong các email giao dịch quan trọng liên quan tới tiền bạc và các thông tin quan trọng. Quý khách và đối tác cùng sử dụng chữ ký số riêng của mình để đảm bảo email nhận được chắc chắn là đúng người gửi.

**Xác thực 2 lớp (Two Factor Authentication)**

Xác thực 2 lớp hay còn được viết tắt là 2FA (Two-factor authentication) bổ sung một bước khi đăng nhập. Nếu không có 2FA, việc đăng nhập của bạn chỉ đơn thuần là nhập Username và Password – thứ duy nhất bảo mật cho tài khoản của bạn. Do đó việc kết hợp thêm một lớp bảo vệ nữa (1 mã ngẫu nhiên từ phần mềm Google Authenticator đã cài đặt trước đó) về lí thuyết sẽ làm cho tài khoản của bạn trở nên an toàn hơn.

**Cài đặt Email footer/disclaimer/domain signature**

Các cài đặt trên sẽ tự động thêm vào nội dung cuối thư mỗi khi nhân viên gửi mail ra ngoài, mục đích sử dụng có thể vì lý do pháp lý, thông tin chung hoặc tuyên bố từ chối trách nhiệm nhằm thông báo cho người nhận về những gì họ có thể và không thể làm với các email được gửi từ công ty của bạn. Việc này cũng sẽ hạn chế được việc giả dạng gửi mail từ một tên miền khác, gần giống với tên miền công ty của bạn đến đối tác với mục đích lừa đảo (mail gửi sẽ không được kèm theo các cấu hình này từ server của bạn)

**Giới hạn truy cập theo quốc gia**

Nếu công ty của bạn chỉ sử dụng trong lãnh thổ Vietnam hoặc một số quốc gia cụ thể, việc giới hạn chỉ cho phép sử dụng tại các quốc gia biết trước này cũng sẽ giảm thiểu nguy cơ bị lợi dụng nếu không may người dùng bị mất thông tin, chiếm đoạt tài khoản.

**Tăng Cường bộ lọc Anti-spam/Anti-virus**

Sử dụng thêm Giải pháp EAP – Email AntiSpam Protection để bảo vệ thêm 1 lớp chống spam/anti-virus/anti-phishing cho hệ thống email bên cạnh bộ lọc sẵn có của dịch vụ Email Server  để ngăn chặn tốt hơn các mối đe dọa như thư rác, lừa đảo, giả mạo , lây lan virus trong nội bộ. Giải pháp ứng dụng trí tuệ nhân tạo (AI), công nghệ đám mây (Cloud) cùng với các trung tâm dữ liệu (Global DC) phủ sóng khắp thế giới giúp cập nhật liên tục các mối đe dọa mới nhất và ngăn chặn kịp thời hiệu quả.

**Backup dữ liệu**

Trường hợp dữ liệu của Quý khách quan trọng, cần thường xuyên backup lại dữ liệu Outlook trên máy tính, hoặc xây dựng hệ thống mail offline để backup tập trung. Ngoài ra Quý khách có thể tham khảo dịch vụ Email Backup do P.A Vietnam cung cấp để được backup trực tiếp dữ liệu trên server theo yêu cầu riêng.

**Xác nhận 2 chiều**

Đối với các giao dịch liên quan đến quan đến chuyển khoản thông qua ngân hàng, thay đổi thông tin tài khoản, … các giao dịch quan trọng liên quan đến tài chính cần kết hợp xác nhận thêm với phía đối tác thông qua 1 kênh khác song song như chat, tin nhắn, gọi điện thoại vào số cố định hoặc bằng văn bản.

**Bảo mật 2 chiều**

Cảnh báo các đối tác đang trao đổi, giao dịch qua email với công ty cần tăng cường các biện pháp bảo mật email server của đối tác để đảm bảo an toàn: Cấu hình kiểm tra SPF, DKIM, DMARC, MX… Mail là dịch vụ 2 chiều, việc bảo mật từ một phía sẽ không hạn chế triệt để được vấn đề.

**Bảo mật thông tin email**

Người dùng cần nâng cao ý thức bảo mật thông tin của email, hạn chế sử dụng đăng ký các dịch vụ online, thay đổi mật khẩu phức tạp và định kỳ, tắt các tính năng cho phép users cấu hình forwarding email ra ngoài hoặc giới hạn truy cập Web Mail nếu users không sử dụng. Luôn sử dụng giao thức SSL khi sử dụng mail, hạn chế sử dụng mail tại nơi công cộng.

**Quy định  bảo mật cho nhân viên**

Thiết lập các qui tắc bảo mật cho nhân viên trong công ty: đổi password định kỳ, không mở các mail lạ và đặc biệt là các file đính kèm từ những người lạ, không được tải và cài đặt các phần mềm không tin cậy lên mấy tính, thiết bị sử dụng email v.v…

**Sử dụng phần mêm bản quyền**

Sử dụng hệ điều hành và các phần mềm gửi nhận mail có bản quyền và tải từ các trang chính thức.

**Kiểm tra virus, mã độc**

Luôn kiểm tra và quét virus thường xuyên các thiết bị cá nhân dùng để nhận và gửi mail bằng phần mềm antivirus tin cậy.
