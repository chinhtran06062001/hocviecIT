# Lập trình Bash Shell

Bash Shell là mọt trình thông dịch dòng lệnh cung cấp giao diện người dùng cho các cửa sổ đầu cuối. Nó cũng có thể được sử dụng để chạy các tập lệnh, ngay cả trong các phiên không tương tác mà không có cửa sổ đầu cuối, như thể các lệnh đang được nhập trực tiếp

```
#!/bin/bash
find /usr/lib -name "*.c" -ls
```
Dòng đầu tiên của tập lệnh được bắt đầu bằng `` #!bin/bash`` chứa đường dẫn đầy đủ của trình thông dịch lệnh sẽ được sử dụng trên tệp. Trình thông dịch lệnh có nhiệm vụ thực thi các câu lệnh. Phiên dịch viên thường được sử dụng bao gồm :

```
/usr/bin/perl
/bin/bash
/bin/csh
/bin/tcsh
/bin/ksh
/usr/bin/python
/bin/sh
```

Những câu lệnh này không chỉ giới hạn ở bash shell mà nó cũng có thể được sử dụng cho các tập lệnh python.

```
# ll script
-rwxr--r--. 1 root root 55 Mar  3 15:22 script
# cat script
#!/usr/bin/python
print "Welcome to the Python script"
# ./script
Welcome to the Python script
```

Các câu lệnh cũng có thể tương tác :

```
# cat script.sh
#!/bin/bash
   # Interactive reading of variables
   echo "ENTER YOUR NAME"
   read sname
   # Display of variable values
   echo "WELCOME "$sname"!"
# ./script.sh
ENTER YOUR NAME
Adriano
WELCOME Adriano!
```

Tất cả câu lệnh Shell đều đưa ra giá trị trả về khi kết thúc quá trình thực thi, được đặt bằng câu lệnh `exit` . Nó cho phép giám sát trạng thái thoát của một quá trình khác thường trong mối quan hệ cha - con. Điều này giúp biết được quá trình được kết thúc như thế nào và nên thực hiện bước cần thiết thích hợp, tuỳ thuộc vào quá trình thành công hay thất bại. Theo quy ước, thành công giá trị sẽ được trả về 0 và thất bại sẽ trả về một giá trị khác 0. Giá trị trả về luôn được lưu trữ trong biến ``$?`.

```
# cat names.txt
01 Mario Rossi
02 Antonio Esposito
03 Michele Laforca
04 Antonio Esposito
# echo $?
0
# cat names
cat: names: No such file or directory
# echo $?
1
```

# Cú pháp câu lệnh đơn giản

Bash Shell yêu cầu phải tuân theo các cú pháp ngôn ngữ chuẩn các quy tắc mô tả xác định cũng như cách xây dựng và định dạng các câu lệnh được phép,... Dưới đây là một số cách dùng ký tự đặc biệt trong bash:

|Character|Description|
|---------|-----------|
|#|Used to add a comment, except when used as \#, or as #! when starting a script|
|\\|Used at the end of a line to indicate continuation on to the next line|
|;|Used to interpret what follows as a new command|
|$|Indicates what follows is a variable|

Vào một số trường hợp bạn muốn dùng nhiều câu lệnh trên một dòng. Khi đó ký tự `;` được k=sử dụng để phân tách các câu lệnh này và thực hiện chúng một cách tuần tự như thể chúng đã được tách trên các dòng riêng biệt.

Ba câu lệnh dưới đây đều được thực thi ngay khi cả những câu lệnh trước chúng không thành công:

```
$ make ; make install ; make clean
```

Tuy nhiên, nếu bạn muốn huỷ bỏ các lệnh tiếp theo nếu một lệnh không thành công. Bạn có thể làm điều này bằng cách sử dụng toán tử and (&&) :

```
$ make && make install && make clean
```

Nếu một câu lệnh đầu tiên không thành công, câu lệnh thứ 2 sẽ không được thực hiện. Nên nếu muốn nó được thực hiện thì chúng ta sử dụng toán tử or (||) :

```
$ cat file1 || cat file2 || cat file3
```

Trong trường hợp này, bạn tiếp tục cho đến khi điều gì đó thành công và sau đó bạn ngừng thực hiện bất kỳ bước nào tiếp theo.

### Các hàm
Hàm là một khối mã thực hiện một tập hợp các hoạt động. Các hàm rất hữu ích để thực hiện các thủ tục nhiều lần có lẽ với các biến đầu vào khác nhau. Các hàm cũng thường được gọi là chương trình con. Sử dụng các hàm trong tập lệnh yêu cầu hai bước:

1. Khai báo hàm
2. Gọi hàm

Khai báo hàm yêu cầu một tên được sử dụng để gọi nó. Cú pháp thích hợp là:
```
    function_name () {
       command...
    }
```
Ví dụ, đặt một hàm là display:
```
    display () {
       echo "This is a sample function"
    }
```
Hàm có thể dài như mong muốn và có nhiều câu lệnh. Sau khi được xác định, hàm có thể được gọi sau nhiều lần nếu cần. Trong ví dụ đầy đủ được hiển thị trong hình, chúng tôi cũng đang chỉ ra một cách sàng lọc thường được sử dụng: cách truyền một đối số cho hàm. Đối số thứ nhất, thứ hai, ..., thứ n có thể được gọi là `` $ 1, $ 2, ..., $ n ``. Tên tập lệnh được gọi là `` $ 0 ``. Tất cả các tham số được gọi là `` $ * `` và tổng số đối số là `` $ # ``.
```
# cat script.sh
#!/bin/bash
echo The name of this program is: $0
echo The first argument passed from the command line is: $1
echo The second argument passed from the command line is: $2
echo The third argument passed from the command line is: $3
echo All of the arguments passed from the command line are : $*
echo All done with $0
exit 0
#
# ./script.sh A B C
The name of this program is: ./script.sh
The first argument passed from the command line is: A
The second argument passed from the command line is: B
The third argument passed from the command line is: C
All of the arguments passed from the command line are : A B C
All done with ./script.sh
```

### Command substitution
Bạn có thể cần thay thế kết quả của một lệnh thành một phần của lệnh khác. Nó có thể được thực hiện theo hai cách:

1. Bằng cách bao bọc lệnh bên trong bằng dấu gạch ngược (`)
2. Bằng cách đặt lệnh bên trong trong $ ()

Bất kể phương pháp nào, lệnh trong cùng sẽ được thực thi trong môi trường shell mới được khởi chạy và đầu ra tiêu chuẩn của shell sẽ được chèn vào nơi thực hiện thay thế lệnh. Hầu như bất kỳ lệnh nào cũng có thể được thực hiện theo cách này. Cả hai phương pháp này đều cho phép thay thế lệnh; tuy nhiên, phương pháp thứ hai cho phép lồng lệnh.
```
# cat ./count.sh
#!/bin/bash
echo "The " $1 " contains " $(wc -l < $1) " lines."
echo $?
# ./count.sh /var/log/messages
The  /var/log/messages  contains  114  lines.
0
```
Trong ví dụ trên, đầu ra của lệnh bên trong trở thành đối số cho lệnh bên ngoài.

### Câu lệnh if
Ra quyết định có điều kiện bằng cách sử dụng câu lệnh if, là một cấu trúc cơ bản mà bất kỳ ngôn ngữ lập trình hoặc kịch bản hữu ích nào đều phải có. Khi một câu lệnh if được sử dụng, các hành động tiếp theo phụ thuộc vào việc đánh giá các điều kiện cụ thể như:
*. So sánh số hoặc chuỗi
*. Giá trị trả về của một lệnh (0 để thành công)
*. Sự tồn tại hoặc quyền của tệp

Ở dạng thu gọn, cú pháp của câu lệnh if là:
```
if TEST-COMMANDS; then CONSEQUENT-COMMANDS; fi
```
Một định nghĩa chung hơn là:
```
if condition
then
       statements
else
       statements
fi
```

Câu lệnh sau kiểm tra đối số tệp và nếu nó được tìm thấy, thì nó sẽ hiển thị thông báo
```
#!/bin/bash
if [ -f $1 ]
then
    echo "The " $1 " contains " $(wc -l < $1) " lines.";
    echo $?
fi
# ./count.sh /etc/passwd
The  /etc/passwd  contains  35  lines.
0
```

Các tùy chọn sau để kiểm tra tệp

|Option|Action|
|------|------|
|-e file|	Check if the file exists.|
|-d file|	Check if the file is a directory.|
|-f file|	Check if the file is a regular file.|
|-s file|	Check if the file is of non-zero size.|
|-g file|	Check if the file has sgid set.|
|-u file|	Check if the file has suid set.|
|-r file|	Check if the file is readable.|
|-w file|	Check if the file is writable.|
|-x file|	Check if the file is executable.|

Bạn có thể sử dụng câu lệnh if để so sánh các chuỗi. Cú pháp như sau:
```
if [ string1 == string2 ]
then
   ACTION
fi
```

Hoặc để so sánh các số, như sau:
```
if [ exp1 OPERATOR exp2 ]
then
   ACTION
fi
```

 Các tùy chọn cho các nhà khai thác là:

Các tùy chọn sau để kiểm tra tệp

|Option|Action|
|------|------|
|-eq|Equal to|
|-ne|Not equal to|
|-gt|Greater than|
|-lt|Less than|
|-ge|Greater than or equal to|
|-le|Less than or equal to|
