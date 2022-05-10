# Tìm hiểu giao thức UDP

I. Khái niệm

- UDP (User Datagram Protocol) được xem như là một gói tương tự như một gói của thông tin.Giao thức UDP làm việc tương tự như TCP, nhưng nó bao gồm tổng quan những thứ đã kiểm tra và có lỗi
- Khi tận dụng UDP, gói chỉ gửi đến bên nhận. Bên gửi sẽ không chờ đợi để đảm bảo rằng bên nhận đã nhận được các gói tin - nó sẽ tiếp tục gửi các gói tiếp theo. Nếu bạn là người nhận và bạn bỏ lỡ một số gói tin UDP vì quá xấu - bạn không thể yêu cầu những gói tin một lần nữa.
Không có gì để đảm bảo rằng bạn đang nhận được tổng quan các gói và không có cách nào để yêu cầu gói một lần nữa nếu bạn bỏ lỡ nó, nhưng bù vào đó, các máy tính hoàn toàn có thể giao tiếp một cách nhanh hơn, bình thường hơn.
- UDP được tận dụng khi tốc độ là nguyện ước và sửa lỗi không cần thiết. Ví dụ, UDP thường được tận dụng cho chương trình phát sóng trực tiếp và trò chơi trực tuyến.

II. Các thuật ngữ UDP
 - Packet : Trong truyền dữ liệu, một packet là một dãy các số nhị phân, biểu diễn dữ liệu và các tín hiệu điều khiển và tinh chỉnh, các gói tin này được chuyển đi và chuyển tới host. Trong gói tin, thông tin được sắp xếp theo một khuôn dạng cụ thể
 - Datagram : Là một gói tin độc lập, tự chứa, mang từ A đến Z dữ liệu để định tuyến từ nguồn tới đích mà không cần thông tin thêm.
 - MTU (Maximum Transmission Unit) : Là một đặc trưng của tầng mối liên quan mô tả số byte thông số tối đa hoàn toàn có thể truyền trong một gói tin. Mặt khác, MTU là gói dữ liệu lớn nhất mà trong môi trường mạng cho trước rất có thể truyền
 - Port : UDP tận dụng các cổng để ánh xạ các thông số đến vào một tiến trình cụ thể đang chạy trên một máy tính. UDP định đường đi cho packet tại vị trí định hướng với cách dùng số hiệu cổng được định hướng trong header của datagram. Các cổng được biểu hiện bởi các số 16-bit, vì thế các cổng nằm trong dải từ 0 - 65535. Các cổng cũng được xem như là các điểm cuối của các kết nối logic, và được chia thành 3 loại sau :
      + Các cổng phổ biến : từ 0-1023
      + Các cổng đã đăng ký : 1024 - 49151
      + Các cổng động/dành riêng 49152 - 65535
Chú ý rằng các cổng UDP có thể nhận nhiều hơn một thông điệp ở một thời điểm. Trong một tình huống, các dịch vụ TCP và UDP rất có thể sử dụng cùng một số hiệu cổng, như 7 (echo) hoặc trên cổng 23 (Telnet)

III. Các cổng UDP

|Cổng UDP|Mô tả |
|------------|-----------|
| 15 | Netstat - Network Status - Tình trạng mạng|
| 53 | DNS - Domain Name Server|
| 69 | TFTP - Trivial file Transfer Protocol Giao thức truyền tệp thông thường|
| 137 | NetBIOS Name Server|
| 138 | Dịch vụ Datagram NetBIOS|
| 161 | SNMP|

IV. Cách thức UDP hoạt động

UDP hoạt động tương tự như TCP nhưng nó bỏ qua quá trình kiểm tra lỗi.
Khi một ứng dụng sử dụng giao thức UDP, các gói tin được gửi cho bên nhận và bên gửi không phải chờ để đảm bảo bên nhận đã nhận được gói tin, do đó nó lại tiếp tục gửi gói tin tiếp theo. Nếu bên nhận bỏ lỡ một vài gói tin UDP, họ sẽ mất vì bên gửi không gửi lại chúng. Do đó thiết bị có thể giao tiếp nhanh hơn.

V. Cấu trúc UDP Header

![image](https://user-images.githubusercontent.com/97047640/167538379-9bbb05dd-6e3a-4683-8f35-42ee261ebc76.png)

- Source port : Số cổng của thiết bị gửi. Trường này có thể đặt là 0 nếu máy tính đích không cần trả lời người gửi.
- Destination port : Số cổng của thiết bị nhận
- Length : Xác định chiều dài của toàn bộ datagram : phần header và dữ liệu . Chiều dài tối thiểu là 8 byte khi gói tin không có dữ liệu, chỉ có header

VI. Ưu - Nhược điểm của giao thức UDP

*So với giao thức TCP, UDP có những nhược điểm sau :

- Thiếu các tín hiệu bắt tay : Trước khi guiwr một đoạn, UDP không gửi các tín hiệu bắt tau giữa bên gửi và bên nhận . Vì thế phía gửi không có cách nào biết Datagram đã đến đích hay chưa.Do vậy UDP không chắc rằng thông số đã đến đích hay chưa.
- Dùng các phiên : Để TCP là hướng mối liên quan, các phiên được duy trì giữa các host.
- TCP tận dụng các chỉ số phiên (session ID) để duy trì các kết nối giữa 2 host : UDP không hỗ trợ bất ký phiên bản nào do bản chất phi kết nối của nó
- Độ tin tưởng : UDP không chắc rằng chỉ có một bản sao số liệu tới đích. Để gửi thông số tới các hệ thống cuối, UDP phân chia thông số thành các đoạn nhỏ. UDP không chắc chắn rằng các đoạn này sẽ đến đích đúng thứ tự như chúng đã tạo ra ở nguồn. 
Ngược lại, TCP tận dụng các số thứ tự cùng với số hiệu xổng và các gói tin xác thực liên tục, điều này chắc chắn rằng các gói tin đến đúng đích đúng thứ tự như chúng đã tạo ra.
- Bảo mật : TCP có tính bảo mật cao hơn UDP. Trong nhiều tổ chức firrewall và router cấm các gói tin UDP, điều này là vì các hacker thường dùng các cổng UDP
- Kiểm soát luồng : UDP không có kiểm soát luồng ; Kết quả là, một phần mềm UDP có thiết kế tồi hoàn toàn có thể làm giảm băng thông của mạng

*Ưu điểm
- Không cần cài đặt mối liên quan. UDP là giao thức phi liên kết, vì thế không cần phải thiết đặt quan hệ. Vì UDP không tận dụng các tín hiệu Handshaking, nên hoàn toàn có thể tránh được thời gian trễ. Đó chính là lý do tại sao DNS thường dùng giao thức UDP hơn là TCP-DNS sẽ chậm hơn rất nhiều khi tận dụng TCP
- Tốc độ : UDP nhanh chóng so với TCP.Bởi vì điều này , nhiều ứng dụng thường được cài đặt trên giao thức UDP hơn so với giao thức TCP
- Hỗ trợ hình dạng (topolory) : UDP hỗ trợ các mối liên quan 1-1,1-n,ngược lại TCP chỉ hỗ trợ quan hệ 1-1
- Kích thước header : UDP chỉ có 8 byte header cho mỗi đoạn, ngược lại TCP cần các header 20 byte, vì vậy dùng băng thông ít hơn.
- 
