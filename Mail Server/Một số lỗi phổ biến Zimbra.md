**Zimbra_01 ) mta stopped + postfix is not running**

Khắc phục :
```
#service postfix stop
#chkconfig postfix off
#su – zimbra
$zmcontrol restart
```
**Zimbra_02 ) Ldap failed khi setup Zimbra**

Khắc phục :
```
#vi /etc/sudoers
```
Tìm đến dòng Defaults requiretty và thêm # đằng trước

#Defaults requiretty

**Zimbra_03 ) Starting zmconfigd…/opt/zimbra/bin/zmconfigdctl: line 94: 17418 Killed**

Khắc phục :
```
#su root
#vi /etc/hosts
```
Thêm # như dòng sau :
```
##::1 localhost localhost.localdomain localhost6 localhost6.localdomain6
#su zimbra
#zmcontrol restart
```
**Zimbra_04 ) stat stoped**

Khắc phục :
```
#vi /etc/hosts
```
Kiểm tra trong host đã đủ dòng sau chưa :
```
127.0.0.1 localhost

192.168.1.1 mail.vnitnews.com mail
```
**Zimbra_05 ) mysql , zmconfigd is not running**

Khắc phục :
```
#zmcontrol stop
#rm -rf /opt/zimbra/db/data/*
#/opt/zimbra/libexec/zmmyinit
#zmcontrol restart
```
**Zimbra_06 ) dnscache is not running**

Khắc phục : 
```
#su zimbra
#zmdnscachectl stop
zmprov ms zmhostname -zimbraServiceEnabled dnscache
zmprov ms zmhostname -zimbraServiceInstalled dnscache
zmcontrol stop
```
**Zimbra_07 ) Không gửi được mail do IP bị Blacklist (Spam)**

Khắc phục :

>Kiểm tra IP Mail đang bị Blacklist tại đây
>
>Nếu IP Mail được MxToolBox cảnh báo nhẹ ( < 3 ) tiến hành đăng ký tài khoản để gỡ Blacklist + Rà soát hệ thống Mail bằng file Log hoặc kiểm tra account lạ trong trang quản trị
>
>Nếu bị nặng, cách nhanh nhất là đổi IP cho Mail , tiến hành rà soát hệ thống Mail bằng Log để tìm nguồn phát tán , xóa các account gửi spam , quét virus hệ thống

**Zimbra_08 ) /opt/zimbra/bin/ldap: line56: kill No such process**

Khắc phục : 

>Tiến hành kiểm tra ổ cứng cho Mail :
>#df -h
>Tiến hành xóa bớt logs để chạy tạm , hoặc tăng ổ cứng cho hệ thống

**Zimbra_09 ) Zimbra zmconfigd not starting/running**

Khắc phục :
```
#su root
#yum install which
#su zimbra
#rm -rf /opt/zimbra/log/zmconfigd.pid
#zmconfigdctl start
```
**Zimbra_10 ) Diffie-Hellman key khi truy cập**

Khắc phục :
```
#su zimbra#zmprov mcf +zimbraSSLExcludeCipherSuites TLS_DHE_RSA_WITH_AES_128_CBC_SHA
#zmprov mcf +zimbraSSLExcludeCipherSuites TLS_DHE_RSA_WITH_AES_256_CBC_SHA
#zmprov mcf +zimbraSSLExcludeCipherSuites SSL_DHE_RSA_WITH_3DES_EDE_CBC_SHA
#zmmailboxdctl restart
```
**Zimbra_11 ) Starting ldap…Done.**

>Unable to determine enabled services from ldap.
>
>Enabled services read from cache. Service list may be inaccurate.

Khắc phục :
```
#su zimbra
#zmlocalconfig -s ssl_allow_untrusted_certs
#zmlocalconfig -e ssl_allow_untrusted_certs=true; zmcontrol restart
```
**Zimbra_12 ) Not send mail by network IP**

>Lỗi do MTA của Zimbra chưa được cấu hình thêm dải mạng khớp với IP Public MX của domain gây nên tình trạng thư không gửi được.

Khắc phục :

Kiểm tra dải mạng MTA Zimbra đang permit :
```
#su – zimbra
#zmprov gs zmhostname | grep zimbraMtaMyNetworks
hoặc
#su – zimbra
#postconf -d mynetworks
```
Nếu không có dải mạng IP Public. Thêm bằng câu lệnh sau :

VD: IP Public Zimbra : 1.1.1.1/24
```
#su – zimbra
#zmprov ms zmhostname zimbraMtaMyNetworks “127.0.0.0/8 1.1.1.1/24”
#zmcontrol restart
```
**Zimbra_13 ) Zimbra not send/receive email**

Nguyên nhân / Khắc phục :

>Lỗi bản ghi MX => Kiểm tra bản ghi MX

>Firewall chặn port => Kiểm tra port 25
