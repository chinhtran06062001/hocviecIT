# Tìm hiểu giao thức định tuyến

I. khái niệm định tuyến

- Là quá trình xác định đường đi tốt nhất trên một mạng máy tính để gói tin tới được đích theo một số thủ tục nhất định nào đó thông qua các nút trung gian là các bộ định tuyến router.Thông tin về những con đường này có thể được cập nhật tự động từ các router khác hoặc là do người quản trị mạng chỉ định cho router.Sau khi router nhận gói tin, thì router sẽ gỡ bỏ phần header lớp 2 để tìm địa chỉ đích thuộc lớp 3. Sau khi đọc xong địa chỉ đích nó tìm kiếm trong Routing Table cho mạng chứa địa chỉ đích.
- Giả sử mạng đó có trong Routing Table, Router sẽ xác định địa chỉ của router hàng xóm (router chia sẻ chung kết nối). Sau đó gói tin sẽ được đẩy ra bộ đệm của cổng truyền đi tương ứng, router sẽ khám phá loại đóng gói lớp 2 nào được sử dụng trên kết nối giữa 2 router. Gói tin được đóng gửi xuống lớp 2 và đưa xuống môi trường truyền dẫn dưới dạng bit và được truyền đi bằng tín hiệu điện, quang hoặc sóng điện từ. Quá trình sẽ tiếp tục cho tới khi gói tin được đưa đến đích thì thôi.
- Để làm được việc này thì các router cần phải được cấu hình một bảng định tuyến (Routing Table) và giao thức định tuyến (Routing Protocol). Bảng định tuyến là bảng chứa tất cả những đường đi tốt nhất đến một đích nào đó tính từ router. Khi cần chuyển tiếp một gói tin, router sẽ xem địa chỉ đích của gói tin, sau đó tra bảng định tuyến và chuyển gói tin đi theo đường tốt nhất tìm được trong bảng. Trong bảng định tuyến có thể bao gồm một tuyến mặc định, được biểu diễn bằng địa chỉ 0.0.0.0 0.0.0.0.
- Bảng định tuyến của mỗi giao thức định tuyến là khác nhau, nhưng có thể bao gồm những thông tin sau:
  + Địa chỉ đích của mạng, mạng con hoặc hệ thống.
  + Địa chỉ IP của router chặng kế tiếp phải đến.
  + Giao tiếp vật lí phải sử dụng để đi đến Router kế tiếp.
  + Subnet mask của địa chỉ đích.
  + Khoảng cách đến đích (ví dụ: số lượng chặng để đến đích).
  + Thời gian (tính theo giây) từ khi Router cập nhật lần cuối.

- Giao thức định tuyến là ngôn ngữ giao tiếp giữa các router. Một giao thức định tuyến cho phép các router chia sẻ thông tin về các Network, router sử dụng các thông tin này để xây dựng và duy trì bảng định tuyến

II. Phân loại định tuyến

Có nhiều tiêu chí để phân loại các giao thức định tuyến khác nhau.Định tuyến được chia thành 2 loại cơ bản :
- Định tuyến tĩnh : Việc xây dựng bảng định tuyến của router được thực hiện bằng tay bởi người quản trị.
- Định tuyến động : Việc xây dựng bảng và duy trì trạng thái của bảng định tuyến được thực hiện tự động bởi router
Việc chọn đường đi đường đi được tuân thủ theo 2 thuật toán cơ bản :
+ Distance vector : chọn đường đi theo hướng và khoảng cách tới đích 
+ Link State : Chọn đường đi ngắn nhất dựa vào cấu trúc của toàn bộ mạng theo trạng thái của các đường liên kết mạng

![image](https://user-images.githubusercontent.com/97047640/167577100-c226ea65-4e4e-47cc-9f68-f331373ee356.png)

Người quản trị mạng khi chọn lựa một giao thức định tuyến động cần cân nhắc một số yếu tố như: độ lớn của hệ thống mạng, băng thông các đường truyền, khả năng của router, loại router và phiên bản router, các giao thức đang chạy trong hệ thống mạng.

III. Định tuyến động

1. Khái quát

- là phương thức định tuyến mạng, sử dụng thuật toán định tuyến tự động trao đổi thông tin định tuyến với các Router khác và xác định tuyến tốt nhất đến mỗi mạng đưa vào bảng định tuyến.

- So với định tuyến tĩnh, định tuyến động tốn ít thời gian cấu hình cho người quả trị.  Tuy nhiên, định tuyến động tốn kém tài nguyên CPU, tài nguyên băng thông mạng.

- Một thuật toán định tuyến là một tập các xử lý, thuật toán và các thông điệp được sử dụng để trao đổi thông tin định tuyến và xác định tuyến tốt nhất đưa vào bảng định tuyến. Mục đính của giao thức định tuyến gồm:

          + Khám phá các mạng từ xa
          + Duy trì và cập nhật thông tin định tuyến
          + Chọn đường đi tốt nhất đến các mạng đích
          + Có khả năng tìm tuyến mới thay thế cho tuyến cũ nếu tuyến cũ không còn sẵn sàng.

- Thành phần của giao thức định tuyến gồm:
          + Cấu trúc dữ liệu
          + Thuật toán định tuyến
          + Thông điệp định tuyến

2. Hoạt động của giao thức định tuyến

Tất cả các giao thức định tuyến có cùng chung mục đích: học về các mạng ở xa và thích ứng nhanh khi có sự thay đổi hình trạng mạng. Mỗi giao thức định tuyến thực hiện định tuyến phụ thuộc vào thuật toán định tuyến và đặc điểm hoạt động của nó. Thông thường, hoạt động của các giao thức định tuyến động có thể được mô tả như sau:

- Router gởi và nhận các thông điệp định tuyến từ các Interface của nó
- Router chia sẻ thông điệp định tuyến và thông tin định tuyến với các Router sử dụng cùng giao thức định tuyến.
- Các Router chia sẻ thông tin định tuyến để học về các mạng từ xa
- Khi Router phát hiện sự thay đổi nào đó trên hình trạng mạng, nó thông báo sự thay đổi này đến các Router khác.

3. Phân loại giao thức định tuyến

Có nhiều cách phân loại giao thức định tuyến mạng.

- Phân loại giao thức định tuyến dựa vào phạm vi sử dụng, ta có giao thức định tuyến bên trong vùng định tuyến (interior gateway protocols) và các giao thức định tuyến giữa các vùng định tuyến (exterior gateway protocols).

- Phân loại giao thức định tuyến dựa vào thuật toán định tuyến sử dụng, ta có giao thức định tuyến theo vector khoảng cách (thuật toán Bellman Ford), giao thức định tuyến theo trạng thái đường liên kết (thuật toán Dijkstra).

-  Nếu dựa vào cấu trúc phân cấp của địa chỉ IP, ta có các giao thức định tuyến dựa trên cấu trúc phân lớp địa chỉ IP (classful) và các giao thức định tuyến không dựa trên cấu trúc phân cấp địa chỉ IP (classless).

- Phân loại giao thức định tuyến dựa trên nền IP, ta có các giao thức sử dụng cho nền IPv4 và các giao thức sử dụng cho nền IPv6.

IV. Định tuyến tĩnh

1. Khái quát

Định tuyến tĩnh là quá trình router thực hiện chuyển gói dữ liệu tới địa chỉ mạng đích dựa vào địa chỉ IP đích của gói dữ liệu. Để chuyển được gói dữ liệu đến đúng đích thì router phải học thông tin về đường đi tới các mạng khác. Thông tin về đường đi tới các mạng khác sẽ được người quản trị cấu hình cho router. Khi cấu trúc mạng thay đổi, người quản trị mạng phải tự thay đổi bảng định tuyến của router.

Kỹ thuật định tuyến tĩnh đơn giản, dễ thực hiện, ít hao tốn tài nguyên mạng và CPU xử lý trên router (do không phải trao đổi thông tin định tuyến và không phải tính toán định tuyến). Tuy nhiên kỹ thuật này không hội tụ với các thay đổi diễn ra trên mạng và không thích hợp với những mạng có quy mô lớn (khi đó số lượng route quá lớn, không thể khai báo bằng tay được).

*Ưu điểm của định tuyến tĩnh :

- Sử dụng ít bandwidth hơn định tuyến động.

- Không tiêu tốn tài nguyên để tính toán và phân tích gói tin định tuyến.

*Nhược điểm:

- Không có khả năng tự động cập nhật đường đi.

- Phải cấu hình thủ công khi mạng có sự thay đổi.

- Phù hợp với mạng nhỏ, rất khó triển khai trên mạng lớn.

*Một số tình huống bắt buộc dùng định tuyến tĩnh:

- Đường truyền có băng thông thấp

- Người quản trị mạng cần kiểm soát các kết nối.

- Kết nối dùng định tuyến tĩnh là đường dự phòng cho đường kết nối dùng giao thức định tuyến động.

- Chỉ có một đường duy nhất đi ra mạng bên ngoài (mạng stub).

- Router có ít tài nguyên và không thể chạy một giao thức định tuyến động.

- Người quản trị mạng cần kiểm soát bảng định tuyến và cho phép các giao thức classful và classless.

3. Ứng dụng của định tuyến tĩnh

- Định Tuyến Tĩnh có thể được sử dụng để xác định cổng ra từ một con router khi không có đường khác có sẵn thông tin trong bảng định tuyến. Điều này được gọi là Default Route.

- Định Tuyến Tĩnh có thể được sử dụng cho các mạng nhỏ chỉ có một hoặc hai con đường, điều này hiệu quả hơn vì một liên kết sẽ không bị quá lãng phí so với việc trao đổi thông tin trong Định Tuyến Động

- Định Tuyến Tĩnh thường được sử dụng giúp chuyển thông tin định tuyến từ một giao thức định tuyến khác (routing redistribution)

4. Cấu hình định tuyến tĩnh 

![image](https://user-images.githubusercontent.com/97047640/167580868-0c5fdcbb-04db-4be1-afcd-344a02ee2008.png)

Hình trên là hai router, R1 sử dụng cổng f0/0 đấu xuống mạng LAN có subnet 192.168.1.0/24. Tương tự, R2 sử dụng cổng f0/0 đấu xuống PC có subnet 192.168.2.0/24. Subnet sử dụng cho kết nối leased-line nối giữa hai router là 192.168.3.0/24. Đầu tiên, chúng ta phải cấu hình đặt địa chỉ IP cho các cổng của router, cũng như IP và Default-gateway cho các PC. Default-gateway hiểu đơn giản là IP của cổng của router gần nhất mà PC đó kết nối trực tiếp đến.

Cấu hình định tuyến tĩnh trên router Cisco được thực hiện bằng cách sử dụng lệnh có cú pháp như sau:

Router (config) # ip route destination_subnet subnetmask{IP_next_hop|output_interface} [AD]

Trong đó:

            destination_subnet: mạng đích đến.

            subnetmask: subnet – mask của mạng đích.

            IP_next_hop: địa chỉ IP của trạm kế tiếp trên đường đi.

            output_interface: cổng ra trên router.

            AD: chỉ số AD của route khai báo, sử dụng trong trường hợp có cấu hình dự phòng.

Trong ví dụ hình trên, từ R1 muốn đi đến mạng 192.168.2.0/24 thì phải đi ra khỏi cổng f1/0. Để thể hiện điều đó vào bảng định tuyến phải thực hiện cấu hình:

            R1 (config) # ip route 192.168.2.0 255.255.255.0 f1/0

            hoặc

            R1 (config) # ip route 192.168.2.0 255.255.255.0 192.168.3.2

            R2 muốn đi đến mạng 192.168.1.0/24 thì phải đi ra khỏi cổng f1/0:

            R2 (config) # ip route 192.168.1.0 255.255.255.0 f1/0

            hoặc

            R2 (config) # ip route 192.168.1.0 255.255.255.0 192.168.3.1

Sau khi đã cấu hình xong các route cho các mạng 192.168.1.0/24 và 192.168.2.0/24, kiểm tra bảng định tuyến trên mỗi router: Bảng định tuyến của R1:

            R1#show ip route

            C 192.168.1.0/24 is directly connected, FastEthernet0/0

            S 192.168.2.0/24 [1/0] via 192.168.3.2

            C 192.168.3.0/24 is directly connected, FastEthernet1/0

Bảng định tuyến của R2:

            R2#show ip route

            S 192.168.1.0/24 [1/0] via 192.168.3.1

            C 192.168.2.0/24 is directly connected, FastEthernet0/0

            C 192.168.3.0/24 is directly connected, FastEthernet1/0

Kí tự “S” ở đầu dòng thể hiện rằng các thông tin định tuyến này được học vào bảng định tuyến thông qua định tuyến tĩnh và các dòng mô tả các mạng kết nối trực tiếp được ký hiệu bởi kí tự “C” – connected – kết nối trực tiếp.

V. So sánh định tuyến động và định tuyến tĩnh

||Định tuyến động|Định tuyến tĩnh|
|-----------|-----------|------------|
 |Độ phức tạp cấu hình|	 Độc lập với kích thước mạng|	 Tăng khi kích thước mạng tăng|
 |Yêu cầu hiểu biết của người quản trị|	 Yêu cầu hiểu biết về định tuyến động của người quản trị	| Không Yêu cầu hiểu biết về định tuyến động của người quản trị|
 |Thay đổi hình trạng mạng|	 Tự động thích ứng khi thây đổi hình trạng mạng	| Yêu cầu sự can thiệp của người quản trị|
 |Khả năng mở rộng|	 Phù hợp với mạng từ đơn giản đến phúc tạp	| Phù hợp với mạng đơn giản|
 |Bảo mật|	 Ít bảo mật	| Bảo mật hơn|
 |Sử dụng tài nguyên|	 Sử dụng tài nguyên CPU, bộ nhớ, băng thông liên kết	|  Không cần nhiều tài nguyên |  
 |Sự ổn định của tuyến|	 Phụ thuộc vào hình trạng mạng hiện thời|	Tuyến đến đích luôn cố định |    
 
 # Tài liệu tham khảo
 
 https://sites.google.com/site/pvanthopdu/cacmonphutrach/dinhtuyen/giaothucdinhtuyen
 
 https://vnpro.vn/thu-vien/khai-niem-va-cau-hinh-dinh-tuyen-tinh-2347.html
