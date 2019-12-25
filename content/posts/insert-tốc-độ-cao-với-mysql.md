---
title: Insert  tốc độ cao với MySQL.
subtitle: cách tăng tộc độ insert vào MySQL
category:
  - MySQL
author: Phạm Ngọc DIệu
date: 2019-12-25T16:30:17.846Z
featureImage: /uploads/1_kz1xya9ba9p_8wprfry64q.jpeg
---
Khi bạn cần insert hàng triệu bản ghi vào CSDL MySQL, bạn sẽ sớm nhận ra gửi từng câu lệnh INSERT không phải là giải pháp khả thi.\
MySQL có vài mẹo để tối ưu hóa INSERT , bạn có thể tham khảo tại [link](<https://dev.mysql.com/doc/refman/5.7/en/insert-optimization.html>).\
Ở đây tôi sẽ cố gắng tóm tắt 2 kỹ thuật chính để tải dữ liệu lên CSDL MysQL một cách hiệu quả.\
**LOAD DATA INFILE**

Nếu bạn đang tìm hiệu năng cơ bản, đây là giải pháp của bạn. LOAD DATA INFILE là một cách tối ưu hóa cấp độ cao. Câu lệnh đặc biệt của MySQL (MySQL-specific) trực tiếp chèn dữ liệu vào bảng từ một file CVS/TSV.\
Có hai cách để dùng LOAD DATA INFILE . Bạn có thể sao chép các file dữ liệu vào thư mục của máy chủ ( thường là /var/lib/mysql-files/) và chạy:

```
LOAD DATA INFILE '/path/to/products.csv' INTO TABLE products;

```



Trong trường hợp này, các file sẽ được đọc từ filesystem của máy khách, trong suốt quá trình sao chếp vào thư mục tạm thời của máy chủ và được import từ đó. Nói chúng nó nhanh như tải trực tiếp từ filesystem của máy chủ. mặc dù bạn cần bật tùy chọn này trên máy chủ của bạn.\
Có nhiều tùy chọn để LOAD DATA INFILE ,chủ yếu liên quan đến cách cấu trúc dữ liệu của bạn( như phân cách các trường, đính kèm,…). Bạn có thể tham khảo thêm tại [link ](<https://dev.mysql.com/doc/refman/5.7/en/load-data.html>):\
Mặc dù LOAD DATA INFILE là tùy chọn tốt nhất để tăng hiệu suất nhưng nó yêu cầu bạn cần chuẩn bị dữ liệu của bạn dưới dạng tệp văn bản phân tách bằng dấu phân cách. Nếu bạn không có các tệp như vậy, bạn có thể cần dùng thêm các công cụ, tài nguyên khác để tạo ra chúng, điều này có thể làm cho ứng dụng của bạn thêm phức tạp. May mắn thay có một cách để thay thế.\
**Extended inserts(chèn mở rộng)**

Một câu lệnh SQL insert như sau:

```
INSERT INTO user (id, name) VALUES (1, 'Ben');
```

\
Một INSERT mở rộng sẽ nhóm một số bản ghi thành một truy vấn duy nhất:

[](<>)

```
INSERT INTO user (id, name) VALUES (1, 'Ben'), (2, 'Bob');
```



\
Chìa khóa ở đây là tìm số lần insert tối ưu trên mỗi truy vấn để gửi. Sẽ không có một cách chúng cho tất cả nên bạn cần tìm ra một điểm chuẩn riêng cho dữ liệu của bạn để có hiệu suất cao nhất, hoặc đánh đổi giữa giới hạn dùng bộ nhớ/hiệu suất.\
Để tận dụng tối đa việc insert mở rộn, bạn nên:\
- Dùng các cấu lệnh prepared (chuẩn bị).\
- Chạy các cấu lệnh trong một phiên.

\
**Điểm chuẩn- The Benchmark**

Tôi đã chèn 1,2 triệu hàng, 6 cột hỗn hợp, trung bình 26 byte mỗi hàng. Tôi đã thử 2 cách phổ biến sau.\
- Máy khách và máy chủ trên cùng một máy, giao tiếp qua ổ cắm UNIX.\
- Máy khách và máy chủ trên các máy riêng biệt trên mạng Gigabit độ trễ thấp ( <0.1 ms).\
Để làm cơ sở cho việc so sánh. Tôi đã sao chép bảng bằng cách dùng INSERT… SELECT , mang lại hiệu suất 313,000 inserts/second.

\
**LOAD DATA INFILE**\
Một ngạc nhiên cho tôi, LOAD DATA INFILE đã chứng tỏ là nhanh hơn :.\
 LOAD DATA INFILE : 377,000 inserts/second.\
 LOAD DATA LOCAL INFILE trên mạng: 322,000 inserts/second.\
Sự chênh lệch giữa hai số trên dường như liên quan tới tốc độ truyền dữ liệu lên máy chủ, tệp dữ liệu có kích thước 53MiB, và chênh lệch thời gian giữa hai cách là 543ms, điều này cho thấy tốc độ truyền khoảng 780mbs, gần với tốc độ gigabit.\
Điều này có nghĩa là nhiều khả năng máy chủ MySQL không sử lý dữ liệu cho đến khi tệp được chuyển xong: tốc độ insert của bạn liên quan đến tốc độ truyền giữa máy khách và máy chủ, bạn sẽ cần tính đến nó nếu máy khách và máy chủ không nằm trên một máy.\
**Extended inserts**

Tôi đã dùng BulkInserter để đo tốc độ insert , một class PHP của thư viên mã nguồn mở tôi đã viết, với tối đa 10,000 inserts mỗi truy vấn.

![](/uploads/insert.png)

\
Chúng ta có thể thấy, tốc độ insert tăng khi số lần insert trên mỗi truy vấn tăng. Chúng ta đã tăng 6 lần hiệu trên localhost và 17 lần qua mang, so với INSERT một cách tuần tự.

\- 40,000 → 247,000 inserts/second trên localhost.\
 -12,000 → 201,000 inserts/second qua mạng.

\
Phải mất khoảng 1000 insert trên mỗi truy vấn để đạt được thông lượng tối đa trên cả hai trường hợp nhưng chỉ cần khoảng 40 insert trên mỗi truy vấn để đạt được 90% thông lượng trên localhost. đó là một sự đánh đổi tốt. Và cũng là mốc quan trọng để xác định việc hiệu suất giảm khi đưa vào nhiều hơn số lần insert trên mỗi truy vấn.\
Giá trị của extended inserts cao hơn khi insert qua mạng, bởi vì insert tuần tự là nguyên nhấn chính cho độ trễ của bạn.

[](<>)\
max sequential inserts per second ~= 1000 / ping in milliseconds

\
Độ trễ giữa máy khách và máy chủ càng cao, bạn càng được lợi nhiều khi dùng extended inserts.

**Kết luận.**\
Như mong đợi, LOAD DATA INFILE là cách ưa thích khi tìm kiếm hiệu năng cơ bản trên một kết nối. Nó yêu cầu bạn chuẩn bị tệp được định dạng đúng nên nếu bạn tạo ra nó trước ,và/hoặc khi chuyển , hãy đảm bảo tính cả nó khi đo tốc độ insert.\
Extended inserts mặt khác không yêu cầu một tệp tạm thời và có thể cho bạn khoảng 60% thông lượng như LOAD DATA INFILE, đó là một tốc độ insert hợp lý. Thật thù vị là nó không quan trong dù bạn tiến hành trên localhost hay qua mạng, việc dùng extended inserts luôn mang lại hiệu suất tốt hơn.\
Nếu bạn quyết định dùng extended insert hay kiểm tra kỹ với các mẫu dữ liệu thực tế và thử nghiệm một vài trương hợp với số lượng insert trên mỗi truy vấn khác nhau để tìm ra giá trị phù hợp.\
Cẩn thận khi tăng số insert trên mỗi truy vấn vì nó có thể cần bạn phải :\
- Phân bổ thêm bộ nhớ cho máy khách.\
- Cài đặt tăng max_allowed_packet trên máy chủ MySQL .

\
Và chú ý cuối cùng, theo Percona , bạn có thể đạt đươc hiệu suất cao hơn nữa bằng cách sử dụng các kết nối đồng thời, phân vùng và nhiều vùng đệm.\
Tham khảo thêm tại [link](<https://www.percona.com/blog/2011/01/07/high-rate-insertion-with-mysql-and-innodb/>) nhé.\
\
Nguồn: 

<https://medium.com/@benmorel/high-speed-inserts-with-mysql-9d3dcd76f723>
