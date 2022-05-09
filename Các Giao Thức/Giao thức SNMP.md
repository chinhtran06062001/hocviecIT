# VIII. Giao thức SNMP

1. Khái niệm 

SNMP (Simple Network Management Protocol) là một giao thức tầng ứng dụng được Hội đồng Kiến trúc Internet (IAB) xác định trong RFC1157 để trao đổi thông tin quản lý giữa các thiết bị mạng. Nó là một phần của Transmission Control Protocol/Internet Protocol (TCP/IP).

Giao thức SNMP là một trong những giao thức mạng được chấp nhận rộng rãi để quản lý và giám sát các phần tử mạng. Hầu hết các thiết bị mạng được cung cấp đi kèm với SNMP agent. Các agent này phải được kích hoạt và cấu hình để giao tiếp với các công cụ giám sát mạng hoặc hệ thống quản lý mạng (NMS).

2. Các thành phần của SMNP

![image](https://user-images.githubusercontent.com/97047640/167378492-6ad5c496-68f0-4f48-a412-c60eca3e07e4.png)

2.1 SNMP Manager

Trình quản lý hoặc hệ thống quản lý là một thực thể riêng biệt có trách nhiệm giao tiếp với các thiết bị mạng được triển khai SNMP agent. Đây thường là một máy tính được sử dụng để chạy một hoặc nhiều hệ thống quản lý mạng.

Các chức năng chính của SNMP manager:

  - Agent truy vấn
  - Nhận response từ các agent
  - Đặt các biến trong agent
  - Xác nhận các sự kiện không đồng bộ từ các agent

2.2 Các thiết bị được SNMP quản lý

Thiết bị được quản lý hoặc phần tử mạng là một phần của mạng yêu cầu một số hình thức giám sát và quản lý, ví dụ: router, switches, server, máy trạm, máy in, UPS, v.v.

2.3 SNMP Agent

Agent là một chương trình được đóng gói trong các thiết bị mạng. Việc kích hoạt agent cho phép nó thu thập cơ sở dữ liệu thông tin quản lý từ thiết bị cục bộ và cung cấp nó cho SNMP manager khi được truy vấn. Các agent này có thể là tiêu chuẩn (ví dụ: Net-SNMP) hoặc cụ thể cho một nhà cung cấp (ví dụ: HP insight agent).

Các chức năng chính của SNMP agent:

   - Thu thập thông tin quản lý về các chỉ số hoạt động cuả thiết bị
   - Lưu trữ và truy xuất thông tin quản lý như được định nghĩa trong MIB.
   - Báo hiệu sự kiện cho trình quản lý.
   - Hoạt động như một proxy cho một số nút mạng không quản lý được – SNMP.

3. Giao thức SNMP hoạt động như thế nào ?

SNMP sử dụng một số command cơ bản để giao tiếp giữa manager và agent

![image](https://user-images.githubusercontent.com/97047640/167378926-67d2ab84-6ae7-4bce-a8eb-93655d7e005f.png)

- GET: Yêu cầu thông tin bất cứ lúc nào
Để nhận thông tin trạng thái từ agent, manager có thể đưa ra message Get và GetNext để yêu cầu thông tin cho một biến cụ thể. Sau khi nhận được message Get hoặc GetNext, agent sẽ gửi message GetResponse cho manager. Nó sẽ chứa thông tin được yêu cầu hoặc lỗi giải thích tại sao không thể xử lý request.

- SET: Điều khiển thiết bị từ xa 
Message SET cho phép manager yêu cầu thực hiện thay đổi đối với đối tượng được quản lý (tức là rơle điều khiển). Sau đó, agent sẽ trả lời bằng message Set-response nếu thay đổi đã được thực hiện hoặc lỗi giải thích tại sao không thể thực hiện thay đổi.

- TRAP: SNMP message phổ biến nhất
Message TRAP được khởi xướng bởi agent và gửi đến manager khi một sự kiện quan trọng xảy ra. Trap dùng để cảnh báo cho manager – thay vì đợi request trạng thái từ manager khi cần thăm dò ý kiến ​​của agent.

- INFORM: Một loại message có giá trị khác
Message INFORM rất giống với TRAP, nhưng chúng đáng tin cậy hơn. Các message INFORM được khởi tạo bởi agent và khi manager nhận được nó, nó sẽ gửi response đến agent cho biết message đã được nhận. Nếu agent không nhận được response từ manager thì agent sẽ gửi lại message INFORM.

- SNMPWALK: Nhận tất cả dữ liệu
SNMPWALK sử dụng nhiều request Get-Next để truy xuất toàn bộ cây dữ liệu mạng từ một đối tượng được quản lý. Công cụ iReasoning MIB Browser sẽ rất hữu ích để xem tất cả các OID mà một agent cung cấp.

4. Tại sao SMNP là "Đơn giản"?

Bên cạnh việc sử dụng số lượng nhỏ command, SNMP được coi là đơn giản vì nó phụ thuộc vào một liên kết giao tiếp không được giám sát hoặc ít kết nối. Nhờ đó mà nó được sử dụng rộng rãi, đặc biệt là trong các ứng dụng internet. SNMP được coi là “mạnh” vì sự độc lập của các manager và agent. Bởi vì chúng thường là các thiết bị riêng biệt, nếu một agent bị lỗi, manager sẽ tiếp tục hoạt động và ngược lại.

5. Cấu trúc của SNMP

![image](https://user-images.githubusercontent.com/97047640/167379173-09e518f7-3424-44a1-a5e5-2db944f074d4.png)

Để gửi thông tin, SNMP sử dụng mô hình truyền thông phân lớp.

 - Layer 1 – Lớp ứng dụng (SNMP)
 - Layer 2 – Lớp vận chuyển (UDP)
 - Layer 3 – Lớp Internet (IP)
 - Layer 4 – Lớp Network interface
Mặc dù mô hình nhiều lớp này có vẻ hơi khó hiểu, nhưng nó rất hiệu quả trong việc tách biệt các nhiệm vụ giao tiếp và hỗ trợ thiết kế, triển khai mạng.

Ví dụ : Để minh họa chức năng của mô hình phân lớp,chúng ta hãy xét một Request SNMP GET từ agent.

- Bước 1: SNMP manager muốn biết Tên hệ thống của Agent và chuẩn bị message GET cho OID thích hợp.

- Bước 2: Sau đó, nó chuyển message đến lớp User Datagram Protocol (UDP). Lớp UDP thêm một khối dữ liệu xác định cổng manager mà response packet sẽ được gửi đến.

- Bước 3: Sau đó packet được chuyển đến lớp IP, nơi khối dữ liệu chứa địa chỉ IP và các địa chỉ Media Access của manager và agent được thêm vào.

- Bước 4: Toàn bộ packet được chuyển đến lớp Network interface. Lớp Network interface xác minh khả năng truy cập và tính khả dụng của phương tiện. Sau đó, nó đặt packet trên phương tiện truyền thông để vận chuyển.

- Bước 5: Sau khi qua các cầu nối và thông qua các router dựa trên thông tin IP, packet cuối cùng cũng đến được agent.

- Bước 6: Ở đây nó đi qua bốn lớp giống nhau theo thứ tự hoàn toàn ngược lại với manager. 

6. Lợi ích của SNMP

Sử dụng SNMP cho phép bạn quản lý các asset mạng không có hệ điều hành, nhưng là các thành phần quan trọng của cơ sở hạ tầng. 

Nó đơn giản hóa nhiệm vụ và giúp bạn có thể tập trung mạng. Nó còn cho phép kiểm soát hiệu quả hơn, ngay cả đối với thiết bị không có hệ điều hành như máy in.

Một ưu điểm khác của SNMP là nó có một ngôn ngữ duy nhất cho phép người dùng tương tác với tất cả các thiết bị từ các nhà sản xuất khác nhau.

Vì vậy, nó tương thích với hầu hết mọi asset và dịch vụ mạng, chẳng hạn như Windows, Linux, Mac và máy ảo Java.

SNMP không chỉ hữu ích để cung cấp hỗ trợ chủ động mà còn để cải thiện trải nghiệm khách hàng, cho phép bạn dự đoán nhu cầu.

Các lợi ích chính khác của SNMP:

- Ưu điểm chính của việc sử dụng SNMP là thiết kế đơn giản. Dễ dàng triển khai nó trên mạng, vì nó không yêu cầu cấu hình lâu.
- Hơn nữa, SNMP rất phổ biến ngày nay. Hầu hết tất cả các nhà sản xuất thiết bị phần cứng liên mạng lớn, như switch hoặc router, đều triển khai hỗ trợ SNMP trong các sản phẩm của họ.
- Mở rộng là một ưu thế khác của SNMP. Do thiết kế đơn giản, dễ dàng cập nhật giao thức để đáp ứng nhu cầu của user trong tương lai.
- SNMP dựa trên giao thức truyền tải UDP, yêu cầu ít tài nguyên hơn và kết nối đồng thời hơn với TCP.

# tài liệu tham khảo

https://hocviencanboxd.edu.vn/snmp-la-gi-co-ban-ve-giao-thuc-snmp/?msclkid=e45f272ecf7611ecb2a93a04940d0a82

https://mesidas.com/snmp/?msclkid=e45fdca8cf7611ec895f0cc6ee93bd66#snmp-hoat-dong-nhu-the-nao
