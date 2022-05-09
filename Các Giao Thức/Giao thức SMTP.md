# VII. Giao thức SMTP

1. Tìm hiểu tổng quan về SMTP là gì?

- SMTP là 3 chữ cái đầu viết tắt của Simple mail Transfer Protocol dịch ra có nghĩa là giao thức truyền tải thư tín đơn giản hóa.
- Giao thức này thực hiện nhiệm vụ chính là gửi mail còn việc nhận mail hay truy xuất dữ liệu mail server sẽ có giao thức IMAP hay POP3 đảm nhiệm.

2. Chức năng SMTP

- Cho phép gửi mail với số lượng lớn,nhanh mà không bị giới hạn như các hòm mail miễn phí
- SMPT Server giúp bạn thao tác gửi thư qua giao thức TCP hoặc IP

2. Một số thông tin về máy chủ smtp có thể quan tâm

- SMTP dùng cổng 25 của giao thức TCP. Để xác định trình chủ SMTP của một tên miền nào đấy (domain name), người ta dùng một mẫu tin MX (Mail eXchange – Trao đổi thư) củaDNS (Domain Name System– Hệ thống tên miền).
- SMTP thường được thực hiện để hoạt động qua cổng Internet 25 (TCP). Tuy nhiên tại châu âu có một phương thức thay thế cho SMTP được sử dụng rộng rãi gọi là X.400.
- Nó xác định cấu trúc của các địa chỉ, yêu cầu tên miền và bất cứ điều gì liên quan đến email. SMTP cũng xác định các yêu cầu cho Post Office Protocol (POP) và truy cập Internet Message Protocol (IMAP) máy chủ, do đó email được gửi đúng cách.
- SMTP bắt đầu được sử dụng rộng rãi vào những năm đầu thập niên kỷ 1980.


3. Phương thức hoạt động của SMTP

Để mô tả hoạt động cơ bản của giao thức SMTP một cách dễ hiểu ta xét một hoạt cảnh phổ biến "An gửi một thông điệp cho Bình" ở hình

![image](https://user-images.githubusercontent.com/97047640/167374549-326d68aa-d94a-4e97-b9ba-2179c9930871.png)

- Bước 1 : An khởi động useragent của mình, cung cấp địa chỉ email của Bình, soạn thông điệp và chỉ thị user agent gửi mail
- Bước 2 : User agent của An gửi thông điệp đến mail server của an và thông điệp trong hàng đợi.
- Bước 3 : SNMP Client chạy trên mail server của An phát hiện ra thông điệp trong hàng đợi và tiến hành mở kết nối TCP đến SMTP server chạy trên mail server của Bình.
- Bước 4 : Sau khi thực hiện bắt tay chào hỏi (hand shaking), SMTP Client của An sẽ gửi thông điệp của An đến kết nối TCP.
- Bước 5 : Tại mail server của Bình, SMTP server nhận được thông điệp và lưu lại ở mailbox
- Bước 6 : Khi Bình khởi động user agent của mình thì sẽ thấy mail của an trong mailbox.

*Lưu ý: SMTP không sử dụng các mail server trung gian để gửi thư, mà chỉ sử dụng một kết nối TCP trực tiếp giữa hai mail server ngay cả khi hai mail server cách nhau một khoảng cách rất xa. Ví dụ : mail server của An ở TP.HCM và mail của Bình ở Mát-Xco-va (Thủ đô của Nga) thì chỉ có các kết nối TCP trực tiếp giữa 2 mail server.Khi mail của Bình bận,thì thông điệp được tiếp tục lưu ở hàng đợi của mail server của An và chờ đợi để gửi lại tin nhắn
