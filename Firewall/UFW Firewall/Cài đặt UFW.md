Bước 1:Truy cập vào hệ thống ubuntu

Bước 2: Cập nhật hệ thống kiểm tra cài đặt

Cập nhật hệ thống

```
sudo apt update
sudo apt upgrade
```

![image](https://user-images.githubusercontent.com/97047640/177903852-18c426df-38d3-481b-a09b-68b3dfb71c73.png)

Kiểm tra cài đặt ufw

Để kiểm tra ufw đã được cài đặt chưa bạn sử dụng lệnh which để kiểm tra như sau.

`which ufw`

![image](https://user-images.githubusercontent.com/97047640/177905615-56544273-b7b1-40d0-a95b-09d059c273b0.png)
    
Và nếu không trả về kết quả hiển thị đầu ra có nghĩa ufw chưa được cài đặt và bạn hãy cài đặt như sau.

Bước 3: Cài đặt ufw
  
`sudo apt-get install ufw`
    
cài đặt cấu hình UFW trên Ubuntu Debian

Sau khi bạn cài đặt ufw hoàn tất, bạn hãy sử dụng lệnh sau để kiểm tra. Và mặc định ban đầu sau khi cài đặt thì UFW sẽ được vô hiệu do chưa kích hoạt. Và bạn phải kích hoạt thủ công.

`sudo ufw status verbose`

![image](https://user-images.githubusercontent.com/97047640/177906050-2067d691-0b47-41fe-a7e7-1534835090c9.png)

III. Hướng dẫn sử dụng ufw

1. Một số lệnh quản lý kích hoạt ufw

1.1 Kích hoạt ufw và khởi động cùng hệ thống
  
`sudo ufw enable`

![image](https://user-images.githubusercontent.com/97047640/177906357-e9608698-10d0-491e-89fb-84711269c9fb.png)
    
cài đặt cấu hình UFW trên Ubuntu Debian

1.2 Vô hiệu kích hoạt ufw
  
`sudo ufw disable`

1.3 Khôi phục ufw về mặc định

Một lý do nào đó bạn cần phục hồi xoá tất cả các rule hiện có để đưa về mặc định ban đầu, bạn hãy sử dụng tuỳ chọn reset để thực hiện như sau.
  
`sudo ufw reset`
    
cài đặt cấu hình UFW trên Ubuntu Debian

1.4 Tải lại các quy tắc
  
`sudo ufw reload`

![image](https://user-images.githubusercontent.com/97047640/177907596-4121b299-acf7-487c-808d-877630522c21.png)
    
2. Sử dụng ufw để quản lý quy tắc

2.1. Cho phép, mở port kết nối

Cú pháp thực hiện

Để thực hiện mở một port (cổng) bất kỳ bạn sử dụng cú pháp như sau.

`sudo ufw allow <port>/<optional: protocol> `

Ví dụ thực tế: Mình sẽ sử dụng ufw để mở port 80, 443 và 8080

`sudo ufw allow 80/tcp`
  
Hoặc
  
`sudo ufw allow http`

`sudo ufw allow 443/tcp`
  
Hoặc
  
`sudo ufw allow https`

`sudo ufw allow 8080/tcp`
    
![image](https://user-images.githubusercontent.com/97047640/177907648-04db4ac2-49a5-4f9c-9ca6-d764247c73cf.png)

2.2 Từ chối, đóng port kết nối
  
Để cấm, từ chối bạn sử dụng deny và thực hiện theo cấu trúc cú pháp như sau.

`sudo ufw deny <port>/<optional: protocol> `
  
Ví dụ thực tế: Mình sẽ đóng cổng kết nối là 3306 và 8080

```  
sudo ufw deny 3306
sudo ufw allow 8080
```    

![image](https://user-images.githubusercontent.com/97047640/177907765-30830bca-faa5-4698-a14d-d8caf2e9b5a7.png)

Ngoài ra ufw còn hỗ trợ cú pháp đơn giản như sau. Nếu bạn xác định được cổng thuộc dịch vụ nào bạn có thể deny dịch vụ thay vì cổng thuộc dịch vụ đó.

Ví dụ: Cổng 3306 thuộc dịch vụ mysql và bạn có thể deny mysql theo cú pháp như sau.

  
`sudo ufw deny mysql`
    

2.3 Cho phép IP truy cập đến cổng nhất định
  
```
sudo ufw allow from 192.168.126.195 to any port 22
sudo ufw allow from 192.168.126.195 to any port 3306
```
  
  ![image](https://user-images.githubusercontent.com/97047640/177907886-fd05ab9d-75d5-4354-acc3-730f0ee5bcb7.png)

    
Với cú pháp này sẽ cho phép một IP cụ thể được quyền truy cập vào cổng đã được chỉ định. Như ví dụ trên mình thực hiện cho phép địa chỉ IP là 192.168.126.137 được phép truy cập vào cổng 22 là ssh và cổng 3306 là mysql

2.4 Xoá bỏ các quy tắc
  
Để quản lý các quy tắc trên UFW của bạn, bạn có thể liệt kê chúng ra theo dạng menu danh sách. Để thực hiện được bạn sử dụng lệnh sau, màn hình hiển thị các quy tắc kèm số thứ tự và bạn sẽ chọn các số thứ tự hoặc tên quy tắc để xoá bỏ.

`sudo ufw status numbered`
  
![image](https://user-images.githubusercontent.com/97047640/177907979-ba7404eb-b462-463d-b93d-c6ed4aa5dbb8.png)

Ví dụ thực tế: Như ảnh trên là tất cả các quy tắc và mình sẽ thực hiện xoá bỏ quy tắt số 7, là cho phép IP 192.168.0.1 sử dụng port 22. Mình sẽ sử dụng cú pháp sau để xoá

`sudo ufw delete [number]`
  
`sudo ufw delete 7`
  
![image](https://user-images.githubusercontent.com/97047640/177910026-cdc71cd8-8e28-41bd-8d3b-be7cc8a8af6b.png)

2.5 Cho phép phạm vi cổng

UFW cho phép bạn truy cập vào phạm vi cổng kết nối thay vì bạn mở cho từng cổng riêng biệt. Và khi bạn cho phép phạm vi cổng bạn cần xác định phạm vi cổng thuộc giao thức TCP hay là UDP để mở nhé.

Ví dụ thực tế: Như bên dưới mình sẽ mở phạm vị từ 35000:35999 trên TCP và 35000:35999 UDP như sau.

  
```
sudo ufw allow 35000:35999/tcp
sudo ufw allow 35000:35999udp
```  

2.6 Đóng phạm vi cổng

  Cũng giống như mở phạm vi cổng kết nối ở phần 2.5 Cho phép phạm vi cổng. Bạn cũng có thể đóng phạm vi cổng bằng deny. Bạn sử dụng cú pháp sau để đóng nhé.

Ví dụ: Bên dưới mình thực hiện đóng phạm vi cổng 35000:35999 TCP và UDP

  
```
    sudo ufw deny 35000:35999/tcp
sudo ufw deny 35000:35999udp
 ```

2.7 Cho phép và từ chối IP

  Cho phép IP truy cập
  
Để cho phép, mở IP bạn sử dụng cú pháp như sau.

`sudo ufw allow from $Your_IP`
  
Ví dụ bên dưới mình thực hiện cho phép, mở IP 192.168.126.137 trên ufw như sau.


`
Sudo ufw allow from 192.168.126.137
Rule added`
Từ chối IP
  
Để từ chối IP truy cập bạn sử dụng cú pháp như sau.

`sudo ufw deny from $Your_IP`
  
`sudo ufw deny from 192.168.0.1`

Rule updated
    
2.8 Bật kích hoạt IPv6
  
Nếu bạn sử dụng IPv6 trên VPS của mình, bạn cần đảm bảo rằng IPv6 được bật trong UFW. Để thực hiện bạn cần mởi file cấu hình ufw /etc/default/ufw và điều chỉnh như sau.

 
`sudo vi /etc/default/ufw`
    
Nếu dòng IPV6=no bạn hãy chuyển sang YES để kích hoạt nhé.
