# Cài đặt CSF Firewall trên CentOS 7

Bước 1: Dừng và vô hiệu hóa tường lửa.

```
systemctl disable firewalld 
systemctl stop firewalld
```

![image](https://user-images.githubusercontent.com/97047640/177726119-57168479-d0fc-4463-9276-68a6636709bd.png)


Bước 2: Cài đặt iptables.

`yum -y install iptables-services`

![image](https://user-images.githubusercontent.com/97047640/177726324-b1d71926-4fcb-4e0e-8733-b080b6dbccc2.png)

**Tạo tập tin cần thiết bởi iptables.**

```
touch /etc/sysconfig/iptables 
touch /etc/sysconfig/iptables6
```

![image](https://user-images.githubusercontent.com/97047640/177726392-48370a8c-b0eb-4a68-85e2-89d303bf4419.png)

Khởi động iptables.

```
systemctl start iptables 
systemctl start ip6tables
```

Kích hoạt iptables mỗi khi khởi động lại VPS/Server.

```
systemctl enable iptables 
systemctl enable ip6tables
```

![image](https://user-images.githubusercontent.com/97047640/177726629-3ef08721-2131-4e8b-a892-c8c7e21cbb78.png)

Bước 3: Cài đặt các thư viện cần thiết.

Tiếp theo các bạn tiến hành cài đặt các thư viện cần thiết cho việc hoạt động của CSF

`yum -y install wget perl unzip net-tools perl-libwww-perl perl-LWP-Protocol-https perl-GDGraph`

![image](https://user-images.githubusercontent.com/97047640/177726839-c9728093-dd90-452c-8364-19d81b169734.png)


Bước 4:  cài đặt CSF.

Sau khi đã cài đặt đầy đủ các thư viện chúng ta tiến hành cài đặt CSF.

```
cd /opt
wget https://download.configserver.com/csf.tgz 
tar -xzf csf.tgz 
cd csf 
sh install.sh
```

![image](https://user-images.githubusercontent.com/97047640/177727071-840dbb1c-54ab-42cd-9acb-94df675de20e.png)

Loại bỏ các tập tin cài đặt.

```
cd /
rm -rf /opt/csf /opt/csf.tgz
```
![image](https://user-images.githubusercontent.com/97047640/177727257-4a45ca8a-54fd-409f-98b5-6be930fa6b03.png)

Bây giờ chúng ta sẽ kiểm tra xem CSF có thực sự hoạt động trên máy chủ không.
```
cd /usr/local/csf/bin/
perl csftest.pl
```

![image](https://user-images.githubusercontent.com/97047640/177727449-863cb47a-8d12-42b7-9159-cf9ef47f0ff9.png)

CSF sẽ hoạt động mà không gặp sự cố nào trên máy chủ của bạn.

```
Testing ip_tables/iptable_filter...OK
Testing ipt_LOG...OK
Testing ipt_multiport/xt_multiport...OK
Testing ipt_REJECT...OK
Testing ipt_state/xt_state...OK
Testing ipt_limit/xt_limit...OK
Testing ipt_recent...OK
Testing xt_connlimit...OK
Testing ipt_owner/xt_owner...OK
Testing iptable_nat/ipt_REDIRECT...OK
Testing iptable_nat/ipt_DNAT...OK

RESULT: csf should function on this server
```

Bước 5: Cấu hình CSF

Cấu hình CSF bằng cách chỉnh sửa file /etc/csf/csf.confcsf.conf.

`nano /etc/csf/csf.conf`


Các bạn sẽ cần sửa một số thông số dưới đây

```
TESTING = "0"
RESTRICT_SYSLOG = "3"
```


```
systemctl enable csf
systemctl enable lfd
systemctl start csf
```

Để kiểm tra xem csf đã hoạt động hay chưa các bạn có thể sử dụng lệnh dưới đây

`systemctl status csf`

![image](https://user-images.githubusercontent.com/97047640/177727689-f0b39ed1-d2dc-4972-a2c5-093a24bcc788.png)


Bước 6: Mở Port SMTP
Theo mặc định CSF sẽ không mở TCP_OUT với port 465, điều này có thể sẽ khiến bạn gặp lỗi khi sử dụng SMTP mail. Để mở port 465 các bạn mở file /etc/csf/csf.conf và tìm dòng sau

`TCP_OUT = "20,21,22,25,53,80,110,113,443,587,993,995"`

Sửa lại thành

`TCP_OUT = "20,21,22,25,53,80,110,113,443,587,465,993,995"`

Tiến hành khởi động lại CSF

```
csf -x
csf -e
```
