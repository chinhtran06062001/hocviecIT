# Các câu lệnh Exim cơ bản

1. Liệt kê danh sách tất cả các email có trong queue (thời gian xếp hàng, kích thước, id thư, người gửi, người nhận)

```
exim -bp
```

2. Xem tin nhắn chưa được gửi trong hàng đợi

```
exim -bpu
```

3. Đếm Số lượng các mail đang trong queue

```
exim -bpc
```

4. Tóm tắt các thông báo trong hàng đợi (số lượng, khối lượng, cũ nhất, mới nhất, miền và tổng số)

```
exim -bp | exiqsumm
```

5. Kiểm tra hành động hiện thời của exim

```
exiwhat
```

6. Chạy một giao dịch SMTP giả dòng lệnh, như thể nó đến từ địa chỉ IP đã cho. Điều này sẽ hiển thị kiểm tra, ACL và bộ lọc của Exim khi chúng được áp dụng. Tin nhắn sẽ KHÔNG thực sự được chuyển đi.
```
exim -bh 192.168.11.22
```
6. Xem thông tin tổng quát về các email trong queue
```
exim -bP 
or
exim -bp | exiqsumm
```
8. Đếm Số lượng các mail đang ở Tình trạng Frozen (bị nhận dạng là spam)
```
exim -bpr | grep frozen | wc -l
```
9. Xóa tất cả các mail đang ở tình trạng frozen
```
exiqgrep -z -i | xargs exim -Mrm
```
10. Xóa tất cả các mail đã nằm trong queue vượt trên 1 khoảng thời gian được định
```
exiqgrep -o <thời gian> -i | xargs exim -Mrm
```
trong đó <thời gian> là số giây tối đa mà các email đã chờ trong queue, nếu email nào đã chờ quá <thời gian> sẽ bị xóa đi.

Ví dụ lệnh SSH sau đây sẽ xóa tất cả email đã chờ quá 1 ngày:
```
exiqgrep -o 86400 -i | xargs exim -Mrm
```
11. Xóa tất cả email được gửi đi từ 1 domain hay 1 account nào đó
```
exiqgrep -f <người gửi> -i | xargs exim -Mrm
```
trong đó <người gửi> là 1 chuỗi (string) sẽ được so sánh với thông tin về người gửi ($header_from) trong header của email, nếu phù hợp sẽ bị xóa đi. Ví dụ lệnh SSH sau sẽ xóa đi tất cả email đang chờ trong queue để gửi đi của account sales@abc.com
```
exiqgrep -f sales@abc.com -i | xargs exim -Mrm
```
12. Xóa tất cả email gửi đến 1 domain hay 1 account nào đó
```
exiqgrep -r <người nhận> -i | xargs exim -Mrm
```
trong đó <người nhận> là 1 chuỗi (string) sẽ được so sánh với thông tin về người nhận( $header_to) trong header của email, nếu phù hợp sẽ bị xóa đi. Ví dụ lệnh SSH sau sẽ xóa đi tất cả email đang chờ được gửi từ các email có chữ “info”
```
exiqgrep -f info -i | xargs exim -Mrm
```
Xóa toàn bộ mail queue:
```
find /var/spool/exim/input -type f -exec rm -rf {} \;
```

# Tìm kiếm hàng đợi với exiqgrep

Exim bao gồm một tiện ích khá hay để chuyển qua hàng đợi, được gọi là exiqgrep. Nếu bạn không sử dụng cái này và nếu bạn không quen thuộc với các loại cờ khác nhau mà nó sử dụng, có thể bạn đang làm mọi thứ một cách khó khăn, chẳng hạn như đưa `exim -bp` vào awk, grep, cut hoặc` wc – l`. Đừng làm cho cuộc sống khó khăn hơn hiện tại.

Đầu tiên, các cờ khác nhau kiểm soát những thông điệp nào được khớp. Chúng có thể được kết hợp để đưa ra một tìm kiếm rất cụ thể.

1. Sử dụng -f để tìm kiếm thư từ một người gửi cụ thể trong hàng đợi:
```
exiqgrep -f [luser]@domain
```
2. Sử dụng -r để tìm kiếm hàng đợi thư cho một người nhận / miền cụ thể:
```
exiqgrep -r [luser]@domain
```
3. Sử dụng -o để in các tin nhắn cũ hơn số giây đã chỉ định. Ví dụ: các tin nhắn cũ hơn 1 ngày:
```
exiqgrep -o 86400 [...]
```
4. Sử dụng -y để in các tin nhắn nhỏ hơn số giây được chỉ định. Ví dụ: tin nhắn cách đây chưa đầy một giờ:
```
exiqgrep -y 3600 [...]
```
5. Sử dụng -s để khớp kích thước của một thông báo với regex. Ví dụ: 700-799 byte:
```
exiqgrep -s '^7..
```
Sử dụng -z để chỉ đối sánh với các tin nhắn đã được đóng băng hoặc -x để chỉ đối sánh với các tin nhắn chưa được đóng băng. Ngoài ra còn có một số cờ điều khiển việc hiển thị đầu ra.

6. Sử dụng -i để chỉ in id thư do một trong hai tìm kiếm ở trên:
```
exiqgrep -i [ -r | -f ] ...
```
7. Sử dụng -c để in số lượng thư phù hợp với một trong các tìm kiếm ở trên:
```
exiqgrep -c ...
```
8. Chỉ in id thông báo của toàn bộ hàng đợi:
```
exiqgrep -i
```
# Quản lý hàng đợi

Mã nhị phân exim chính (/ usr / sbin / exim) được sử dụng với các cờ khác nhau để làm cho mọi thứ xảy ra với các thư trong hàng đợi. Hầu hết trong số này yêu cầu một hoặc nhiều ID thông báo được chỉ định trong dòng lệnh, đó là nơi mà `exiqgrep -i` như được mô tả ở trên thực sự hữu ích.

1. Bắt đầu chạy hàng đợi
```
exim -q -v
```
2. Force run queue để gửi các email trong local
```
exim -ql -v
```
3. Xóa tin nhắn khỏi hàng đợi:
```
[email protected]# exim -Mrm <mail-id> [ <mail-id> ... ]
```  
4. Cố định một tin nhắn:
```
[email protected]# exim -Mf <mail-id> [ <mail-id> ... ]
```  
5. Ném một tin nhắn:
```
[email protected]# exim -Mt <mail-id> [ <mail-id> ... ]
```  
6. Gửi một tin nhắn, cho dù nó bị đóng băng hay không, cho dù đã đến thời gian thử lại hay chưa:
```
[email protected]# exim -M <mail-id> [ <mail-id> ... ]
```  
7. Gửi tin nhắn, nhưng chỉ khi đã đến thời gian thử lại:
```
[email protected]# exim -Mc <mail-id> [ <mail-id> ... ]
```  
8. Buộc tin nhắn không thành công và bị trả lại là “bị hủy bởi quản trị viên”:
```
[email protected]# exim -Mg <mail-id> [ <mail-id> ... ]
```  
9. Xóa tất cả các tin nhắn bị đóng băng:
```
[email protected]# exiqgrep -z -i | xargs exim -Mrm
```  
10. Xóa tất cả các tin nhắn cũ hơn năm ngày (86400 * 5 = 432000 giây):
```
[email protected]# exiqgrep -o 432000 -i | xargs exim -Mrm
```  
11. Cố định tất cả thư đã xếp hàng từ một người gửi nhất định:
```
[email protected]# exiqgrep -i -f [email protected] | xargs exim -Mf
```  
12. Xem header của 1 mail nào đó
```
exim -Mvh <id của mail>
```  
13. Xem nội dung của 1 mail nào đó
```
exim -Mvb <id của mail>
```  
14. Xem nhật ký của một mail:
```
[email protected]# exim -Mvl <mail-id>
```  
15. Thêm người nhận vào tin nhắn:
```
[email protected]# exim -Mar <mail-id> <address> [ <address> ... ]
```  
16. Chỉnh sửa người gửi tin nhắn:
```
[email protected]# exim -Mes <mail-id> <address>
```
