# V. Giao thức DHCP

# Mục lục
[1. Khái niệm DHCP](#khainiem)
[2. Các thuật ngữ DHCP](#thuatngu)
[3. Gói tin DHCP](#goitin)
[4. Các thông điệp DHCP](#thongdiep)
[5. Ưu điểm khi sử dụng DHCP](#uudiem)
[6. Cách hoạt động DHCP](#hoatdong)
[7. Phân tích gói 4 bản tin](#phantich)

<a name = "khainiem"></a>

1. Khái niệm

Đây là giao thức hoạt động ở lớp Application trong mô hình TCP/IP và là giao thức cấu hình tự động địa chỉ IP, DHCP có 2 version: cho IPv4 và IPv6, sử dụng port 67,68 và dùng giao thức UDP.

DHCP Server cấp địa chỉ mạng, phân phối thông số cấu hình tương ứng xuống cho client
DHCP hỗ trợ 3 cơ chế cấp địa chỉ IP

    - Cấp tự động: DHCP gán 1 địa chỉ IP thường trực → 1 Client
    - Cấp động: DHCP gán địa chỉ IP cho 1 khoảng thời gian hữu hạn nào đó
    - Cấp thủ công: 1 địa chỉ IP được gán bời người quản trị. DHCP chỉ để đưa địa chỉ này đến Client
Ngoài ra cơ chế cấp động là cơ chế duy nhất được sử dụng để cấp lại địa chỉ mà không còn được sử dụng nữa trên client cho 1 máy client khác

<a name = "thuatngu"></a>

2. Các thuật ngữ DHCP

![image](https://user-images.githubusercontent.com/97047640/167357981-2e5de053-7c4b-4c8d-b2b7-c087eafa65d9.png)


- DHCP Server: máy chủ quản lý việc cấu hình và cấp phát địa chỉ IP cho Client
- DHCP Client: máy trạm nhận thông tin cấu hình IP từ DHCP Server
- Scope: phạm vi liên tiếp của các địa chỉ IP có thể cho một mạng.
- Exclusion Scope: là dải địa chỉ nằm trong Scope không được cấp phát động cho Clients.
- Reservation: Địa chỉ đặt trước dành riêng cho máy tính hoặc thiết bị chạy các dịch vụ (tùy chọn này thường được thiết lập để cấp phát địa chỉ cho các Server, Printer,…..)
- Scope Options: các thông số được cấu hình thêm khi cấp phát IP động cho Clients như DNS Server(006), Router(003)
- DHCP Replay Agent: DHCP Replay Agent là một máy tính hoặc một Router được cấu hình để lắng nghe và chuyển tiếp các gói tin giữa DHCP Client và DHCP Server từ subnet này sang subnet khác.

<a name = "goitin"></a>

3. Gói tin DHCP

![image](https://user-images.githubusercontent.com/97047640/167358714-be651cf4-21b9-4fbe-92db-0cf96683cffb.png)

![image](https://user-images.githubusercontent.com/97047640/167358771-b85e92bc-8719-46d7-8651-e5c5e6334d8d.png)

<a name = "thongdiep"></a>

4. Các thông điệp DHCP

![image](https://user-images.githubusercontent.com/97047640/167358844-d5726df8-97fa-4470-96b3-9e2fc864420e.png)

- DHCP Discover: Thời gian đầu tiên một máy tính DHCP Client nỗ lực để gia nhập mạng, nó yêu cầu thông tin địa chỉ IP từ DHCP Server bởi việc broadcast một gói DHCP Discover. Địa chỉ IP nguồn trong gói là 0.0.0.0 bởi vì client chưa có địa chỉ IP.

- DHCP Offer: Mỗi DHCP server nhận được gói DHCP Discover từ client đáp ứng với gói DHCP Offer chứa địa chỉ IP không thuê bao và thông tin định cấu hình TCP/IP bổ sung(thêm vào), chẳng hạn như subnet mask và gateway mặc định. Nhiều hơn một DHCP server có thể đáp ứng với gói DHCP Offer. Client sẽ chấp nhận gói DHCP Offer đầu tiên nó nhận được.

- DHCP Request: Khi DHCP client nhận được một gói DHCP Offer, nó đáp ứng lại bằng việc broadcast gói DHCP Request mà chứa yêu cầu địa chỉ IP, và thể hiện sự chấp nhận của địa chỉ IP được yêu cầu.

- DHCP Acknowledge : DHCP server được chọn lựa chấp nhận DHCP Request từ Client cho địa chỉ IP bởi việc gửi một gói DHCP Acknowledge. Tại thời điểm này, Server cũng định hướng bất cứ các tham số định cấu hình tuỳ chọn. Sự chấp nhận trên của DHCP Acknowledge, Client có thể tham gia trên mạng TCP/IP và hoàn thành hệ thống khởi động.

- DHCP Nak: Nếu địa chỉ IP không thể được sữ dụng bởi client bởi vì nó không còn giá trị nữa hoặc được sử dụng hiện tại bởi một máy tính khác, DHCP Server đáp ứng với gói DHCP Nak, và Client phải bắt đầu tiến trình thuê bao lại. Bất cứ khi nào DHCP Server nhận được yêu cầu từ một địa chỉ IP mà không có giá trị theo các Scope mà nó được định cấu hình với, nó gửi thông điệp DHCP Nak đối với Client.

- DHCP Decline : Nếu DHCP Client quyết định tham số thông tin được đề nghị nào không có giá trị, nó gửi gói DHCP Decline đến các Server và Client phải bắt đầu tiến trình thuê bao lại.

- DHCP Release: Một DHCP Client gửi một gói DHCP Release đến một server để giải phóng địa chỉ IP và xoá bất cứ thuê bao nào đang tồn tại.

<a name = "uudiem"></a>

5. Ưu điểm khi sử dụng DHCP

- Tập trung quản trị thông tin cấu hình host
- Cấu hình động các máy
- Cấu hình IP cho các máy một cách liền mạch.
- Sự linh hoạt
- Đơn giản hóa vài trò quản trị của việc cauas hình địa chỉ IP của client.
- Sự linh hoạt

<a name = "hoatdong"></a>

6.Cách hoạt động DHCP

- Bước 1: Khi muốn có địa chỉ IP để truy cập vào internet thì client sẽ tạo ra bản tin DISCOVERY để yêu cầu cấp phát địa chỉ IP
- Bước 2: Client chưa biết địa chỉ chính xác của Server cấp phát địa chỉ cho mình do đó nó sẽ gửi bản tin này dưới dạng broadcast.
- Bước 3: Server sẽ nhận bản tin DISCOVERY của client. Sau khi biết client muốn được cấp địa chỉ IP nó sẽ kiểm tra xem địa chỉ IP nào phù hợp để cấp cho client sử dụng
- Bước 4: Server tạo bản tin OFFER. Gói tin này sẽ lưu trữ thông tin về IP và các thông số cấu hình khác mà client yêu cầu để có thể sử dụng để truy cập internet
- Bước 5: Tất cả các server sẽ gửi bản OFFER dưới dạng broadcast
- Bước 6: Client nhận gói OFFER và nó sẽ chọn ra bản OFFER đầu tiên mà nó nhận được. Nếu không nhận được OFFER nào trong một khoảng thời gian nào đó thì nó sẽ gửi lại DISCOVERY một lần nữa
- Bước 7: Client tạo ra gói REQUEST. Và gửi dưới dạng broadcast tới tất cả các server. Server nào được nhận OFFER sẽ mang ý nghĩa là nó đồng ý nhận IP. Server nào không được nhận OFFER thì thông báo là không nhận OFFER đó
- Bước 8: Server nhận bản tin REQEST. Các server không được nhận OFFER sẽ bỏ qua gói tin này. Gói tin nào được nhận OFFER sẽ nhận và xử lý nó. Nó sẽ kiểm tra sem IP này còn sử dụng được hay không. Nếu còn sử dụng được thì nó sẽ ghi lại thông tin và gửi lại gói tin PACK cho client. Còn nếu không thì nó sẽ gửi lại PNAK để quay lại bước 1.

<a name = "phantich"></a>

7. Phân tích gói 4 bản tin

Để phân tích được gói tin của giao thức DHCP thì ta phải sử dụng một lệnh được gọi là "tcpdump"

![image](https://user-images.githubusercontent.com/97047640/167359776-7eb81ee6-e8d5-4ca9-8983-bb4aceadf344.png)

7.1 DHCP DISCOVERY

- 1: là địa chỉ đầu và địa chỉ cuối của gói tin ghi bằng MAC
- 2: là địa chỉ đầu và cuối nhưng được ghi bằng IPv4
- 3: là port mà gói tin đó sử dụng
- 4: địa chỉ IP của client
- 5: MAC của client
- 6: IP client yêu cầu được cấp phát

7.2 DHCP OFER

Trong đó

- Option 54: chỉ đính danh DHCP server
- Option 51: thời gian cho thuê địa chỉ IP
- Option 1: địa chỉ subnet Mask
- Option 28 : địa chỉ broadcast
- Option 3 : địa chỉ default gateway
- Option 6 : địa chỉ DNS

7.3 DHCP REQUEST

- Option 53: Kiểu tin nhắn
- Option 55: Danh sách tham số yêu cầu
- Option 50: Địa chỉ IP yêu cầu


7.4 DHCP ACK

Nhiệm vụ của gói tin này là để xác nhận lại thông tin đã cấp cho client

# Tài liệu tham khảo 

https://blog.cloud365.vn/ccna/dhcp-tong-quan/?msclkid=1efeb8b6cf6511ec8231206a3603db02

https://kipalog.com/posts/Tat-ca-ve-giao-thuc-DHCP-ede79d6d-8784-41ba-b722-3719e421c06f?msclkid=38aea486cf6311eca7825f98cb808cbb
