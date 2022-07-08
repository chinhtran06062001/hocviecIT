# Lỗ hổng bảo mật trong Mail Server Zimbra

1. Lỗ hổng đầu tiên có mã là CVE-2021-35208: Cross-Site Scripting (Lỗ hổng XSS nằm trong ZmMailMsgView.java). Khi người dùng mở email trên trình duyệt web, họ có thể sẽ kích hoạt đoạn mã JavaScript, cho phép hacker truy cập và sử dụng mọi tính năng như người chủ sở hữu thực sự.

Các lỗ hổng XSS thường rất phổ biến ở các phần mềm bảo mật, do có nhiều loại máy khách front-end cho web và di động, cũng như các hệ điều hành khác nhau. Hacker sẽ thường xuyên khai thác các lỗ hổng XSS để có được các phiên truy cập hợp lệ.

Dù Zimbra vẫn tuân thủ các tiêu chí bảo mật OWASP kỹ lưỡng. Nhưng một trong những giao diện người dùng của Zimbra đã gây ra sự cố XSS lần này.

2. Lỗ hổng thứ hai có mã là CVE-2021-35209: Hacker có khả năng xâm nhập vào Server-Side Request Forgery (SSRF) của hệ thống. Lỗ hổng SSRF có thể giúp hacker điều khiển mail server thực hiện các yêu cầu của chúng như: truy cập vào các dịch vụ mạng nội bộ như cơ sở dữ liệu, trang quản trị và các dịch vụ nội bộ khác.

Các lỗ hổng SSRF đang ngày càng được các hacker tận dụng để làm bàn đạp xâm nhập vào bên trong hệ thống của doanh nghiệp.

Nếu 2 lỗ hổng này kết hợp cùng lúc, hacker có thể trích xuất Google Cloud API Tokens hoặc chứng chỉ AWS IAM.

Các nhà nghiên cứu đã chỉ ra rằng: các lỗ hổng Zimbra XSS và CSRF có thể được hacker liên kết khá dễ dàng, điều này bắt buộc Zimbra phải nâng cao hệ thống bảo mật email của họ một cách thường xuyên và triệt để hơn.

# Cách Bảo mật Email và Bảo vệ doanh nghiệp 

1. Xác minh và mã hoá các email quan trọng

Việc mã hoá nội dung email là bước quan trọng cho những email cần độ bảo mật cao. Bạn có thể cần đến một phần mềm chuyên nghiệp để ngăn chặn hacker đánh cắp dữ liệu của mình.

2. Lưu ý khi chọn sử dụng các dịch vụ

Hãy trang bị hệ thống tường lửa email cho doanh nghiệp để đảm bảo tên miền đã được gắn mã hoá bảo mật SSL.

3. Sử dụng công cụ lọc Mail

Các công cụ quét lọc nội dung email sẽ rất hữu ích cho vấn đề bảo mật email doanh nghiệp.

Thị trường hiện nay có một số công cụ lọc mail miễn phí, giúp doanh nghiệp kiểm tra các mối đe dọa và tìm ra các email thường xuyên gặp rủi ro nhiều nhất.

4. Chọn tường lửa bảo mật Email thông minh

Các loại tường lửa email ứng dụng công nghệ AI và Machine Learning có khả năng phân tích và kiểm soát toàn bộ luồng email bên trong hệ thống. Chúng có thể đảm bảo sự an toàn tối đa cho mọi hoạt động giao dịch tài chính của doanh nghiệp.

5. Thêm bản ghi nhằm tăng độ tin cậy

Bước 1 : Truy cập công cụ postmaster theo đường dẫn https://postmaster.google.com/managedomains?pli=1

Bước 2 : Đăng nhập tên miền vào 

![image](https://user-images.githubusercontent.com/97047640/175460009-cd4232fb-2040-4bf6-8cf1-06dd9fbd61ad.png)

Thêm các bản ghi CName cũng như TXT yêu cầu vào 

![image](https://user-images.githubusercontent.com/97047640/175461368-2fbde10a-f5fe-4a8f-97e5-51afa70e7524.png)

![image](https://user-images.githubusercontent.com/97047640/175461334-73900ff5-b972-4ae8-89a5-bffff057b3b6.png)

![image](https://user-images.githubusercontent.com/97047640/175461444-e9c85652-4134-4083-a828-0cbc9e94b631.png)
