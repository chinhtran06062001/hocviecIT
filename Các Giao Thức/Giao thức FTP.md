# III. Giao thức FTP

1. Tổng quan

- FTP(File Transfer Protocol) là giao thức truyền tệp tin khá phổ biển hiện nay

- Mục đích sử dụng : 

 + Được sử dụng để trao đổi tập tin qua mạng lưới truyền thông sử dụng TCP/IP (internet, mạng nội bộ, ...)
 + Sử dụng để tải xuống máy tính các file từ máy chủ
 + Mặc dù việc truyền file từ hệ thống này sang hệ thống khác rất đơn giản và dễ hiểu, nhưng đôi khi xảy ra những vấn đề khác nhau. Ví dụ, 2 hệ thống có các cách khác 
 nhau để thể hiện văn bản và dữ liệu hay 2 hệ thống có cấu trúc thư mục khác nhau,... Giao thức FTP khắc phục những vấn đề này bằng các thiết lập 2 kết nối  giữa các 
 máy chủ. Một kết nối để sử dụng truyền dữ liệu, một kết nối còn lại được sử dụng để điều khiển kết nối.

2. Mô hình và nguyên lý hoạt động của FTP
2.1 Mô hình cơ bản FTP
   a. Kết nối TCP trong FTP
      Giống như hầu hết các giao thức TCP/IP, FTP dựa trên mô hình Client - Server. Tuy nhiên, khác với các ứng dụng khác chạy trên nền TCP/IP, FTP cần tới 2 kết nối TCP :
      * Control Connecttion (sử dụng port 21 - trên server): Đây là kết nối TCP logic chính thức được tạo ra khi phiên bản làm việc được thiết lập.Nó được thực hiện 
      giữa các quá trình điều khiển. Nó được thực hiện giữa các quá trình điều khiển. Nó được duy trì trong suốt phiên làm việc chỉ cho các thông tin điều khiển đi qua 
      như lệnh hay respone (phản hồi)
      
      * Data Connect (Sử dụng port 20 - trên server): Kết nối này sử dụng các quy tắc rất phức tạp vì các loại dữ liệu có thể khác nhau. Nó được thực hiện giữa các quá 
      trình truyền dữ liệu. Kết nối này mở khi có lệnh chuyển tệp và đóng khi tệp truyền xong.
  b. Mô hình FTP
  
  ![image](https://user-images.githubusercontent.com/97047640/167326840-fbb208bd-b5a9-46bf-a2fc-5d7b30ce5e65.png)

  Do chức năng điều khiển và dữ liệu được truyền tải bằng cách sử dụng các kênh riêng biệt nên mô hình FTP chia sẻ mỗi thiết bị thành 2 thành phần giao thức logic chịu 
  trách nhiệm cho mỗi kết nối ở trên :
      
      * Protocol interpreter (PI) : Là thành phần quản lý kênh điều khiển, phát và nhận lệnh trả lời.
      
      * Data transfer process (DTP) : chịu trách nhiện gửi và nhận dữ liệu từ client và server.
     
c. Chức năng trong từng phần trong mô hình FTP

- Phía server 

   + Server Protocol Interpreter (Server - PI) : Chịu trách nhiệm quản lý Control Connection trên server. Nó lắng nghe yêu cầu kết nối hướng từ User trên cổng 21. Khi 
   kết nối được thiết lập, Nó nhận lệnh từ User-PI, gửi phản hồi và quản lý tiến trình truyền dữ liệu trên Server.
   + Server Data Transfer  Process (Server-DTP): Chịu trách nhiệm nhận và gửi file từ User-DTP. Server-DTP vừa làm nhiệm vụ thiết lập Data Connection và lắng nghe Data 
   Connect ủa User thông qua cổng 20. Nó tương tác với Server File System trên hệ thống cục bộ để đọc và chép file.
- Phía Client 
   + User Inter : Đây là chương trình được chạy trên máy tính, nó cung cấp giao diện xử lý cho người dúng, chỉ có trên phía Client. Nó cho Phép người dùng sử dụng những 
   lệnh đơn giản để điều kiển các session FTP, từ đó có thể theo dõi được các thông tin và kết quả xảy ra trong quá trình.
   + User Protocol Interpreter (User - PI) : Chịu trách nhiệm quản lý Control Connection phí Client. Nó khỏi tạo liên kết nối FTP bằng việc phát hiện ra request tới 
   Server-IP. Sau khi kết nối được thiết lập, nó xử lý các lệnh nhận được trên Interface, gửi chúng tới Server-PI rồi đợi nhận Respone trở lại. Nó cũng quản lý các 
   tiến trình trên Client.
   + User Data Transfer Process (User-DTP) : Có nhiệm vụ gửi hoặc nhận dữ liệu từ Server-DTP. User DTP có thể thiết lập hoặc lắng nghe Data Connection từ Server thông 
   qua cổng 20. Nó tương tác với Client File System trên Client để lưu trữ file. 
   
2.2 Nguyên lý hoạt động của FTP

Cần có 2 kết nối TCP trong phiên làm việc của FTP: TCP Data Connection trên cổng 20, TCP Control Connection trên cổng 21.

- Control connection : Luôn được mở ở mọi thời điểm khi dữ liệu hoặc lệnh được gửi.
- Data Connection : chỉ được mở khi có trao đổi dữ liệu thực.

* Trình tự chung của FTP :
    1.FTP mở Control Connection đến FTP server(trên port 21) và chỉ định 1 cổng trên Client để Server gửi lại phản hổi. Đường kết nối này dùng để truyền lệnh và không phải dữ liệu. Control Connection sẽ mở trong suốt thười gian của phiên làm việc (telnet giữa 2 hệ thống)
    2.Client chuyể tiếp thông tin như Username, password tới Server để thực hiện xác thực(authertication). Server sẽ tra lời bằng mã chấp nhận hay từ chối của các Request.
    3.Client gửi thêm các lệnh với tên tệp, kiểu dữ liệu,... để vận chuyên, thêm luồng dữ liệu (tức là chuyển tập tin từ máy khách đến máy chủ hoặc ngược lại).Server sẽ phản hồi với mã (Reply code) chấp nhận hoặc từ chối.
    4.Khi dữ liệu đã sẵn sàng, 2 bên sẽ mở kết nối TCP trên cổng 20
    5.Dữ liệu có thể được vạn chuyển giữa Client và Server trên cổng 20. Dữ liệu vận chuyển được mã hóa theo 1 số định dạng bao gồm NVT-ASCII hoặc nhị phân(binary)
    6.Khi quá trình vận chuyển dữ liệu được hoàn thành, phiên làm việc của FTP Server sẽ đóng lại Data Connection trên cổng 20. Nhưng vẫn giữ Control Connection trên cổng 21.
    7.Control Connection có thể được sử dụng để thiết lập truyền dữ liệu khác hoặc đóng liên kết
2.3 Một số lệnh Command sử dụng trên FTP

|Command|Đối số (Argument)|Mô tả (Description)|
|--------|--------|---------|
|USER|username|Tên người dùng|
|PASS|	password|	Password|
|ACCT|	account info|	User account|
|CWD	|pathname	|Thay đổi thư mục làm việc|
|CDUP|	none	|Thay đổi thư mục cha|
|SMNT|	pathname|	Kết cấu|
|REIN|	none	|Dừng và khởi động lại|
|QUIT|	none	|Đăng xuất khỏi FTP|
|RETR|	pathname|	Lấy tập tin từ máy chủ|
|STOR|	pathname|	Lưu trữ dữ liệu trên máy chủ|
|RNFR|	pathname|	Đổi tên từ …|
|RNTO|	pathname|	Đổi tên thành …|
|DELE|	pathname|	Xóa file|
|RMD	|pathname	|Xóa thư mục|
|MKD	|pathname	|Tạo thư mục|
|LIST|	pathname|	Liệt kê tệp tin hoặc văn bản|
|STAT|	pathname|	Status|
|HELP|	subject|	Hiện màn hình trợ giúp|
|PORT|	host-port|	Chỉ định cổng vận chuyển(không mặc định)|
|TYPE|	type code|	Kiểu vận chuyển(ASCII, image,…)|
|MODE|	mode code|	Chế độ truyền (stream, block,…)|

2.4 FTP Reply

Mỗi lần User-PI gửi lệnh đến Server-PI qua Control Connection, Server sẽ gửi lại phản hồi dưới dạng các code. Code Reply nhằm các mục đích sau :
    - Xác nhận máy chủ đã nhận được lệnh.
    - Cho biết lệnh từ phía người dùng có được chấp nhận hay không, nếu xảy ra lỗi đó thì đó là lỗi gì?
    - Cho biết nhiều thông tin khác nhau cho người dùng về phiên, ví dụ như là : tình trạng truyền file,...

* Cấu trúc FTP Reply Code : Xyz.
  Ý nghĩa của X trong FTP Reply Code
  |Reply Code Format|Description|
  |---------|----------|
  |1yz	|Đã khởi tạo hành động. Chờ 1 reply trước khi gửi 1 lệnh khác|
  |2yz	|Hành động hoàn thành. Có thể gửi lệnh mới|
  |3yz	|Lệnh được chấp nhận. Nhưng bị giữ do thiếu thông tin|
  |4yz	|Lệnh không được chấp nhận hoặc không hoàn thành. Tình trạng lỗi tồn tại tạm thời. Lệnh có thể được ban hanh lại|
  |5yz	|Lệnh không được chấp nhận hoặc đã hoàn thành. Không ban hành lại lệnh, ban hành lại lệnh sẽ dẫn đến cùng một lỗi|
  Tham số y cung cấp thêm thông tin như bảng dưới. z cũng cung cấp thêm thông tin nhưng ý nghĩa chính xác có thể khác nhau giữa các cài đặt.\
  |Reply Code Format|Description|
  |---------|----------|
  |X0z	|Lỗi cú pháp hoặc lệnh bất hợp pháp|
  |X1z	|Trả lời Request thông tin|
  |X2z	|Trả lời đề cập đến Connection management|
  |X3z	|Trả lời trạng thái máy chủ|
  Chú ý: Điều quan trọng cần lưu ý trong FTP, các Request không nhất thiết phải được thực hiện theo cùng 1 trình tự khi đã gửi, các giao dịch (transactions) và trả lời (reply) có thể được xen kẽ.
  
2.5 Tính bảo mật của FTP

Giống như phần lớn các giao thức cũ, phương pháp đăng nhập đơn giản của FTP là một sự kế thừa từ những giao thức ở thời kì đầu của Internet. Ngày nay, nó không còn đảm bảo tính an toàn cần thiết trên môi trường Internet toàn cầu vì username và password được gửi qua kênh kết nối điều khiển dưới dạng clear text(không mã hóa).

Điều này làm cho bảo mật FTP đã định ra thêm nhiều tùy chọn chứng thực và mã hóa phức tạp cho những ai muốn tăng thêm mức độ an toàn vào trong phần mềm FTP của họ.

3. Kênh dữ liệu trong FTP
Kênh điều khiển được tạo ra giữa Server-PI và User-PI, sử dụng quá trình thiết lập kết nối và chứng thực được duy trì trong suốt phiên kết nối FTP. Các lệnh và các hồi đáp được trao đổi giữa bộ phận PI (Protocol Interpreter) qua kênh điều khiển, những dữ liệu thì không.

Mỗi khi cần phải truyền dữ liệu giữa các server và client, một kênh dữ liệu cần phải được tạo ra. Kênh dữ liệu kết nối bộ phận User-DTP và Server-DTP. Kết nối này cần thiết cho cả hoạt động truyền file trực tiếp (gửi hoặc nhận một file) cũng như đối với việc truyền dữ liệu ngầm, như là yêu cầu một danh sách file trong thư mục nào đó trên server.

Để tạo ra kênh dữ liệu, FTP sử dụng 2 phương thức khác nhau: Normal (Active) Data Connections (mặc định) và Passive Data Connections.

Khác biệt giữa 2 phương thức này là phía Client hay bên Server đưa ra yêu cầu khởi tạo kết nối.

3.1 Normal (Active) Data Connection (mặc định) 
Phương thức tạo kết nối dữ liệu bình thường hay còn gọi là Kết nối kênh dữ liệu ở dạng chủ động.

Phía Server-DTP tạo kênh dữ liệu bằng cách mở một cổng kết nối tới User-DTP. Server sử dụng cổng đặc biệt được dành riêng cho kết nối dữ liệu là cổng số 20. Trên máy Client, cổng mặc định được sử dụng chính là cổng được sử dụng để kết nối điều khiển, nhưng Server sẽ thường chọn mỗi cổng khác nhau cho mỗi chuyển giao.

3.2 Passive Data Connections.

Phương thức tạo kết nối bị động.

- Server sẽ chấp nhận 1 yêu cầu kết nối dữ liệu được khởi tạo từ Client.
- Server sẽ trả lời lại phía Client với địa chỉ IP cũng như địa chỉ cổng mà Server sẽ sử dụng.
- Sau đó phía Server-DTP lắng nghe trên cổng này một kết nối TCP đến từ User-DTP.
- Theo mặc định, phía Client sẽ sử dụng cùng cổng mà nó sử dụng cho Control Connection như trong trường hợp chủ động. Tuy nhiên, trong phương pháp này, Client cũng có thể chọn sử dụng một cổng khác cho Data Connection nếu cần thiết.

4. Các phương thức truyền dữ liệu

Khi Client-DTP và Server-DTP thiết lập xong kênh dữ liệu, dữ liệu sẽ được truyền trực tiếp từ phía Client tới phía Server, hoặc ngược lại, tùy theo các lệnh được sử dụng. Do thông tin điều khiển được gửi đi trên kênh điều khiển, nên toàn bộ kênh dữ liệu có thể được sử dụng để truyền dữ liệu. FTP có ba phương thức truyền dữ liệu, đó là: stream mode, block mode, và compressed mode.

4.1 Stream mode

- Dữ liệu truyền đi liên tiếp dưới dạng các byte không cấu trúc.
- Thiết bị gửi chỉ đơn thuần đẩy luồng dữ liệu qua kết nối TCP tới phía nhận.
- Không có trường tiêu đề nhất định
- Không có cấu trúc dạng Header, nên việc báo hiệu kết thúc file sẽ đơn giản được thực hiện khi thiết bị gửi ngắt kênh kết nối dữ liệu khi đã truyền dữ liệu xong.
- Được sử dụng nhiều nhất trong 3 phương thức trong triển khai FTP thực tế. Do:
     + Là phương thức mặc định và đơn giản nhất.
     + Là phương thức phổ biến nhất, vì nó xử lí các file chỉ đơn thuần là xử lí dòng byte, mà không cần để ý tới nội dung.
     + Không tốn 1 lượng byte “overload” nào để thông báo Header.

4.2 Block Mode

- Phương thức truyền dữ liệu mang tính quy chuẩn hơn.
- Dữ liệu được chia thành nhiều khối nhỏ và đóng gói thành các FTP block.
- Mỗi block có 1 trường Header 3 byte: báo hiệu độ dài, và chứa thông tin về các khối dữ liệu đang được gửi.
- Một thuật toán đặc biệt được sử dụng để kiểm tra các dữ liệu đã truyền đi. Và để phát hiện, khởi tạo lại đối với 1 phiên truyền dữ liệu đã bị ngắt kết nối.

4.3 Compressed mode (Chế độ nén)

- Phương thức truyền dữ liệu sử dụng 1 kỹ thuật nén đơn giản, là “run-lenght encoding (mã hóa chiều dài)” – có tác dụng phát hiện và xử lí các đoạn lặp trong dữ liệu được truyền đi để giảm chiều dài của toàn bộ thông điệp.
- Thông tin sau khi được nén, sẽ được xử lí như Block mode, với trường Header.
- Trong thực tế, việc nén dữ liệu thường được thực hiện ở chỗ khác, làm cho phương thức Compressed mode trở nên không cần thiết.

5. Dữ liệu trong FTP

Các tập tin được coi như một tập hợp các byte. FTP không quan tâm nội dung tập tin, sẽ chỉ đơn giản là di chuyển các tệp tin, các byte cùng 1 thời điểm, từ nơi này sang nơi khác.

1. FTP Data types:

Phần đầu tiên của thông tin có thể được đưa ra về tập tin là kiểu dữ liệu của nó.

Có 4 kiểu dữ liệu khác nhau được quy định trong chuẩn của FTP.

    - ASCII: file văn bản ASCII
    - EBCDIC: tương tự ASCII, nhưng sử dụng kiểu kí tự EBCDIC do IBM đặt.
    - Image: Các tập tin không có cấu trúc nội bộ chính thức.
    - Local: Kiểu dữ liệu này được sử dụng để xử lí các tập tin có thể lưu trữ dữ liệu trong byte logic. Cách xác định loại này cùng với cách dữ liệu có cấu trúc cho phép dữ liệu được lưu trữ trên hệ thống đích một cách phù hợp với đại diện local của nó.
Trong thực tế, hai loại kiểu dữ liệu thường xuyên nhất được sử dụng là ASCII và Image. Kiểu ASCII được sử dụng cho các tập tin văn bản, và cho phép chúng được di chuyển giữa các hệ thống với dòng kết thúc mã chuyển đổi tự động. Loại Image được sử dụng cho các tập tin nhị phân, chẳng hạn như đồ họa hình ảnh, tập tin ZIP và các dữ liệu khác. Nó cũng thường được gọi là kiểu nhị phân vì lý do đó.

2. FTP Format Control

Đối với các loại ASCII và EBCDIC, FTP xác định 1 tham số tùy chọn được gọi là “format control” (điều khiển định dạng), nó cho phép người dùng chỉ định một đại diện cụ thể cho cách sử dụng định dạng dọc để mô tả tệp.

Các tùy chọn kiểm soát định dạng được tạo ra cho mục đích cụ thể đúng cách xử lý các tập tin chuyển giao từ các thiết bị máy chủ đến máy in. Nó không được sử dụng ngày nay, hoặc nếu nó được sử dụng, nó chỉ là trong ứng dụng đặc biệt.

3 tùy chọn trong FTP Format Control:

      - Non Print : Đây là tùy chọn mặc định, cho biết không có định dạng dọc
      - Telnet Format : Tệp sử dụng các kí tự điều khiển định dạng dọc, như được chỉ định trong giao thức Telnet
      - Carriage Control/FORTRAN : Tệp sử dụng kí tự điều khiển được định dạng đưa ra làm kí tự đầu tiên của mỗi dòng, như được xác định cho ngôn ngữ lập trình FORTRAN.

3. FTP Data Structures

Ngoài việc xác định một loại dữ liệu tệp tin, ta cũng có thể xác định cấu trúc tệp tin theo 3 cách:

      - File Structure : Tệp là 1 luồng byte liền kề không có cấu trúc bên trong. Đây là cách mặc định và được sử dụng cho hầu hết các loại tệp.
      - Record Structure : Tệp bao gồm một tập hợp các bản ghi, mỗi bản ghi được phân định bằng đánh dấu end-of-record. Cấu trúc bản ghi có thể sử dụng cho các tệp văn bản ASCII, nhưng chúng thường được gửi với cấu trúc tệp thông thường sử dụng kiểu dữ liệu ASCII.
      - Page Structure : Tệp chứa 1 trang dữ liệu được lập chỉ mục đặc biệt. Cấu trúc này không được sử dụng phổ biến. Nó được tạo ra cho 1 máy tính cổ xưa được sử dụng trong ARPAnet đời đầu.
