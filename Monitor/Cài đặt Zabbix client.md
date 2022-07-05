# Cài đặt zabbix client for linux

Tải zabbix về

`rpm -ivh https://repo.zabbix.com/zabbix/5.0/rhel/7/x86_64/zabbix-agent2-5.0.21-1.el7.x86_64.rpm`

![image](https://user-images.githubusercontent.com/97047640/177116536-9c59d9cf-95ac-48d4-87dc-9ac0fb248277.png)
  
Cài đặt zabbix release

`rpm -ivh zabbix-release-5.0-1.el8.noarch.rpm`

Cài đặt zabbix agent

![image](https://user-images.githubusercontent.com/97047640/177116861-58bdf41d-ac1b-4ed6-b41f-08cb4b9f5437.png)

Cấu hình file /etc/zabbix/zabbix_agent2.conf

Điền IP của zabbix server vào  Server và ServerActive , sửa đổi tên host name :

![image](https://user-images.githubusercontent.com/97047640/177117101-d155deb9-c465-4b6c-9c97-8ba8bbb5729b.png)

![image](https://user-images.githubusercontent.com/97047640/177117423-0d5370ee-bba1-4697-94ad-126fe01b3376.png)

Sau đó khởi động lại zabbix bằng lệnh :

`systemctl restart zabbix-agent`

# Cài đặt Zabbix Client For Windowns

Truy cập https://www.zabbix.com/download_agents?version=5.0+LTS&release=5.0.24&os=Windows&os_version=Any&hardware=amd64&encryption=OpenSSL&packaging=MSI&show_legacy=0 để tải phần mềm zabbix dành cho windown

![image](https://user-images.githubusercontent.com/97047640/177124596-5e330a01-6bab-4dc6-b23c-1d99a66cd5c4.png)

Tiến hành cài đặt phần mềm 

![image](https://user-images.githubusercontent.com/97047640/177128584-7892d8e5-5bd7-45ac-bce2-5badcafbf549.png)

Chấp nhận điều khoản và Next 

![image](https://user-images.githubusercontent.com/97047640/177238399-211f56f7-44b7-42d4-9ddf-a2b32e7f3de9.png)

Điền NameHost và các thông tin khác 

![image](https://user-images.githubusercontent.com/97047640/177238486-5349c989-3804-4083-84bb-d8bfc5b284c4.png)

Tiếp tục nhấn next

![image](https://user-images.githubusercontent.com/97047640/177238581-0ad0dd6e-a3c2-4e43-a038-aeca7a5075d3.png)

Chọn Install và đợi cài đặt hoàn tất 

![image](https://user-images.githubusercontent.com/97047640/177238623-d8a3ca96-ec65-4a0f-92a6-d6b0d36e1c54.png)
 
![image](https://user-images.githubusercontent.com/97047640/177238705-958b6759-8551-4aba-8330-7f2209d20d51.png)


# Hướng dẫn cấu hình zabbix trên windowns 

Truy cập Computer Management -> Service -> Zabbix Agent -> Properties -> Sửa đổi Automatic thành Automatic (Delayed Start)

![image](https://user-images.githubusercontent.com/97047640/177242060-9e7458cb-c211-45c3-85e1-ec53da5b345a.png)

Truy cập Control Pannel -> System and Security -> Windowns Defender Firewall -> Allow Apps -> Tiến hành add các file path .exe của zabbix vào 

![image](https://user-images.githubusercontent.com/97047640/177242317-5bc6f4e7-03ac-49b3-9a12-cc1976f1e34c.png)

![image](https://user-images.githubusercontent.com/97047640/177242350-54b3f9a2-1d37-46fa-94c3-6a02f2abe8eb.png)

![image](https://user-images.githubusercontent.com/97047640/177242686-7bd83f75-e486-437f-9bcb-b3ff3a12a803.png)
