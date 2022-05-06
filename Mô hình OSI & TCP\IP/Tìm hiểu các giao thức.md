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

II. Giao thức DNS

1. Giao thức DNS là gì?

![image](https://user-images.githubusercontent.com/97047640/167128549-d26d0c0f-85c4-4ec1-aaa1-53850d6c4622.png)


DNS viết tắt của Domain Name System có nghĩa là hệ thống phân giải tên miền. DNS là hệ thống cho phép thiết lập tương ứng giữa địa chỉ IP và tên miền trên Internet.

Được phát minh vào năm 1984 cho Internet và đây là một trong số các chuẩn công nghiệp của các cổng bao gồm cả TCP/IP. Hệ thống phân giải tên miền chính là chìa khóa chủ chốt của nhiều dịch vụ mạng hiện nay như Internet, Mail server, Web server…

2. DNS dùng để làm gì ?

Mỗi máy tính khi kết nối vào Internet sẽ được gán cho 1 địa chỉ IP (Ví dụ: 1414.1158.62462) riêng biệt và không trùng lẫn với bất kỳ máy tính nào khác trên thế giới. Cũng giống như vậy đối với website cũng có địa chỉ IP riêng biệt của website đó.

    Ví dụ địa chỉ IP là 103.200.21.192 dẫn đến website Vietnix thay vì gõ vietnix.vn trên thanh tìm kiếm. 
    Lúc này là lúc DNS “trổ tài chuyển đổi” (ánh xạ) dãy số địa chỉ IP thành những ký tự thân thiện hơn. 
    Chính vì nhờ có giao thức DNS nên bạn không cần phải nhớ địa chỉ IP để vào website Vietnix mà chỉ cần nhớ vietnix.vn là được.
    
Nói cách khác, DNS cũng giống như một danh bạ điện thoại dành riêng cho Internet. Nếu bạn biết tên của một người nhưng không biết số điện thoại hay ngược lại, bạn có thể tham khảo trong sổ danh bạ dễ dàng.

3. Cách thức hoạt động.
   Quá trình phân giải DNS bao gồm chuyển đổi tên máy chủ (chẳng hạn như www.example.com) thành địa chỉ IP thân thiện với máy tính (chẳng hạn như 192.168.1.1). Một địa chỉ IP được cung cấp cho mỗi thiết bị trên Internet và địa chỉ đó là cần thiết để tìm thiết bị Internet phù hợp. Giống như một địa chỉ đường phố được sử dụng để tìm một ngôi nhà cụ thể.

Khi người dùng muốn tải một trang web, một bản dịch phải xảy ra giữa những gì người dùng nhập vào trình duyệt web của họ (example.com) và địa chỉ thân thiện với máy cần thiết để định vị trang web example.com.

Để hiểu quy trình đằng sau quá trình phân giải DNS, điều quan trọng là phải tìm hiểu về các thành phần khác nhau mà một truy vấn DNS phải vượt qua. Đối với trình duyệt web, việc tra cứu DNS diễn ra ở chế độ ẩn. Và không yêu cầu sự tương tác từ máy tính của người dùng ngoài yêu cầu ban đầu.

4.  Các loại DNS bản ghi DNS thường sử dụng

- CNAME Record: Là một bản ghi tên quy chuẩn (Canonical Name Record). Đây là một dạng bản ghi tài nguyên trong hệ thống tên miền.

- A Record: Dùng để trỏ tên miền website tới một địa chỉ IP cụ thể. Đây được xem là bản ghi DNS đơn giản nhất.

- MX Record: Bản ghi này bạn có thể sử dụng để trỏ tên miền đến mail server. MX Record chỉ định server nào quản lý các dịch vụ Email của tên miền đó.

- AAAA Record: Dùng để trỏ tên miền đến địa chỉ IPv6 và cho phép thêm host mới, TTL và IPv6.

- TXT Record: Ngoài ra, có thể thêm giá trị TXT, Host mới, TTL và Point To để chứa các thông tin định dạng văn bản domain.

- SRV Record: Đây là bản ghi DNS đặc biệt, dùng để xác định chính xác dịch vụ nào đang chạy Port nào. Và thông qua bản ghi này bạn có thể thêm Priority, Port, Weight, TTL, Point to.

- NS Record: Bản ghi này có thể chỉ định Name Server cho từng tên miền phụ và bên cạnh đó có thể tạo tên Name Server, TTL hay host mới.


5. Các loại DNS Server

DNS Server gồm hai loại là Root Name Server và Local Name Server. 

5.1. Root Name Server

Root Name Server là một dịch vụ phân giải tên miền gốc và trên thế giới có khoảng 12 DNS root Server.

DNS root Server quản lý tất cả các tên miền Top-level. Khi có yêu cầu phân giải một Domain Name thành một địa chỉ IP, client sẽ gửi yêu cầu đến DNS gần nhất (DNS ISP). DNS ISP sẽ kết nối tới DNS root Server để hỏi địa chỉ của Domain Name.

DNS root Server sẽ căn cứ và dựa vào các Top Level của tên miền và từ đó có những tài liệu hướng dẫn phù hợp để chuyển hướng cho khách hàng đến đúng địa chỉ cần truy vấn.

5.2. Local Name Server

DNS Server này dùng để chứa thông tin để truy xuất và tìm kiếm máy chủ tên miền. Và thường được duy trì và phát triển bởi các doanh nghiệp hay các nhà cung cấp dịch vụ Internet.

6. Cách sử dụng DNS

Nếu bạn sử dụng DNS của nhà cung cấp mạng thì bạn sẽ không cần điền địa chỉ DNS. Nhưng nếu trường hợp bạn sử dụng DNS khác, thì bạn phải điền địa chỉ cụ thể của máy chủ đó để thay đổi DNS Server :

Bước 1 : Nhấn vào Start Menu > Gõ Control Panel > Chọn Control Panel

Bước 2 : Truy cập vào View network status and task

Bước 3 : Truy cập vào mạng Internet

Bước 4 : Vào phần properties để bắt đầu thay đổi DNS máy tính

Bước 5 : Nhấp vào Internet Protocol Vesion 4 > Chọn Use the following DNS server addresses > Đổi DNS > OK

7. Các loại truy vấn DNS 

- Recursive query: DNS client yêu cầu máy chủ DNS (thường là recursive DNS resolver). Sẽ trả lời máy khách bằng bản ghi tài nguyên được yêu cầu. Hoặc thông báo lỗi nếu resolver không thể tìm thấy bản ghi.

- Iterative query: Trong tình huống này, DNS client sẽ cho phép máy chủ DNS trả về câu trả lời tốt nhất có thể. Nếu máy chủ DNS được truy vấn không có kết quả trùng khớp với tên truy vấn. Nó sẽ trả về một giới thiệu đến máy chủ DNS có thẩm quyền cho mức thấp hơn. DNS client sau đó sẽ thực hiện một truy vấn đến địa chỉ được giới thiệu. Quá trình này tiếp tục với các máy chủ DNS bổ sung trong chuỗi truy vấn cho đến khi xảy ra lỗi hoặc hết thời gian.

- Non-recursive query: Thông thường điều này sẽ xảy ra khi DNS resolver client truy vấn máy chủ DNS một record mà server có quyền truy cập hoặc bản ghi tồn tại bên trong bộ đệm của server. Thông thường, một máy chủ DNS sẽ lưu các bản ghi DNS để ngăn chặn việc tiêu thụ thêm băng thông và giảm tải cho các máy chủ DNS khác.

8. Cách DNS Server giải quyết một DNS query ?

Điển hình, trong một DNS query mà không có caching, có bốn server hoạt động cùng nhau để  cung cấp địa chỉ IP cho client : Recursive Resolvers, Root Namesevers, TLD Nameserver, và Authoriative Nameserver

DNS recursor (DNS resolver) là một máy chủ nhận truy vấn từ DNS Client, sau đó tương tác với các DNS server khác để truy tìm Ip chính xác. Khi resolver nhận được yêu cầu từ Client, Resolver sau đó thực sự hoạt động như một Client, truy vấn ba loại DNS Server khác đẻ tìm kiếm đúng IP.

* DNS Lookup

Đầu tiên, resolver truy vấn root nameservers. Root-server là bước đầu tiên trong việc phân giải các tên miền có thể đọc được thành địa chỉ IP. Sau đó, root server sẽ phản hồi lại resolver bằng địa chỉ của Top Level Domain (TLD) DNS server (chẳng hạn như .com hoặc .net) lưu trữ thông tin cho các miền của nó.

Tiếp theo, resolver truy vấn TLD server. TLD server phản hồi bằng địa chỉ IP Authoritative Nameserver của tên miền. Sau đó, recursor sẽ truy vấn authoritative nameserver. Sau đó máy chủ này sẽ respond bằng địa chỉ IP của origin server.

Resolver cuối cùng sẽ chuyển địa chỉ IP của origin server trở lại client. Sử dụng địa chỉ IP này, client sau đó có thể bắt đầu truy vấn trực tiếp đến origin server. Và origin server sẽ phản hồi bằng cách gửi dữ liệu trang web cho trình duyệt web để hiển thị.

* DNS Caching
Ngoài quy trình được nêu ở trên, recursive resolver cũng có thể giải quyết các truy vấn DNS. Bằng cách sử dụng dữ liệu được lưu trong bộ nhớ cache. Sau khi truy xuất địa chỉ IP chính xác cho một trang web nhất định. Resolver sẽ lưu trữ thông tin đó trong bộ nhớ cache của nó trong một khoảng thời gian giới hạn. Trong khoảng thời gian này, nếu bất kỳ máy khách nào khác gửi yêu cầu cho tên miền đó, resolver có thể bỏ qua quy trình tra cứu DNS thông thường và chỉ cần trả lời client bằng địa chỉ IP được lưu trong bộ nhớ cache.

Khi thời gian lưu vào bộ nhớ đệm hết hạn, resolver phải truy xuất lại địa chỉ IP, tạo entry mới trong bộ nhớ cache của nó. Giới hạn thời gian này, được gọi là thời gian tồn tại (TTL) được đặt trong DNS Record cho mỗi trang web. Thông thường, thì TTL nằm trong khoảng 24-48 giờ. TTL là cần thiết vì máy chủ web đôi khi thay đổi địa chỉ IP của chúng. Do đó, các resolver không thể phân phát cùng một IP từ bộ nhớ cache vô thời hạn.

    
<a name = "ftp"> </a>

<a name = "ssh"> </a>

<a name = "dhcp"> </a>

<a name = "arp"> </a>

<a name = "smnp"> </a>

<a name = "smtp"> </a>
