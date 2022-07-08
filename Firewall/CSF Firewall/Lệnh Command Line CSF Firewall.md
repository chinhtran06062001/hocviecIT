1. Khởi động “csf” và “lfd” nếu chưa khởi động
```
# csf -e
# csf --enable
```

2. Tắt “csf” và “lfd”
```
# csf -x
# csf --disable
```
3. Khởi động lại các rule tường lửa
```
# csf -r
# csf --restart
```
4. Khởi động rule tường lửa
```
# csf -s
# csf --start
```
5. Xoá toàn bộ rule tường lửa
```
# csf -f
# csf --stop
```
6. Liệt kê cấu hình rule IPv4 Iptables
```
# csf -l
# csf --status
```
7. Liệt kê cấu hình rule IPv6 Iptables
```
# csf -l6
# csf --status6
```
8. Cho phép (allow) 1 IP và thêm IP đó vào file /etc/csf/csf.allow
```
# csf -a ip [comment]
# csf --add ip [comment]
```
Ví dụ :
```
# csf -d 192.168.1.110 DDOS IP
Adding 192.168.1.110 to csf.deny and iptables DROP...
```

9. Gỡ bỏ IP khỏi danh sách cho phép, bỏ IP đó khỏi file /etc/csf/csf.allow
```
# csf -ar ip
# csf --addrm ip
```

10. Chặn (deny) 1 IP và thêm IP đó vào file /etc/csf/csf.deny
```
# csf -d ip [comment]
# csf --deny ip [comment]
```

Ví dụ :
```
# csf -d 192.168.1.110 DDOS IP
Adding 192.168.1.110 to csf.deny and iptables DROP...
```

11. Chặn 1 IP vĩnh viễn không bị xoá khỏi danh sách IP trong /etc/csf/csf.deny
– Số lượng IP chặn cũng như số lượng IP entry có thể chứa trong file /etc/csf/csf.deny được quy định bởi cấu hình giá trị “DENY_IP_LIMIT” trong /etc/csf/csf.conf. Nên khi số lượng IP bị deny đạt ngưỡng này thì CSF sẽ tuần tự xoá các IP cũ nhất khỏi danh sách IP bị chặn để thêm 1 IP mới vào danh sách chặn.
– Trong trường hợp đó ta muốn 1 IP đã thêm vào danh sách chặn sẽ không bị CSF gỡ bỏ để phục vụ nhu cầu lấy khoảng trống cho IP mới bị chặn, thì ta sẽ thêm dòng comment “do not delete” khi gõ lệnh chặn IP.
```
# csf -d ip do not delete
# csf --deny ip do not delete
```

12. Gỡ bỏ IP khỏi danh sách bị chặn, bỏ IP đó khỏi file /etc/csf/csf.deny
```
# csf -dr ip
# csf --denyrm ip
```

13. Xoá toàn bộ các IP bị chặn cũng như là xoá bộ IP thông tin trong file /etc/csf/csf.deny
```
# csf -df
# csf --denyf
```

14. Tìm thông tin về IP trong danh sách rule tường lửa chặn
– Áp dụng cho cả việc tìm kiếm trong các rule IPv4 và IPv6, giúp xác định IP cần kiểm tra có bị chặn tạm thời, chặn vĩnh viễn hay đang được cho phép như thế nào.
```
# csf -g ip
```
Ví dụ :
```
# csf -g 192.168.1.100
```
```
Chain            num   pkts bytes target     prot opt in     out     source               destination         
DENYIN           2        0     0 DROP       all  --  !lo    *       192.168.1.100        0.0.0.0/0           

ip6tables:
Chain            num   pkts bytes target     prot opt in     out     source               destination         
No matches found for 192.168.1.100 in ip6tables

Temporary Blocks: IP:192.168.1.100 Port: Dir:in TTL:3600 (Manually added: 192.168.1.100 (-/-/-))
```

15. Thêm IP vào danh sách IP tạm thời được cho phép
```
# csf -ta ip ttl [-p port] [-d direction] [comment]
# csf --tempallow ip ttl [-p port] [-d direction] [comment]
```

Ví dụ :
```
# csf -ta 192.168.1.100

ACCEPT  all opt -- in !lo out *  192.168.1.100  -> 0.0.0.0/0
ACCEPT  all opt -- in * out !lo  0.0.0.0/0  -> 192.168.1.100
csf: 192.168.1.100 allowed on port * for 3600 seconds in and outbound
```

16. Thêm IP vào danh sách IP tạm thời bị chặn
```
# csf -td ip ttl [-p port] [-d direction] [comment]
# csf --tempdeny ip ttl [-p port] [-d direction] [comment]
```

Ví dụ :
```
# csf -td 192.168.1.100
```
```
DROP  all opt -- in !lo out *  192.168.1.100  -> 0.0.0.0/0
csf: 192.168.1.100 blocked on port * for 3600 seconds inbound
```

17. Liệt kê các IP đang nằm trong danh sách IP tạm thời bị chặn hoặc tạm thời cho phép
```
# csf -t 
# csf --temp
```

Ví dụ :
```
# csf -t
A/D   IP address                               Port   Dir   Time To Live     Comment
DENY  192.168.1.100                              *    in    59m 48s          Manually added: 192.168.1.100 (-/-/-)
ALLOW 192.168.1.110                              *    inout 59m 56s          Manually added: 192.168.1.110 (-/-/-)
```

18. Gỡ bỏ IP khỏi danh sách IP tạm thời bị chặn hoặc tạm thời cho phép
```
# csf -tr ip
# csf -temprm ip
```

19. Xoá toàn bộ danh sách IP đang nằm trong danh sách tạm thời
```
# csf -tf
# csf --tempf
```

Một số lệnh CSF khác

20. Xem phiên bản CSF hiện tại trên hệ thống
```
# csf -v
# csf --version
```

21. Kiểm tra phiên bản cập nhật, nhưng không tiến hành cập nhật
```
# csf -c
# csf --check
```

22. Danh sách các options hỗ trợ
```
# csf -h
# csf --help
 ```
