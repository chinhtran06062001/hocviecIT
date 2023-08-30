# 1. Đường truyền: 

Một trong các tiêu chí đầu tiên phải đề cập đến là tốc độ đường truyền của bạn. Đảm bảo rằng đường truyền của bạn ở mức tốt nhất, điều kiện lý tưởng đường truyền chuẩn đạt tốc độ download là 20 – 30 Mbps (tương đương 2.5MB/s – 3.75MB/s). 

Để kiểm tra, bạn có thể truy cập vào link: https://www.speedtest.net/ và ấn vào nút GO

![image](https://github.com/chinhtran06062001/hocviecIT/assets/97047640/f1ba25c7-afcf-4df9-819c-375f8d9932f8)

Tốc độ đường truyền của bạn sẽ được thể hiện ở mục DOWNLOAD và UPLOAD.

![image](https://github.com/chinhtran06062001/hocviecIT/assets/97047640/7eddb780-ae22-4e07-a4af-13214c4e4bfc)

# 2. Bố cục website: 

– Dựa vào Lighthouse và Google PageSpeed Insights số DOM khuyến nghị cho 1 website như sau: 

+ Có tổng số nút (nodes) không vượt quá 1500 nút (nodes).   

+ Có độ sâu (node-depth) không quá 32 nút (nodes). Cac 

+ Một nút chính (parent node) có số nút con (child nodes) không quá 60 nút (nodes).

![image](https://github.com/chinhtran06062001/hocviecIT/assets/97047640/2b4e84b1-703e-4a99-bea9-c37f34018e04)

Công cụ để kiểm tra: PageSpeed Insights.

Hướng dẫn chi tiết xem tại đây.

# 3. Hình ảnh và video: 

– Hình ảnh trên website cần được nén và dùng các định dạng phù hợp như Webp  

– Để đảm bảo tốc độ tải trang tốt nhất, dung lượng của một hình ảnh tải lên website nên được tối ưu trong khoảng 70kb – 200kb. 

– Các định dạng hình ảnh nên dùng như WebP và AVIF thường nén tốt hơn so với các định dạng PNG hoặc JPEG. 

![image](https://github.com/chinhtran06062001/hocviecIT/assets/97047640/da979d9c-99d8-4bdc-821d-64fda9648c18)

– Ngoài ra cần kết hợp trì hoãn tải (Lazy Load) các hình ảnh trên trang web. 

![image](https://github.com/chinhtran06062001/hocviecIT/assets/97047640/2b938343-b4f7-4dfe-b614-5f5583e4000c)

– Sử dụng video từ nguồn ngoài hosting, chẳng hạn video từ Youtube và Vimeo để thay thế video tải lên Website. 

Công cụ để kiểm tra: PageSpeed Insights.
Hướng dẫn chi tiết xem tại đây.

# 4. Tối ưu các tệp tin tài nguyên: 

– Cần đảm bảo rằng các tài nguyên HTML/CSS/JS trên website của bạn đã được tối ưu bằng các thủ thuật như:  

+ Tránh chèn hoặc nhúng code CSS/JS vào file HTML. 

+ Nén GZIP. 

+ Nối (gộp) các file css/js lại với nhau. 

+ Tải CSS trước JS. 

+ Sử dụng các kĩ thuật tải không đồng bộ. 

+ Loại bỏ các CSS/JS không dùng trên trang web. 

+ Sử dụng bộ nhớ đệm (cache) cho trang web. 

Công cụ để kiểm tra: PageSpeed Insights.

Hướng dẫn chi tiết xem tại đây.

# 5. Tối ưu hosting/máy chủ: 

– Cần sử dụng hosting có cấu hình (CPU/RAM) phù hợp với website, khả năng chịu tải đáp ứng được lượng truy cập từ người dùng. 

– Không sử dụng các phiên bản PHP quá cũ (dưới 5.6). 

– Trang bị ổ cứng lưu trữ SSD. 

– Tối ưu dung lượng của database xuống dưới 1 GB. 

