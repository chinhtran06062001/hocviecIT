# VI. Giao thức ARP

# Mục lục

[1. Giao thức phân giải ARP là gì?](#khainiem)
[2. Giao thức ARP hoạt động như thế nào?](#hoatdong)
[3. Các loại ARP](#cacloai)
[4. Tại sao giao thức ARP lại quan trọng?](#giaithich)
[5. Ví dụ về giao thức ARP](#vidu)
[6. Ưu điểm của giao thức ARP](#uudiem)

<a name = "khainiem"></a>

1. Giao thức phân giải ARP là gì?

- ARP là phương thức phân giải địa chỉ động giữa địa chỉ lớp network và địa chỉ lớp datalink. Quá trình thực hiện bằng cách: một thiết bị IP trong mạng gửi một gói tin local broadcast đến toàn mạng yêu cầu thiết bị khác gửi trả lại địa chỉ phần cứng ( địa chỉ lớp datalink ) hay còn gọi là Mac Address của mình.
- ARP là giao thức lớp 2 – Data link layer trong mô hình OSI và là giao thức lớp Link layer trong mô hình TCP/IP.
- Ban đầu ARP chỉ được sử dụng trong mạng Ethernet để phân giải địa chỉ IP và địa chỉ MAC. Nhưng ngày nay ARP đã được ứng dụng rộng rãi và dùng trong các công nghệ khác dựa trên lớp hai.

<a name = "hoatdong"></a>

2. Giao thức ARP hoạt động như thế nào?

a. Cấu trúc bản tin ARP

![image](https://user-images.githubusercontent.com/97047640/167363498-b75f0c83-f304-4101-9301-5f846acdd6ae.png)

- Hardware type:

     + Xác định kiểu bộ giao tiếp phần cứng cần biết.

     + Xác định với kiểu Ethernet giá trị 1.

- Protocol type:

     + Xác định kiểu giao thức cấp cao (layer 3) máy gửi sử dụng để giao tiếp.

     + Giao thức dành cho IP có giá trị 0x0800.

- Hardware address length: Xác định độ dài địa chỉ vật lý (tính theo đơn vị byte). Địa chỉ MAC nên giá trị của nó sẽ là 6.

- Protocol address length: Xác định độ dài địa chỉ logic được sử dụng ở tầng trên (layer 3). Tùy thuộc vào IP sử dụng mà có giá trị khác nhau, hiện tại IPv4 được sử dụng rộng rãi nên trường này sẽ có giá trị là 4 (byte).

- Operation code: Xác định loại bản tin ARP mà máy gửi gửi. Có một số giá trị phổ biến:

     + 1 : bản tin ARP request.

     + 2 : bản tin ARP rely.

     + 3 : bản tin RARP request.

     + 4 : bản tin RARP reply.

- Sender hardware address (SHA): Xác định địa chỉ MAC máy gửi.

- Trong bản tin ARP request: trường này xác định địa chỉ MAC của host gửi request.

- Trong bản tin ARP reply: trường này xác định địa chỉ MAC của máy host mà máy gửi bên trên muốn tìm kiếm.

- Sender protocol address (SPA): Xác định địa chỉ IP máy gửi.

- Target hardware address (THA): Xác định địa chỉ MAC máy nhận mà máy gửi cần tìm.

- Trong bản tin ARP request: Trường này chưa được xác định (nên sẽ để giá trị là: 00:00:00:00:00:00)

- Trong bản tin ARP reply: Trường này sẽ điền địa chỉ của máy gửi bản tin ARP request.

b. Cách thức hoạt động của ARP

- Hoạt động của ARP trong mạng LAN

![image](https://user-images.githubusercontent.com/97047640/167366560-0bb4271b-3a29-413c-8d17-61783d6fa461.png)

   + Bước 1: Máy gửi kiểm tra cache của mình. Nếu đã có thông tin về sự ánh xạ giữa địa chỉ IP và địa chỉ MAC thì chuyển sang Bước 7.

   + Bước 2: Máy gửi khởi tạo gói tin ARP request với địa chỉ SHA và SPA là địa chỉ của nó, và địa chỉ TPA là địa chỉ IP của máy cần biết MAC. (Trường THA để giá trị toàn 0 để biểu hiện là chưa tìm được địa chỉ MAC)

   + Bước 3: Gửi quảng bá gói tin ARP trên toàn mạng (Địa chỉ MAC đích của gói tin Ethernet II là địa chỉ MAC quảng bá ff:ff:ff:ff:ff:ff).

   + Bước 4: Các thiết bị trong mạng đều nhận được gói tin ARP request. Gói tin được xử lý bằng cách các thiết bị đều nhìn vào trường địa chỉ Target Protocol Address.

     Các thiết bị không trùng địa chỉ TPA thì hủy gói tin.

   + Thiết bị với IP trùng với IP trong trường Target Protocol Address sẽ bắt đầu quá trình khởi tạo gói tin ARP Reply bằng cách lấy các trường Sender Hardware Address và Sender Protocol Address trong gói tin ARP nhận được đưa vào làm Target trong gói tin gửi đi. Đồng thời thiết bị sẽ lấy địa chỉ MAC của mình để đưa vào trường Sender Hardware Address. Đồng thời cập nhất giá trị ánh xạ địa chỉ IP và MAC của máy gửi vào bảng ARP cache của mình để giảm thời gian xử lý cho các lần sau.

   + Bước 5: Thiết bị đích bắt đầu gửi gói tin Reply đã được khởi tạo đến thiết bị nguồn vừa gửi bản tin ARP request. Gói tin reply là gói tin gửi unicast.

   + Bước 6: Thiết bị nguồn nhận được gói tin reply và xử lý bằng cách lưu trường Sender Hardware Address trong gói reply như địa chỉ phần cứng của thiết bị đích cần tìm.

   + Bước 7: Thiết bị nguồn update vào ARP cache của mình giá trị tương ứng giữa địa chỉ IP và địa chỉ MAC của thiết bị đích. Lần sau sẽ không còn cần tới ARP request.

- Hoạt động của ARP trong môi trường liên mạng

   Hoạt động của ARP trong một môi trường phức tạp hơn đó là hai hệ thống mạng gắn với nhau thông qua một Router.

   Máy A thuộc mạng A muốn gửi gói tin tới máy B thuộc mạng B. 2 mạng này kết nối với nhau thông qua router C.

   Xem thêm: Atelectasis Là Gì – Atelectasis Sau Khi Phẫu Thuật

   Do các broadcast lớp MAC không thể truyền qua Router nên khi đó máy A sẽ xem Router C như một cầu nối hay một trung gian (Agent) để truyền dữ liệu. Trước đó, máy A sẽ biết được địa chỉ IP của Router C (địa chỉ Gateway) và biết được rằng để truyền gói tin tới B phải đi qua C.

   Để tới được router C thì máy A phải gửi gói tin tới port X của router C (là gateway trong LAN A). Quy trình truyền dữ liệu được mô tả như sau:

   Máy A gửi ARP request để tìm MAC của port X.

   Router C trả lời, cung cấp cho A địa chỉ MAC của port X.

   Máy A truyền gói tin tới port X của router C (với địa chỉ MAC đích là MAC của port X, IP đích là IP máy B).

   Router C nhận được gói tin của A, forward ra port Y. Trong gói tin có chứa địa chỉ IP máy B, router C sẽ gửi ARP request để tìm MAC của máy B.

   Trên thực tế ngoài dạng bảng định tuyến này người ta còn dùng phương pháp proxy ARP (sẽ tìm hiểu phần sau), trong đó có một thiết bị đảm nhận nhiệm vụ phân giải địa chỉ cho tất cả các thiết bị khác. Theo đó các máy trạm không cần giữ bảng định tuyến nữa Router C sẽ có nhiệm vụ thực hiện, trả lời tất cả các ARP request của tất cả các máy.   

<a name = "cacloai"></a>

3. Các loại ARP

ARP được phân thành 4 loại chính:

- Proxy ARP

Trong phương pháp Proxy ARP, các thiết bị Layer 3 có thể phản hồi các ARP request. Loại ARP này được cấu hình sao cho router sẽ phản hồi địa chỉ IP đích, và ánh xạ địa chỉ MAC đến địa chỉ IP đích và người gửi khi nó đến được đích.

- Gratuitous ARP

Gratuitous ARP là một loại ARP request khác của host. Loại request này giúp mạng có thể xác định các địa chỉ IP bị trùng lặp. Do đó, khi router hay switch gửi ARP request để lấy địa chỉ IP, nó sẽ không nhận được phản hồi ARP nào. Vì vậy cũng không có node nào có thể sử dụng địa chỉ IP được cấp cho router hay swictch đó

- Reverse ARP

Reverse ARP (RARP) là một loại giao thức ARP được hệ thống client trong LAN sử dụng để yêu cầu địa chỉ IPv4 của nó từ bảng ARP router. Quản trị viên mạng chủ yếu tạo một bảng trong bộ gateway-router, giúp xác định địa chỉ MAC đến IP cụ thể.

- Inverse ARP

InARP là một loại ARP dùng để tìm địa chỉ IP của các node từ địa chỉ lớp liên kết dữ liệu. InARP được sử dụng rộng rãi cho các rơ-le frame mạng ATM, trong đó địa chỉ mạch ảo Lớp 2 thu được từ việc signal của Layer 2.

<a name = "giaithich"></a>

4. Tại sao giao thức ARP lại quan trọng?

ARP là một giao thức có vai trò to lớn, vì địa chỉ phần mềm (địa chỉ IP) của host hay máy tính kết nối với mạng cần phải được phiên dịch thành địa chỉ phần cứng (tức là địa chỉ MAC). Nếu không có ARP, host sẽ không thể tìm ra địa chỉ phần cứng của host khác. Mạng LAN sẽ giữ một bảng hay directory ánh xạ địa chỉ IP đến địa chỉ MAC của các thiết bị khác nhau. Trong đó bao gồm cả các endpoint lẫn router trên mạng đó.

Bảng hoặc directory này không được duy trì bởi người dùng hay admin mạng. Thay vào đó, giao thức ARP sẽ tạo ra các entry. Nếu thiết bị của người dùng không biết địa chỉ phần cứng của host đích, thiết bị sẽ gửi một thông báo đến tất cả host trên mạng để tìm địa chỉ này. Khi host đích thích hợp biết được request, nó sẽ phản hồi bằng địa chỉ phần cứng của nó. Địa chỉ này sau đó sẽ được lưu trữ trong bảng hay directory của ARP.

<a name = "vidu"></a>

5. Ví dụ về giao thức ARP

Các thông báo ARP Request và ARP Reply có thể được capture. Sau đây là một ví dụ về các thông báo ARP Request được capture để minh họa cách hoạt động của ARP là gì. Ta có thể thấy rằng địa chỉ MAC ở ví dụ dưới được bỏ trống (00:00:00:00:00:00).

Thông báo request sẽ chứa nhiều trường khác nhau như:

- Loại phần cứng – Chỉ định phần cứng được sử dụng trong quá trình tuyền thông báo ARP. Loại phần cứng chủ yếu là Ethernet.
- Loại giao thức – một con số được gán cho từng giao thức, ở đây là giao thức IPv4: 2048 (hay 0x0800 trong hệ Hexa).
- Kích thước giao thức – độ dài địa chỉ IPv4 (ở đây là 4 byte).
- Opcode – xác định bản chất của thông báo ARP. Trong đó, 1 là ARP Request, còn ARP Reply là 0.
- Địa chỉ IP nguồn – ở đây là 10.10.10.2
- Địa chỉ IP đích – ở đây là 10.10.10.1
- Địa chỉ MAC nguồn – trong ví dụ này là 00:1a:6b:6c:0c:cc

![image](https://user-images.githubusercontent.com/97047640/167366959-0e20d5b4-e713-4324-848a-bd398bfae60c.png)

Tiếp đến, một thông báo ARP Reply được capture. Tin nhắn phản hồi sẽ chứa địa chỉ MAC mà nguồn yêu cầu. Địa chỉ MAC 00:1d:09:f0:92:ab được gửi ở trong thông báo ARP Reply.

![image](https://user-images.githubusercontent.com/97047640/167367151-6a49efb7-b093-4c90-8e50-397708b91513.png)


<a name = "uudiem"></a>

6. Ưu điểm của giao thức ARP

- Trước hết, với giao thức ARP, các địa chỉ MAC có thể dễ dàng được tìm thấy nếu người dùng đã biết được địa chỉ IP của cùng hệ thống.
- Các end node không nên được cấu hình để “biết” các địa chỉ MAC. Chúng sẽ được tìm thấy khi cần thiết.
- Mục đích của ARP là enable mọi host trên mạng cho phép người dùng tạo một ánh xạ giữa địa chỉ IP và địa chỉ vật lý.
- Tập hợp các ánh xạ hoặc bảng được lưu trữ trong host được gọi là bảng ARP hay ARP cache.

