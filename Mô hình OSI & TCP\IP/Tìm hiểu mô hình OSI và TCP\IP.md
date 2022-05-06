# Tìm hiểu mô hình OSI và TCP\IP

# Mục lục

[I. Mô hình OSI](#osi)

[1.Mô hình OSI là gì ?](#khainiem)

[2.Nguyên tắc định nghĩa các tầng hệ thống mở](#nguyentac)

[3. Các giao thức trong mô hình OSI](#giaothuc)

[4.Vai trò và chức năng chủ yếu các tầng ](#vaitro)

[II. Mô hình TCP\IP](#tcpip)

[III. Phân biệt và mối tương quan của mô hình OSI và TCP\IP](#phanbiet)

<a name = "osi"> </a>

# I. Mô hình OSI

<a name = "khainiem"> </a>
1. Mô hình OSI là gì?

   - là mô hình căn bản về các tiến trình truyền thông, thiết lập các tiêu chuẩn kiến trúc mạng ở mức Quốc tế, là cơ sở chung để các hệ thống khác nhau có thể liên kết và 
   truyền thông được với nhau.
   
   - Mô hình OSI tổ chức các giao thức truyền thông thành 7 tầng, mỗi một tầng giải quyết một phần hẹp của tiến trình truyền thông, chia tiến trình truyền thông thành nhiều 
     tầng và trong mỗi tầng có thể có nhiều giao thức khác nhau thực hiện các nhu cầu truyền thông cụ thể.
     
     <a name = "nguyentac"> </a>
2. Nguyên tắc định nghĩa các tầng hệ thống mở

   Mô hình OSI tuân theo các nguyên tắc phân tầng như sau:

      - Mô hình gồm N = 7 tầng. OSI là hệ thống mở, phải có khả năng kết nối với các hệ thống khác nhau, tương thích với các chuẩn OSI.

      - Quá trình xử lý các ứng dụng được thực hiện trong các hệ thống mở, trong khi vẫn duy trì được các hoạt động kết nối giữa các hệ thống.

      - Thiết lập kênh logic nhằm mục đích thực hiện việc trao đổi thông tin giữa các thực thể.
      
      ![image](https://user-images.githubusercontent.com/97047640/166890808-9293973e-ed99-4c82-8073-02c31fd2b0ce.png)
      
      <a name = "giaothuc"> </a>
3. Các giao thức trong mô hình OSI

   Trong mô hình OSI có hai loại giao thức được sử dụng: giao thức hướng liên kết (Connection – Oriented) và giao thức không liên kết (Connectionless).
   
   a. Giao thức hướng liên kết
   
      Trước khi truyền dữ liệu, các thực thể đồng tầng trong hai hệ thống cần phải thiết lập một liên kết logic. Chúng thương lượng với nhau về tập các tham số sẽ sử dụng 
      trong giai đoạn truyền dữ liệu, cắt/hợp dữ liệu, liên kết sẽ được hủy bỏ. Thiết lập liên kết logic sẽ nâng cao độ tin cậy và an toàn trong quá trình trao đổi dữ liệu.

   b. Giao thức không liên kết
   
      Dữ liệu được truyền độc lập trên các tuyến khác nhau. Với các giao thức không liên kết chỉ có giai đoạn duy nhất truyền dữ liệu.
      
      <a name = "vaitro"> </a>
4. Vai trò và chức năng chủ yếu các tầng.
   4.1. Vai trò và chức năng tầng ứng dụng (Application Layer)
   
   ![image](https://user-images.githubusercontent.com/97047640/166892256-2eab015e-2ce9-4829-a59e-69ba1218b2bf.png)

        Nhiệm vụ của tầng này là xác định giao diện giữa người sử dụng và môi trường OSI. Bao gồm nhiều giao thức ứng dụng cung cấp các phương diện cho người sử dụng truy 
        cập vào môi trường mạng và cung cấp các dịch vụ phân tán. Khi các thực thể ứng dụng AE (Application Entity) được thiết lập, nó sẽ gọi đến các phần tử dịch vụ ứng dụng 
        ASE (Application Service Element). Mỗi thực thể ứng dụng có thể gồm một hoặc nhiều các phần tử dịch vụ ứng dụng. Các phần tử dịch vụ ứng dụng được phối hợp trong môi 
        trường của thực thể ứng dụng thông qua các liên kết gọi là đối tượng liên kết đơn SAO (Single Association Object). SAO điều khiển việc truyền thông và cho phép tuần tự 
        hóa các sự kiện truyền thông.
        
   4.2. Vai trò và chức năng tầng trình bày (Presentation Layer)

   ![image](https://user-images.githubusercontent.com/97047640/166892644-325b5221-1a55-44f8-b313-7c312d4fef01.png)
   
   Tầng trình bày giải quyết các vấn đề liên quan đến các cú pháp và ngữ nghĩa của thông tin được truyền. Biểu diễn thông tin người sử dụng phù hợp với thông tin làm 
   việc của mạng và ngược lại. Thông thường biểu diễn thông tin các ứng dụng nguồn và ứng dụng đích có thể khác nhau bởi các ứng dụng được chạy trên các hệ thống có 
   thể khác nhau. Tầng trình bày phải chịu trách nhiệm chuyển đổi dữ liệu gửi đi trên mạng từ một loại biểu diễn này sang một loại biểu diễn khác. Để đạt được điều đó 
   nó cung cấp một dạng biểu diễn truyền thông chung cho phép chuyển đổi từ dạng biểu diễn cục bộ sang biểu diễn chung và ngược lại


   4.3. Vai trò và chức năng tầng phiên (Session Layer)

   ![image](https://user-images.githubusercontent.com/97047640/166892668-5b73497c-787a-4d94-b06d-5741c880703d.png)
   
   Tầng phiên cho phép người sử dụng trên các máy khác nhau thiết lập, duy trì và đồng bộ phiên truyền thông giữa họ với nhau. Nói cách khác tầng phiên thiết lập “các 
   giao dịch” giữa các thực thể đầu cuối.
   
   Dịch vụ phiên cung cấp một liên kết giữa 2 đầu cuối sử dụng dịch vụ phiên sao cho trao đổi dữ liệu một cách đồng bộ và khi kết thúc thì giải phóng liên kết. Sử dụng
   thẻ bài (Token) để thực hiện truyền dữ liệu, đồng bộ hóa và hủy bỏ liên kết trong các phương thức truyền đồng thời hay luân phiên. Thiết lập các điểm đồng bộ hóa trong 
   hội thoại. Khi xảy ra sự cố có thể khôi phục hội thoại bắt đầu từ một điểm đồng bộ hóa đã thỏa thuận.


   4.4. Vai trò và chức năng tầng vận chuyển (Transport Layer)

   ![image](https://user-images.githubusercontent.com/97047640/166892737-e5bcf733-f98d-4e05-a171-2c2466692ea1.png)
   
   Là tầng cao nhất liên có liên quan đến các giao thức trao đổi dữ liệu giữa các hệ thống mở, kiểm soát việc truyền dữ liệu từ nút tới nút (End-to-End). Thủ tục trong 
   3 tầng dưới (vật lý, liên kết dữ liệu và mạng) chỉ phục vụ việc truyền dữ liệu giữa các tầng kề nhau trong từng hệ thống. Các thực thể đồng tầng hội thoại, thương 
   lượng với nhau trong quá trình truyền dữ liệu.
   
   Tầng vận chuyển thực hiện việc chia các gói tin lớn thành các gói tin nhỏ hơn trước khi gửi đi và đánh số các gói tin và đảm bảo chúng chuyển theo đúng thứ tự. Là tầng
   cuối cùng chịu trách nhiệm về mức độ an toàn trong truyền dữ liệu nên giao thức tầng vận chuyển phụ thuộc nhiều vào bản chất của tầng mạng. Tầng vận chuyển có thể thực 
   hiện việc ghép kênh (multiplex) một vài liên kết vào cùng một liên kết nối để giảm giá thành.

   4.5. Vai trò và chức năng tầng mạng (Network Layer)

   ![image](https://user-images.githubusercontent.com/97047640/166892795-e31c90f8-83c5-4bf2-bdff-6befdb183a2d.png)
   
   Tầng mạng thực hiện các chức năng chọn đường đi (routing) cho các gói tin nguồn tới đích có thể trong cùng một mạng hoặc khác mạng nhau. Đường có thể được cố định, 
   cũng có thể được định nghĩa khi bắt đầu hội thoại và có thể đường đi là động (Dynamic) có thể thay đổi với từng gói tin tùy theo trạng thái tải tức thời của mạng. 
   Trong mạng kiểu quảng bá (Broadcast) routing rất đơn giản.
   Một chức năng quan trọng khác của tầng mạng là chức năng điều khiển tắc nghẽn (Congestion Control). Nếu có quá nhiều gói tin cùng lưu chuyển trên cùng một đường thì 
   có thể xảy ra tình trạng tắc nghẽn. Thực hiện chức năng giao tiếp giữa các mạng khi các gói tin đi từ mạng này sang mạng khác để tới đích.
   
   4.6. Vai trò và chức năng tầng liên kết dữ liệu (Data Link Layer)

   ![image](https://user-images.githubusercontent.com/97047640/166892843-d3eb078e-6ec2-4229-b618-aea198c87152.png)
   
   Chức năng chủ yếu của tầng liên kết dữ liệu là thực hiện thiết lập các liên kết, duy trì và hủy bỏ các liên kết dữ liệu. Kiểm soát lỗi và kiểm soát lưu lượng.
   
   Chia thông tin thành các khung thông tin (Frame), truyền các khung tuần tự và xử lý các thông điệp xác nhận (Acknowledgement Frame) từ bên máy thu gửi về. Tháo gỡ các 
   khung thành chuỗi bit không cấu trúc chuyển xuống tầng vật lý. Tầng 2 bên thu, tái tạo chuỗi bit thành các khung thông tin. Đường truyền vật lý có thể gây ra lỗi, nên 
   tầng liên kết dữ liệu phải giải quyết vấn đề kiểm soát lỗi, kiểm soát luồng, kiểm soát lưu lượng, ngăn không để nút nguồn gây “ngập lụt” dữ liệu cho ben thu có tốc độ 
   thấp hơn. Trong các mạng quảng bá, tầng con MAC (Medium Access Sublayer) điều khiển việc duy trì nhập đường truyền.

   4.7. Vai trò và chức năng tầng vật lý (Physical Layer)

   ![image](https://user-images.githubusercontent.com/97047640/166892874-01cd1b98-fb6f-4a19-a7a1-8698805f6704.png)
   
   Tầng vật lý là tầng thấp nhất trong mô hình 7 lớp OSI. Các thực thể tầng giao tiếp với nhau qua một đường truyền vật lý. Tầng vật lý xác định các chức năng, thủ tục 
   về điện, cơ, quang để kích hoạt, duy trì và giải phóng các kết nối vật lý giữa các hệ thống mạng. Cung cấp các cơ chế về điện, hàm, thủ tục, … nhằm thực hiện việc kết 
   nối các phần tử của mạng thành một hệ thống bằng các phương pháp vật lý. Đảm bảo cho các yêu cầu về chuyển mạch hoạt động nhằm tạo ra các đường truyền thực cho các chuỗi 
   bit thông tin. Các chuẩn trong tầng vật lý là các chuẩn xác định giao diện người sử dụng và môi trường mạng. Các giao thức tầng vật lý có hai loại: truyền dị bộ (Asynchronous) 
   và truyền đồng bộ (Synchronous).


<a name = "tcpip"> </a>

# II. Mô hình TCP\IP

1. TCP\IP là gì?
   
   TCP/IP viết tắt của Transmission Control Protocol (TCP) và Internet Protocol (IP) là giao thức cài đặt truyền thông, chồng giao thức mà hầu hết các mạng máy tính ngày nay đều sử dụng để kết nối. TCP/IP được đặt theo tên của 2 giao thức là giao thức điều khiển giao vận và giao thức liên mạng. Đây là 2 giao thức đầu tiên trên thế giới được định nghĩa.

2. Phương thức hoạt động của TCP\IP
   Trong giao thức TCP/IP, IP có vai trò quan trọng. IP cho phép máy tính chuyển tiếp gói tin tới một máy tính khác. Thông qua một hoặc nhiều khoảng (chuyển tiếp) gần với người nhận gói tin. TCP sẽ giúp kiểm tra các gói dữ liệu xem có lỗi không? Sau đó gửi yêu cầu truyền lại nếu có lỗi được tìm thấy.

Như vậy, quy cách hoạt động của TCP/IP thật ra rất đơn giản. Bạn có thể hình dung việc truyền tin trên Internet tựa như một dây chuyền sản xuất. Các công nhân sẽ lần lượt chuyền các bán thành phẩm qua những giai đoạn khác nhau để bổ sung hoàn thiện sản phẩm. Khi đó, IP giống như là quy cách hoạt động của nhà máy, còn TCP lại đóng vai trò là một người giám sát dây chuyền, đảm bảo cho dây chuyền liên tục nếu có lỗi xảy ra.

3. Sự phát triển của mô hình TCP/IP
   
   TCP/IP là giao thức điều khiển truyền nhận/ giao thức liên mạng. Đây là từ viết tắt của Transmission Control Protocol/Internet Protocol. TCP/IP là một tập hợp các quy tắc, bộ giao thức trao đổi thông tin được tiêu chuẩn hóa cho phép các máy tính giao tiếp trên một mạng như Internet. TCP/IP có khả năng phục hồi tự động.

Từ các thông tin tôi tổng hợp được thì bộ giao thức liên mạng trong công trình DARPA năm 1970 chính là nơi khởi nguồn cho ý tưởng hình thành mô hình TCP/IP ra đời. Ý tưởng này được bắt nguồn bởi Kỹ sư Vinton Cerf và Robert E. Kahn. Họ là những người được xem là cha đẻ của Internet. hai kỹ sư này kết hợp cùng nhiều nhóm nghiên cứu tiến hành nghiên cứu qua nhiều năm để phát triển, hoàn thiện giao thức này. Giao thức TCP/ IP được ổn định hóa từ dầu năm 1978. 

Thử nghiệm thông nối giữa 2 mô hình TCP/IP đã thực hiện thành công vào vào năm 1975. Các cuộc thử nghiệm này sau đó được triển khai nhiều hơn với kết quả tốt. Chính nhờ những thành tựu này mà Internet Architecture Broad mở hội thảo mời hơn 250 công ty thương mại tham dự. Kể từ đó, mô hình TCP/IP được phổ biến rộng rãi trên khắp thế giới đến nay mà tôi và bạn chắc hẳn đều có sử dụng.

4. Ưu điểm của TCP\IP.
   Ưu điểm thứ nhất của TCP/IP chính là không chịu sự kiểm soát của bất kỳ tổ chức nào. Vì vậy, bạn có thể tự do trong việc sử dụng. Thứ hai, TCP/IP có khả năng tương thích cao với tất cả các hệ điều hành, phần cứng máy tính và mạng. Vì vậy, giao thức này hoạt động hiệu quả với nhiều hệ thống khác nhau.

Cuối cùng, TCP/IP có khả năng mở rộng cao. Giao thức này có thể định tuyến. Và thông qua mạng có thể xác định được đường dẫn hiệu quả nhất.

5.Các giao thức TCP/IP phổ biến nhất.

![image](https://user-images.githubusercontent.com/97047640/166900729-7fda1a0c-5fb5-4676-b4dc-3ca98b2a1656.png)

  Hiện nay, TCP/IP có 3 giao thức được sử dụng phổ biến nhất là HTTP, HTTPS, FTP.

HTTP: HTTP được sử dụng để truyền dữ liệu không an toàn giữa một web client và một web server. Theo quy trình, web client (trình duyệt Internet trên máy tính) sẽ gửi một yêu cầu đến một web server để xem một website. Sau đó, máy chủ web nhận được yêu cầu đó và gửi thông tin website về cho web client.

HTTPS: HTTPS được sử dụng để truyền dữ liệu an toàn giữa một web client và một web server. Giao thức này được dùng để gửi dữ liệu giao dịch thẻ tín dụng hoặc dữ liệu cá nhân khác từ một web tới một web server.

FTP: FTP là phương thức trao đổi file được sử dụng giữa hai hoặc nhiều máy tính thông qua Internet. Nhờ FTP, các máy tính có thể gửi và nhận dữ liệu đến nhau một các trực tiếp.

6. Mô hình phân tầng trong TCP/IP

 ![image](https://user-images.githubusercontent.com/97047640/166900817-d1b216f8-dbe9-4ba2-9d68-b3f9c81b35ae.png)
 
 Mô hình TCP/IP tiêu chuẩn bao gồm 4 tầng được chồng lên nhau, bắt đầu từ tầng thấp nhất là:

- Tầng 1: Tầng vật lý (Physical) 
- Tầng 2: Tầng mạng (Network)
- Tầng 3: Tầng giao vận (Transport)
- Tầng 4: Tầng ứng dụng (Application).

6.1. Tầng 4: Application của TCP/IP là gì?

Tầng Application hay còn gọi là tầng ứng dụng. Tầng ứng dụng đảm nhận vai trò giao tiếp dữ liệu giữa 2 máy khác nhau thông qua các dịch vụ mạng khác nhau (duyệt web, chay hay các giao thức trao đổi dữ liệu SMTP, SSH, FTP…). Dữ liệu khi đến được tầng 4 sẽ được định dạng để kết nối theo kiểu Byte nối Byte. Các thông tin định tuyến tại đây sẽ giúp xác định đường đi đúng của một gói tin.

6.2. Tầng 3: Transport của TCP/IP là gì?

Tầng dữ liệu hoạt động thông qua hai giao thức chính là TCP (Transmisson Control Protocol) và UDP (User Datagram Protocol).

TCP sẽ đảm bảo chất lượng truyền gửi gói tin, tuy nhiên lại mất thời gian khá lâu để thực hiện các thủ tục kiếm soát dữ liệu. Ngược lại, UDP lại cho tốc độ truyền tải nhanh nhưng lại không đảm bảo được chất lượng dữ liệu. Ở tầng này, TCP và UDP sẽ hỗ trợ nhau phân luồng dữ liệu.

6.3. Tầng 2: Internet (Tầng mạng)

Tầng Internet đảm nhận việc truyền tải dữ liệu một cách hợp lý. Các giao thức của tầng này bao gồm IP (Internet Protocol), ICMP (Internet Control Message Protocol), IGMP (Internet Group Message Protocol).

6.4. Tầng 1: Physical (Tầng vật lý)

Tầng vật lý (còn được gọi là tầng liên kết dữ liệu) là tầng thấp nhất trong mô hình TCP/IP. Tầng này chịu trách nhiệm truyền dữ liệu giữa hai thiết bị trong cùng một mạng. Tại đây, các gói dữ liệu được đóng vào khung (gọi là Frame) và được định tuyến đi đến đích đã được chỉ định ban đầu.

<a name = "phanbiet"> </a>

                                                                            # Tài Liệu Tham Khảo
                                                                            
                                    https://www.totolink.vn/article/149-mo-hinh-tcp-ip-la-gi-chuc-nang-cua-cac-tang-trong-mo-hinh-tcp-ip.html
                                    
                                    https://quantrimang.com/kien-thuc-co-ban-ve-mang-phan-17-mo-hinh-osi-43991
