Trong quá trình sử dụng Mail Server Zimbra, chúng ta không thể nào tránh khỏi một số rủi ro, bài viết này chúng tôi sẽ hướng dẫn bạn xử lý lỗi "System failure exception executing command"

I. Nguyên nhân

![image](https://github.com/chinhtran06062001/hocviecIT/assets/97047640/5cd90a51-b4c9-4602-a730-7f875adcbab7)

Do trên VPS hoặc máy chủ không sử dụng với port SSH mặc định 22 mà cấu hình Zimbra luôn sử dụng port 22 để Monitor.

Trong khi truy cập hàng đợi email hoặc đồ thị giám sát và các dịch vụ khác, máy chủ đôi khi sẽ báo lỗi và cho biết “Đã gặp lỗi máy chủ” với lỗi hệ thống trong quá trình xác thực.

II. Các bước xử lý

1. Tạo SSH và cập nhật key SSH trên máy chủ.
   
Để tạo lại các khóa ssh, bạn sử dụng lệnh sau với user zimbra.

```sh
[root@webmail ~]# su zimbra
[zimbra@webmail ~]$ cd && zmsshkeygen
```
  
```sh
Generating public/private rsa key pair.
Your identification has been saved in /opt/zimbra/.ssh/zimbra_identity.
Your public key has been saved in /opt/zimbra/.ssh/zimbra_identity.pub.
The key fingerprint is:
SHA256:yolGi/6hcCcUKDqihNx8yjh0p6HCca2rxi6E73t8IA8 webmail.azdigi.online
The key's randomart image is:
+---[RSA 2048]----+
|                 |
| .               |
|o .              |
|= o..            |
|*=.*.+  S        |
|B+EoO+ o         |
|**+X*.+          |
|o*o==..          |
|++*=..           |
+----[SHA256]-----+
```

Tiếp theo bạn sử dụng lệnh bên dưới để cập nhật ssh key trên VPS và máy chủ.

```sh
[zimbra@webmail ~]$ zmupdateauthkeys
```  
  
```sh
Updating keys for webmail.azdigi.online
Fetching key for webmail.azdigi.online
Updating keys for webmail.azdigi.online
Updating /opt/zimbra/.ssh/authorized_keys
```

2. Kiểm tra và cập nhật port SSH

Nếu bạn có cấu hình thay đổi port ssh thành port khác thì cần phải cập nhật lại thuộc tính zimbraRemoteManagementPort trên VPS hoặc máy chủ thành port mà bạn đã cấu hình thay đổi nhé!

Bạn sử dụng lệnh như bên dưới để thay đổi lại:
  
```sh
[zimbra@webmail ~]$ zmprov ms webmail.azdigi.online zimbraRemoteManagementPort 2022
```

webmail.azdigi.online: Bạn thay thành hostname trên VPS hoặc máy chủ của bạn.

2022: Bạn thay vào port ssh mà bạn đã cấu hình thay đổi.

Tiếp theo bạn thêm dòng cấu hình sau vào file /etc/ssh/sshd_config để xác minh allow user zimbra.

Vì trước đó đang sử dụng user zimbra, nên bạn cần phải thoát user ra và sử dụng user root mới có thể thay đổi cấu hình file sshd_config được nhé!

```sh
[zimbra@webmail ~]$ exit
exit
[root@webmail ~]# vi /etc/ssh/sshd_config

#       $OpenBSD: sshd_config,v 1.100 2016/08/15 12:32:04 naddy Exp $

# This is the sshd server system-wide configuration file.  See
# sshd_config(5) for more information.

# This sshd was compiled with PATH=/usr/local/bin:/usr/bin

# The strategy used for options in the default sshd_config shipped with
# OpenSSH is to specify options with their default value where
# possible, but leave them commented.  Uncommented options override the
# default value.

# If you want to change the port on a SELinux system, you have to tell
# SELinux about this change.
# semanage port -a -t ssh_port_t -p tcp #PORTNUMBER
#
Port 2022
AllowUsers root admin zimbra      # Thêm dòng này vào file.
#AddressFamily any
#ListenAddress 0.0.0.0
#ListenAddress ::

HostKey /etc/ssh/ssh_host_rsa_key
#HostKey /etc/ssh/ssh_host_dsa_key
:wq
```

Sau khi đã thêm vào file sshd_config hoàn tất, bạn lưu lại và thoát ra với lệnh :wq. và restart lại dịch vụ sshd.

```sh
[root@webmail ~]# systemctl restart sshd
```
 
Chúc bạn thực hiện thành công và thuận lợi.
