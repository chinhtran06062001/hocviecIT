# Cài đặt chương trình theo tên 

- Nếu Exim được gọi tên là *mailq* thì thể tuỳ chọn -bp có trước bắt kỳ lệnh nào. 
- Tuỳ chọn -bp yêu cầu liệt kê hàng đợi mail trên standard output.
- Có tác dụng tương thích với một số hệ thống chứa lệnh có tên đó với liên kết là `/usr/sbin/sendmail` hoặc `/usr/lib/sendmail`
- Nếu Exim được gọi dưới tên *rsmtp* thì thể -bS được sử dụng để tương thích với các tuỳ chọn và tương thích với Smail. Nó được sử dụng để đọc một số thư ở định dạng SMTP theo từng đợt.
- Nếu Exim được gọi là *rmail*, lúc đó các thể -i và -oee được đặt trước các tùy chọn khác, nhằm tương thích với Smail. *Rmail* được một số hệ thống UUCP sử dụng làm giao diện.
- Nếu được gọi là *runq*, thể -q có trước các tùy chọn khác. Nó khiến một quá trình hàng đợi bắt đầu.
- Nếu được gọi là *newaliases*, tùy chọn -bi hoạt động trước bất kỳ tùy chọn nào khác. Nó được sử dụng để xây dựng lại Alias của Sendmail. Exim không có khái niệm một alias duy nhất, nhưng có thể cấu hình chạy được một lệnh nhất định nếu sử dụng tùy chọn -bi.

# Trusted User Exim (Người dùng đáng tin cậy) và Admin Exim (Quản trị viên)

Một số chức năng Exim chỉ có sẵn cho Trusted User và một số thì chỉ dùng được cho User Exim. 
