Thời gian trở lại đây, chúng tôi thường xuyên nhận được nhiều thông báo từ Khách hàng về lỗi Failed to retrieve directory listing khi họ dùng FileZilla kết nối FTP đến hosting, mặc dù các thông tin sử dụng của người dùng + cấu hình hệ thống trước giờ không thay đổi.

![image](https://github.com/chinhtran06062001/VietBai/assets/97047640/652e288c-93c7-4741-a0c2-e660def134f7)

Sau khi tìm hiểu với nhiều nguồn thông tin từ Khách hàng cũng như ngoài Internet, chúng tôi biết được rằng lỗi này chỉ phát sinh đối với FileZilla 3.10.x: do từ phiên bản này trở đi FileZilla cấu hình Encryption mặc định sử dụng FTP over TLS trong khi đến thời điểm hiện nay, đại đa số các nhà cung cấp dịch vụ Web-Hosting vẫn chưa hỗ trợ hoàn toàn FTPs.

![image](https://github.com/chinhtran06062001/VietBai/assets/97047640/f8c0200e-9186-4116-808a-fdb290cd4d34)

Để khắc phục vấn đề này, chúng ta có 2 giải pháp thực hiện:

# 1.Cài đặt và sử dụng các phiên bản thấp hơn (cũ hơn)

Các bạn download tại link http://sourceforge.net/projects/filezilla/files/FileZilla_Client/

# 2.Nếu bạn vẫn muốn sử dụng phiên bản 3.10.x.

Thay đổi cấu hình _Encryption_ thành **Only use plain FTP (insecure)**.

![image](https://github.com/chinhtran06062001/VietBai/assets/97047640/b2d9f845-3f45-4ee6-8a02-6ce03a91cc53)

Ngoài ra,bạn cũng có thể theo dõi thêm thông tin tại forum FileZilla.

Chúc bạn thành công!

![image](https://github.com/chinhtran06062001/VietBai/assets/97047640/b2d3d55e-ac9c-4de8-8ecd-af9397a13cfc)
