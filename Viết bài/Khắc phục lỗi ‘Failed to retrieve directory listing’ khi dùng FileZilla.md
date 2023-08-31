Thời gian trở lại đây, chúng tôi thường xuyên nhận được nhiều thông báo từ Khách hàng về lỗi Failed to retrieve directory listing khi họ dùng FileZilla kết nối FTP đến hosting, mặc dù các thông tin sử dụng của người dùng + cấu hình hệ thống trước giờ không thay đổi.

![image](https://github.com/chinhtran06062001/hocviecIT/assets/97047640/3ee45e21-529e-4648-a1c3-0dd662819775)

Sau khi tìm hiểu với nhiều nguồn thông tin từ Khách hàng cũng như ngoài Internet, chúng tôi biết được rằng lỗi này chỉ phát sinh đối với FileZilla 3.10.x: do từ phiên bản này trở đi FileZilla cấu hình Encryption mặc định sử dụng FTP over TLS trong khi đến thời điểm hiện nay, đại đa số các nhà cung cấp dịch vụ Web-Hosting vẫn chưa hỗ trợ hoàn toàn FTPs.

![image](https://github.com/chinhtran06062001/hocviecIT/assets/97047640/4bb2ce43-108f-4402-a4c8-4d8c46f2cc97)

Để khắc phục vấn đề này, chúng ta có 2 giải pháp thực hiện:

# 1.Cài đặt và sử dụng các phiên bản thấp hơn (cũ hơn)

Các bạn download tại link http://sourceforge.net/projects/filezilla/files/FileZilla_Client/

# 2.Nếu bạn vẫn muốn sử dụng phiên bản 3.10.x.

Thay đổi cấu hình _Encryption_ thành **Only use plain FTP (insecure)**.

![image](https://github.com/chinhtran06062001/hocviecIT/assets/97047640/ce944512-fbbe-4e75-a778-eceac206dcbc)

Ngoài ra,bạn cũng có thể theo dõi thêm thông tin tại forum FileZilla.

Chúc bạn thành công!

![image](https://github.com/chinhtran06062001/hocviecIT/assets/97047640/f8c93d58-a8c1-4bac-9474-1a2a0935e786)
