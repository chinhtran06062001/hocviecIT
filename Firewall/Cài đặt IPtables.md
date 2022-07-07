# IPtables là gì?

IPtables là ứng dụng tường lửa miễn phí trong Linux, cho phép thiết lập các quy tắc riêng để kiểm soát truy cập, tăng tính bảo mật. Khi sử dụng máy chủ, tường lửa là một trong những công cụ quan trọng giúp bạn ngăn chặn các truy cập không hợp lệ. Đối với các bản phân phối Linux như Ubuntu, Fedora, CentOS… bạn có thể tìm thấy công cụ tường lửa tích hợp sẵn IPtables.

IPtables là một ứng dụng tường lửa có sẵn trên Linux, IPtables Linux firewall cho phép người dùng thiết lập các quyền truy cập để kiểm soát lưu lượng một cách chọn lọc trên máy chủ.

![image](https://user-images.githubusercontent.com/62273292/167060805-5383f22f-6d35-4944-a83a-bcadb7caec01.png)

## Các bảng trong IPtables là gì?

Table được IPtables sử dụng để định nghĩa các rules(quy tắc) dành cho các gói tin. Trong đó, có các Table sau. 

**Filter Table**

Là một trong những tables được IPtables sử dụng nhiều nhất, Filter Table sẽ quyết định việc một gói tin có được đi đến đích dự kiến hay từ chối yêu cầu của gói tin.

**NAT Table**

Để dùng các rules về NAT(Network Address Translation), NAT Table sẽ có trách nhiệm chỉnh sửa source(IP nguồn) hoặc destination(IP đích) của gói tin khi thực hiện cơ chế NAT.

**Mangle Table**

Cho phép chỉnh sửa header của gói tin, giá trị của các trường TTL, MTU, Type of Service.

**Raw Table**

IPtables là một stateful firewall với các gói tin được kiểm tra liên quan đến trạng thái(state). Ví dụ gói có thể là một phần của một kết nối mới hoặc là một phần của kết nối hiện có. Raw Table sẽ giúp bạn làm việc với các gói tin trước khi kernel bắt đầu kiểm tra trạng thái và có thể loại một số gói khỏi việc tracking vì vấn đề hiệu năng của hệ thống.

**Security Table**

Một vài kernel có thể hỗ trợ thêm Security Table, được dùng bởi SELinux để thiết lập các chính sách bảo mật.

### Chains
Chains được tạo ra với một số lượng nhất định ứng với mỗi Table, giúp lọc gói tin tại các điểm khác nhau.

**Chain PREROUTING** tồn tại trong Nat Table, Mangle Table và Raw Table, các rules trong chain sẽ được thực thi ngay khi gói tin vào đến giao diện mạng (Network Interface).

**Chain INPUT** chỉ có ở Mangle Table và Nat Table với các rules được thực thi ngay trước khi gói tin gặp tiến trình.

**Chain OUTPUT** tồn tại ở Raw Table, Mangle Table và Filter Table, có các rules được thực thi sau khi gói tin được tiến trình tạo ra.

**Chain FORWARD** tồn tại ở Manle Table và Filter Table, có các rules được thực thi cho các gói tin được định tuyến qua host hiện tại.

**Chain POSTROUTING** chỉ tồn tại ở Manle Table và Nat Table với các rules được thực thi khi gói tin rời giao diện mạng.


### Target

Target có thể được hiểu là hành động dành cho các gói tin khi gói tin thỏa mãn các rules đặt ra.

- ACCEPT: chấp nhận và cho phép gói tin đi vào hệ thống.

- DROP: loại gói tin, không có gói tin trả lời.

- REJECT: loại gói tin những có trả lời table gói tin khác. Ví dụ: trả lời table 1 gói tin “connection reset” đối với gói TCP hoặc “destination host unreachable” đối với gói UDP và ICMP.

- LOG: chấp nhận gói tin nhưng có ghi lại log.

- Gói tin sẽ được đi qua tất cả các rules đặt ra mà không dừng lại ở bất kì rule nào đúng. Trường hợp gói tin không khớp với rules nào mặc định sẽ được chấp nhận

## Cấu hình IPtables cơ bản là gì?

Một target (mục tiêu) sẽ được đưa ra khi có một gói tin được xác định. Target có thể là một chuỗi khác để khớp với một trong các giá trị sau:

**ACCEPT**: gói tin được phép đi qua.
**DROP:** gói tin không được phép đi qua.
**RETURN:** bỏ qua chuỗi hiện tại và quay trở lại quy tắc tiếp theo từ chuỗi mà nó được gọi.




1. Cài đặt Iptables

CentOS 7 sử dụng FirewallD làm tường lửa mặc định thay vì Iptables. Nếu bạn muốn sử dụng Iptables thực hiện tắt service firewall:

```
sudo systemctl stop firewalld        
sudo systemctl disable firewalld     | Không cho phép firewalld tự bật khi reboot server.
sudo systemctl mask --now firewalld  | Đảm bảo không cho các dịch vụ khác start firewalld.
sudo yum install iptables-services   | Cài đặt packages iptables-services từ CentOS repositories.
sudo systemctl start iptables        | Khởi động dịch vụ iptables.
sudo systemctl enable iptables       | Bật tự động iptables khi boot server, để đảm bảo server luôn luôn có sự bảo vệ từ iptables.
sudo systemctl status iptables       | Kiểm tra trạng thái iptables đảm bảo nó đang hoạt động.
```

![image](https://user-images.githubusercontent.com/97047640/177748508-d3dc0b49-f9dd-4761-98a1-b4b66f7c0e5e.png)

– Kiểm tra Iptables đã được cài đặt trong hệ thống:
Trên CentOS:

```
# rpm -q iptables
iptables-1.4.7-16.el6.x86_64
# iptables --version
iptables v1.4.7
```

![image](https://user-images.githubusercontent.com/97047640/177748590-6125be2b-1bb5-4ff7-a9b9-320e0acdfaa1.png)

Sử dụng lệnh sau để hiển thị các rule đang có:

```
sudo iptables -nvL
```

![image](https://user-images.githubusercontent.com/97047640/177748848-a6dc1fd9-8dfa-47c2-bb66-354a402f7c9f.png)

2. Các nguyên tắc áp dụng trong Iptables

Để bắt đầu, bạn cần xác định các services muốn đóng/mở và các port tương ứng.

Ví dụ, với một website và mail server thông thường

Để truy cập VPS bằng SSH, bạn cần mở port SSH – 22.

Để truy cập website, bạn cần mở port HTTP – 80 và HTTPS – 443.

Để gửi mail, bạn sẽ cần mở port SMTP – 22 và SMTPS – 465/587

Để người dùng nhận được email, bạn cần mở port POP3 – 110, POP3s – 995, IMAP – 143 và IMAPs – 993

Sau khi đã xác định được các port cần mở, bạn cần thiết lập các quy tắc tường lửa tương ứng để cho phép.

Bạn có thể xóa toàn bộ các quy tắc firewall mặc định để bắt đầu từ đầu: # iptables -F

Mình sẽ hướng dẫn các bạn xem và hiểu các quy tắc của iptables. Liệt kê các quy tắc hiện tại:

`# iptables -L`


Chain INPUT (policy ACCEPT)

target     prot opt source               destination

ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED

ACCEPT     icmp --  anywhere             anywhere

ACCEPT     all  --  anywhere             anywhere

ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh

REJECT     all  --  anywhere             anywhere            reject-with icmp-host-prohibited

ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:http

ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:https

ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:smtp

ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:urd

ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:pop3

ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:pop3s

ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:imap

ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:imaps

Chain FORWARD (policy ACCEPT)

target     prot opt source               destination

REJECT     all  --  anywhere             anywhere            reject-with icmp-host-prohibited

Chain OUTPUT (policy ACCEPT)

target     prot opt source               destination

![image](https://user-images.githubusercontent.com/97047640/177750021-e2a85fee-e374-4986-a43d-fa1235f10c8c.png)


### Cột 1: TARGET hành động sẽ được áp dụng cho mỗi quy tắc

**Accept:** gói dữ liệu được chuyển tiếp để xử lý tại ứng dụng cuối hoặc hệ điều hành

![image](https://user-images.githubusercontent.com/97047640/177750549-9cb1567a-4a7c-4f57-91c2-4d2867da5e84.png)

**Drop:** gói dữ liệu bị chặn, loại bỏ

![image](https://user-images.githubusercontent.com/97047640/177750633-0a8c9961-3cdd-47a6-87a0-d1501de5170e.png)

**Reject:** gói dữ liệu bị chặn, loại bỏ đồng thời gửi một thông báo lỗi tới người gửi

![image](https://user-images.githubusercontent.com/97047640/177750683-e02b461c-2647-468c-81d7-8a98165c6c6b.png)

#### Cột 2: PROT (protocol – giao thức) quy định các giao thức sẽ được áp dụng để thực thi quy tắc, bao gồm all, TCP hay UDP. Các ứng dụng SSH, FTP, sFTP… đều sử dụng giao thức TCP.

### Cột 4, 5: SOURCE và DESTINATION địa chỉ của lượt truy cập được phép áp dụng quy tắc.

3. Cách sử dụng Iptables để mở port VPS

thiết lập một rule đơn giản vào IPtables bằng command:

`iptables -A INPUT -i lo -j ACCEPT`

Với ý nghĩa :

-A INPUT: khai báo kiểu kết nối sẽ được áp dụng (-A nghĩa là Append).

-i lo: Khai báo thiết bị mạng được áp dụng (-i < interface-name > nghĩa là Interface).

-j ACCEPT: khai báo hành động sẽ được áp dụng cho quy tắc này (-j < target > nghĩa là Jump).

Hoặc ta cùng xem một ví dụ sau :

`iptables -A INPUT -s 0/0 -i ens33 -d 192.168.176.154 -p TCP -j ACCEPT`

![image](https://user-images.githubusercontent.com/97047640/177750189-8e3d93a2-5cec-4b72-8bc8-07a2dbad5f3a.png)

Với ý nghĩa : IPtables được cấu hình cho phép “firewall” chấp nhận các gói dữ liệu TCP, đến từ card mạng eth0, có bất kỳ địa chỉ IP nguồn đi đến địa chỉ 192.168.1.1 – là địa chỉ IP của firewall. 0/0 nghĩa là bất kỳ địa chỉ IP nào.


Để mở port trong Iptables, bạn cần chèn chuỗi ACCEPT PORT. Cấu trúc lệnh để mở port xxx như sau:

`# iptables -A INPUT -p tcp -m tcp --dport xxx -j ACCEPT`

A tức Append – chèn vào chuỗi INPUT (chèn xuống cuối)

hoặc

`# iptables -I INPUT [rulenum] -p tcp -m tcp --dport xxx -j ACCEPT`

I tức Insert- chèn vào chuỗi INPUT (chèn vào dòng chỉ định rulenum)

Để tránh xung đột với rule gốc, các bạn nên chèn rule vào đầu, sử dụng -I

3.1. Mở port SSH

Để truy cập VPS qua SSH, bạn cần mở port SSH 22. Bạn có thể cho phép kết nối SSH ở bất cứ thiết bị nào, bởi bất cứ ai và bất cứ dâu.

# iptables -I INPUT -p tcp -m tcp --dport 22 -j ACCEPT

Mặc định sẽ hiển thị ssh cho cổng 22, nếu bạn đổi ssh thành cổng khác thì iptables sẽ hiển thị số cổng

ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh

Bạn có thể chỉ cho phép kết nối VPS qua SSH duy nhất từ 1 địa chỉ IP nhất định (xác định dễ dàng bằng cách truy cập các website check ip hoặc lệnh # w)

# iptables -I INPUT -p tcp -s xxx.xxx.xxx.xxx -m tcp --dport 22 -j ACCEPT

Khi đó, trong iptables sẽ thêm rule

ACCEPT     tcp  --  xxx.xxx.xxx.xxx       anywhere            tcp dpt:ssh

3.2. Mở port Web Server

Để cho phép truy cập vào webserver qua port mặc định 80 và 443:

```
# iptables -I INPUT -p tcp -m tcp --dport 80 -j ACCEPT
# iptables -I INPUT -p tcp -m tcp --dport 443 -j ACCEPT
```

Mặc định Iptables sẽ hiển thị HTTP và HTTPS

```
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:http
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:https
```

3.3. Mở port Mail

– Để cho phép user sử dụng SMTP servers qua port mặc định 25 và 465:

```
# iptables -I INPUT -p tcp -m tcp --dport 25 -j ACCEPT
# iptables -I INPUT -p tcp -m tcp --dport 465 -j ACCEPT
```

Mặc định Iptables sẽ hiển thị SMTP và URD

```
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:smtp
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:urd
```

– Để user đọc email trên server, bạn cần mở port POP3 (port mặc định 110 và 995)

```
# iptables -A INPUT -p tcp -m tcp --dport 110 -j ACCEPT
# iptables -A INPUT -p tcp -m tcp --dport 995 -j ACCEPT
```

Mặc định Iptables sẽ hiển thị POP3 và POP3S

```
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:pop3
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:pop3s
```

Bên cạnh đó, bạn cũng cần cho phép giao thức IMAP mail protocol (port mặc định 143 và 993)

```
# iptables -A INPUT -p tcp -m tcp --dport 143 -j ACCEPT
# iptables -A INPUT -p tcp -m tcp --dport 993 -j ACCEPT
```

Mặc định Iptables sẽ hiển thị IMAP và IMAPS

```
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:imap
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:imaps
```

3.4. Chặn 1 IP truy cập

`# iptables -A INPUT -s IP_ADDRESS -j DROP`

– Chặn 1 IP truy cập 1 port cụ thể:

`#iptables -A INPUT -p tcp -s IP_ADDRESS –dport PORT -j DROP`

Sau khi đã thiết lập đầy đủ, bao gồm mở các port cần thiết hay hạn chế các kết nối, bạn cần block toàn bộ các kết nối còn lại và cho phép toàn bộ các kết nối ra ngoài từ VPS

```
# iptables -P OUTPUT ACCEPT
# iptables -P INPUT DROP
```

Sau khi đã thiết lập xong, bạn có thể kiểm tra lại các quy tắc

`# service iptables status`

Hoặc

`# iptables -L –n`

-n nghĩa là chúng ta chỉ quan tâm mỗi địa chỉ IP . Ví dụ, nếu chặn kết nối từ hocvps.com thì iptables sẽ hiển thị là xxx.xxx.xxx.xxx với tham số -n
Cuối cùng, bạn cần lưu lại các thiết lập tường lửa Iptables nếu không các thiết lập sẽ mất khi bạn reboot hệ thống. Tại CentOS, cấu hình được lưu tại /etc/sysconfig/iptables.

`# iptables-save | sudo tee /etc/sysconfig/iptables`

Hoặc

`# service iptables save`

iptables: Saving firewall rules to /etc/sysconfig/iptables:[ OK ]



# Danh sách các lệnh iptables chính quản lý firewall iptables trên Linux

1. Quản lý ‘chain’

– Khởi tạo 1 chain mới.

`# iptables -N new_chain`

– Chỉnh sửa 1 chain, đổi tên chain.

`# iptables -E new_chain old_chain`
 
– Xoá 1 chain.

`# iptables -X old_chain`

**Thêm, sữa và xóa chain**

![image](https://user-images.githubusercontent.com/97047640/177751390-9ba2c60b-43e3-4143-8f0f-b903987cdaab.png)
 
– Chuyển hướng packet đến 1 chain được khởi tạo. Ví dụ dưới.

`# iptables -A INPUT -p icmp -j new_chain`


2. Liệt kê rule iptables

– Liệt kê toàn bộ rules trong các chain, mặc định là table ‘filter‘.

`# iptables -L`
 
– Liệt kê, kèm theo thông tin bộ đếm packet.

`# iptables -L -v`
 
![image](https://user-images.githubusercontent.com/97047640/177751780-2745aa8c-eb3b-483b-bb3d-08daac0bf8c9.png)

– Liệt kê thông tin rules-chain trong table cụ thể như NAT.

`# iptables -L -t nat`

![image](https://user-images.githubusercontent.com/97047640/177751895-5721e2ce-fb6c-492d-837f-778cfd42ec51.png)

– Liệt kê các rules với số thứ tự từng dòng rule của từng CHAIN. Mặc định vẫn là table ‘filter‘, nếu không chỉ định rõ table.

`# iptables -L -n --line-numbers`
 
![image](https://user-images.githubusercontent.com/97047640/177751990-17a4aa4a-5587-4582-988e-b08c45139339.png)
 
– Liệt kê các rule cụ thể của chain cụ thể như INPUT với số dòng thứ tự.

`# iptables -L INPUT -n --line-numbers`

![image](https://user-images.githubusercontent.com/97047640/177752076-6732a9c4-4f81-4698-8dde-1819e3801a6f.png)

3. Quản lý rule trong chain

– Mở rộng thêm 1 rule vào cuối danh sách rule của chain được chỉ định.

`# iptables -A chain`
 
– Thêm một 1 rule vào đầu danh sách các rule của chain được chỉ định.

`# iptables -I chain [rulenum]`
 
– Thay thế thông tin rule trong 1 chain được chỉ định với tham số cụ thể về dòng thứ tự rule cần thay thế.

`# iptables -R chain rulenum`
 
– Xoá bỏ 1 rule cụ thể của 1 chain được chỉ định, bạn nên nhớ chỉ định rõ số thứ tự dòng rule mà bạn muốn xoá nhé. Không thôi mặc định xoá rule số thứ tự 1 đấy.

`# iptables -D chain rulenum`

`# iptables -D chain`

Xóa hết các ruler trong chain và toàn bộ chain 

`iptables -F`

4. Thay đổi cấu hình rule mặc định cuối cùng

– Thay đổi policy rule mặc định cuối cùng của 1 chain khi 1 packet không lọc được bởi bất kì rule nào đang tồn tại hoặc không tồn tại.

`# iptables -P chain target`
 
– Thay đổi các policy rule cuối cùng mặc định của 3 chain INPUT, OUTPUT, FORWARD thành DROP.

```
# iptables -P INPUT DROP
# iptables -P OUTPUT DROP
# iptables -P FORWARD DROP
```
