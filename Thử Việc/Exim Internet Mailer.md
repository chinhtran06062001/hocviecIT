# Exim là gì ? 

Exim là một phần mềm chuyển thư điện tử (MTA) được sử dụng trên các hệ điều hành giống Unix. Exim là một phần mềm mã nguồn mở miễn phí được phân phối theo các điều khoản của Giấy phép Công cộng GNU.

Exim tương đối giống với Smail 3 nhưng các tính năng vượt trội hơn nhiều. Nó có tính linh hoạt trong cách thức gửi thư có thể được định tuyến và có nhiều phương tiện để kiểm tra thư đến. Exim có thể được cài đặt thay Sendmail mặc dù cấu hình của chúng khá khác nhau.

Dễ dàng quản lý qua dòng lệnh, dễ dàng loại bỏ hàng đợi thư. Nếu bất kỳ người dùng cụ thể nào gửi một lượng lớn email (spam), có thể dễ dàng tìm ra tài khoản đó và xoá chúng.

Vì nó là miễn phí nên hầu hết các Control Panel phổ biến hiện nay như DA, cPanel đều sử dụng Exim làm bộ chuyển tiếp Email.

## Hướng dẫn cài đặt Exim 

Để cài đặt Exim chúng ta phải thực hiện 2 bước sau :

**Bước 1 :** SSH vào hệ thống Để cài đặt Exim, việc đầu tiên chúng ta cần làm là SSH hoặc truy cập VPS hoặc máy chủ của bạn với quyền root trước.

Sau khi đã SSH thành công chúng ta tiếp tục với bước 2 để thực hiện các lệnh cài đặt Exim.

**Bước 2 :** Sau khi bạn đã SSH thành công ở bước 1, chúng ta sử dụng các lệnh sau để tiến hành cài đặt Exim.

```
cd /usr/local/directadmin(cpanel)/custombuild
./build set exim yes
./build exim
```

Giải thích các lệnh trên:

- Lệnh 1: Di chuyển vào thư mục Custombuild.
- Lệnh 2: Khai báo với Custombuild rằng chúng ta sẽ sử dụng Exim.
- Lệnh 3: Cài đặt Exim.

Sau khi cài xong các bạn có thể kiểm tra lại với lệnh sau để xem các port mà Exim sử dụng:

```
netstat -tulpn
```

Hình ảnh minh hoạ:

![image](https://user-images.githubusercontent.com/97047640/180832607-474cc039-7baf-4b6c-8398-8cf23caf514e.png)

Các Port dịch vụ Exim sử dụng.

Vậy là chúng ta đã hoàn tất việc cài đặt Exim 
