# Những cách import file sql vào sql server nhanh nhất, hiệu quả nhất

## Cách 1 : Sử dụng Detack - Attack Cơ sở dữ liệu

Bước 1 : Click chuột phải vài Database tiếp theo chọn Task - Detack

![image](https://user-images.githubusercontent.com/97047640/172792674-f4631180-5750-43fc-b88d-57a29fb443d2.png)


Bước 2 : Thực hiện sao chép 2 file Database

Thông thường 2 file nằm trong thư mục Data nên chúng ta truy cập theo đường dẫn sau : 

Chọn ổ C -> Program Files -> Microsoft SQL Server -> MSSQL15.SQLEXPRESS -> MSSQL -> DATA 

![image](https://user-images.githubusercontent.com/97047640/172794837-c22fea51-2b66-4880-8a9d-c279f473898c.png)

Bạn chỉ cần gửi 2 file này cho người mà bạn muốn chia sẻ, với 2 file đó họ đủ sức khôi phục lại dữ liệu trên máy tính không giống.

Bước 3 : Khôi phục dữ liệu trên máy tính khác 

Sau khi người nhận đã nhận được 2 file đã chia sẻ , bạn dán 2 file vào đường link :

ổ C -> Program Files -> Microsoft SQL Server -> MSSQL15.CHINHTRAN -> MSSQL -> DATA 

thực hiện paste xong tiếp theo chúng ta tiến hành attack lại database bằng cách :

Click chuột phải vào Database chọn Attack tiếp đến chọn Add -> Chọn Database -> OK -> OK

![image](https://user-images.githubusercontent.com/97047640/172795007-995e653d-6d36-4d50-b0a7-b464975149ba.png)

![image](https://user-images.githubusercontent.com/97047640/172795519-7bb70ecd-0ad7-45a6-98ee-277b8420b3bc.png)

Sau khi thực hiện xong các bạn sẽ thấy Database vừa mưới thêm hiển thị ở phần Data . Nếu nó chưa hiện thì hay Refresh lại để thấy phần Database vừa mới có trong SQL.

![image](https://user-images.githubusercontent.com/97047640/172795587-e4773201-d167-4f97-bc91-b69f6783fc23.png)

# Cách 2 : Xuất File SQL 

Bước 1 : Click chuột phải vào Database chọn Task - Chọn Generate Scripts :

![image](https://user-images.githubusercontent.com/97047640/172796051-c78f2893-0022-4fde-b7f4-78967122f0d8.png)

Bước 2 Nhấn Next để tiếp tục quá trình 

![image](https://user-images.githubusercontent.com/97047640/172798010-6d3344d2-754a-4ff3-8f9b-060065339a60.png)

Bước 3 : Chọn 1 số Table hoặc chọn lựa tất cả

![image](https://user-images.githubusercontent.com/97047640/172798073-6bfaaafb-1829-4fbc-8b86-c75017e3ab50.png)

Bước 4 : Để có thể xuất file .sql kèm thêm dữ liệu thì cần phải thực hiện các thao tác như sau :

Advanced - Types of data no script chọn Schema and data - OK - Next 

![image](https://user-images.githubusercontent.com/97047640/172799032-c766d8c7-898e-44ee-9a7a-d706c733d394.png)

Bước 5 : Bấm next để tiếp tục 

![image](https://user-images.githubusercontent.com/97047640/172799488-d9984a15-8a64-4ff6-bd7f-2e6051f23db1.png)

![image](https://user-images.githubusercontent.com/97047640/172799773-390bc1d3-ca14-4a13-a3ed-be470cdb45f3.png)


Bước 6 : Kiểm tra tình trạng xuất file và bấm Finish để hoàn thành công cuộc xuất file chinhtran.sql

![image](https://user-images.githubusercontent.com/97047640/172800407-9d89ef94-1717-4f70-adc0-6158077f090e.png)

Sau khi thành công 6 bước chúng ta sẽ thấy file chinhtran.sql nằm trong đường dẫn : C:\Users\vip\Documents\chinhtran.sql

![image](https://user-images.githubusercontent.com/97047640/172800534-963388b1-9c15-4fcd-a4d7-2eadb576a5bf.png)

## Cách dùng file chinhtran.sql

Bước 1 : mở SQL Server lên chọn vào File - Open - File 

![image](https://user-images.githubusercontent.com/97047640/172800772-5f69b2ee-fdce-4866-a9b5-935feb3b69c6.png)

Bước 2 : Chọn file chinhtran.sql để mở lên trong SQL Server 

*Lưu ý : Cần tạo 1 Database giống với tên database cũ để chứa dữ liệu chuẩn bị nhập vào .

Bước 3 : Lự chọn tất cả các câu lệnh và nhấn Execute. Kết quả sẽ hiện ra thông báo : Command (s) completed successfully. Open Database Chinhtran ra sẽ thấy được toàn bộ các bảng và dữ liệu mà chúng ta cần.

![image](https://user-images.githubusercontent.com/97047640/172801833-805ff96c-8ddb-44fc-9b24-053ad297549e.png)



