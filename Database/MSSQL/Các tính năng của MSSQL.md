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

