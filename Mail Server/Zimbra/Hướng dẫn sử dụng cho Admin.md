# Hướng dẫn sử dụng phần quản trị Admin 

Bước 1 : Truy cập vào Zimbra với tài khoản của Admin

![image](https://user-images.githubusercontent.com/97047640/175456381-8ee0f4fd-008d-42ac-95a7-01258fee3802.png)

Bước 2 : Ở góc trên cùng bên phải chọn tài khoản admin, chọn Bảng quản trị 

![image](https://user-images.githubusercontent.com/97047640/175456517-1d1b152c-3df3-4d59-b664-00758aad5271.png)

Tiếp theo bạn sẽ được chuyển vào phần Zimbra Admin Console 

![image](https://user-images.githubusercontent.com/97047640/175456651-da895702-b33d-4e05-b206-77dc4f553c8b.png)

Bước 3 : Tiến hành đăng nhập tài khoản quản trị và sử dụng .

![image](https://user-images.githubusercontent.com/97047640/175456718-631741fa-14f6-4328-a9c9-6681ba4b5555.png)

## Các chức năng phần quản trị Admin

**Trang chủ**

![image](https://user-images.githubusercontent.com/97047640/175457003-064dbfe1-e253-47e1-975a-2d5f8d6471a5.png)

**Giám sát**

Trạng thái máy chủ

![image](https://user-images.githubusercontent.com/97047640/175457037-e8de496c-54de-43bd-8e5c-4f55964bb6d2.png)

Thống kê nâng cao 

![image](https://user-images.githubusercontent.com/97047640/175457143-1e2ff5d3-981d-406c-8895-e245da5ae6c7.png)

Đếm thư

![image](https://user-images.githubusercontent.com/97047640/175457183-19eda1d9-c89a-4b6a-9163-a41901c40c76.png)

Dung lượng thư

![image](https://user-images.githubusercontent.com/97047640/175457438-933365f1-d9ff-4d72-a8a7-912a130b41a3.png)

Chống thư rác 

![image](https://user-images.githubusercontent.com/97047640/175457482-fc97c0f5-b336-4261-b849-fb400221ad59.png)

Thống kê máy chủ

![image](https://user-images.githubusercontent.com/97047640/175457547-95020884-0ff8-48c8-8afc-40ef4069c6f0.png)

Hàng đợi thư

![image](https://user-images.githubusercontent.com/97047640/175457600-18293160-825c-4bf3-b292-39ac92aeff51.png)

**Quản lý**

Quản lý tài khoản 

![image](https://user-images.githubusercontent.com/97047640/175457629-e93b7824-4870-4369-9c8d-0b2a98680c18.png)

Bí danh 

![image](https://user-images.githubusercontent.com/97047640/175457662-b3dc7a3b-6327-47bc-a8ee-24616efe1cba.png)

Cách danh sách gửi thử

![image](https://user-images.githubusercontent.com/62273292/164370581-f8d0574e-5816-4b52-b8a1-10de310f414f.png)

Tài nguyên 

![image](https://user-images.githubusercontent.com/62273292/164370950-e73ae093-b085-48aa-bce0-611c2751f2ba.png)


**Cấu hình**

Lớp dịch vụ 

![image](https://user-images.githubusercontent.com/97047640/175457773-9b374cb2-43b2-4ba5-8dcf-bbd187e49760.png)

Tên Miền 

![image](https://user-images.githubusercontent.com/97047640/175457791-4850f480-bab9-44be-82ae-21b978c571a8.png)

Máy chủ 

![image](https://user-images.githubusercontent.com/97047640/175457827-6edd1813-6000-48f8-abeb-527967205e5d.png)

Thiết lập chung

![image](https://user-images.githubusercontent.com/97047640/175457867-76dd5f2b-1763-4818-bf9b-a94e6cf0047a.png)

Các zimlet

![image](https://user-images.githubusercontent.com/97047640/175457958-ee6a6d3e-be56-4bf7-b2b9-8f74a108b22f.png)

Phần mở rộng của quản trị viên

![image](https://user-images.githubusercontent.com/97047640/175457992-a7f38356-cab6-41d3-b2d6-117168dcf25c.png)

Chứng chỉ

![image](https://user-images.githubusercontent.com/97047640/175458013-0222fba8-df8a-4a1c-ad2a-e43e05eaf261.png)


Tìm kiếm 

![image](https://user-images.githubusercontent.com/97047640/175458048-81c6bf57-4a34-4e3b-8f33-c9ef17934c59.png)

## Test thành công gửi nhận mail

![image](https://user-images.githubusercontent.com/97047640/175458112-43da9b81-3103-45e0-9eae-34f6bb553d45.png)

## Nhật ký Logs 

Nhật ký logs nằm ở phần trang chủ - quản lý - tài khoản

![image](https://user-images.githubusercontent.com/97047640/175458368-7a3c9d35-d542-4243-bcef-1a9fd22fceba.png)

## KIỂM TRA LOG GỬI / NHẬN EMAIL ZIMBRA

`/var/log/maillog`

![image](https://user-images.githubusercontent.com/97047640/175458636-48b44e9c-22c0-442c-9b60-30ae22fe0b3c.png)

**– Chu trình gửi: Khi click gửi thư => Connect tới email server => MTA kiểm tra địa chỉ người nhận => Kiểm tra qua các rule filter, đánh giá spam, virus => Xếp vào queue => Gửi thư => Xóa khỏi queue => Thông báo Message accepted for delivery**

```
Mar 22 17:35:03 mail postfix/postscreen[26703]: CONNECT from [103.101.163.27]:57274 to [103.101.163.27]:25
Mar 22 17:35:03 mail postfix/postscreen[26703]: WHITELISTED [103.101.163.27]:57274
Mar 22 17:35:03 mail postfix/smtpd[26704]: connect from mail.hvn.space[103.101.163.27]
Mar 22 17:35:03 mail postfix/smtpd[26704]: NOQUEUE: filter: RCPT from mail.hvn.space[103.101.163.27]: <kiendt@hvn.space>: Sender address triggers FILTER smtp-amavis:[127.0.0.1]:10026; from=<kiendt@hvn.space> to=<kiendt@hvn.com.vn> proto=ESMTP helo=<mail.hvn.space>
Mar 22 17:35:03 mail postfix/smtpd[26704]: 8C0C11035C8: client=mail.hvn.space[103.101.163.27]
Mar 22 17:35:03 mail postfix/cleanup[26705]: 8C0C11035C8: message-id=<1461502541.19.1584873303494.JavaMail.zimbra@hvn.space>
Mar 22 17:35:03 mail postfix/smtpd[26704]: disconnect from mail.hvn.space[103.101.163.27] ehlo=1 mail=1 rcpt=1 data=1 quit=1 commands=5
Mar 22 17:35:03 mail postfix/qmgr[18088]: 8C0C11035C8: from=<kiendt@hvn.space>, size=1332, nrcpt=1 (queue active)
Mar 22 17:35:10 mail postfix/amavisd/smtpd[26711]: connect from localhost[127.0.0.1]
Mar 22 17:35:10 mail postfix/amavisd/smtpd[26711]: AF0C11035D3: client=localhost[127.0.0.1]
Mar 22 17:35:10 mail postfix/cleanup[26705]: AF0C11035D3: message-id=<VAlxpN_C_TkZ7F@mail.hvn.space>
Mar 22 17:35:10 mail postfix/qmgr[18088]: AF0C11035D3: from=<admin@hvn.space>, size=2537, nrcpt=1 (queue active)
Mar 22 17:35:10 mail postfix/dkimmilter/smtpd[26713]: connect from localhost[127.0.0.1]
Mar 22 17:35:10 mail postfix/dkimmilter/smtpd[26713]: BB0111035D4: client=localhost[127.0.0.1]
Mar 22 17:35:10 mail postfix/cleanup[26705]: BB0111035D4: message-id=<1461502541.19.1584873303494.JavaMail.zimbra@hvn.space>
Mar 22 17:35:10 mail postfix/qmgr[18088]: BB0111035D4: from=<kiendt@hvn.space>, size=1867, nrcpt=1 (queue active)
Mar 22 17:35:10 mail postfix/smtp[26706]: 8C0C11035C8: to=<kiendt@hvn.com.vn>, relay=127.0.0.1[127.0.0.1]:10026, delay=7.3, delays=0.03/0.02/0.01/7.3, dsn=2.0.0, status=sent (250 2.0.0 from MTA(smtp:[127.0.0.1]:10030): 250 2.0.0 Ok: queued as BB0111035D4)
Mar 22 17:35:10 mail postfix/qmgr[18088]: 8C0C11035C8: removed
Mar 22 17:35:11 mail postfix/lmtp[26712]: AF0C11035D3: to=<admin@hvn.space>, relay=mail.hvn.space[103.101.163.27]:7025, delay=0.55, delays=0.03/0.01/0.42/0.09, dsn=2.1.5, status=sent (250 2.1.5 Delivery OK)
Mar 22 17:35:11 mail postfix/qmgr[18088]: AF0C11035D3: removed
Mar 22 17:35:12 mail postfix/amavisd/smtpd[26716]: connect from localhost[127.0.0.1]
Mar 22 17:35:12 mail postfix/amavisd/smtpd[26716]: CF0671035C8: client=localhost[127.0.0.1]
Mar 22 17:35:12 mail postfix/cleanup[26705]: CF0671035C8: message-id=<1461502541.19.1584873303494.JavaMail.zimbra@hvn.space>
Mar 22 17:35:12 mail postfix/amavisd/smtpd[26716]: disconnect from localhost[127.0.0.1] ehlo=1 mail=1 rcpt=1 data=1 quit=1 commands=5
Mar 22 17:35:12 mail postfix/qmgr[18088]: CF0671035C8: from=<kiendt@hvn.space>, size=2920, nrcpt=1 (queue active)
Mar 22 17:35:12 mail postfix/smtp[26706]: BB0111035D4: to=<kiendt@hvn.com.vn>, relay=127.0.0.1[127.0.0.1]:10032, delay=2.1, delays=0.11/0.01/0/2, dsn=2.0.0, status=sent (250 2.0.0 from MTA(smtp:[127.0.0.1]:10025): 250 2.0.0 Ok: queued as CF0671035C8)
Mar 22 17:35:12 mail postfix/qmgr[18088]: BB0111035D4: removed
Mar 22 17:35:15 mail postfix/smtp[26717]: CF0671035C8: to=<kiendt@hvn.com.vn>, relay=mx07.email-hvn.net[203.162.79.167]:25, delay=2.9, delays=0.01/0.02/2.8/0.05, dsn=2.0.0, status=sent (250 2.0.0 5e773f65-00009f59 Message accepted for delivery)
Mar 22 17:35:15 mail postfix/qmgr[18088]: CF0671035C8: removed
```

**– Chu trình nhận: Chấp nhận kết nối từ email server gửi => Kiểm tra qua các rule filter, đánh giá spam, virus => Xếp vào queue => Nhận thư và xóa khỏi queue => Thông báo nhận thư 250 2.1.5 Delivery OK**

```
Mar 22 17:43:23 mail postfix/postscreen[32077]: CONNECT from [209.85.208.44]:44796 to [103.101.163.27]:25
Mar 22 17:43:29 mail postfix/postscreen[32077]: PASS NEW [209.85.208.44]:44796
Mar 22 17:43:29 mail postfix/smtpd[32078]: connect from mail-ed1-f44.google.com[209.85.208.44]
Mar 22 17:43:30 mail postfix/smtpd[32078]: Anonymous TLS connection established from mail-ed1-f44.google.com[209.85.208.44]: TLSv1.2 with cipher ECDHE-RSA-AES128-GCM-SHA256 (128/128 bits)
Mar 22 17:43:31 mail postfix/smtpd[32078]: NOQUEUE: filter: RCPT from mail-ed1-f44.google.com[209.85.208.44]: <kiendt@hvn.com.vn>: Sender address triggers FILTER smtp-amavis:[127.0.0.1]:10026; from=<kiendt@hvn.com.vn> to=<kiendt@hvn.space> proto=ESMTP helo=<mail-ed1-f44.google.com>
Mar 22 17:43:31 mail postfix/smtpd[32078]: NOQUEUE: filter: RCPT from mail-ed1-f44.google.com[209.85.208.44]: <kiendt@hvn.com.vn>: Sender address triggers FILTER smtp-amavis:[127.0.0.1]:10024; from=<kiendt@hvn.com.vn> to=<kiendt@hvn.space> proto=ESMTP helo=<mail-ed1-f44.google.com>
Mar 22 17:43:31 mail postfix/smtpd[32078]: 4B67C1035C8: client=mail-ed1-f44.google.com[209.85.208.44]
Mar 22 17:43:31 mail postfix/cleanup[32086]: 4B67C1035C8: message-id=<CAE71=UqPysBzQEWso90x+v6UAFnHPu7uc8zMs8nL+-CEUDgptg@mail.gmail.com>
Mar 22 17:43:31 mail postfix/qmgr[18088]: 4B67C1035C8: from=<kiendt@hvn.com.vn>, size=7240, nrcpt=1 (queue active)
Mar 22 17:43:32 mail postfix/smtpd[32078]: disconnect from mail-ed1-f44.google.com[209.85.208.44] ehlo=2 starttls=1 mail=1 rcpt=1 data=1 quit=1 commands=7
Mar 22 17:43:40 mail postfix/amavisd/smtpd[32092]: connect from localhost[127.0.0.1]
Mar 22 17:43:40 mail postfix/amavisd/smtpd[32092]: 014E01035D3: client=localhost[127.0.0.1]
Mar 22 17:43:40 mail postfix/cleanup[32086]: 014E01035D3: message-id=<VALGB39FdscOxm@mail.hvn.space>
Mar 22 17:43:40 mail postfix/amavisd/smtpd[32092]: disconnect from localhost[127.0.0.1] ehlo=1 mail=1 rcpt=1 data=1 quit=1 commands=5
Mar 22 17:43:40 mail postfix/qmgr[18088]: 014E01035D3: from=<admin@hvn.space>, size=4345, nrcpt=1 (queue active)
Mar 22 17:43:40 mail postfix/amavisd/smtpd[32092]: connect from localhost[127.0.0.1]
Mar 22 17:43:40 mail postfix/amavisd/smtpd[32092]: 066BC1035D4: client=localhost[127.0.0.1]
Mar 22 17:43:40 mail postfix/cleanup[32086]: 066BC1035D4: message-id=<CAE71=UqPysBzQEWso90x+v6UAFnHPu7uc8zMs8nL+-CEUDgptg@mail.gmail.com>
Mar 22 17:43:40 mail postfix/amavisd/smtpd[32092]: disconnect from localhost[127.0.0.1] ehlo=1 mail=1 rcpt=1 data=1 quit=1 commands=5
Mar 22 17:43:40 mail postfix/qmgr[18088]: 066BC1035D4: from=<kiendt@hvn.com.vn>, size=8203, nrcpt=1 (queue active)
Mar 22 17:43:40 mail postfix/smtp[32087]: 4B67C1035C8: to=<kiendt@hvn.space>, relay=127.0.0.1[127.0.0.1]:10024, delay=8.7, delays=0.63/0.02/0.01/8.1, dsn=2.0.0, status=sent (250 2.0.0 from MTA(smtp:[127.0.0.1]:10025): 250 2.0.0 Ok: queued as 066BC1035D4)
Mar 22 17:43:40 mail postfix/qmgr[18088]: 4B67C1035C8: removed
Mar 22 17:43:40 mail postfix/lmtp[32094]: 066BC1035D4: to=<kiendt@hvn.space>, relay=mail.hvn.space[103.101.163.27]:7025, delay=0.25, delays=0.01/0.01/0.14/0.08, dsn=2.1.5, status=sent (250 2.1.5 Delivery OK)
Mar 22 17:43:40 mail postfix/qmgr[18088]: 066BC1035D4: removed
Mar 22 17:43:40 mail postfix/lmtp[32093]: 014E01035D3: to=<admin@hvn.space>, relay=mail.hvn.space[103.101.163.27]:7025, delay=0.28, delays=0.01/0.01/0.16/0.1, dsn=2.1.5, status=sent (250 2.1.5 Delivery OK)
Mar 22 17:43:40 mail postfix/qmgr[18088]: 014E01035D3: removed
```
