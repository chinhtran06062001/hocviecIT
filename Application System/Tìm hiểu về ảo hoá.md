# Công nghệ ảo hóa là gì?
Hiểu theo một cách khái quát nhất, ảo hóa là quá trình tạo ra một bản sao ảo của một thực thể nào đó. Trong theo định nghĩa trong công nghệ thông tin; ảo hóa là công nghệ được thiết kế để tạo ra tầng trung gian giữa hệ thống phần cứng (hardware) và phần mềm (OS); giúp quản lý, phân phối tài nguyên phần cứng cho lớp OS ảo hoạt động trên nó. Từ một máy vật lý đơn lẻ, công nghệ ảo hóa giúp tạo ra nhiều máy ảo độc lập. Mỗi máy ảo có một thiết lập nguồn hệ thống riêng lẻ; hệ điều hành riêng lẻ và các ứng dụng riêng lẻ.
# Môi trường ảo hóa
Một hệ thống ảo hóa có 4 thành phần chính sau đây:

Tài nguyên vật lý chính (Host): Máy chủ vật lý, CPU, RAM, ổ đĩa cứng, card mạng… Nhiệm vụ là phân chia tài nguyên cho các máy ảo.

Phần mềm ảo hóa (Hypervisor): cung cấp truy cập cho mỗi máy chủ ảo đến tài nguyên của máy chủ vật lý; cung cấp giao diện quản lý cho các máy chủ ảo; phân chia tài nguyên vật lý cho các máy chủ ảo.

Hệ điều hành khách (Guest): được cài đặt trên một máy chủ ảo; thao tác như ở trên hệ điều hành thông thường.

Máy ảo (Virtual Machine): nó hoạt động như một máy chủ vật lý thông thường; với tài nguyên riêng, giao diện riêng, hệ điều hành riêng.
# Mô hình tham chiếu ảo hóa 
![image](https://user-images.githubusercontent.com/101684058/158721876-7669aa37-be67-4532-a3cd-e32493fc1a75.png)
# Mục đích của ảo hóa
Mục đích đầu tiên của ảo hóa là, Optimization, tức sử dụng triệt để tài nguyên phần cứng; hạn chế tối đa sự lãng phí bằng cách giảm số lượng thiết bị vật lý cần thiết.

Thứ hai là Availability, nghĩa là giúp các ứng dụng hoạt động liên tục; không bị gián đoạn, không xảy ra tình trạng downtime khi phần cứng gặp sự cố; khi nâng cấp hoặc di chuyển.

Thứ ba là Scalability, khả năng tùy biến, linh hoạt thu hép hay mở rộng mô hình server một cách dễ dàng hơn mà không làm ảnh hưởng đến ứng dụng.

Cuối cùng là Management, khả năng quản lý tập trung nhờ vào việc tạo nhiều bản sao của tài nguyên.
# Lợi ích của ảo hóa
1. Nó giúp tiết kiệm rất nhiều chi phí và cho phép dễ dàng bảo trì nó, với chi phí thấp hơn.
2. Nó cho phép nhiều hệ điều hành trên một nền tảng ảo hóa; tận dụng tối đa nguồn tài nguyên; tránh tình trạng lãng phí.
3. Nó loại bỏ sự phụ thuộc của phần cứng nặng để chạy ứng dụng.
4. Nó cung cấp các máy chủ hợp nhất được sử dụng cho sự cố của một mục đích máy chủ
5. Nó làm giảm dung lượng được sử dụng bởi các trung tâm dữ liệu và dữ liệu công ty
6. Giảm số lượng thiết bị vật lý cần thiết (giảm số lượng server, switch, cáp, phí gia công)
7. Quản lý tập trung, liên tục, nâng cao hiệu quả làm việc của quản trị viên.
# 3 mức độ ảo hóa
### Full Virtualization (Ảo hóa toàn phần)
Ảo hóa toàn phần là một kỹ thuật ảo hóa được sử dụng để cung cấp một VME (Virtual Machine Environment) mô phỏng hoàn toàn phần cứng bên dưới. Trong loại môi trường này, bất kỳ phần mềm nào có khả năng thực thi trên phần cứng vật lý; đều có thể chạy trong máy ảo và bất kỳ hệ điều hành nào được phần cứng hỗ trợ; thì đều có thể chạy trong từng máy ảo riêng lẻ. Người dùng có thể chạy đồng thời nhiều hệ điều hành khách khác nhau.

Trong ảo hóa toàn phần, máy ảo mô phỏng đủ phần cứng; để cho phép một hệ điề hành khách chưa sửa đổi được chạy một cách riêng biệt. Điều này đặc biệt hữu ích trong một số tình huống. Ví dụ, khi phát triển hệ điều hành; mã mới thử nghiệm có thể được chạy cùng lúc với các phiên bản cũ hơn; mỗi phiên bản trong một máy ảo riêng biệt. Hypervisor cung cấp cho mỗi máy ảo tất cả các dịch vụ của hệ thống vật lý; bao gồm BIOS ảo, thiết bị ảo và quản lý bộ nhớ ảo hóa. Hệ điều hành khách hoàn toàn được tách rời khỏi phần cứng bên dưới bởi lớp ảo hóa.

Nói một cách đơn giản hơn, hệ điều hành khách (Guest) và các phần mềm được cài đặt trên nó; chạy trong môi trường hệ điều hành chủ (Host); mà chúng ta không cần phải chỉnh gì bất kỳ cái gì. Điều này đồng nghĩa, khi một phần mềm nào đó chạy trên Guest; đoạn code của nó không bị biến đổi, mà chay trực tiếp trên Host.

Ví dụ: Vmware.

### Para Virtualization (Ảo hóa song song)
Paravirtualization (PV) là một cải tiến của công nghệ ảo hóa; trong đó hệ điều hành khách (client OS) được sửa đổi; trước khi cài đặt bên trong máy ảo (VM); để cho phép tất cả hệ điều hành khách trong hệ thống chia sẻ tài nguyên và cộng tác thành công, đúng hơn là cố gắng mô phỏng toàn bộ môi trường phần cứng.

Với PV, các máy ảo có thể được truy cập thông qua các giao diện tương tự như phần cứng bên dưới. Dung lượng này giảm thiểu chi phí, và tối ưu hóa hiệu suất hệ thống; bằng cách hỗ trợ việc sử dụng các máy ảo mà nếu không được sử dụng trong ảo hóa phần cứng thông thường hoặc toàn bộ.

Ví dụ: Xen, Denali

### Hardware-assisted Virtualization (Ảo hóa được hỗ trợ bởi phần cứng)
Trong máy tính, ảo hóa được phần cứng hỗ trợ là một cách tiếp cận ảo hóa nền tảng cho phép ảo hóa toàn bộ hiệu quả; bằng cách sử dụng sự trợ giúp từ các khả năng phần cứng, chủ yếu từ bộ xử lý chủ. Ảo hóa toàn phần được sử dụng để mô phỏng một môi trường phần cứng hoàn chỉnh, hay còn gọi là máy ảo; trong đó, hệ điều hành khách chưa được sửa đổi (sử dụng cùng một tập lệnh như máy chủ) thực thi một cách hoàn toàn hiệu quả. Ảo hóa hỗ trợ phần cứng đã được thêm vào bộ xử lý x86 (Intel VT-x hoặc AMD-V) vào năm 2005 và 2006 (tương ứng).

Ảo hóa được hỗ trợ bởi phần cứng còn được gọi là ảo hóa tăng tốc; hay còn gọi là máy ảo phần cứng (HVM) hay ảo hóa gốc.

Ảo hóa có sự hỗ trợ của phần cứng cải thiện hiệu quả tổng thể của ảo hóa. Nó liên quan đến các CPU cung cấp hỗ trợ ảo hóa trong phần cứng và các thành phần phần cứng khác giúp cải thiện hiệu suất của môi trường khách. Phần mềm phần mềm hỗ trợ kiến ​​trúc để chạy O/S một cách riêng biệt (Công nghệ AMD-V / Intel VT)
# Các loại ảo hóa
### Server Virtualization
Ảo hóa máy chủ – hợp nhất nhiều máy chủ vật lý thành máy chủ ảo chạy trên một máy chủ vật lý duy nhất.

### Application Virtualization
Ảo hóa ứng dụng – một ứng dụng chạy trên một máy chủ khác; từ đó, nó được cài đặt theo nhiều cách khác nhau. Nó có thể được thực hiện bằng cách phát trực tuyến ứng dụng; ảo hóa máy tính để bàn hoặc VDI ​​hoặc một gói VM (như VMware ACE tạo bằng trình phát). Microsoft Softgrid là một ví dụ về ảo hóa Ứng dụng.

### Presentation Virtualization
Đây là những gì mà khung Citrix Met (và giao thức ICA) cũng như Microsoft Terminal Services (và RDP) có thể tạo ra. Với ảo hóa bản trình bày, một ứng dụng thực sự chạy trên một máy chủ khác; và bạn thấy tất cả những điều đó trên màn hình máy khách từ nơi nó được chạy.

### Network Virtualization
Với ảo hóa này, network được “khắc phục” và có thể được sử dụng cho nhiều mục đích; như phân tích giao thức bên trong bộ chuyển mạch Ethernet. Các thành phần của mạng ảo có thể bao gồm NIC; bộ chuyển mạch, VLAN, thiết bị lưu trữ mạng, vùng chứa mạng ảo và phương tiện mạng.

### Storage Virtualization
Ảo hóa lưu trữ được mô tả là “trừu tượng hóa” lưu trữ logic khỏi lưu trữ vật lý. Với ảo hóa lưu trữ, phương tiện lưu trữ cho dữ liệu của bạn được hợp nhất; và quản lý bởi một hệ thống lưu trữ ảo. Các máy chủ được kết nối với hệ thống lưu trữ không biết dữ liệu thực sự ở đâu.

### Hardware Virtualization 
Ảo hóa phần cứng – hoạt động bằng cách bắt chước tài nguyên phần cứng bằng lớp phần mềm (Hypervisor).
![image](https://user-images.githubusercontent.com/101684058/158722873-2dc19483-b136-4ce3-aabc-84495c1170e0.png)
## Hypervisor
Hypervisor là một chương trình quản lý máy ảo. Nó hoạt động giống như một trình quản lý máy ảo quản lý nhiều máy ảo từ một nơi. Nó cho phép nhiều hệ điều hành chia sẻ một máy chủ phần cứng duy nhất.

Mỗi hệ điều hành trong hệ điều hành này bao gồm không gian xác định riêng của nó (bộ nhớ, bộ xử lý và các tài nguyên khác). Nó được sử dụng như một chương trình điều khiển; để điều khiển các bộ xử lý máy chủ và tài nguyên; bằng cách lần lượt phân bổ những gì cần thiết cho từng hệ điều hành. Vì vậy, hệ điều hành khách đó (được gọi là máy ảo) không thể xung đột với một hệ điều hành khác. Có hai loại Hypervisor:

#### Type 1 Hypervisor
• Còn được gọi là Bare Metal hoặc Embedded hoặc Native Hypervisor.

• Nó hoàn toàn độc lập với Hệ điều hành.

• Nó hoạt động trực tiếp trên phần cứng của máy chủ; và có thể giám sát các hệ điều hành chạy phía trên hypervisor.

• Nhiệm vụ chính của nó là chia sẻ và quản lý tài nguyên phần cứng giữa các hệ điều hành khác nhau.

• Một ưu điểm chính là bất kỳ sự cố nào trong một máy ảo hoặc hệ điều hành khách không ảnh hưởng đến các hệ điều hành khách khác đang chạy trên hypervisor.

Ví dụ: Máy chủ VMware ESXi, Microsoft Hyper-V, Máy chủ Citrix / Xen

#### Type 2 Hypervisor
• Còn được gọi là Hosted Hypervisor.

• Nó hoàn toàn phụ thuộc vào Hệ điều hành máy chủ cho các hoạt động của nó

• Hypervisor được cài đặt trên một hệ điều hành; và sau đó hỗ trợ các hệ điều hành khác trên nó.

• Mặc dù có hệ điều hành cơ sở cho phép đặc tả chính sách tốt hơn; nhưng bất kỳ sự cố nào trong hệ điều hành cơ sở cũng sẽ ảnh hưởng đến toàn bộ hệ thống; ngay cả khi hypervisor chạy phía trên hệ điều hành cơ sở được bảo mật.

Ví dụ: VMware Workstation, Microsoft Virtual PC, Oracle Virtual Box



