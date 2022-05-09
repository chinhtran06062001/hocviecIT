# IV. Giao thức SSH

1. SSH là gì?

SSH (Secure Socket Shell) là một giao thức mạng mật mã cho phép hai máy tính giao tiếp là chia sẻ dữ liệu an toàn qua Internet.

Được phát triển bởi SSH Communication Sercurity Ltd để giao tiếp an toàn cho máy từ xa.

2. Công dụng của giao thức SSH.

- Được sủ dụng để đăng nhập vào một máy chủ từ xa để thwucj hiện các lệnh và truyền dữ liệu từ máy này sang máy khác.
- Gaio tiếp an toàn cung cấp xác thực mật khẩu mạnh và giao tiếp được mã hóa bằng khóa công khai qua một kênh không an toàn. Nó được sử dụng để thay thế các giao thức đăng nhập từ xa không được bảo vệ như Telnet, Rlogin, RSH, v.v. và giao thức FTP
- Các tính năng bảo mật của nó được các quản trị viên mạng sủ dụng rộng rãi để quản lý hệ thống và ứng dụng từ xa.
- Giao thức SSh bảo vệ mạng khỏi các cuộc tấn công khác nhau như giả mạo DNS, định tuyến nguồn IP và giả mạo IP.

* Mô phỏng giao thức SSH
Trước SSH :

![image](https://user-images.githubusercontent.com/97047640/167337929-8f82b4b4-6556-4e8f-b143-4f3e4b8a8189.png)

Sau SSH :

![image](https://user-images.githubusercontent.com/97047640/167337962-2cc913d8-2816-4da6-9ade-cf9b5f097120.png)

3. Đặc điểm của giao thức SSH

Các cách sử dụng phổ buến của giao thức SSH được đưa ra dưới đây:
- SSH cung cấp quyền truy cập an toàn cho người dùng và các quy trình tự động.
- Đây là một cahs dễ dàng và an toàn để chuyển các tệp từ hệ thống này sang hệ thống khác qua một mạng không an toàn.
- SSH cũng đưa ra các lệnh từ xa cho người dùng
- SSH giúp người dùng quản lý cơ sở hạ tầng mạng và các thành phần hệ thống quan trọng khác
- SSH được sử dụng để đăng nhập vào hệ thống từ xa (Máy chủ), thay thế Telnet và Rlogin và được sử dụng để thực thi một lệnh duy nhất trên máy chủ, thay thế cho RSH.
- SSH kết hợp với tiện ích rssync để sao lưu, sao chép và nhân bản các tệp với tính bảo mật và hiệu quả hoàn toàn.
- SSH có thể được sử dụng  để chuyển tiếp một cổng
- Bằng cách sử dụng SSH, chúng tôi có thể thiết lập đăng nhập tự động vào máy chủ từ xa như OpenSSH
- Chúng tôi có thể duyệt web một cahs an toàn thông qua kết nối proxy được mã hóa với máy khách SSH, hỗ trợ giao thức SOCKS

4. Cách mà SSH hoạt động ?

Giao thức SSH hoạt động theo mô hình máy khách - máy chủ, có nghĩa là nó kết nối ứng dụng máy khách trình bao an toàn (Kết thúc ở nói phiên được hiển thị) với máy chỉ SSH (Kết thúc ở nơi phiên thực thi).

SSH hoạt động qua 3 bước : 
   - Định danh host : Xác định danh của hệ thống tham gia làm việc SSH.
   - Mã hóa : Thiết lập kênh làm việc mã hóa.
   - Chứng thực : Chứng thực người dùng có quyền đăng nhập hệ thống.

4.1 Định danh host

Quá trình định danh host được thực hiện bằng việc trao đổi khoá. Mỗi máy tính có hỗ trợ kiểu truyền thông SSH có một khoá định danh duy nhất. Khoá này có hai thành phần là khoá riêng và khoá công cộng.

Khi có sự thay đổi về cấu hình trên máy chủ: Tức thay đổi chương trình SSH, thay đổi cơ bản trong hệ điều hành, thì khoá định danh cũng sẽ thay đổi. Khi đó mọi người dùng SSH để truy cập vào máy chủ này đều được thông báo về sự thay đổi này.

Khi hai hệ thống bắt đầu làm việc SSH, máy chủ sẽ gửi khoá công cộng của nó cho máy khách. Máy khách tạo ra một khoá ngẫu nhiên và mã hoá khoá này bằng khoá công cộng từ máy chủ, tiếp đó nó gửi lại cho máy chủ.

Máy chủ sẽ giải mã khoá phiên này bằng khoá riêng của mình và nhận được khoá phiên. Khoá phiên này sẽ là khoá dùng để trao đổi dữ liệu giữa hai máy. Đây là quá trình được xem như các bước nhận diện máy khách và máy chủ.

4.2 Mã hóa

Sau khi thiết lập phiên làm việc bảo mật (trao đổi khoá, định danh), quy trình trao đổi dữ liệu diễn ra thông qua một bước trung gian đó là mã hoá/giải mã. 

Điều này có nghĩa là dữ liệu gửi/nhận trên đường truyền đều được mã hoá và giải mã theo quy tắc đã thoả thuận trước giữa máy chủ và máy khách. Việc lựa chọn cơ chế mã hoá thường là do máy khách quyết định. Những cơ chế mã hoá thường được chọn bao gồm: 3DES, IDEA, và Blowfish.

4.3 Chứng thực

Đây là bước cuối cùng, tại thời điểm này kênh trao đổi bản thân nó đã được bảo mật. Mỗi định danh và truy nhập của người dùng có thể được cung cấp theo nhiều cách khác nhau. 

Cụ thể như kiểu xác thực Rhosts, được dùng để xác thực định danh tính của những máy khách đã được nêu trong file rhost theo địa chỉ DNS và IP. Cách thức xác thực mật khẩu là cách rất thông dụng để định danh người dùng. Ngoài ra, cũng có các cách khác như: chứng thực RSA, dùng ssh-agent và ssh-keygen để xác thực những cặp khoá.

5.Lịch sử của giao thức SSH

Có 3 phiên bản SSH: 
   - Phiên bản 1.x: Phiên bản đầu tiên của SSH được ra mắt vào năm 1995 và được thiết kế bởi Tatu Ylönen, nhà nghiên cứu tại Đại học Công nghệ Helsinki, Phần Lan. Nó được gọi là SSH-1. Trong phiên bản này, có một số vấn đề và do đó nó bị giảm giá trị. 
   - Phiên bản 2.x: Phiên bản thứ hai được gọi là SSH-2, phiên bản hiện tại của giao thức SSH. Vào năm 2006, nó đã được chọn là đặc điểm kỹ thuật của Theo dõi Tiêu chuẩn bởi Lực lượng Đặc nhiệm Kỹ thuật Internet (IETF). Phiên bản này không tương thích với giao thức SSH-1. Nó có các tính năng bảo mật tốt hơn so với SSH-1. 
   - Phiên bản 1.99: Phiên bản 1.99 được chỉ định là phiên bản proto của 2.1. Nó không phải là phiên bản thực tế mà là một cách để xác định khả năng tương thích ngược.

6. Kiến trúc của giao thức SSH

Kiến trúc SSH được tạo thành từ ba lớp được phân tách rõ ràng. Các lớp này là:

   - Transport Layer (Lớp vận chuyển)
   - User-authentication layer (Lớp xác thực người dùng)
   - Connection Layer (Lớp kết nối)
   
Kiến trúc giao thức SSH là một kiến trúc mở.Do đó nó cung cấp tính linh hoạt cao và cho phép sử dụng SSH cho nhiều mục đích khác thay vì chỉ một lớp bảo mật. Trong kiến trúc, lớp truyền tải tương tự như bảo mật lớp truyền tải (TLS). Lớp xác thực người dùng có thể được sử dụng với các phương pháp xác thực tùy chỉnh và lớp kết nối cho phép ghép các phiên phụ khác nhau thành một kết nối SSH duy nhất.

6.1 Lớp vận chuyển

 Lớp truyền tải là lớp trên cùng của bộ giao thức TCP/IP. Đối với SSH-2, lớp này chịu trách nhiệm xử lý trao đổi khóa ban đầu, xác thực máy chủ, thiết lập mã hóa, nén và xác minh tính toàn vẹn. Nó hoạt động như một giao diện để gửi và nhận các gói tin rõ ràng với kích thước lên đến 32, 768byte.

6.2 Lớp xác thực người dùng

 Như tên gọi của nó, lớp xác thực người dùng chịu trách nhiệm xử lý xác thực máy khách và cung cấp các phương pháp xác thực khác nhau. Việc xác thực được thực hiện ở phía máy khách; do đó, khi một lời nhắc xảy ra cho một mật khẩu, nó thường dành cho một máy khách SSH hơn là một máy chủ và máy chủ sẽ phản hồi lại những xác thực này.

 Lớp này bao gồm các phương pháp xác thực khác nhau, những phương pháp này là:

     - Password: Xác thực bằng mật khẩu là một cách xác thực đơn giản. Nó bao gồm tính năng thay đổi mật khẩu để dễ dàng truy cập. Nhưng nó không được sử dụng bởi tất cả các ứng dụng.
     - Public-key: Khóa công khai là một phương pháp xác thực dựa trên khóa công khai, hỗ trợ các cặp khóa DSA, ECDSA hoặc RSA.
     - Keyboard-interactive: Đây là một trong những phương pháp xác thực linh hoạt. Trong trường hợp này, máy chủ sẽ gửi lời nhắc nhập thông tin và máy khách sẽ gửi lại thông tin đó cùng với các phản hồi đã nhập của người dùng. Nó được sử dụng để cung cấp mật khẩu một lần hoặc xác thực OTP.
     - GSSAPI: Trong phương pháp này, xác thực được thực hiện bởi các phương pháp bên ngoài như Kerberos 5 hoặc NTLM, cung cấp khả năng đăng nhập một lần cho các phiên SSH.

6.3 Lớp kết nối

 Lớp kết nối xác định các kênh khác nhau mà qua đó các dịch vụ SSH được cung cấp. Nó định nghĩa khái niệm kênh, yêu cầu kênh và yêu cầu toàn cục. Một kết nối SSH có thể lưu trữ đồng thời các kênh khác nhau và cũng có thể truyền dữ liệu theo cả hai hướng đồng thời. Yêu cầu kênh được sử dụng trong lớp kết nối để chuyển tiếp dữ liệu kênh cụ thể ngoài băng tần, ví dụ, kích thước đã thay đổi của cửa sổ đầu cuối hoặc mã thoát của quy trình phía máy chủ. Các loại kênh tiêu chuẩn của lớp kết nối là:

      - shell: Nó được sử dụng cho các shell đầu cuối, SFTP và các yêu cầu thực thi.
      - direct-tcpip: Nó được sử dụng cho các kết nối được chuyển tiếp từ máy khách đến máy chủ.
      - forwarded-tcpip: Nó được sử dụng cho các kết nối được chuyển tiếp từ máy chủ đến máy khách.

7. Kỹ thuật mã hóa SSH

 Để thực hiện một đường truyền an toàn, SSH sử dụng ba kỹ thuật mã hóa khác nhau tại các điểm khác nhau trong quá trình truyền. Các kỹ thuật này là:

     - Mã hóa đối xứng (Symmetrical Encryption)
     - Mã hóa không đối xứng (Asymmetrical Encryption)
     - Băm (Hashing)

7.1 Mã đối xứng

 Chỉ một khóa có thể được sử dụng trong kỹ thuật mã hóa đối xứng để mã hóa và giải mã các thông điệp được gửi và nhận từ đích. Kỹ thuật này còn được gọi là mã hóa khóa chia sẻ vì cả hai thiết bị đều sử dụng cùng một khóa để mã hóa dữ liệu chúng gửi và giải mã dữ liệu nhận được.

Kỹ thuật này mã hóa toàn bộ kết nối SSH để ngăn chặn các cuộc tấn công man-in-middle. Trong kỹ thuật này, một vấn đề phát sinh tại thời điểm trao đổi khóa ban đầu. Đối với vấn đề này, nếu một bên thứ ba có mặt trong quá trình trao đổi khóa, họ có thể biết khóa và đọc toàn bộ thông báo.

 Các thuật toán trao đổi chính được sử dụng để ngăn chặn vấn đề này. Với thuật toán này, các khóa bí mật có thể được trao đổi một cách an toàn mà không bị đánh chặn.

Mã hóa không đối xứng được yêu cầu để thực hiện thuật toán trao đổi khóa.

7.2 Mã hóa không đối xứng

 Trong mã hóa không đối xứng, hai khóa khác nhau được sử dụng để mã hóa và giải mã, khóa riêng và khóa công khai. Khóa riêng tư chỉ dành riêng cho người dùng và không thể được chia sẻ với bất kỳ người dùng nào khác, trong khi khóa công khai được chia sẻ công khai. Khóa công khai được lưu trên máy chủ SSH, trong khi khóa riêng được lưu cục bộ trên máy khách SSH; hai khóa này tạo thành một cặp khóa. Thông báo được mã hóa bằng khóa công khai chỉ có thể giải mã bằng khóa riêng tương ứng.

Đây là một kỹ thuật an toàn hơn rất nhiều, như thể một bên thứ ba có được khóa công khai và họ không thể giải mã thông điệp vì họ không biết khóa riêng tư.

Mã hóa không đối xứng không mã hóa phiên SSH hoàn chỉnh. Thay vào đó, nó chủ yếu được sử dụng cho thuật toán trao đổi khóa của mã hóa đối xứng. Trong điều này, trước khi thiết lập kết nối, cả hai hệ thống (máy khách và máy chủ) tạm thời tạo ra các cặp khóa công khai và riêng tư và sau đó chia sẻ khóa riêng của chúng để tạo khóa bí mật được chia sẻ.

Sau khi thiết lập kết nối đối xứng an toàn, máy chủ sử dụng khóa công khai để truyền nó đến máy khách để xác thực. Máy khách chỉ có thể giải mã dữ liệu nếu nó có khóa riêng và do đó phiên SSH được thiết lập.

7.3 Băm

BămTrong SSH, băm một chiều được sử dụng làm kỹ thuật mã hóa, là một dạng mật mã khác. Kỹ thuật băm khác với hai phương pháp trên, vì nó không có nghĩa là giải mã. Nó tạo ra chữ ký hoặc bản tóm tắt thông tin. SSH sử dụng HMAC (Xác thực tin nhắn dựa trên băm) để đảm bảo rằng các tin nhắn được gửi đến ở dạng hoàn chỉnh và không bị sửa đổi.

Trong kỹ thuật này, mỗi bản tin được truyền đi phải có một MAC, MAC này sử dụng ba thành phần: khoá đối xứng, số thứ tự gói và nội dung bản tin. Ba thành phần này tạo thành hàm băm tạo ra một chuỗi không có bất kỳ ý nghĩa nào và chuỗi này được gửi đến máy chủ. Máy chủ lưu trữ cũng có thông tin tương tự, vì vậy họ cũng tạo ra một hàm băm và nếu hàm băm được tạo khớp với hàm băm đã nhận, điều đó có nghĩa là thông báo không được xử lý.

8. Mục tiêu của SSH

 Giao thức SSH có thể chuyển những điều sau:

     - Dữ liệu
     - Văn bản
     - Lệnh
     - Các tập tin
     - Các tệp được truyền bằng SFTP (Giao thức truyền tệp an toàn), phiên bản được mã hóa của FTP cung cấp bảo mật để ngăn chặn bất kỳ mối đe dọa nào.

9. Sự khác nhau giữa SSH và Telnet

 - Telnet là giao thức ứng dụng internet đầu tiên được sử dụng để tạo và duy trì một phiên đầu cuối trên một máy chủ từ xa.
 - Cả SSH và Telnet đều có chức năng giống nhau. Tuy nhiên, sự khác biệt chính là giao thức SSH được bảo mật bằng mật mã khóa công khai xác thực điểm cuối trong khi thiết lập phiên đầu cuối. Mặt khác, không có xác thực nào được cung cấp trong Telnet để xác thực của người dùng, khiến nó kém an toàn hơn.
 - SSH gửi dữ liệu được mã hóa, trong khi Telnet gửi dữ liệu ở dạng văn bản thuần túy.
 - Do tính bảo mật cao, SSH là giao thức ưa thích cho các mạng công cộng, trong khi do tính bảo mật kém hơn, Telnet thích hợp cho các mạng riêng.
 - SSH chạy trên port số 22 theo mặc định, nhưng nó có thể được thay đổi, trong khi Telnet sử dụng cổng số 23, được thiết kế đặc biệt cho mạng cục bộ.

10. SSH2

 SSH2 cũng giống với SSH là giao thức mạng có chức năng thiết lập các kết nối bảo mật, nó sử dụng một cơ chế mã hóa đủ mạnh để tránh các hiện tượng nghe trộm, đánh cắp thông tin trên đường truyền, chính vì vậy các kết nối trên internet của bạn sẽ được an toàn hơn.

Phần mở rộng tệp SSH2 được liên kết với SSH Secure Shell Client, giao thức Internet bảo vệ giao tiếp và cùng một máy chủ có tên cũng như phần mềm máy khách.

11. Một số phần mềm SSH phổ biển

- Windowns PowerShell
- PuTTy
- Secure Shell
- WinSCP
- FileZilla
- OpenSSH
- Dameware FreeSSH
- SmarTTY
