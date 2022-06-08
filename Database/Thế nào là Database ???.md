# SQL là gì?

![image](https://user-images.githubusercontent.com/97047640/172563598-db92ad60-971b-4f95-ac5a-19d7931303c1.png)

SQL là viết tắt của cụm từ tiếng anh “Structured Query Language”, tạm dịch là ngôn ngữ truy vấn có cấu trúc. Có nghĩa là SQL chỉ làm việc với những dữ liệu có cấu trúc dạng bảng (table) như của Foxpro, DBase, Access… Nếu bạn chỉ làm việc với các tệp dữ liệu dạng văn bản như của Winword, hay các ảnh, âm thanh… thì bạn không thể ứng dụng SQL được.

Đối tượng của SQL là các bảng dữ liệu và các bảng này bao gồm nhiều cột và hàng. Cột được gọi là trường và hàng là bản ghi của bảng. Cột với tên gọi và kiểu dữ liệu xác định tạo nên cấu trúc của bảng. Khi bảng được tổ chức có hệ thống cho một mục đích, công việc nào đó ta có một CSDL.

## Một số công dụng chính của SQL

![image](https://user-images.githubusercontent.com/97047640/172563745-c709d967-083d-4934-97ef-9b956140cdde.png)

- Chọn lọc một số cột nhất định trong bảng dữ liệu: Thường ta không sử dụng tất cả các thông tin của bảng cùng một lúc. Có thể dùng SQL để tách ra chỉ những cột cần thiết mà thôi.
- Lọc các bản ghi theo những tiêu chuẩn khác nhau: như tách riêng các hoá đơn của một khách hàng nào đó, hay in danh sách nhân viên chỉ của một vài phòng ban…
- Sắp xếp các bản ghi theo những tiêu chuẩn khác nhau: Mỗi loại báo cáo thường có yêu cầu sắp xếp các bản ghi theo những cột khác nhau để tiện cho việc theo dõi. Có báo cáo thống kê sắp xếp theo khách hàng, báo cáo khác lại sắp xếp theo mặt hàng được bán, mặc dù tất cả thông tin nằm trong cùng một bảng Bán hàng. Ta có thể thực hiện sắp xếp theo một hoặc nhiều cột khác nhau bằng SQL. Cập nhật, xoá các bản ghi trên toàn bảng theo những điều kiện khác nhau: ví dụ như khi cần xoá toàn bộ các hoá đơn đã phát hành cách đây 5 năm…
- Kết hợp hai hay nhiều bảng theo chiều ngang: Trong CSDL, mỗi bảng lưu trữ thông tin về một đối tượng và các bảng liên hệ với nhau qua các trường khoá. Dùng SQL để thực hiện việc kết hợp các bảng này với nhau thông qua các trường khoá như ở ví dụ trên để có được bảng kết quả theo yêu cầu.
- Nối hai hay nhiều bảng theo chiều dọc: khi dữ liệu rất lớn hoặc phân tán ở nhiều nơi ta có thể phải quản lý nhiều bảng theo cùng một mẫu, như mỗi bảng cho một quý, tháng hoặc một công ty. Khi cần tổng hợp dữ liệu của cả năm hoặc của cả tổng công ty ta có thể dùng SQL để nối các bảng lại với nhau.
- Tạo bảng mới, thay đổi cấu trúc bảng đã có: phục vụ cho việc lập trình.
- Thực hiện các phép tính toán thống kê theo từng nhóm: tổng, trung bình, max, min… Đây là chức năng thường xuyên được sử dụng để tổng hợp thông tin trước khi in báo cáo như tính tổng số lượng của từng mặt hàng, số hàng đã bán cho từng khách hàng…
- Kết nối với dữ liệu trên máy chủ (Server): Khi kho dữ liệu được tập trung trên máy chủ trong MS SQL Server hay Oracle … ta phải dùng lệnh SQL để trực tiếp thâm nhập vào cơ sở dữ liệu.
- Kết hợp các trang Web với CSDL bằng lệnh SQL. Có thể phân ra hai loại câu lệnh SQL, một loại tổng hợp dữ liệu sang bảng mới (bảng mới có thể chỉ tồn tại trong bộ nhớ hoặc được ghi ra đĩa) và một loại chỉ cập nhật dữ liệu, cấu trúc của các bảng đã có. Bảng mới được tạo ra từ câu lệnh SQL có thể được sử dụng ở mọi nơi trong chương trình có yêu cầu dữ liệu dạng bảng, đặc biệt dùng cho báo cáo (report), danh sách (list), đối tượng lưới (grid)…

## 50 câu hỏi & đáp về SQL

|STT|	Câu hỏi|Câu trả lời|
|-----------|-----------|-----------|
|1	|SQL là gì?|	SQL là viết tắt của Structured Query Language – ngôn ngữ truy vấn mang tính cấu trúc. Nó được thiết kế để quản lý dữ liệu trong một hệ thống quản lý cơ sở dữ liệu quan hệ (RDBMS). SQL là ngôn ngữ cơ sở dữ liệu, được dùng để tạo, xóa, lấy các hàng và sửa đổi các hàng.|
|2	|Làm thế nào để chọn tất cả bản ghi từ table?|	Sử dụng cú pháp sau: Select * from table_name;|
|3	|Định nghĩa JOIN và các loại JOIN khác nhau?|	Từ khóa JOIN được sử dụng để nạp dữ liệu từ hai hay nhiều bảng liên quan. Khi cần truy vấn các cột dữ liệu từ nhiều bảng khác nhau để trả về trong cùng một tập kết quả, cần sử dụng từ khóa “JOIN”
Loại JOIN là –
INNER JOIN (Hoặc JOIN)
LEFT OUTER JOIN (Hoặc LEFT JOIN)
RIGHT OUTER JOIN (Hoặc RIGHT JOIN)
FULL OUTER JOIN (Hoặc OUTER JOIN)
CROSS JOIN
SELF JOIN|
|4	|Cú pháp để thêm bản ghi vào một bảng là gì?|	Để thêm bản ghi trong một bảng cú pháp INSERT được sử dụng.
Ví dụ:INSERT into table_name VALUES (value1, value2..);|
|5	|Làm thế nào để bạn thêm một cột vào một bảng?|	Để thêm một cột khác trong bảng sử dụng lệnh.
ALTER TABLE table_name ADD (column_name);|
|6	|Xác định câu lệnh Delete SQL.|	Xóa được sử dụng để xóa hàng hoặc các hàng từ một bảng dựa trên điều kiện được chỉ định. Cú pháp cơ bản như sau:
DELETE FROM table_name <br> WHERE <Condition>|
|7	|Xác định COMMIT?|	COMMIT lưu tất cả các thay đổi được thực hiện bởi các câu lệnh DML.
DML cho phép thực thi các câu truy vấn, bao gồm cú pháp để cập nhật – sửa đổi, chèn thêm và xoá các mẩu tin.|
|8	|Khóa chính (PRIMARY KEY ) là gì?|	Khóa chính là cột có các giá trị xác định duy nhất mỗi hàng trong một bảng. Giá trị khóa chính không bao giờ được sử dụng lại.
Một cột là PRIMARY KEY thì không được phép có giá trị NULL.
Một bảng chỉ cho phép tối đa một PRIMARY KEY.
Mỗi bảng đều cần có khóa chính.|
|9	|Khóa ngoại (Foreign key) là gì?|	Khi một trường khoá chính của một bảng được thêm vào các bảng có liên quan để tạo ra trường phổ biến có liên quan đến hai bảng, nó được gọi là khoá ngoại trong các bảng khác. Các ràng buộc khóa ngoại thực thi toàn vẹn tham chiếu.|
|10|	CHECK Constraint – Ràng buộc CHECK là gì?|	Một ràng buộc CHECK được sử dụng để giới hạn các giá trị hoặc loại dữ liệu có thể được lưu trữ trong một cột. Nếu bản ghi không đáp ứng được điều kiện này, thì sẽ không được lưu trữ vào trong bảng|
|11|	Một bảng có thể có nhiều hơn một khoá ngoại?|	Đúng, một bảng có thể có nhiều khóa ngoài và chỉ có một khóa chính.|
|12|	Trường dữ liệu BOOLEAN có giá trị nào?|	Đối với trường dữ liệu BOOLEAN, có hai giá trị: -1 (TRUE) và 0 (FALSE).|
|13|	Thủ tục lưu trữ (stored procedure) là gì?|	Một thủ tục lưu trữ là một tập hợp các truy vấn SQL có thể lấy đầu vào và gửi lại đầu ra.|
|14|	IDENTITY trong SQL là gì?|	Một cột IDENTITY trong SQL sẽ tự động sinh ra các giá trị số tự tăng. Có thể định nghĩa giá trị bắt đầu và gia tăng của cột nhận dạng.|
|15|	NORMALIZATION – Chuẩn hóa trong sql là gì?|	Quá trình thiết kế bảng để giảm thiểu sự thừa số liệu được gọi là chuẩn hóa. Chúng ta cần phải chia một cơ sở dữ liệu thành hai hay nhiều bảng và xác định các mối quan hệ giữa chúng.|
|16|	Trigger là gì ?|	Trigger là một thủ tục dược thực thi từ phía máy chủ CSDL khi một sự kiện bảng xảy ra (Chèn, cập nhật hoặc xóa lệnh thực hiện đối với một bảng cụ thể) .|
|17|	Làm thế nào để lấy ra các hàng ngẫu nhiên từ một bảng?|Sử dụng mệnh đề SAMPLE chúng ta có thể chọn các hàng ngẫu nhiên.
Ví dụ:
SELECT * FROM table_name SAMPLE (10);|
|18|	Cổng TCP/IP nào mà SQL Server chạy?|	Mặc định SQL Server chạy trên cổng 1433.|
|19|	Viết một truy vấn SELECT SQL mà trả về mỗi bản ghi chỉ một lần từ một bảng?	|Để có được mỗi tên một lần duy nhất, chúng ta cần phải sử dụng từ khoá DISTINCT.
SELECT DISTINCT name FROM table_name;|
|20|	DML và DDL trong sql là gì?|	DML là viết tắt của Ngôn ngữ Thao tác Dữ liệu ( Data Manipulation Language): INSERT, UPDATE và DELETE là các câu lệnh DML.
DDL là viết tắt của Ngôn ngữ Định nghĩa Dữ liệu (Data Definition Language): CREATE, ALTER, DROP, RENAME là các câu lệnh DDL.|
|21|	Lệnh nào để đổi tên một cột trong đầu ra của truy vấn SQL?|	Có sử dụng cú pháp sau đây.:
SELECT column_name AS new_name FROM table_name;|
|22|	Thứ tự của SQL SELECT?|	Thứ tự các mệnh đề SQL SELECT là: SELECT, FROM, WHERE, GROUP BY, HAVING, ORDER BY. Trong đó SELECT và FROM là bắt buộc|
|23|	Giả sử một cột Student có hai cột, Name và Marks. Làm thế nào để có được Name và Marks của ba sinh viên top đầu.|	SELECT Name, Marks FROM Student s1 where 3 <= (SELECT COUNT(*) FROM Students s2 WHERE s1.marks = s2.marks)|
|24|	SQL comments là gì?|	Khi muốn ghi chú thích vào câu truy vấn SQL, để làm cho câu truy vấn ấy trở nên rõ ràng và dễ hiểu hơn, thì sử dụng SQL comment.
SQL comments có thể được đặt bởi hai dấu nối liên tiếp (-) hoặc /* …. */
Khi câu truy vấn được thực thi thì trình biên dịch sẽ tự động bỏ qua những dòng có comment.|
|25|	Sự khác biệt giữa các lệnh TRUNCATE, DELETE và DROP?|	DELETE xóa một hoặc tất cả các hàng từ một bảng dựa trên điều kiện và có thể được phục hồi lại.
TRUNCATE xóa tất cả các hàng từ một bảng bằng cách phân bổ các trang bộ nhớ và không thể phục hồi lại
DROP xóa hoàn toàn một bảng từ cơ sở dữ liệu.|
|26|	Các thuộc tính của một giao dịch là gì?|	Nói chung các thuộc tính này được gọi là thuộc tính ACID bao gồm:
Tính nguyên tử (Atomicity)
Tính nhất quán (Consistency)
Cô lập (Isolation)
Độ bền (Durability).|
|27|	ROWID nghĩa là gì?|	Đó là một cột giả dài 18 ký tự gắn liền với mỗi hàng của một bảng.|
|28|	Xác định UNION, MINUS, UNION ALL, INTERSECT?|	MINUS – sử dụng để kết hợp 2 câu lệnh SELECT, nó trả về tất cả các bản ghi chỉ thuộc vào bảng của câu truy vấn SELECT đầu tiên, những bản ghi giao nhau và những bản ghi của câu truy vấn SELECT thứ 2 thì không được lấy vào kết quả..
UNION – Bạn viết hai hay nhiều câu truy vấn SELECT khác nhau nhưng bạn muốn nó trả về một danh sách kết quả duy nhất thì bạn phải sử dụng toán tử UNION
UNION ALL – trả về tất cả các hàng được chọn bởi một trong hai truy vấn, giữ lại các kết quả trùng
INTERSECT – lấy ra những bản ghi nào mà nó hiện diện ở trong cả 2 bảng (có trong bảng này và cũng có trong bảng kia)|
|29|	Giao dịch ( transaction) là gì?|	Một giao dịch là một dãy mã chạy trên cơ sở dữ liệu. Cần có cơ sở dữ liệu từ một trạng thái nhất quán sang trạng thái khác.|
|30|	Sự khác nhau giữa UNIQUE và PRIMARY KEY constraints là gì?|	Một bảng có thể chỉ có một PRIMARY KEY và có thể không có hoặc có mộ hay nhiều UNIQUE keys.
PRIMARY KEY không thể chứa giá trị Null , UNIQUE có thể chứa giá trị Null.|
|31|	Khóa tổng hợp (Composite primary key) là gì?|	Khóa chính được tạo trên nhiều cột được gọi là khóa chính tổng hợp.|
|32|	Index là gì?|	Index (Chỉ mục) là bảng tra cứu đặc biệt mà Database Search Engine có thể sử dụng để tăng nhanh thời gian và hiệu suất thực hiện các truy vấn.
Index có thể được tạo ra trên một hoặc nhiều cột của một bảng|
|33|	Subquery là gì?|	Truy vấn con (còn được gọi truy vấn phụ hay truy vấn lồng nhau) là một truy vấn bên trong truy vấn SQL khác và được nhúng bên trong mệnh đề WHERE.|
|34|	Tối ưu hoá truy vấn là gì?|	Tối ưu hóa truy vấn là một quá trình trong đó hệ thống cơ sở dữ liệu so sánh các chiến lược truy vấn khác nhau và chọn truy vấn với chi phí thấp nhất.|
|35|	Collation là gì?|	Bộ quy tắc định nghĩa cách dữ liệu được lưu trữ, cách phân biệt chữ hoa chữ thường và ký tự Kana có thể được xử lý như thế nào.|
|36|	Tính toàn vẹn tham chiếu là gì?|	Tập các quy tắc hạn chế các giá trị của một hoặc nhiều cột của các bảng dựa trên các giá trị của khóa chính hoặc khóa duy nhất của bảng tham chiếu.|
|37|	Hàm Case là gì?|	Trường hợp tạo điều kiện logic kiểu if-then-else trong SQL. Nó đánh giá một danh sách các điều kiện và trả về một trong nhiều biểu thức kết quả tốt.|
|38|	Xác định một bảng tạm thời?	|Một bảng tạm là một cấu trúc lưu trữ tạm thời để lưu trữ dữ liệu tạm thời.|
|39|	Làm thế nào chúng ta có thể tránh trùng lặp hồ sơ trong một truy vấn?|	Bằng cách sử dụng từ khoá DISTINCT sao chép hồ sơ trong một truy vấn có thể tránh được.|
|40|	Giải thích sự khác nhau giữa Đổi tên (Rename) và Bí danh (Alias)?|	Đổi tên là một tên thường xuyên cho một bảng hoặc cột
Bí danh là tên tạm thời cho một bảng hoặc cột.|
|41|	View là gì?|	Một khung nhìn là một bảng ảo chứa dữ liệu từ một hoặc nhiều bảng. Lượt xem hạn chế quyền truy cập dữ liệu của bảng bằng cách chỉ chọn các giá trị được yêu cầu và thực hiện các truy vấn phức tạp một cách dễ dàng|
|42|	Lợi ích của Views là gì?|	Ưu điểm của Views:
Chế độ xem hạn chế quyền truy cập vào dữ liệu vì chế độ xem có thể hiển thị các cột được chọn từ bảng.
Có thể sử dụng chế độ xem để truy vấn các kết quả tìm kiếm phức tạp. Ví dụ: chế độ xem có thể được sử dụng để truy vấn thông tin từ nhiều bảng mà không có sự hiểu biết của người dùng.|
|43|	Liệt kê các đặc quyền khác nhau mà người dùng có thể cấp cho người dùng khác?|	SELECT, CONNECT, RESOURCES.|
|44|	Schema trong sql là gì?|	Lược đồ là tập hợp các đối tượng cơ sở dữ liệu của Người dùng.|
|45|	Bảng trong sql là gì?|	Một bảng là đơn vị cơ bản của lưu trữ dữ liệu trong hệ thống quản lý cơ sở dữ liệu. Dữ liệu bảng được lưu trữ trong hàng và cột.|
|46|	Chế độ xem (View) có chứa dữ liệu không?|	Không, View là cấu trúc ảo.|
|47|	Chế độ xem có thể dựa trên chế độ xem khác không?|	Chế độ xem dựa trên một Chế độ xem khác.|
|48|	Sự khác biệt giữa mệnh đề Having và mệnh đề Where?|	Cả hai đều chỉ định điều kiện tìm kiếm nhưng mệnh đề Having chỉ được sử dụng với câu lệnh SELECT và thường được sử dụng với mệnh đề GROUP BY. Nếu mệnh đề GROUP BY không được sử dụng thì Havingn sử dụng giống như mệnh đề WHERE.|
|49|	Sự khác nhau giữa bảng tạm cục bộ (Local) và bảng tạm toàn cầu (Global) là gì?|	Nếu được định nghĩa bên trong câu lệnh hợp chất,
Một bảng tạm thời cục bộ tồn tại trong 1 kết nối. Khi kết thúc kết nối thì bảng tạm này sẽ tự động được xóa. Tên của bảng tạm kiểu Local được bắt đầu bằng ký tử #
Một bảng tạm thời toàn cầu tồn tại vĩnh viễn trong db nhưng các hàng của nó biến mất khi kết nối được đóng lại. Tên bảng tạm kiểu Global được bắt đầu bằng ##.|
|50|	CTE trong sql là gì?|	Biểu thức bảng CTE ( Common Table Expression) hoặc bảng chung là một biểu thức có chứa tập kết quả tạm thời được định nghĩa trong câu lệnh SQL|
