# Tìm hiểu các giao thức 

# Mục lục

[I. Giao thức HTTP](#http)

[1. Khái niệm](#khainiemhttp)

[2. Đặc trưng](#dactrunghttp)

[3. Cấu trúc cơ bản](#cautruchttp)

[4. Kết nối của HTTP](#ketnoihttp)

[5. HTTP status code - Mã trạng thái HTTP](#statushttp)

[II. Giao thức DNS](#dns)

[III. Giao thức FTP](#ftp)

[IV. Giao thức SSH](#ssh)

[V. Giao thức DHCP](#dhcp)

[VI. Giao thức ARP](#arp)

[VII. Giao thức SMNP](#smnp)

[VIII. Giao thức SMTP](#smtp)

# Nội Dung

<a name = "http"> </a>

I. Giao thức HTTP

<a name = "khainiemhttp"> </a>
1.Khái niệm

Http (HyperText Transfer Protocol) là giao thức truyền tải siêu văn bản được sử dụng trong www dùng để truyền tải dữ liệu giữa Web server đến các trình duyệt Web và 
ngược lại. Giao thức này sử dụng cổng 80 (port 80) là chủ yếu.

Nó là nền tảng của bất kỳ sự trao đổi dữ liệu nào trên Web và cũng là giao thức giữa client (thường là các trình duyệt hay bất kỳ loại thiết bị, chương trình nào) và 
server (thường là các máy tính trên đám mây). 1 doc hoàn chỉnh được tái tạo từ các doc con khác nhau được fetch – tìm nạp, chẳng hạn như văn bản, mô tả layout, hình 
ảnh, video, script v..v..

<a name = "dactrunghttp"> </a>
2. Đặc trưng

- HTTP đơn giản:HTTP thường được thiết kế để trở nên đơn giản và thân thiện để con người có thể đọc được, ngay cả khi có thêm sự phức tạp được giới thiệu trong HTTP/2 
- bằng cách đóng gói các HTTP message thành các frame. Với các HTTP message, chúng ta có thể được đọc và hiểu được, cung cấp khả năng testing hơn cho các dev và giảm 
- thiểu độ phức tạp cho bất cứ người mới nào.

- HTTP có thể mở rộng:Được giới thiệu trong HTTP/1.0, các header HTTP làm cho giao thức này dễ dàng mở rộng và thử nghiệm hơn nữa. Chức năng mới thậm chí có thể được 
giới thiệu bằng 1 thỏa thuận đơn giản giữa 1 client và 1 máy chủ về ngữ nghĩa của 1 header mới.

- HTTP là stateless, nhưng không sessionless:Không có liên kết giữa 2 yêu cầu được thực hiện liên tiếp trên cùng 1 kết nối. Điều này ngay lập tức có khả năng trở thành
vấn để với người dùng cố gắng tương tác với các trang nhất định 1 cách mạch lạc, chẳng hạn như sử dụng shopping cart trên các trang e-commerce, tức thương mại điện tử.

Nhưng trong khi cốt lõi bản thân HTTP là stateless, các cookie HTTP cho phép sử dụng các session trạng thái. Sử dụng khả năng mở rộng header, các cookie HTTP được thêm 
vào quy trình vận hành, cho phép tạo các session trên mỗi yêu cầu HTTP để chia sẻ cùng 1 ngữ cảnh hay cùng 1 trạng thái.

<a name = "cautruchttp"> </a>
3. Cấu trúc cơ bản
 ![image](https://user-images.githubusercontent.com/97047640/167105586-c93f77ea-4159-4610-86c0-f3a59aca2672.png)

HTTP còn là 1 giao thức Yêu cầu – Phản hồi dựa trên cấu trúc Client – Server. Client và Server giao tiếp với nhau bằng cách trao đổi các message độc lập (trái ngược với
1 luồng dữ liệu). Các message được gửi bởi client, thông thường là 1 trình duyệt web, được gọi là các yêu cầu và message được gửi bởi server như 1 sự trả lời, được gọi 
là phản hồi.

<a name = "ketnoihttp"> </a>
4. Kết nối của HTTP

1 kết nối được kiểm soát tại layer truyền tải, do đó về cơ bản nằm ngoài phạm vi của HTTP. Dù HTTP không yêu cầu giao thức truyền tải cơ bản phải dựa trên sự kết nối, 
vì chỉ yêu cầu nó đáng tin cậy hoặc không bị mất message (ít nhất là trình báo 1 lỗi). Trong số hai giao thức truyền tải phổ biến nhất trên Internet, TCP thì đáng tin 
cậy còn UDP thì không. HTTP do đó dựa vào tiêu chuẩn TCP vốn là connection-based (dựa trên sự kết nối).

Trước khi 1 client và server có thể trao đổi 1 cặp yêu cầu – phản hồi HTTP, chúng phải thiết lập 1 kết nối TCP, 1 quá trình vốn yêu cầu 1 số vòng lặp. Hoạt động mặc 
định của HTTP/1.0 là mở 1 kết nối TCP riêng biệt cho từng cặp yêu cầu – phản hồi HTTP. Điều này làm nó kém hiệu quả hơn việc chia sẻ 1 kết nối TCP đơn lẻ khi nhiều yêu 
cầu được gửi liên tiếp.

Để giảm thiểu lỗ hỏng này, HTTP/1.1 đã giới thiệu pipelining (nhưng được chứng minh là khá khó để thực hiện) và kết nối liên tục: kết nối TCP bên dưới có thể được kiểm 
soát 1 phần bằng cách sử dụng tiêu đề Connection. HTTP/2 đã tiến 1 bước xa hơn bằng cách ghép các thông báo qua 1 kết nối duy nhất, giúp giữ cho kết nối ổn định và hiệu 
quả hơn.

Các thử nghiệm đang được tiến hành để thiết kế một giao thức truyền tải tốt hơn phù hợp hơn với HTTP. Ví dụ: Google đang thử nghiệm QUIC được xây dựng trên UDP để cung 
cấp giao thức truyền tải cũng đáng tin cậy và hiệu quả hơn.

<a name = "statushttp"> </a>
5. HTTP status code - Mã trạng thái HTTP
   - HTTP status code 
     Khi được nhận và phiên dịch 1 yêu cầu HTTP từ phía client, HTTP status code sẽ được máy chủ cung cấp để đáp ứng yêu cầu đó của họ. Nó bao gồm code từ IETF Request 
     for Comments (RFC), các thông số kỹ thuật khác và 1 số code bổ sung được sử dụng trong 1 số ứng dụng phổ biến của giao thức HTTP.
     
     Chữ số đầu tiên của HTTP status code chỉ định 1 trong 5 loại phản hồi quy chuẩn. Các cụm tin nhắn được hiển thị chỉ mang tính tượng trưng, nhưng cũng có thể cung 
     cấp bất kỳ thông tin bổ sung nào để chúng ta có thể đọc được. Trừ khi có những chỉ định khác, HTTP status code được xem như 1 phần của quy chuẩn HTTP/1.1 (RFC 
     7231).
     Cơ Quan Cấp Số Được Ấn Định Trên Internet (tức IANA hay The Internet Assigned Numbers Authority) chính là nơi duy trì sổ đăng ký chính thức của các HTTP status code.
     
   - Hạng mục các HTTP status code
     Tất cả các HTTP status code phản hồi được chia ra thành 5 hạng mục riêng biệt và là các số nguyên có 3 chữ số. Chữ số đầu được dùng để xác định loại phản hồi, 
     trong khi 2 chữ số cuối thì không có bất kỳ vai trò phân loại nào. HTTP status code sẽ cho ta biết liệu 1 yêu cầu HTTP cụ thể đã được hoàn thành thành công hay 
     chưa.
     
     Các ứng dụng hiểu HTTP status code không cần phải biết hết tất cả code, tức là dù code không xác định cũng có cụm từ để chỉ lý do không xác định. Cụm từ này không
     cho phía client nhiều thông tin nhưng các ứng dụng HTTP đó phải hiểu được nó thuộc 1 trong 5  hạng mục riêng biệt. 5 hạng mục đó bao gồm:

        + 1xx (100 – 199): Information responses / Phản hồi thông tin – Yêu cầu đã được chấp nhận và quá trình xử lý yêu cầu của bạn đang được tiếp tục.

        + 2xx (200 – 299): Successful responses / Phản hồi thành công – Yêu cầu của bạn đã được máy chủ tiếp nhận, hiểu và xử lý thành công.

        + 3xx (300 – 399): Redirects / Điều hướng – Phía client cần thực hiện hành động bổ sung để hoàn tất yêu cầu.

        + 4xx (400 – 499): Client errors / Lỗi phía client – Yêu cầu không thể hoàn tất hoặc yêu cầu chứa cú pháp không chính xác. 4xx sẽ hiện ra khi có lỗi từ phía 
          client do không đưa ra yêu cầu hợp lệ.
 
        + 5xx (500 – 599): Server errors / Lỗi phía máy chủ – Máy chủ không thể hoàn thành yêu cầu được cho là hợp lệ. Khi 5xx xảy ra, bạn chỉ có thể đợi để bên hệ 
          thống máy chủ xử lý xong.
        
<a name = "dns"> </a>



<a name = "ftp"> </a>

<a name = "ssh"> </a>

<a name = "dhcp"> </a>

<a name = "arp"> </a>

<a name = "smnp"> </a>

<a name = "smtp"> </a>
