# Một số thao tác cơ bản trên GITHUB.

### Mục lục  
.[I. Cách tạo một Github Reponsitory](#I)

[II. MARKDOWN](#II)  

[Markdown là gì?](#markdown)  

[1. Tạo tiêu đề](#tieude)  

[2. Định dạng chữ](#dinhdang)  

[3.Xuống dòng](#xuongdong)  

[4.Tạo danh sách](#danhsach)  

[5. Tạo  liên kết](#lienket)  

[6.Tạo hình ảnh](#hinhanh)  

[7. Bảng](#bang)  

[III. Hướng dẫn sử dụng Github chi tiết](#III) 

[1. Commit Command](#commitcommand) 

[2. Pull Command](#pullcommand) 

[3. Merge Command](#mergecommand) 

[Cloning dự án từ Github](#cloning) 

[Push dự án lên Github](#push) 

<a name = "I"></a>
# I. Cách tạo một Github Repository

Repository là một không gian để lưu trữ dự án của bạn. Do tính chất phân tán của Git, nên có thể hiểu repository là nơi lưu trữ mã nguồn ở cả local và server.

Bạn có thể lưu trữ file code, text, hình ảnh hoặc bất kỳ loại tệp nào trong repository.

Để tạo một repository trên Github bạn làm như sau:

- Vào Github, đăng ký một tài khoản bằng cách click vào “Sign up for Github”.

(Xem hướng dẫn tạo tài khoản ở file: https://github.com/chinhtran06062001/buoi1/blob/main/timhieugithub.md)

- Sau khi đăng ký và kích hoạt thành công. Bạn bắt đầu tạo mới một project với “Start a new project”.
Bạn có thể xem hình bên dưới cho rõ thêm nhé:

![image](https://user-images.githubusercontent.com/65167293/157231192-c7a25cc2-b0ac-4c9e-b565-9fc64a376062.png)

- Nhập tên Repositoty và nhấn nút “Create Repository”. Ngoài ra, bạn cũng có thể thêm mô tả cho repo ( Cái này chỉ là lựa chọn, không bắt buộc phải có).

![image](https://user-images.githubusercontent.com/65167293/157231382-d15ad9ca-1dce-4782-a56a-660fe2bfff6c.png)

Trong đó, bạn lưu ý 2 options sau:

- Theo mặc định thì repository để là public. Tức là ai cũng có thể xem được repo này của bạn. Nếu dự án của bạn chưa muốn công khai mà chỉ muốn quản lý nội bộ thì chọn Private.
- Bạn có thêm một README file để giới thiệu repo kèm với một file .gitignore. Github đã có sẵn template .gitignore cho bạn, cứ chọn một template phù hợp với mã nguồn dự án là được.
Khi tạo xong, repo sẽ như sau:

![image](https://user-images.githubusercontent.com/65167293/157231520-82ab80de-86ae-4424-916b-925e4e9acc6f.png)

Khi đã có repository, bạn có thể clone, pull, push… source code của mình lên đó rồi.

Phần tiếp theo của bài viết, chúng ta sẽ tìm hiểu về branch trên Github.

<a name = "II"></a>
# II.MARKDOWN
<a name="markdown"></a>
#  Markdown là gì?
- Markdown là ngôn ngữ đánh dấu văn bản thô được tạo ra bởi John Gruber. 
- Văn bản được viết bằng Markdown sẽ có thể được chuyển đổi sang HTML và ngược lại.
- Thường được dùng để:
 * tạo tập tin readme
 * viết tin nhắn trên diễn đàn
 * tạo văn bản có định dạng bằng một trình biên tập văn bản thô    
 
# Các cú pháp thường sử dụng:  

<a name="tieude"></a>
## 1.*Tạo tiêu đề*
> # Tiêu đề 1 (h1)  
> ## Tiêu đề 2 (h2)  
> ### Tiêu đề 3 (h3)  
> #### Tiêu đề 4 (h4)  
> ##### Tiêu đề 5 (h5)  
> ###### Tiêu đề 6 (h6)

<a name="dinhdang"></a>
## 2.*Định dạng chữ*
* *In nghiêng* : `*kí tự cần in nghiêng*` hoặc  `__ kí tự cần in nghiêng__`  
* **In đậm** :`**In đậm**` hoặc `__In đậm__`  
* ~~Gạch ngang~~: `~~gạch ngang~~`  

<a name="xuongdong"></a>
## 3.*Xuống dòng* :  
`<space><space>`: sử dụng hai khoảng trắng

<a name="danhsach"></a>
## 4.*Tạo danh sách*  
Chú pháp : `1. danh sách `

1. danh sách 1
2. danh sách 2
3. danh sách 3

hoặc `-danh sách` hoặc `* danh sách`
- danh sách 1
- danh sách 2
- danh sách 3

<a name="lienket"></a>
## 5.*Tạo liên kết*
- Có thể chèn Link trực tiếp  
https://www.w3schools.com/  
hoặc đặt trong cặp dấu ngoặc  
`<https://www.w3schools.com/>` 
hoặc
`![Tên link](đường dẫn) (<a>)`    
`![Tên link với chú thích](đường dẫn "chú thích") (<a name="chú thích">)`    

<a name="hinhanh"></a>
## 6.*Tạo hình ảnh*  
Cú pháp: `![mô tả](link)`  

![VÍ DỤ](![image](https://user-images.githubusercontent.com/97047640/166864748-3677ae95-4e5d-4a77-8c1e-623f62e5338c.png)  

<a name="bang"></a>
##  7.*Bảng*
 Các cột được tách nhau bằng dấu ngăn thẳng đứng |   
 header được tách với content bằng dấu gạch ngang -.
 ~~~
  
|       A       |      B        | C     |
| :------------:|:-------------:|:-----:|
|    3          |        2      |  1    |
|     2         |        4      |   1   |
|     a         | b             |    d  |
~~~  

|       A       |      B        | C     |
| :-----------: |:-------------:| :----:|
|    3          |        2      |  1    |
|     2         |        4      |   1   |
|     a         | b             |    d  |  

<a name = "sublime"></a>

<a name  = "III"> </a>
# III. Hướng dẫn sử dụng Github chi tiết

<a name  = "commitcommand"> </a>
# 1. Commit Command
Commit command cho phép bạn lưu lại những thay đổi của file. Khi bạn commit, nên viết mô tả rõ ràng trong commit message. Điều này sẽ giúp cho quản lý dự án tốt hơn, có thể theo dõi, review những thay đổi source code sau này.
Để tạo commit, bạn làm như sau:

- Chọn file muốn sửa
- Chọn “Edit” để sửa file.
- Sau khi sửa xong thì điền thông tin message và nhấn Commit.

![image](https://user-images.githubusercontent.com/65167293/157231987-b42911f8-4ba2-4ea9-9975-1a053a140b58.png)

<a name  = "pullcommand"> </a>
# 2. Pull Command
Lệnh PULL request là lệnh quan trọng  nhất trên Github. Nó cho biết những thay đổi trong source code, và yêu cầu owner của source code xem xét nó và merge nó vào master branch.

Một khi commit xong, bất kể ai cũng có thể update sự thay đổi và thảo luận về sự thay đổi đó.

Tính năng này rất hay cho các dự án mã nguồn mở. Khi mà bất kì cũng có thể đóng góp công sức cho dự án. Tất nhiên, mọi sự thay đổi đều phải được sự đồng ý của owner dự án.

Ở đây, mình cần làm rõ hơn với các bạn đỡ nhầm lẫn về lệnh Pull:

- Lệnh pull request : Là lệnh yêu cầu chủ owner dự án xem xét một thay đổi nào đó trước khi merge vào master branch.
- Lệnh Pull: đây là lệnh của git, đơn thuần có thể hiểu là lệnh update source code từ server về local. Nếu có bất kì sự xung đột code nào (conflict) thì bạn cần phải resolve nó.

![image](https://user-images.githubusercontent.com/65167293/157232093-3c664e57-6df2-4d3b-a988-28834297603e.png)

![image](https://user-images.githubusercontent.com/65167293/157232166-2cdb90bb-58e1-4417-ae0f-f305127fc2c9.png)

![image](https://user-images.githubusercontent.com/65167293/157232188-7449f7d9-08eb-4895-a007-7a9a014a88fc.png)

<a name  = "merge command"> </a>
# 3. Merge command 
Lệnh cơ bản cuối cùng mà mình muốn nhắc đến là merge. Lệnh merge này cho phép bạn hợp nhất những thay đổi vào một branch.

- Click vào “Merge pull request” để hợp nhất những thay đổi vào master branch.
- Click vào “Confirm merge”.
Bạn có thể tham khảo hình bên dưới:

![image](https://user-images.githubusercontent.com/65167293/157232305-b63c71b9-12c1-4406-aa7f-889728a9abb1.png)

<a name  = "cloning"> </a>
# Cloning dự án từ Github
Tiếp tục hướng dẫn sử dụng Github. Đây có lẽ là thao tác bạn hay dùng nhất khi tìm kiếm mã nguồn mở trên mạng. Khi bạn thấy một dự án nào đó hay ho và có thể ứng dụng được cho dự án của mình, bạn muốn download dự án này về máy tính để tham khảo.

Có 2 cách để tải dự án từ Github:

- Một là bạn chọn Zip toàn bộ dự án và tải về

![image](https://user-images.githubusercontent.com/65167293/157232431-9b97fb24-7f23-4400-a84b-f1b4b1d662aa.png)

Hai là bạn có thể clone dự án về bằng lệnh git. Bạn cũng click vào “Clone or Download”. Sau đó copy đường dẫn và gõ trong cửa sổ terminal trên máy tính như sau

      git clone git@github.com:vntalking/demo-create-repro.git

<a name = "push"> </a>

# Push dự án lên Github

Trước tiên, nếu như máy bạn chưa cài Git, hãy download Git theo link sau: https://git-scm.com/downloads

Sau khi download và cài đặt, kiểm tra bằng lệnh:
git --version
![image](https://user-images.githubusercontent.com/97047640/166861120-bb0e0794-fc4f-4955-a4b8-7789abffd735.png)
Sau khi đã cài Git, làm theo các bước sau để đẩy code lên Github:

Bước 1: Tạo tài khoản Github
- Các bạn truy cập vào trang Github.com và đăng kí tài khoản

Bước 2: Tạo một repository mới trên Github 
- Sau khi đăng kí tài khoản thành công, tạo một repo mới bằng cách nhấp vào mũi tên nơi avatar, chọn your repositories, trang repositories xuất hiện, nhấn nút New màu xanh bên phải.
![image](https://user-images.githubusercontent.com/97047640/166861483-a4cc3b23-c48c-4fb4-be15-894beedf2217.png)
![image](https://user-images.githubusercontent.com/97047640/166861514-18152bf4-828b-4599-b4a7-750bceea46ed.png)

- Đặt tên cho repo mới, sau đó click Create Repository. 
![image](https://user-images.githubusercontent.com/97047640/166861564-a8ff203f-43aa-43ae-8c91-f15dec28d636.png)

Lưu ý: Nếu các bạn muốn triển khai một website tĩnh trên Github, các bạn phải đặt tên repo theo cú pháp sau: [username của tài khoản Github của bạn].github.io

![image](https://user-images.githubusercontent.com/97047640/166861648-efdbfe08-1458-48fd-aebb-fb315e364f88.png)

Bước 3: Clone repo về máy
- Copy đường dẫn của repo mới tạo
![image](https://user-images.githubusercontent.com/97047640/166861690-a090ad93-ce34-49d3-89e9-816d8a48ecfa.png)

- Clone repo về máy bằng lệnh sau:
git clone https://github.com/chinhtran06062001/pushdata.git

Bước 4: Thiết lập Git
Muốn thiết lập tên người dùng / địa chỉ email
git config --global user.name <username>
git config --global user.email <mailaddress>
Khi không thêm lựa chọn--global thì chỉ những repository có liên quan mới trở nên hữu hiệu với thiết lập.
 ![image](https://user-images.githubusercontent.com/97047640/166862080-66cfeeb0-ad19-43df-aab3-59d2d222486e.png)

 Bước 5: Thêm/sửa/xóa file/thư mục trên repo vừa clone về, sau đó push lên Github
-  Thêm/sửa/xóa các file/thư mục trên repo vừa clone về, sau đó lần lượt chạy từng lệnh sau:
 
 git status
 
git add *
 
git commit -m "điền nội dung commit vào đây" (Ví dụ : "Add new file chinhtran.txt")
 
git push --set-upstream origin main

 ![image](https://user-images.githubusercontent.com/97047640/166863188-236cef51-a1da-4bf4-bdbc-7fad500d2348.png)
 ![image](https://user-images.githubusercontent.com/97047640/166882768-664b52ad-bdad-4ccd-89ef-d7eb62e45b3b.png)


 Chú ý: Trỏ đúng thư mục mà chúng ta clone git về, ví dụ cd 'tên thư muc' để chuyển đến
 
- Vào Github repo để kiểm tra:
 
 https://github.com/chinhtran06062001/pushdata
 
 ![image](https://user-images.githubusercontent.com/97047640/166882826-68457674-42b9-479a-b918-6bdd86ae9e9e.png)


#Tham Khảo
 
 https://vntalking.com/
 
 https://www.codelean.vn/2020/01/git-clone-du-co-san-tu-git.html
 
 https://dotnet.edu.vn/TinTucND/Huong-dan-pushday-code-len-Github-1884.aspx
  
                                                           # THE END
 
