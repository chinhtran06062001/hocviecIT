# Mail server là gì?
Mail server (Email server) là hệ thống máy chủ được cấu hình riêng theo domain (tên miền) của doanh nghiệp. Hệ thống này được sử dụng để gửi, nhận thư điện tử, có đầy đủ thông số như một máy chủ thông thường như CPU, RAM, Storage,… Bên cạnh đó, Mail server còn có các yếu tố khác như số lượng tài khoản Email, Mail list, Email forwarder,…

Mail server có tính năng lưu trữ, sắp xếp Email qua internet. Mail server là giao thức quản lý, giao tiếp thư tín, giao dịch thương mại và truyền thông nội bộ. Hệ thống máy chủ Mail này có khả năng thao tác với tốc độ ổn định, nhanh chóng, đảm bảo an toàn và khả năng khôi phục dữ liệu cao.

# Phương thức hoạt động của Mail Server

1. Outgoing Mail server là gì?

Outgoing Mail server hay chính kà Mail server gửi đi. Mail này sử dụng giao thức SMTP, hỗ trợ dịch chuyển mail đơn giản, thường dùng để liên lạc với máy chủ từ xa và cho phép gửi nhiều thư cùng một lúc đến các máy chủ khác nhau.

2. Incoming Mail server là gì?

- POP3 : Chuyển Email đến và lưu ở máy tính chứa Mail Client thông qua ứng dụng Outlook, Windowns Mail, Mac Mail,...
- IMAP : Phương thức này cho phép nhiều máy khách kết nối cùng lúc đến một Mailbox. Bản gốc của Email được lưu tại Mail Server và Email từ Mailbox sẽ được sao chép đến máy khách.

# Các loại Mail Server

1. Mail Server Microsoft Và Google

Mail server này có nền tảng xây dựng quy mô và hệ thống bảo mật chặt chẽ, có khả năng quản lý hiệu quả dữ liệu hiện có. Giá của dịch vụ Mail server Microsoft và Google khá cao bởi nó hỗ trợ nhiều tiện ích khác nhau.

2. Mail Server độc lập

Đây là hệ thống Mail được thiết kế riêng cho các tổ chức hay ISP có khối lượng lớn Email, yêu cầu kiểm soát và các dịch vụ linh hoạt. Mail server độc lập bổ sung các tính năng như đồng bộ hóa Outlook, Webmail, hợp tác, quản trị từ xa, quản trị web nâng cao, kết nối CSDL, cung cấp sức mạnh và khả năng kiểm soát các hoạt động quy mô lớn.

# Những tính năng của Mail Server

![mail-server-cho-phep-gui-va-nhan-email-truc-tiep-qua-internet-](https://user-images.githubusercontent.com/97047640/173729749-ea314f97-69d2-4144-90f3-174bc364ccf0.png)

- Cho phép gửi và nhận Email trực tiếp qua internet với những tên miền cụ thể của từng tổ chức hay doanh nghiệp
- Hạn chế tối đa Email chứa virus hay spam
- Thông tin nội bộ được bảo mật chặt chẽ
- Mỗi người sử dụng Mail server sẽ được thiết lập dung lượng tối đa
- Thành viên thuộc hệ thống sẽ được quản lý tất cả nội dung Email
- Chức năng sao lưu dữ liệu di động được thiết lập, thông tin quan trọng được đảm bảo

# Tại sao nên sử dụng Mail server?

Sử dụng Mail server để:

- Có Email tên miền riêng cho doanh nghiệp, thể hiện sự chuyên nghiệp trong hoạt động
- Khả năng bảo mật cao
- Tốc độ
- Tích hợp nhiều tiện ích
- Kiểm tra Email mọi lúc mọi nơi trên tất cả các loại trình duyệt Mail
- Tùy biến chức năng và thông số cho mỗi User
- Khả năng ngăn chặn virus và spam hiệu quả
- Không gian lưu trữ riêng biệt
- Trang bị giao thức SSL nên có tính bảo mật cao
- Tránh được việc vô cớ rơi vào Blacklist nhờ sử dụng IP riêng
- Tính năng Forward Email giúp cài đặt Mail Offline

# Thuật ngữ thường đi kèm Mail Server

- TLS Mail Server là gì?

TLS là bảo mật tầng truyền tải (Transport Layer Security). TLS hoạt động cùng với tầng ổ bảo mật SHL (Secure Sockets Layer). Mục đích chính cung cấp phương thức vận chuyển mã hoá cho đăng nhập được chứng thực của SASL.

- SASL Mail Server là gì?

SASL là lớp xác thực và bảo mật đơn giản (Simple Authentication and Security Layer). Để xác thực người dùng. SASL thực hiện xác thực, sau đó TLS cung cấp vận chuyển mã hoá dữ liệu xác thực.

- Webmail là gì?

Webmail là email trên nền website. Một số webmail mà các bạn có thường thấy như hotmail, gmail, yahoo mail. Webmail cho phép người dùng truy cập email bất cứ lúc nào.

- SMTP-IN Queue là gì?

Trước khi phân tán thư đến các Local queue hoặc Remote Queue, giao thức SMTP sẽ làm một thao tác sao lưu toàn bộ thư điện tử gửi đi từ email server của doanh nghiệp ở SMTP-IN Queue. Nói cách khác, SMTP-IN Queue chính là kho lưu trữ thông tin thư từ trước khi được gửi đi.

- Local Queue là gì?

Sau khi tiếp nhận thông tin thư từ, hệ thống sẽ tự động điều phối phân loại và xếp thư từ theo thứ tự ngay hàng thẳng lối trước khi chuyến vào hộp thư của người nhận. Việc xếp hàng các bức thư chính là Local Queue.

Để tăng cường khả năng bảo mật và giữ an toàn cho hệ thống email server, trước khi thư được gửi đến người dùng, local queue và remote queue sẽ tiến hành quét virut. Sau đó kiểm tra spam để chắc chắn về chất lượng thư gửi đi. Tránh trường hợp mail server bị các Blacklist liệt vào danh sách IP spam.

- Local Mailboxes là gì?

Local Mailboxes là hộp thư của các account có đăng kí tài khoản mail server của công ty.

- Email Authentication là gì?

Email Authentication là tính năng xác nhận danh tính của các user khi truy cập vào hộp thư email. Tính năng này giúp bạn bảo mật thông tin thư từ của chính mình. Nói cách khác Alternate Email là một dạng email dự phòng. Khi quên mật khẩu của mail server, bạn có thể sử dụng email này để giúp bạn lấy lại mật khẩu một cách nhanh chóng.

- Mail Exchanger Record (MX) là gì?

MX record có nhiệm vụ là chỉ đường cho email đi đến mail server của bạn. MX record thường đi kèm theo một A record sẽ trỏ về địa chỉ IP của mail server. Một thông số pref có giá trị số để chỉ ra mức độ ưu tiên của các mail server. Giá trị pref càng nhỏ thì mức độ ưu tiên càng cao.
