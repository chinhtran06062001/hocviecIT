# Cài đặt zabbix client for linux

Tải zabbix về

`rpm -ivh https://repo.zabbix.com/zabbix/5.0/rhel/7/x86_64/zabbix-agent2-5.0.21-1.el7.x86_64.rpm`

![image](https://user-images.githubusercontent.com/97047640/177116536-9c59d9cf-95ac-48d4-87dc-9ac0fb248277.png)
  
Cài đặt zabbix release

`rpm -ivh zabbix-release-5.0-1.el8.noarch.rpm`

![image](https://user-images.githubusercontent.com/62273292/165902608-e0ac13af-84fe-4759-a99a-41f7d4c6a194.png)

Cài đặt zabbix agent

![image](https://user-images.githubusercontent.com/97047640/177116861-58bdf41d-ac1b-4ed6-b41f-08cb4b9f5437.png)

Cấu hình file /etc/zabbix/zabbix_agent2.conf

Điền IP của zabbix server vào  Server và ServerActive , sửa đổi tên host name :

![image](https://user-images.githubusercontent.com/97047640/177117101-d155deb9-c465-4b6c-9c97-8ba8bbb5729b.png)

![image](https://user-images.githubusercontent.com/97047640/177117423-0d5370ee-bba1-4697-94ad-126fe01b3376.png)

Sau đó khởi động lại zabbix bằng lệnh :

`systemctl restart zabbix-agent`
