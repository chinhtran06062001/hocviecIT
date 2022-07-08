## Cài đặt OMD - Check MK trên CentOS 7

#### Menu

- [1. Mô hình triển khai](#1)
- [2. Cài đặt trên Server](#2)
    - [2.1 Cài đặt repo EPEL](#21)
    - [2.2 Tải file cài đặt OMD - Check MK](#22)
    - [2.3  Cài đặt OMD - Check MK](#23)
    - [2.4 Tạo và khởi động site trên OMD](#24)
- [3. Tham khảo](#3)

<a name="1"></a>
### 1. Mô hình triển khai

#### Mô hình triển khai

![image](https://user-images.githubusercontent.com/97047640/177449501-c18b3812-2778-4dde-a448-37bd3a9e5e68.png)>

<a name="2"></a>
### 2. Cài đặt trên Server

<a name="21"></a>
#### 2.1. Cài đặt repo EPEL

`Check MK` cần khá nhiều các gói dependence đi kèm, vì thế chúng ta cài đặt thêm gói repo này để có thể đáp ứng được một số gói mà local repo không cung cấp.

```
yum install -y epel-release wget
```

Sau khi cài đặt `epel-release` xong, chúng ta sẽ được kết quả như hình.

![image](https://user-images.githubusercontent.com/97047640/177302130-33fdea00-e10f-45be-8956-fc252994156a.png)

<a name="22"></a>

#### 2.2. Tải file cài đặt OMD - Check MK

```
wget https://download.checkmk.com/checkmk/2.0.0p26/check-mk-raw-2.0.0p26-el7-38.x86_64.rpm
```

![image](https://user-images.githubusercontent.com/97047640/177303444-8eab3744-5b28-4e20-9e19-0ea4706c7751.png)

<a name="23"></a>
#### 2.3. Cài đặt OMD - Check MK

Chúng ta sử dụng `yum` để cài đặt gói RPM, mục đích là để yum 'hoàn thiện' những gói dependence mà `check mk` cần.

```
yum install -y check-mk-raw-2.0.*
```

Chờ cho server tự động cài đặt khoảng 5p, chúng ta thấy kết quả như sau

![image](https://user-images.githubusercontent.com/97047640/177304118-e4837b2f-657d-4e2e-b400-a2b6c3dc5c34.png)

![image](https://user-images.githubusercontent.com/97047640/177304159-11c0d563-287a-4660-936b-5cef52637f81.png)

<a name="24"></a>
#### 2.4. Tạo và khởi động site trên OMD

- **Bước 1**: Tạo site

```
omd create monitoring
```

**Chú ý**: `monitoring` là tên tùy chọn, bạn có thể đặt bất cứ tên gì bạn muốn

![image](https://user-images.githubusercontent.com/97047640/177448953-f5d69ab5-f3b3-4e9c-b07a-bd788ef56098.png)

Thông tin `site` được mô tả ở hình.
   
- **Bước 2**: Khởi động site

```
omd start monitoring
```

![image](https://user-images.githubusercontent.com/97047640/177448971-c6f852f3-2b43-45c1-b0fd-043f5d93e543.png)

- **Bước 3:** Mở port 80 cho HTTPD trên Firewalld

Nếu server của bạn có sử dụng Firewalld, hãy mở port cho httpd bằng lệnh:

```
firewall-cmd --permanent --add-port=80/tcp
firewall-cmd --reload
```

- **Bước 4:** Tắt SELinux 

Tắt tức thời bằng lệnh:

```
setenforce 0
```

Chỉnh sửa file cấu hình của SELinux:

```
vi /etc/sysconfig/selinux
```

Sửa dòng `SELINUX=enforcing` thành `SELINUX=disabled`.


- **Bước 5**: Kiểm tra bằng trình duyệt Web

Dùng trình duyệt truy cập vào địa chỉ

```
http://192.168.126.167/monitoring
```

**Chú ý**: Thay địa chỉ IP của bạn vào đường dẫn và đăng nhập theo tài khoản mật khẩu mà hệ thống cung cấp 

![image](https://user-images.githubusercontent.com/97047640/177449130-3ba4ff50-05e3-4738-91e1-328d9cd35446.png)

![image](https://user-images.githubusercontent.com/97047640/177449280-b64f2161-de15-436c-a594-85a9ed5e0876.png)

![image](https://user-images.githubusercontent.com/97047640/177449336-6628e68b-78e9-4068-8c1f-60315a237287.png)


<a name="3"></a>
### 3. Tham khảo

Script cài đặt: [Xem chi tiết](https://gist.github.com/hoangdh/f5894b682d984a9d7e8f4818d63fcc0c)

- **Bonus:** [Quản lý các site trên OMD](Management-OMD.md)
