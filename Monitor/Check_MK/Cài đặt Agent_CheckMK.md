### Cài đặt Agent trên Host giám sát

Đầu tiên, chúng ta vào Web UI để tải `Agent` cho client. Ở giao diện Web, chúng ta kéo xuống phần `setup` -> `agent` -> `chọn loại máy chủ agent`

![image](https://user-images.githubusercontent.com/97047640/177458203-4afd1d76-9e29-422d-b80b-e3374318e98b.png)

![image](https://user-images.githubusercontent.com/97047640/177458473-e8d1a79c-7e64-465c-9f33-f52305591346.png)

Ở đây, có 3 packet dành cho 3 DISTRO:

- *.deb: Dành cho các host sử dụng DEBIAN
- *.rpm: Dành cho các host sử dụng RHEL
- *.msi: Dành cho các host sử dụng MS Windows

Đầu tiên, tôi sẽ giám sát host CentOS 7. Vì thế tôi sẽ tải file `RPM`. Trên Host CentOS cần giám sát, chúng ta tải `agent` cho nó từ server. Để lấy link tải, chúng ta vào Web UI và chuột phải vào link, chọn **Copy link address** (Tiếng Việt: **Sao chép địa chỉ liên kết**)

<a name="copylink" ></a>
![image](https://user-images.githubusercontent.com/97047640/177458605-50087390-214e-4201-bd0f-40a54df29d28.png)

Và sau đó qua terminal của máy cần cài đặt và dùng `wget` để tải file

```
wget http://192.168.126.167/monitoring/check_mk/agents/check-mk-agent-2.0.0p26-1.noarch.rpm
```

![image](https://user-images.githubusercontent.com/97047640/177458920-5f01f95e-cc02-4674-b23d-d0c9efece721.png)

**Lưu ý:** 
- Ở những phiên bản thấp hơn 1.2.8, khi dùng `wget` để tải agent OMD sẽ yêu cầu xác thực.
- Thay thế địa chỉ IP server vào câu lệnh trên.
- Link này được copy từ Web UI (Để câu lệnh thực hiện chính xác, vui lòng copy từ Web UI của bạn như bước [trên](#copylink).)

Kiểm tra `xinet.d` đã được cài đặt.

```
rpm -qa | grep xinetd
```

![image](https://user-images.githubusercontent.com/97047640/177459078-2fb5973b-3db3-4fd6-a6ac-1920c786d753.png)

Nếu câu lệnh trả về kết quả như hình, vui lòng cài đặt theo lệnh sau:

```
yum install xinetd -y
```

![image](https://user-images.githubusercontent.com/97047640/177459148-d3663aac-9acf-478e-a38d-ba1d4168f9ea.png)

![image](https://user-images.githubusercontent.com/97047640/177459179-b70956e9-5909-4293-9163-71394481c9d1.png)

Khởi động dịch vụ và cho chạy cùng hệ thống:

```
systemctl start xinetd
systemctl enable xinetd
```

Cài đặt `agent` bằng lệnh

```
rpm -ivh check-mk-agent-*
```

![image](https://user-images.githubusercontent.com/97047640/177459276-637760a4-3f5a-4768-94ac-694cd1c2d29a.png)

Để cho phép OMD Server được truy cập vào host, chúng ta chỉnh sửa file cấu hình `agent` trên host

```
vi /etc/xinetd.d/check_mk
```
![image](https://user-images.githubusercontent.com/97047640/177459641-a7884b18-0fe2-41ca-a8cf-623a47873127.png)

![image](https://user-images.githubusercontent.com/97047640/177459690-54a73ef6-4bda-499d-b051-faa98b52e5e2.png)

Có 3 thông số chúng ta cần phải chỉnh cho chính xác:

- port: 6556
- only_from: Thêm địa chỉ IP server OMD của bạn
- disable: no (Có nghĩa cho phép dịch vụ chạy)

Sau khi chỉnh xong, chúng ta lưu lại file và khởi động lại `xinetd`.

```
systemctl restart xinetd
```

Kiểm tra port đã hoạt động

```
netstat -npl | grep 6556
```

![image](https://user-images.githubusercontent.com/97047640/177459804-9cfdc9c9-6b2e-4db0-b873-6c1627a21233.png)

Nếu không có lệnh `netstat` vui lòng cài tiện ích `net-tools`:

```
yum install -y net-tools
```

- **Chú ý:** Nếu sử dụng Firewall vui lòng mở port 6556. Thực hiện các bước sau:

	- Với CentOS:
	
	```
	firewall-cmd --add-port=6556/tcp --permanent
	firewall-cmd --reload
	```
	
	Tắt SELINUX tức thời bằng lệnh:

	```
	setenforce 0
	```

	Chỉnh sửa file cấu hình của SELinux:

	```
	vi /etc/sysconfig/selinux
	```

	Sửa dòng `SELINUX=enforcing` thành `SELINUX=disabled`.

Sau khi cài thành công, chúng ta cấu hình trên [Web UI](#4).

<a name="4" ></a>
### Thêm host trên Web UI

Quay trở lại Web UI, chúng ta sẽ thêm mới 1 host. Đầu tiên, Vào Menu `Setup`, chọn `Hosts` và click vào `Add Host`

![image](https://user-images.githubusercontent.com/97047640/177460385-a6d5359c-dfff-45ff-a38d-b0ad229d12ff.png)  

Điền thông tin của host của bạn như hình:

![image](https://user-images.githubusercontent.com/97047640/177463606-7586576f-b91c-4558-b1e9-99dc15fda13a.png)

Click vào `Save & go to Services`, sau đó Server sẽ thu thập thông tin từ Agent cài trên host giám sát.

![image](https://user-images.githubusercontent.com/97047640/177463698-4c1dd437-b6d1-4e02-bcd8-3c6601124541.png)

Các thay đổi được Appy thành công.

![image](https://user-images.githubusercontent.com/97047640/177464062-0e156910-8525-4c4d-9d24-271ee12c0033.png)

Tại Tab `Monitor`, `Overview` > `All Services`, click vào biểu tượng `Rerfesh` để force check dịch vụ:

![image](https://user-images.githubusercontent.com/97047640/177464144-b89a709d-cd80-4cce-b1e8-9ccf4de96e3f.png)

Sau khi tạo host

![image](https://user-images.githubusercontent.com/62273292/165695741-9abdae60-5f46-4f55-ad75-d9b39e04c1fb.png)

Lưu lại nhật kỹ mỗi khi update

![image](https://user-images.githubusercontent.com/62273292/165698599-5bae5817-5cb3-46d2-afba-35b7f818b37f.png)

![image](https://user-images.githubusercontent.com/62273292/165698669-4e7d34ff-b4b9-438a-bd35-245fec32de5a.png)

Biết được có bao nhiêu hosts và services

![image](https://user-images.githubusercontent.com/62273292/165699881-b60afc28-44b5-45d6-b64b-cbe996ad613a.png)

Kiểm tra CPU hoạt động

![image](https://user-images.githubusercontent.com/62273292/165700203-9ebcf26c-4cda-4b62-8a43-f12062407674.png)
