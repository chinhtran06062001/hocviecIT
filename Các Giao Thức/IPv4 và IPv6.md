# Tìm hiểu IPv4 & IPv6

I. Địa chỉ IP là gì?

Địa chỉ IP (Internet Protocol)  là địa chỉ giao thức của internet, nó cung cấp danh tính của các thiết bị được kết nối mạng – tương tự như địa chỉ nhà hay địa chỉ doanh nghiệp. Địa chỉ IP sẽ giúp các thiết bị trên mạng internet phân biệt và nhận ra nhau, từ đó có thể giao tiếp với nhau.

*Các loại địa chỉ IP :

- IP Public: IP public là địa chỉ IP công cộng được ISP (nhà cung cấp dịch vụ internet) chỉ định. Đây là địa chỉ mà mạng gia đình hay doanh nghiệp sử dụng để liên lạc với các thiết bị kết nối internet khác, cho phép các thiết bị trong mạng truy cập web hay liên lạc trực tiếp với máy tính của người dùng khác
- IP Private: Khác với IP Puclic – IP Private hay còn gọi là IP riêng là địa chỉ IP được cấp phát bởi InterNIC, nó dành riêng cho việc sử dụng nội bộ thông qua router hoặc thiết bị Network Address Translation (NAT) khác, hoàn toàn cô lập với các mạng bên ngoài.
- IP Static: IP Static hay còn gọi là IP tĩnh, đây là cách đặt IP cho từng thiết bị hoàn toàn thủ công và không bị thay đổi theo thời gian.
- IP Dynamic: Tương tự trái ngược với IP tĩnh đó là IP động hay còn gọi là IP Dynamic, có nghĩa rằng địa chỉ IP của máy tính có thể thay đổi, địa chỉ hôm nay sẽ khác với địa chỉ IP ngày mai. Và nó được quản lý thông qua DHCP Server.

II. Địa chỉ IPv4

1. Khái niệm 

- IPv4 (Internet Protocol Version 4) dịch ra có nghĩa là giao thức Internet Phiên bản thứ 4. IPv4 đã được bộ quốc phòng Hoa kỳ chuẩn hóa trong bản MIL-STD-1777.
- Giao thức Internet IP đã trải qua nhiều phiên bản khác nhau và phiên bản Ipv4 là phiên bản đầu tiên được sử dụng rộng rãi trên toàn thế giới và hiện vẫn còn đang là nòng cốt của Internet trên toàn thế giới.
- Ipv4 là giao thức mang tính hướng dữ liệu và được sử dụng cho hệ thống chuyển mạch gói. Ipv4 không quan tâm đến thứ tự truyền gói tin, cũng không đảm bảo gói tin sẽ đến đích hay là có xảy ra tình trạng lặp gói tin ở đích đến hay không. Nó chỉ có cơ chế đảm bảo tính toàn vẹn dữ liệu bằng việc sử dụng những gói kiểm tra được thiết lập đi kèm với nó.
- Địa chỉ Ipv4 là 1 địa chỉ đơn nhất đang được sử dụng bởi các thiết bị điện tử hiện nay để nhận diện và liên lạc với nhau trên Internet. Để đánh địa chỉ, Ipv4 sử dụng 32bit và chia ra làm 4 octet (mỗi octet có 8 bit = 1 byte). Dấu chấm được sử dụng để ngăn các octet với nhau.

2. Cấu trúc của địa chỉ IPv4
Về cấu tạo, địa chỉ IPv4 sẽ có 32 bit và được biểu diễn thành một dãy số nhị phân và chia thành 4 cụm. Mỗi cụm như vậy sẽ gọi là octet. Mỗi octet sẽ là 8 bit và chúng được ngăn cách bằng dấu chấm (.)

Về hình dáng, cấu trúc của một địa chỉ IPv4 sẽ gồm 4 con số ở dạng thập phân tượng trưng cho 4 cụm. Địa chỉ này gồm 2 phần là phần mạng và phần host.

![image](https://user-images.githubusercontent.com/97047640/167599142-4032cdd7-7ea4-43e0-a273-bf328e7e456e.png)

*Quy tắc đặt địa chỉ IP:

- Không được đặt những bit ở phần network bằng 0 cùng một lúc. Khi đặt tất cả những bit ở phần network bằng không thì địa chỉ IP sẽ có 3 số đầu là 0.0.0. Đây là một địa chỉ sai.
- Nếu đặt tất cả các bit ở phần host bằng 0 thì số cuối cùng của địa chỉ IP sẽ bằng 0. Khi đó địa chỉ đó là một địa chỉ mạng, không thể dùng làm host. Ví dụ: 191.168.10.0 là một địa chỉ mạng.
- Nếu đặt tất cả các bit ở phần host là 1 thì số cuối cùng của địa chỉ IP là 255. Khi đó địa chỉ này sẽ là một địa chỉ broadcast của mạng đó. Ví dụ: 192.168.10.255 là một địa chỉ broadcast.

4. Phân lớp của địa chỉ IPv4

Ban đầu, 1 địa chỉ Ipv4 được chia ra làm 2 phần là địa chỉ của mạng (Network ID) và địa chỉ của máy (Host ID). Địa chỉ của mạng (Network ID) được xác lập bởi octet đầu tiên và địa chỉ của máy (Host ID) được xác lập cho 3 octet còn lại. Với cách chia này thì địa chỉ của network bị giới hạn ở con số 256. Đây là con số quá ít so với nhu cầu sử dụng thực tế. Vì vậy người ta đã định nghĩa phân lớp mạng để vượt qua giới hạn này và tập hợp thành 1 lớp mạng đầy đủ còn được gọi là classful.

Địa chỉ IP được phân ra thành 5 lớp khác nhau: lớp A, lớp B, lớp C, lớp D,lớp E. Với cách phân loại này sẽ tạo được vô số địa chỉ IPv4 khác nhau.

- Lớp A
 Lớp A của địa chỉ Ipv4 sử dụng octet đầu làm network và 3 Octet sau làm host. Bit đầu tiên của địa chỉ lớp A luôn được chọn là 0. Dải địa chỉ mạng lớp A chạy từ 1.0.0.0 đến 126.0.0.0. Vì vậy lớp A sẽ có tổng cộng 126 mạng. Trong khi đó mạng Loopback là 127.0.0.0. Phần host của lớp A có tất cả 24 bit. Do đó, mỗi lớp A có (224 – 2) host.
 
- Lớp B : Lớp B của địa chỉ Ipv4 sử dụng 2 obtet đầu làm phần mạng và 2 obtet sau làm phần host. Hai bit đầu tiên của lớp B luôn là 1 và 0. Dải địa chỉ mạng lớp B chạy từ 128.0.0.0 đến 191.255.0.0. Như vậy lớp B sẽ có tổng cộng 214 mạng. Vì phần host dài 16 bit nên mạng lớp B có (216 – 2) host.
- Lớp C : Lớp C của địa chỉ Ipv4 dùng 3 octet đầu làm phần mạng và 1 octet sau làm phần host. Địa chỉ lớp C luôn có 3 bit đầu là 1 1 0. Dải mạng lớp C chạy từ 192.0.0.0 -> 223.255.255.0. Như vậy sẽ có 221 mạng trong lớp C. Đối với phần host gồm 1 octet sau cùng nên dài 8 bit và sẽ có (28 – 2) host trong lớp C.
- Lớp D : Lớp D được sử dụng làm các địa chỉ multicast và dải địa chỉ lớp D từ 224.0.0.0 -> 239.255.255.255.
  Ví dụ : 240.0.0.5 dùng cho OSPF; 224.0.0.9 dùng cho RIPv2
- Lớp E : Lớp E gòm các giải số từ 240.0.0.0 trở đi và được sử dụng cho mục đích dự phòng

4. Những lưu ý của IPv4

- Các địa chỉ của lớp A, lớp B, lớp C của Ipv4 thường được dùng để đặt cho các host.

- Bạn nên quan sát octet đầu tiên của địa chỉ Ipv4 để xác định địa chỉ IP thuộc lớp nào. Nếu octet đầu tiên từ 1 đến 126 thì địa chỉ thuộc lớp A. Nếu octet đầu tiên từ 128 đến 191 thì địa chỉ thuộc lớp B. Nếu octet đầu tiên từ 192 đến 223 thì địa chỉ thuộc lớp C. Nếu octet đầu tiên từ 224 đến 239 thì địa chỉ thuộc lớp D. Cuối cùng, nếu octet đầu tiên từ 240 đến 255 thì địa chỉ thuộc lớp E.
 
 5. Một số hạn chế của IPv4

- Cấu trúc thiết kế không có bất cứ cách thứ bảo mật nào cũng như không có phương tiện mã hóa dữ liệu. Vì thế, lưu lượng truyền tải dữ liệu giữa các host với nhau không được bảo mật, chỉ được phổ biến ở mức ứng dụng mà thôi.
- Thiếu hụt không gian địa chỉ : Để đánh địa chỉ, phiên bản IPv4 chỉ sử dụng 32 bit, do đó không gian của nó chỉ có khoảng 236 địa chỉ. Sự bùng nổ Internet đến thời điểm hiện tại khiến cho tài nguyên IPv4 được sử dụng gần như là cạn kiệt - vì thế phiên bản này không đủ đáp ứng nhu cầu hiện nay.

Vì những nguy cơ thiếu hụt không gian địa chỉ cũng như để khắc phục những hạn chế của IPv4 đã thúc đẩy phát triển một giao thức mới ra đời đó chính là IPv6.

III. Địa chỉ IPv6

1. Lịch sử về IPv6 

- Được ra đời vào năm 1981,khi các máy tính hầu như chỉ có thể truy cập internet phục vụ cho các tổ chức nghiên cứu quân sự. Với môi trường làm việc 8 bit, kết hợp với không gian địa chỉ 32 bit do phiên bản Internet Protocol 4 (viết tắt là IPv4) cung cấp cho phép kết nối tới 4 tỷ địa chỉ khác nhau. 
- Đầu những năm 1990, IETF phát triển một giao thức mới có tên gọi là IP Next Generation (IPng). Và vào năm 1998, giao thức này chính thức chuẩn hóa, được Tổng công ty Internet cho tên miền và số (viết tắt là ICANN) phê duyệt, cho phép sử dụng trên rộng rãi trên toàn cầu. Giao thức được đặt tên IPv6 (RFC 1883).
- IPv6 ra đời đã giải quyết được những hạn chế tồn tại của IPv4 trong hệ thống Internet, tạo ra bước tiến nhảy vọt của công nghệ số.
- 1 số điểm cải tiến IPv6 so với IPv4 :
  + Không gian lưu trữ lớn
  + Độ bảo mật cao hơn
  + Khả năng định tuyến được tăng cao
  + Cấu hình được thiết kế theo hướng đơn giản hơn so với IPv4

2. Một số lợi ích mà IPv6 mang lại

- Cho phép không gian địa chỉ lớn, giúp việc quản lý không gian này trở nên dễ dàng hơn.
- Quản trị dễ dàng hơn. Do IPv6 có khả năng tự động cấu hình mà không cần đến máy chủ DHCP. Trong khi đó, IPv4 cần DHCP để cấu hình.
- Định tuyến IPv6 có thiết kế phân cấp nên cấu trúc tốt.
- IPv6 hỗ trợ tốt hơn về Multicast.
- Việc sắp xếp và định dạng header được thực hiện khoa học và tối ưu giúp việc bảo mật thông tin được cải tiến hơn.
- IPv6 hỗ trợ tốt cho các thiết bị di động.

3. Cấu trúc địa chỉ IPv6

IPv6 gồm 128 bit, được phân thành 8 nhóm. Trong đó, mõi nhóm có 16 bit và được phân chia bởi dấu ":"

Một địa chỉ IPv6 được thể hiện theo cấu trúc sau :

         FEDC:BA98:768A:0C98:FEBA:CB87:7678:1111:1080:0000:0000:0070:0000:0989:CB45:345F
        
Vì cấu trúc quá dài nên người ta thường bỏ số 0 ở đầu mỗi nhóm để rút gọn. Đối với nhóm nào chỉ có duy nhất dãy số 0 thì nó sẽ được biểu diễn bằng dấu “::”

![image](https://user-images.githubusercontent.com/97047640/167605335-84dcb2b7-33d9-49a7-9bf4-33908a1f3b9c.png)

*Cấu trúc của Address Prefixes

Address Prefixes có cấu trúc tương tự IPv4 CIDR. Cách thể hiện của nó là IPv6-address/ prefix-length. 

Trong đó:

- IPv6-address: Địa chỉ IPv6 với giá trị bất kỳ.

- Prefix-length: Số bit liền kề nhau trong prefix.

Ví dụ: Quy tắc biểu diễn của 56 bit prefix 200F00000000AB là

200F::AB00:0:0:0:0/56

200F:0:0:AB00::/56

Lưu ý: Với địa chỉ IPv6, kí hiệu “::” chỉ được dùng duy nhất 1 lần trong một sự biểu diễn.

4. Các thành phần cảu IPv6

Địa chỉ IPv6 có 3 thành phần: site prefix, subnet ID và interface ID. Trong đó:

- Site prefix: Đây là thông số được gán với website thông qua ISP. Do đó, toàn bộ máy tính ở cùng vị trí sẽ chia sẻ với nhau bằng một site prefix. Có thể thấy, đặc tính của site prefix là khi đã nhận ra mạng của người dùng và cho phép truy cập thông qua internet thì nó sẽ hướng đến việc dùng chung.
- Subnet ID: Đây là thành phần bên trong website. Nó được dùng để miêu tả cấu trúc site của mạng. Vì thế, một IPv6 subnet sẽ có cấu trúc tương đương một nhánh mạng đơn.
- Interface ID: Cấu trúc của nó tương tự ID trong IPv4. Các thông số sẽ nhận dạng một host riêng. Interface ID có cấu hình tự động. 

Ví dụ: Địa chỉ IPv6 có cấu trúc: 2001:0f68:0000:0000:0000:0000:1986:69af bao gồm:

- Site prefix: 2001:0f68:0000

- Subnet ID: 0000

- Interface ID: 0000:0000:1986:69af

![image](https://user-images.githubusercontent.com/97047640/167605698-6db18975-17d4-4172-b7c3-2b0986641fcb.png)

5. Phân loại địa chỉ IPv6 connectivity

Có 3 loại địa chỉ IPv6:

- Unicast: Một địa chỉ Unicast được chỉ định riêng cho một cổng của node IPv6. Khi có một gói tin gửi đến địa chỉ Unicast, nó sẽ được đưa đến cổng đã chỉ định bởi địa chỉ đó.
- Multicast: Đây là nhóm các cổng IPv6. Khi một gói tin gửi đến địa chỉ Multicast thì nó sẽ được toàn bộ thành viên trong nhóm multicast xử lý.
- Anycast: Đây là địa chỉ đăng ký cho nhiều cổng (tức trên nhiều node). Khi có gói tin gửi đến địa chỉ Anycast, nó sẽ được chuyển đến một cổng bất kỳ, tuy nhiên, phần lớn là đến cổng gần nhất.
