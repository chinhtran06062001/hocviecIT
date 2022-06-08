# Cài đặt và sử dụng Mssql trên windows server

Link download: https://www.microsoft.com/en-us/sql-server/sql-server-downloads

![image](https://user-images.githubusercontent.com/62273292/161185558-1ef111cc-e8b3-4402-b8e5-069989c6a6fb.png)

Chọn custom

![image](https://user-images.githubusercontent.com/62273292/161185663-be0f044f-23b3-4bbf-a81a-e0b1d4ddb635.png)

Cài đặt

![image](https://user-images.githubusercontent.com/62273292/161186812-2b7663be-5717-4972-bd4c-061ed386cbe2.png)

Cài ssms

![image](https://user-images.githubusercontent.com/62273292/161187204-0c6aed17-661f-4e66-a018-e20119c599cd.png)

![image](https://user-images.githubusercontent.com/62273292/161188700-8ebae1ff-b79f-4396-8f83-f5ca260a5fe3.png)

![image](https://user-images.githubusercontent.com/62273292/161212254-df2083dd-ffdf-4518-827c-f26c6e7e3daa.png)


Có 2 chế độ xác thực chính là Windows Authentication và SQL Server Authentication

![image](https://user-images.githubusercontent.com/62273292/161212428-3c09c86a-ad58-4fce-ae4a-585a86a591e3.png)


  Chế độ Windows Authentication: Là chế độ xác thực người dùng windows, chỉ cần có user vào windows là được, không cần nhập Password.
  
  Chế độ SQL Server Authentication: Là chế độ xác thực người dùng mức SQL Server, do SQL server quản lý user và password, người dùng phải có user và password mới có thể  truy cập vào SQL Server
      - SQL Server có 1 user mặc định full quyền là security admin- viết tắt là sa.
      - Password của user sa do người dùng nhập vào khi cài đặt SQL Server
   


Khi đăng nhập vào thì sẽ có giao diện chính 

![image](https://user-images.githubusercontent.com/62273292/161212767-bec8cdda-244e-4aba-b6b0-49756e35e4a4.png)

Chọn new Query và bắt đầu thực hiện các câu lệnh cơ bản

Tạo 1 cơ sỡ dữ liệu mới

![image](https://user-images.githubusercontent.com/97047640/172532679-aa7249f5-5b97-49b8-bdaf-9dc09163c9be.png)

Tạo bảng cho database

![image](https://user-images.githubusercontent.com/97047640/172533547-863aa637-6c6d-42ea-ab6a-fbf1f227cf8a.png)

Chèn dữ liệu vào trong bảng

![image](https://user-images.githubusercontent.com/97047640/172535085-a7b7e5a3-6961-4dec-9887-30486b0d424f.png)

Nối 2 bảng lại với nhau với trường id

![image](https://user-images.githubusercontent.com/97047640/172561013-2476a769-55fa-4356-a78b-7d1562c717a5.png)


![image](https://user-images.githubusercontent.com/97047640/172561307-f2aed51f-3b4b-48e9-af07-fb6ec7569330.png)

![image](https://user-images.githubusercontent.com/97047640/172561388-85c4637c-6622-418f-99f8-230702ccaba1.png)

Dùng lệnh select để xem dữ kiệu trong bảng

![image](https://user-images.githubusercontent.com/97047640/172559038-ba96c7a6-fc11-4e80-98a0-1c2f3bdd0dd4.png)

Dùng lệnh update để cập nhật dữ liệu trong bảng

![image](https://user-images.githubusercontent.com/97047640/172559456-79e48b39-8ee9-45fd-aa76-d7746682a59b.png)

Lệnh delete: chúng ta có thể xóa dữ liệu,  xóa  database

![image](https://user-images.githubusercontent.com/97047640/172560175-89b5341b-adc6-4546-878a-dd3983d1a5b1.png)


![image](https://user-images.githubusercontent.com/97047640/172560294-59fc78c9-4149-4b4e-96b1-6a66412f91ab.png)


![image](https://user-images.githubusercontent.com/97047640/172560742-2bc7f135-7123-401e-9799-ddf4cfbb41ae.png)

![image](https://user-images.githubusercontent.com/97047640/172560821-cf00bdc5-8dba-497e-a466-0bc53b1106cb.png)























      
      
