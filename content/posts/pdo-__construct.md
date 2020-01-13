---
title: 'PDO::__construct'
subtitle: PDO
category:
  - PHP
author: Bạch Long
date: 2020-01-13T02:47:02.105Z
featureImage: uploads/what-is-a-database-management-system.png
---
## PDO là gì?

PDO là một từ viết tắt của PHP Data Object. PDO là 1 cách gọn gàng, nhất quán để truy cập vào database. Điều này có nghĩa là nhà phát triển có thể viết code di động và dễ dàng hơn. PDO không phải là một lớp trừu tượng như PearDB. PDO giống như là một lớp truy cập dữ liệu, sử dụng một cách thống nhất[API](http://xn--api%20l%20g-e7a4n/?) (Application Programming Interface).

PDO chính là đại diện giữa PHP và một database server.

[![](https://1.bp.blogspot.com/-IN2jRAVRxUo/XgsJ7t-aCGI/AAAAAAAABD4/2xc2smVBK8UsofYQhRoIbm7Xo-hrUwE0ACLcBGAsYHQ/s1600/what-is-a-database-management-system.png)](https://1.bp.blogspot.com/-IN2jRAVRxUo/XgsJ7t-aCGI/AAAAAAAABD4/2xc2smVBK8UsofYQhRoIbm7Xo-hrUwE0ACLcBGAsYHQ/s1600/what-is-a-database-management-system.png)





## PDO::__construct



PDO::__construct -- Tạo một cá thể PDO thể hiện một yêu cầu kết nối đến database.





### **Mô tả**



> publicPDO::__construct(string `$dsn`[,string `$username`[,string `$passwd`[,array `$options`]]]



Tạo 1 cá thể PDO thể hiện một yêu cầu truy cập đến database .





## Tham số

#### dsn

dsn là viết tắt cả Data Source Name ( tên nguồn dữ liệu ), chưa đựng thông tin, yêu cầu truy cập đến database.



Nhìn chung, một dsn gồm có tên trình điều khiển PDO, theo bởi một dấu hai chấm, theo sau là cú pháp kết nối cho trình điều khiển PDO.





Tham số dsn hỗ trợ ba phương thức khác nhau để chỉ định các đối số cần thiết để tạo kết nối cơ sở dữ liệu:



**Yêu cầu trình điều khiển**

dsn chứa dsn đầy url: theo bởi một URI định nghĩa vị trí của thư mục chứa chuỗi DSN. URI có thể chỉnh định một thư mục cục bộ hoặc một URI từ xa.



`uri:file:///path/to/dsnfile`



**Aliasing (Bí danh)**



dsn gồm một tên, tên ánh xạ đến pdo.dsn.name trong php.ini định nghĩa chuỗi DSN.



Ghi chú:

Alias có thể định nghĩa php.ini, và không có đuôi .htaccess hoặc httpd.conf



**username**



username cho chuỗi dsn. Tham số là tùy chọn cho một số trình điều kiển PDO.



**password**



password cho chuỗi dsn. Tham số là tùy chọn cho một số trình điều kiển PDO.



**options**



1 khóa => giá trị mảng của trình điều khiển riêng kết nối với các lựa cho



### Return Giá trị

Trả lại giá trị đối tượng PDO khi thành công.

### Lỗi/ Ngoại lệ

**PDO::__construct()**ném ra một **PDOException**nếu cố gắng kết nối với yêu cầu cơ sở dữ liệu bị lỗi.



### Ví dụ

Tạo 1 ví dụ PDO thông qua gọi trình điều khiển



<?php/\* Connect to a MySQL database using driver invocation \*/$dsn='mysql:dbname=testdb;host=127.0.0.1';$user='dbuser';$password='dbpass';\
\
try {\
$dbh= newPDO($dsn,$user,$password);\
} catch (PDOException $e) {\
echo'Connection failed: '.$e->getMessage();\
}?>





Ví dụ # 2 Tạo một cá thể PDO thông qua việc gọi URI



Theo ví dụ giả định file`/usr/local/dbconnect tồn tại với quyền truy cập thư mục cho phép PHP đọc file.FIle chưa PDO DSN kết nối đến cơ sở dữ liệu DB2 thông qua trình điều khiển PDO_IDBC`

``

```
odbc:DSN=SAMPLE;UID=john;PWD=mypass
```

Tập lệnh PHP sau đó có thể tạo kết nối cơ sở dữ liệu bằng cách chuyển tham số uri: và trỏ đến tệp URI:

```
<?php
/* Connect to an ODBC database using driver invocation */
$dsn = 'uri:file:///usr/local/dbconnect';
$user = '';
$password = '';

try {
    $dbh = new PDO($dsn, $user, $password);
} catch (PDOException $e) {
    echo 'Connection failed: ' . $e->getMessage();
}

?>
```



Ví dụ # 3 Tạo một cá thể PDO bằng bí danh

Ví dụ sau giả định rằng php.ini chứa mục nhập sau để cho phép kết nối tới cơ sở dữ liệu MySQL chỉ sử dụng bí danh mydb:

```
[PDO]
pdo.dsn.mydb="mysql:dbname=testdb;host=localhost"
```

```
<?php
/* Connect to an ODBC database using an alias */
$dsn = 'mydb';
$user = '';
$password = '';

try {
    $dbh = new PDO($dsn, $user, $password);
} catch (PDOException $e) {
    echo 'Connection failed: ' . $e->getMessage();
}

?>
```

\
Bạch Thành Long tham khảo nguồn: <https://www.php.net/manual/en/pdo.construct.php>
