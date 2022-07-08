# IPtables là gì?

IPtables là một ứng dụng Firewall trong Linux. Nó hoàn toàn miễn phí. Ứng dụng này cho phép người dùng có thể cấu hình các quy tắc riêng cho tường lửa, nhằm kiểm soát tất cả các truy cập, chọn lọc truy cập và tăng cường bảo mật.

![image](https://user-images.githubusercontent.com/97047640/177910919-33b2a040-8bae-4269-b1be-dd6830e455c2.png)

# Các thành phần của IPtables linux

IPtables cơ bản chỉ là dòng lệnh dùng để tương tác với thành phần packet filtering của netfilter framework. Packet filtering có cơ chế hoạt động gồm 3 phần là Tables, Chains, Targets.

Trong đó:

Table được IPtables dùng để định nghĩa các quy tắc cho những gói tin. Nó gồm các Table sau. 
- Filter Table: Đây là bảng được IPtables dùng nhiều nhất. Bảng này quyết định kết quả gói tin được đi đến đích hay bị từ chối.

- NAT Table: Là bảng sử dụng các quy tắc về Network Address Translation (NAT). Nó có nhiệm vụ chỉnh sửa source (IP nguồn), hay nhận dạng (IP đích) gói tin khi triển khai cơ chế NAT. 

- Mangle Table: Bảng này có công dụng chỉnh sửa header của gói tin và các giá trị của trường MTU, TTL hay Type of Service.

- Raw Table: Là bảng giúp người dùng có thể làm việc với gói tin trước khi kernel thực hiện kiểm tra trạng thái. Raw Table cũng có thể loại một vài gói tin khỏi tracking, do chúng liên quan đến hiệu năng chung của hệ thống. 

- Security Table: Bảng này được một số kernel hỗ trợ để thiết lập chính sách bảo mật.

Chains: Được tạo ra tương ứng với mỗi Table và có số lượng nhất định. Nó có tính năng lọc gói tin ở nhiều điểm khác nhau. Cụ thể như sau.
- Chain PREROUTING có trong Nat Table, Raw Table, Mangle Table. Các quy tắc trong chain được thực thi tại thời điểm gói tin đi đến giao diện mạng. 

- Chain INPUT có trong Mangle Table, Nat Table và các quy tắc trong chain này được thực thi trước khi gói tin đi đến tiến trình.

- Chain OUTPUT có trong Raw Table, Mangle Table, Filter Table. Các quy tắc trong chain được thực thi sau thời điểm gói tin được tạo ra bởi tiến trình. 

- Chain FORWARD có trong Manle Table, Filter Table. Các quy tắc trong chain được thực thi riêng cho những gói tin định tuyến qua host hiện hành. 

- Chain POSTROUTING có trong Manle Table, Nat Table. Các quy tắc trong chain được thực thi tại thời điểm gói tin rời khỏi giao diện mạng.

Target: Đây là hành động cho những gói tin đáp ứng các quy tắc. Bao gồm:

- ACCEPT: Cho phép gói tin có thể đi vào hệ thống.

- DROP: Gói tin bị loại bỏ và nó không trả lời.

- REJECT: Gói tin bị loại bỏ nhưng nó có trả lời với table của gói tin khác. 

- LOG: Gói tin được chấp nhận và ghi lại log.

# Cách thức hoạt động cơ bản của IPtables

Toàn bộ dữ liệu trong gói tin gửi đi được internet định dạng. Tiếp đến, Linux kernel thực hiện lọc chúng thông qua giao diện bảng các bộ lọc. Và IPtables chính là ứng dụng dòng lệnh, đồng thời cũng là tường lửa của Linux. Nó giúp người dùng cấu hình, duy trì và quản lý các bảng này.

Người dùng có thể thiết lập nhiều bảng khác nhau. Trong đó, mỗi bảng chứa nhiều chuỗi và mỗi chuỗi ứng với một quy tắc. Các quy tắc này sẽ định nghĩa hành động được thực thi khi gói tin phù hợp với nó.

Một mục tiêu (target) chỉ đưa ra khi đã xác định được một gói tin. Mục tiêu có thể là chuỗi khớp với một trong những giá trị như: ACCEPT (gói tin được đi qua), DROP (gói tin bị từ chối, không được đi qua), RETURN (chuỗi hiện tại bị bỏ qua, quy lại quy tắc kế tiếp của chuỗi mà gói tin được gọi).

# Các quy tắc trong IPtables là gì?

Để xem các quy tắc đang có trong IPtables Linux, bạn sử dụng câu lệnh sau: 

IPtables -L –v

TARGET    PROT OPT  IN OUT SOURCE DESTINATION

ACCEPT    all --   lo any anywhere   anywhere

ACCEPT    all --   any any anywhere   anywhere ctstate  RELATED,ESTABLISHED

ACCEPT    tcp --   any any anywhere   anywhere tcp dpt:ssh

ACCEPT    tcp --   any any anywhere   anywhere tcp dpt:http

ACCEPT    tcp --   any any anywhere   anywhere tcp dpt:https

DROP      all --   any any anywhere   anywhere

Trong đó:

- TARGET: Hành động được thực thi.
- PROT: Chính là Protocol. Nó là giao thức được sử dụng để thực thi quy tắc với 3 chọn lựa all, TCP hay UDP. Hầu hết những ứng dụng phổ biến như FTP, sFTP, SSH,… đều dùng TCP.
- IN: Quy tắc được áp dụng đối với những gói tin đi vào từ một interface được xác định hay cho tất cả các interface.
- OUT: Quy tắc được áp dụng đối với những gói tin đi ra từ một interface được xác định hay cho tất cả các interface.
- DESTINATION: Là địa chỉ của lượt truy cập áp dụng quy tắc. 
- ACCEPT    all - - lo any anywhere   anywhere: Là chấp nhận tất cả các gói tin từ interface lo (đây là một interface ảo của nội bộ).
- ACCEPT    all - - any any anywhere   anywhere ctstate  RELATED,ESTABLISHED: Là chấp nhận tất cả các gói tin của kết nối. 
- ACCEPT    tcp - - any any anywhere   anywhere tcp dpt:ssh: Là chấp nhận tất cả các gói tin của giao thức SSH đến từ bất kỳ interface, không loại trừ bất cứ IP nguồn hay đích. Mặc định, hệ thống hiển thị dpt:ssh, tức là cổng 22 của SSH. Trong trường hợp, bạn muốn đổi thành cổng khác thì điền giá trị cổng vào. 
- ACCEPT    tcp - - any any anywhere   anywhere tcp dpt:http: Mặc định hiển thị là http, tức cho phép kết nối đến cổng 80.
- ACCEPT    tcp - - any any anywhere   anywhere tcp dpt:https: Mặc định hiển thị là https, tức cho phép kết nối đến cổng 443.
- DROP      all - -   any any anywhere   anywhere: Toàn bộ những gói tin không khớp với các quy tắc trên sẽ bị loại bỏ.

Các tùy chọn của IPtables Centos 7

Một số tùy chọn được dùng để chỉ định thông số của IPtables là:
```
-t: Tên table
-p: Loại giao 
-i: Card mạng vào
-o: Card mạng ra
-s <địa_chỉ_ip_nguồn>: Địa chỉ IP nguồn
-d <địa_chỉ_ip_đích>: Địa chỉ IP đích
–sport: Cổng nguồn
–dport: Cổng đích
```

Các tùy chọn được dùng thao tác với chain là: 
```
IPtables-N: Tạo chain mới
IPtables –X: Xóa các quy tắc đã tạo trong chain 
IPtables –P: Thiết lập chính sách cho các chain
IPtables –L: Liệt kê các quy tắc trong chain
IPtables –F: Xóa các quy tắc trong chain 
IPtables –Z: Chuyển bộ đếm packet về giá trị 0
```

Các tùy chọn được dùng thao tác với quy tắc là:
```
-A: Thêm quy tắc
-D: Xóa quy tắc
-R: Thay thế quy tắc
-I: Chèn thêm quy tắc
```

Các lệnh cơ bản của IPtables 

Tạo một quy tắc mới, bạn sử dụng câu lệnh sau
```
IPtables -A INPUT -i lo -j ACCEPT
```

Trong đó:

- `A INPUT`: Là kiểu kết nối được áp dụng.

- `i lo`: Là thông tin thiết bị mạng được áp dụng.

- `j ACCEPT`: Là hành động được áp dụng đối với quy tắc.

Bạn thực hiện nhập lại lệnh `IPtables -L –v` thì một quy tắc mới sẽ xuất hiện.

`after-created-IPtables-rule`

Sau khi tiến hành thêm mới hoặc điều chỉnh quy tắc, bạn phải gõ lệnh lưu rồi tái khởi động IPtables để các thay đổi được cập nhật và có thể áp dụng. 

Câu lệnh:
```
service IPtables save 

service IPtables restart
```
Sau đó, bạn tiếp tục thêm một quy tắc mới để lưu lại các kết nối đang có, đồng thời, tránh tình trạng tự block khỏi máy chủ. Cú pháp câu lệnh:

```
IPtables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
```

Kế đến, bạn nhập lệnh để cho phép các port (SSH có port là 22, HTTP có port là 80, HTTPs có port là 443) có thể được truy cập từ ngoài vào bằng giao thức TCP. 

Câu lệnh như sau:
```
IPtables -A INPUT -p tcp --dport 22 -j ACCEPT
```

Trong đó:
```
-p tcp: Giao thức áp dụng (ví dụ như tcp, udp, all)

- - dport 22: Cổng áp dụng và 22 là giá trị của SSH
```

Sau cùng, bạn tiến hành chặn tất cả các kết nối từ bên ngoài không đáp ứng điều kiện của các quy tắc trên. Câu lệnh có dạng:

```
IPtables -A INPUT -j DROP
```

Bổ sung 1 quy tắc mới

Nếu muốn chèn 1 quy tắc mới vào bất kỳ vị trí nào, bạn chỉ việc thay tham số -A table bằng –I (INSERT).

```
IPtables -I INPUT 2 -p tcp --dport 8080 -j ACCEPT
```

Xóa 1 quy tắc

Để xóa 1 quy tắc ở vị trí bất kỳ, bạn dùng tham số -D.

Ví dụ, xóa 1 rule ở hàng 4 thì câu lệnh có dạng:
```
IPtables -D INPUT 4
```
Nếu muốn xóa tất cả các quy tắc chứa hành động DROP thì câu lệnh là: 
```
IPtables -D INPUT -j DROP
```
Cài đặt IPtables trên Centos 7 để mở port VPS

Để mở cổng trong IPtables, bạn chèn chuỗi ACCEPT PORT vào cấu trúc câu lệnh mở port xxx:
```
# IPtables -A INPUT -p tcp -m tcp --dport xxx -j ACCEPT
```
Với A (viết tắt của Append) là chèn vào chuỗi INPUT, tức chèn ở vị trí cuối.
```
# IPtables -I INPUT -p tcp -m tcp --dport xxx -j ACCEPT
```
Với I (viết tắt của Insert) là chèn vào chuỗi INPUT, tức chèn ở dòng được chỉ định rulenum.

Đồng thời, bạn chèn quy tắc vào đầu để tránh xung đột với quy tắc gốc.

Mở port SSH

Khi thực hiện mở port SSH để truy cập VPS sẽ cho phép kết nối SSH ở mọi thiết bị tại bất kỳ vị trí nào và không phân biệt người dùng.

Cú pháp câu lệnh:
```
# IPtables -I INPUT -p tcp -m tcp --dport 22 -j ACCEPT

ACCEPT

tcp  -- anywhere
anywhere

cp dpt:ssh 
```
Nếu bạn đổi cổng khác thì IPtables hiển thị giá trị cổng tương ứng. 

Trong trường hợp, bạn chỉ cho kết nối VPS thông qua SSH từ một IP xác định thì câu lệnh lúc này là: 
```
# IPtables -I INPUT -p tcp -s xxx.xxx.xxx.xxx -m tcp --dport 22 -j ACCEPT
```
Với xxx.xxx.xxx.xxx là địa chỉ của IP cho phép kết nối.

Như vậy, IPtables sẽ thêm quy tắc:
```
ACCEPT  tcp  -- xxx.xxx.xxx.xxx    anywhere         tcp dpt:ssh
```
Mở port Web Server
Khi bạn muốn cho các truy cập vào máy chủ web thông qua cổng mặc định là 80 và 443 thì câu lệnh có dạng:
```
# IPtables -I INPUT -p tcp -m tcp --dport 80 -j ACCEPT

# IPtables -I INPUT -p tcp -m tcp --dport 443 -j ACCEPT
```
Lúc đó, IPtables sẽ hiển thị theo mặc định tương ứng với cổng là HTTP và HTTPS:
```
ACCEPT tcp -- anywhere       anywhere    tcp dpt:http

ACCEPT tcp -- anywhere      anywhere     tcp dpt:https
```

Mở port Mail
- Khi bạn muốn cho phép user sử dụng máy chủ SMTP thông qua cổng mặc định 25 và 465 thì câu lệnh sẽ là:
```
# IPtables -I INPUT -p tcp -m tcp --dport 25 -j ACCEPT

# IPtables -I INPUT -p tcp -m tcp --dport 465 -j ACCEPT
```
Lúc này IPtables cũng hiển thị tương ứng SMTP và URD mặc định là
```
ACCEPT   tcp  -- anywhere      anywhere           tcp dpt:smtp

ACCEPT   tcp  -- anywhere      anywhere           tcp dpt:urd
```
- Tương tự như trên, nếu muốn mở cổng POP3 có giá trị mặc định là 110 và 995 để cho phép user có thể đọc mail trên máy chủ thì câu lệnh như sau:
```
# IPtables -A INPUT -p tcp -m tcp --dport 110 -j ACCEPT

# IPtables -A INPUT -p tcp -m tcp --dport 995 -j ACCEPT
```
Và IPtables hiển thị POP3 và POP3S tương ứng là:
```
ACCEPT tcp  --  anywhere         anywhere        tcp dpt:pop3

ACCEPT tcp  --  anywhere         anywhere        tcp dpt:pop3s
```
- Đối với giao thức IMAP mail protocol có cổng là 143 và 993 thì câu lệnh như sau:
```
# IPtables -A INPUT -p tcp -m tcp --dport 143 -j ACCEPT

# IPtables -A INPUT -p tcp -m tcp --dport 993 -j ACCEPT
```
Lúc này, IPtables hiển thị IMAP và IMAPS mặc định sẽ là:
```
ACCEPT tcp  --  anywhere         anywhere        tcp dpt:imap

ACCEPT tcp  --  anywhere         anywhere        tcp dpt:imaps
```

Chặn truy cập của một địa chỉ IP 
Câu lệnh có dạng:
```
# IPtables -A INPUT -s IP_ADDRESS -j DROP
```
Nếu muốn chặn 1 địa chỉ IP cụ thể truy cập vào 1 port xác định thì câu lệnh sẽ là: 
```
#IPtables -A INPUT -p tcp -s IP_ADDRESS –dport PORT -j DROP
```
Nếu muốn kiểm tra lại tất cả các rule sau khi thiết lập, bạn sử dụng một trong 2 câu lệnh sau:
```
# service IPtables status
```
Hay:
```
# IPtables -L –n
```
Trong đó:

Tham số -n: là địa chỉ IP. Ví dụ, khi muốn chặn kết nối từ 1 IP xác định, lúc này IPtables hiển thị là xxx.xxx.xxx.xxx với tham số -n

Sau đó, bạn lưu lại tất cả các thiết lập. Câu lệnh là: 
```
# IPtables-save | sudo tee /etc/sysconfig/IPtables
```
Hay có thể sử dụng lệnh sau:
```
# service IPtables save
```
IPtables: Saving firewall rules to /etc/sysconfig/IPtables:[ OK ]
