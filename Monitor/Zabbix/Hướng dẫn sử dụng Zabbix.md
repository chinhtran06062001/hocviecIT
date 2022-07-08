# Hướng dẫn thao tác trên Dashboard zabbix #

Đây là giao diện tổng quan khi cài đặt zabbix thành công. Gồm nhiều mục lớn như Monitoring, Inventory, Reports, Configuration, Administrator. Trong các tab lớn sẽ bao gồm nhiều task thành phần nhỏ hơn.

![image](https://user-images.githubusercontent.com/97047640/177247051-3c791b14-2673-4ad7-90e9-5bbf05283cef.png)


## 1. Tab Monitoring ##


![image](https://user-images.githubusercontent.com/97047640/177248207-a03df9ff-3310-4430-ae0f-5f68030f77b0.png)

**1.1. Dashboard**

**Dashboard**: Là giao diện hiển thị các dashboard trực quan để người quản trị nhìn trực tiếp, người quản trị có thể tạo ra rất nhiều các dashboard khác nhau, nhưng tại một tab screen chỉ có thể xem được 1 dashboard bất kỳ nào đó.

Từ Dashboard có thể nhanh chống liên kết đến các thành phần như Graphs, Screens, Map bằng cách thêm các thành phần mong muốn vào mục Favourite graphs, Favourite Screen và Favourite map.

![image](https://user-images.githubusercontent.com/97047640/177248288-b7a38156-a6e6-4df9-9d32-f640dc83ccd2.png)

Gồm nhiều phần hiển thị nhỏ hơn:

+ Status of Zabbix

Bảng này hiển thị trạng thái của zabbix server, số lượng các host, trigger, item, số người đang đăng nhập và trạng thái của các thông số trên ở 2 cột value và Details

![image](https://user-images.githubusercontent.com/97047640/177248630-2b4bd1a4-6fc2-4f36-b5f4-93c4e1aedf16.png)

+ System status: Hiển thị mức độ cảnh báo của từ host trong từng group

![image](https://user-images.githubusercontent.com/97047640/177249150-9ae3d306-bc2b-420c-b9e0-9594630d7526.png)

+ Problems: Tất cả các vấn đề xảy ra với các host trong các group thống kê theo thời gian.

![image](https://user-images.githubusercontent.com/97047640/177249228-81f529be-5d4b-4488-bee7-741facef91a9.png)

Có thể tùy chỉnh add thêm những gì muốn hiển thị theo ý muốn tương ứng với từng mục.

+ Đối với mỗi bảng có thể tùy chỉnh thờ gian interval để update lại data

Click vào dấu ... nhỏ để cấu hình như ở dưới

![image](https://user-images.githubusercontent.com/97047640/177250704-6c3ba6a1-bd7e-400d-ab60-831091f07f04.png)

**1.2. Problems**

+Problems: Hiển thị các vấn đề đối với từng device mà zabbix server thu thập dữ liệu về. Hỗ trợ cơ chế lọc theo ý người quản trị.

![image](https://user-images.githubusercontent.com/97047640/177250862-2464ecfc-1440-4d81-a3ca-4e10d435178a.png)

+ Có thể lọc theo các tiêu chí sau và có thể export ra file csv để lưu trữ lại.

![](https://i.imgur.com/3LHKazf.png)

Show: Recent problems (Hiển thị vấn đề hiện tại đang gặp phải), Problems (Hiển thị các vấn đề đã gặp phải), History (Lịch sử các vấn đề đã gặp phải).

Host group, Host, Application, Trigger, Problem, Host inventory, Tags, Show hosts in maintenance... là các lựa chọn để lọc thông tin, có thể lọc theo một tiêu chí hoặc kết hợp nhiều tiêu chí.
 
**1.3. Overview**

+Overview: Là sự tổng hợp thông tin về data zabbix zerver thu thập được, có thể lọc them group -> host -> Kiểu data.

![image](https://user-images.githubusercontent.com/97047640/177251319-21abacc9-f278-4aaa-aaae-8f81eac46564.png)

**1.4. Latest data**

+Latest data: Dữ liệu mới nhất mà zabbix server thu thập được.

![image](https://user-images.githubusercontent.com/97047640/177251739-3ad974d0-47c2-407f-9db7-af75fc6081cd.png)

**1.5. Screen**

+Screen: Là tập hợp các thông tin như Graphs, maps,data overview… vào chung một màn hình giám sát. Giúp người quản trị có thể lựa chọn các thông tin cần thiết hiển thị, giúp có cái nhìn tổng quát những thông tin mà người quản trọ mong muốn.

![image](https://user-images.githubusercontent.com/97047640/177290709-7179bef9-7843-41c8-9b88-0aab8feeca98.png)

**1.6. Maps**

+Maps: Là thành phân cung cấp khả năng giám sát hệ thống dưới hình thức mô hình mạng. Giúp người quản trị có cái nhìn tổng quan về hệ thống sống mạng dưới dạng sơ đồ, trong trường hợp có sự cố sẽ giúp người quản trị đánh giá tầm ảnh hưởng của thiết bị gặp sự cố và đưa ra giải pháp phù hợp.

![image](https://user-images.githubusercontent.com/97047640/177291002-452bc37b-8b45-42c8-8830-265024cc8868.png)

**1.7. Discovery**

+Discovery: Tính năng cho phép zabbix server tự động tìm kiếm các thiết bị được cài đặt zabbix agent đã cấu hình kết nối về zabbix server trong cùng mạng với zabbix server.

![image](https://user-images.githubusercontent.com/97047640/177291176-b9a24d91-0719-4229-a6ee-f7ad468934d3.png)

![](https://i.imgur.com/fz3rDLa.png)



## 2. Tab Configuration ##

**2.1.Host group** 

+ Host group: Tập hợp lại các host có chung một mục đích sử dụng hoặc người quản trị tâp hợp lại để phục vụ một mục đích quản lý chung.

![image](https://user-images.githubusercontent.com/97047640/177291369-869aeb8f-e831-48ba-a5ce-5a6378ef13e7.png)

**2.2. Templates**

+ Templates: Đây là tập hợp các thực thể có thể áp dụng cho các Host, một Template sẽ chứa trong nó các tập lệnh để truy vấn lấy dữ liệu, hiển thị thông tin dữ liệu lấy được, thông tin tình trạng thiết bị, hiển thị và thông báo lỗi…

Trong mỗi Template, các tệp lệnh được chia thành: items, triggers, graphs, applications, screens (có từ Zabbix 2.0),low-level discovery rules (có từ Zabbix 2.0), web scenarios (có từ Zabbix 2.2). Tùy theo giám sát thiết bị, dịch vụ, ứng dụng… nào thì các thành phần này được thiết lập khác nhau.

Có thể import template tự viết vào.

![image](https://user-images.githubusercontent.com/97047640/177291514-051c6e67-6ea8-4375-9c89-8cc3890d8868.png)

**2.3. Host**

+ Host: Là một máy tính, server, vps, chạy các hệ điều hành khác nhau hoặc một thực thể trong hệ thống mạng như là máy in, máy chấm công, máy photo, máy camera có hỗ trợ các giao thức mà monitor zabbix cung cấp.

![image](https://user-images.githubusercontent.com/97047640/177291637-9644bce5-f836-4d05-b54b-c77a006743e0.png)

**2.4. Maintance**

+ Maintance: Có thể xác định thời gian bảo trì cho máy chủ và group trong Zabbix. Có hai loại Maintance - với thu thập dữ liệu và không thu thập dữ liệu.

Ví dụ server của bạn off trong khoảng thời gian này để nâng cấp sửa chữa, thì maintance sẽ được lựa chọn cấu hình để không thu thập data trong khoảng thời gian đó. 

![image](https://user-images.githubusercontent.com/97047640/177292981-48a49a3e-c5dc-4c65-9784-26c1130c4164.png)

**2.5. Action**

+ Action: Nơi cấu hình, lựa chọn các kiểu thông báo khi có sự kiện xảy ra bởi cấu hình trigger. Người dùng phải tự định nghĩa các action theo mục đích.

![image](https://user-images.githubusercontent.com/97047640/177293105-06a9cdbc-2dd6-4b28-9599-d0ed623ea6cb.png)

**2.6. Event correlation**

Cho phép cấu hình tương quan giữa các sự kiến với độ chính xác vào và tùy biến linh hoạt.

**2.7. Discovery**

Thiết lập range IP, nếu trong range có có thiết bị nào mà cài đặt các giao thức mà Zabbix server hỗ trợ thì sẽ tự động thu thập data về

![image](https://user-images.githubusercontent.com/97047640/177293829-9b77a95c-8997-4ee5-ac01-87b365f059fa.png)

## 3. Tab Administrator ##

Chức năng của của tab Administrator là để cấu hình chung cho zabbix đối với user có quyền Admin

![](https://i.imgur.com/oJJFz7K.png)

**3.1. General**
Mục này cho phép người quản trị cấu hình tùy chỉnh giao diện cho Zabbix Webinterface. 

![image](https://user-images.githubusercontent.com/97047640/177294125-a2f061d3-2577-43de-a14f-99588ef74365.png)

Có thể tùy chỉnh rất nhiều giao diện như :

+ GUI: Cung cấp một số tùy chỉnh mặc định liên quan đến giao diện người dùng.

![image](https://user-images.githubusercontent.com/97047640/177293977-c45ccc8c-7765-44ea-ae7e-be5c45291e16.png)

Default theme: Chủ đề mặc định của giao diện. Thường là màu xanh da trời.

Dropdown first entry: Chọn nó là mục đầu tiên trong Drop down.

Search/Filter elements limit: Số lượng tối đa hiển thị các hàng trong tìm kiếm và lọc.

Max count of elements to show inside table cell: Giới hạn hiển thị trong bảng.

Enable event acknowledges: Cho phép các event trong Zabbix kích hoạt.

Show events not older than (in days): Cho phép hiển thị trạng thái Trigger bao nhiêu ngày.

Max count of events per trigger to show: Số event được kích hoạt tối đa trong màn hình trạng thái.

Show warning if Zabbix server is down: Cho phép hiển thị một thông điệp cảnh báo khi không kết nối được Zabbix Server.


+ HouseKeeping: quy định các thời gian định kì được thực hiện bởi Zabbix . Quá trình xóa thông tin hết hạn và thông tin được xóa bởi người dùng .Có thể tùy chỉnh các dữ liệu được lưu tối đa trong bao lâu trên Zabbix. Gồm các phần có thể cấu hình như Event and alerts, Services, Audit, User sessions, History, Trends.

![image](https://user-images.githubusercontent.com/97047640/177294243-f4afdea1-3541-4a11-9066-f93e2f8f3762.png)

Enable internal housekeeping: Lựa chọn bật hoặc tính time để xóa bỏ thông tin.


Trigger data storage period: Khoảng thời gian dọn dẹp các thông in về việc lưu trữ data trigger

Internal data storage period: Khoảng thời gian dọn dẹp Internal data storage.

Network discovery data storage period: Khoảng thời gian dọn dẹp discovery data storage.

+ Images: Chứa tất cả các hình ảnh, icon, background được hiển thị trong Zabbix.

![image](https://user-images.githubusercontent.com/97047640/177294321-1c4654d5-6dc5-4843-ab18-35bbe1299050.png)

+ Icon mapping: Phần này cho phép tạo biểu tượng bản đồ của một host với các biểu tượng nhất định. Các thông tin trong các tùy chọn đều phục vụ cho việc tạo bản đồ.

![image](https://user-images.githubusercontent.com/97047640/177294532-1259857f-70f0-4af1-bec6-0982952f2dfd.png)

Name: Tên icon map (duy nhất).

Mappings: Danh sách các ánh xạ mà Icon map tham chiếu đến.

Inventory field: List các danh sách thiết bị tồn tại.

Expression: Mô tả biểu thức chính quy.

Icon: Icon được dùng nếu biểu thức chính quy lỗi.

Default: icon mặc định được dùng.

+ Regular expressions: Tạo và quy ước các biểu thức chính quy.

![image](https://user-images.githubusercontent.com/97047640/177294606-46769e6c-d3d2-419f-8579-e2c2ef65b6dc.png)

+ Macros: Tạo các đoạn macro tương ứng với giá trị.

![image](https://user-images.githubusercontent.com/97047640/177294725-ee1cc94f-b60b-4382-ad7c-181224ec9f5d.png)

+ Value mapping: Tạo các giá trị tương ức với các mức.

![image](https://user-images.githubusercontent.com/97047640/177294793-4ab5c8cb-3e94-4f42-aba0-e41cb9d65166.png)

+ Working time: Tham số toàn hệ thống xác định thời gian làm việc.

![image](https://user-images.githubusercontent.com/97047640/177294885-44b55c28-e186-4056-9fdb-554f8b394fdf.png)

+ Trigger severities: Cấu hình màu hiển thị đối với các mức cảu trigger.

![image](https://user-images.githubusercontent.com/97047640/177294949-86ffefcd-cf57-4c37-ae14-e362aaaf3383.png)

+ Trigger displaying options: Mầu sắc, hiệu ứng iển thị khi có event.

![image](https://user-images.githubusercontent.com/97047640/177294999-219cc6e7-64b5-4f9e-8f55-45f57e10d7f8.png)


+ Other configuration parameters



**3.2. Proxies**

Cho phép cấu hình các Proxy trên giao diện Zabbix

![](https://i.imgur.com/mLXQkfA.png)

Name: Tên của Proxy.

Mode: Chế độc của Proxy (active hoặc passive).

Encryption: Mã hóa kết nối từ Zabbix Server đến Proxy.

Last seen (age): Thời gian tại thời điểm kết nối cuối cùng với Proxy.

Host count: Số Host mà Proxy quản lý.

Item count: Số lượng Item mà Proxy sử dụng.

Required performance (vps): Hiệu suất Proxy.

Host: Danh sách các host mà proxy quản lý.

**3.3. Authentication**
Phương pháp xác thực người dùng Zabbix : Thẩm định nội bộ, LDAP và HTTP

![image](https://user-images.githubusercontent.com/97047640/177295279-caccafc5-9799-46c0-a022-1b2770247795.png)

**3.4. User groups**

Quản lý các nhóm trong Zabbix

![image](https://user-images.githubusercontent.com/97047640/177295426-759d2d21-3ca2-4581-994b-bb956ac72f79.png)

**3.5. Users**

Tùy chỉnh các tài khoản user cho zabbix

![image](https://user-images.githubusercontent.com/97047640/177295512-b59ef9e5-488b-4160-b6cf-191c916cbf51.png)

Có thể tạo thêm các user khác với việc phân quyền tương ứng.

**3.6. Media types**

Các kênh alert

![image](https://user-images.githubusercontent.com/97047640/177295566-976840da-4d52-4ab6-ae0f-48fd4fec6599.png)

**3.7. Scripts**

**3.8. Queue**

Thông tin về hàng đợi trong quá trình cập nhật dữ liệu về từ các nguồn agent.

![image](https://user-images.githubusercontent.com/97047640/177295618-508d69da-c1bb-4a72-acb9-f906e2719781.png)


