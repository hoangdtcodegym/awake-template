---
title: So sánh giữa MySQL và MS SQL Server
subtitle: so-sanh-mysql-va-ms-sql-server
category:
  - MySQL
author: Vu Minh Cuong
date: 2019-12-23T03:31:31.313Z
featureImage: /uploads/1_kz1xya9ba9p_8wprfry64q.jpeg
---
Trong khi phát triển các phần mềm ứng dụng, lập trình viên sử dụng cơ sở dữ liệu quan hệ để quản lý hệ thống (RDBMS) để thêm, đọc, cập nhật và xóa các dữ liệu back-end. Họ cũng vận dụng các RDBMS để tùy chỉnh các truy vấn trong ngôn ngữ (SQL) với các câu lệnh. Các nhà phát triển có thể tùy chọn từ một số RDBMS theo yêu cầu riêng của một số dự án.

Nhưng các sự lựa chọn của cơ sở dữ liệu sẽ khác nhau tùy vào lập trình viên. Phần lớn doanh nghiệp thương mại họ ưa thích sử dụng các hệ thống cơ sở dữ liệu mã nguồn mở để tiết kiệm chi phí. NHưng cũng có nhiều doanh nghiệp lớn họ lựa chọn RDBMS vì tính năng bảo mật nâng cao với các cơ chế bảo mật và các công nghệ mã hóa mới nhất.

Cả MySQL và MS SQL Server đều là cơ sở dữ liệu được sử dụng rộng rãi trong các doanh nghiệp. MySQL là một mã nguồn mở RDBMS, trong khi SQL Server là một sản phẩm của Microsoft. Microsoft cho các doanh nghiệp lựa chọn tùy vào ngân sách và nhu cầu phù hợp với mình. Các lập trình viên họ tùy hiểu sự khác biệt giua MySQL và MS SQL Server để lựa chọn RDBMS phù hợp cho dự án của mình.

## Sự khác biệt chính giua MySQL và MS SQL Server

**Hỗ trợ nền tảng**

SQL Server ban đầu được phát triển bởi Microssoft cho hệ điều hành Windows. Mới đây Microssoft đã cung cấp RDBMS trên LInux và Mac OS X (thông qua Docker).Vậy lên, các doanh nghiệp hiện có thể lựa chọn chạy hệ thống cơ sở dữ liệu trên ba nền tảng riêng biệt.Tuy nhiên sẽ có một số tính năng nhất định khi chạy SQL Server trên Linux và Mac OS X. Còn đối với MySQL các doanh nghiệp có thể chạy mượn mà trên các hệ điều hành phổ biến như Windows, Linux và Mac OS X.

**Hỗ trợ ngôn ngữ lập trình**

MySQL và SQL Server hỗ trợ nhiều loại ngôn ngữ lập trình. RDBMS hỗ trợ Java, PHP, C++, Python, Ruby, Visual Basic, Delphi, Go và R. Nhưng MySQL còn hỗ trợ thêm một sô ngôn ngữ khác như  Perl, Scheme, Tcl, Haskel và Eiffel. Sự hỗ trợ nhiều ngôn ngữ lập trình của MySQL làm cho nó trở lên phổ biến trong cộng đồng phát triển khác nhau.

**Công cụ lưu trữ**

MySQL hỗ trợ một số công cụ lưu trữ. Khi sử dụng MySQL, các lập trình viên có thể sử dụng các công cụ Plugin hỗ trợ. Ở những phiên bản trước của RDBMS chỉ hỗ trợ công cụ lưu trữ phi thương mại. Vì thế, các lập trình vien sử dụng phiên bản cũ cần nâng cấp cơ sở dữ liệu hệ thống lên phiên bản mới nhất. Tương tự, khi làm việc với SQL Server các nhà phát triển phải sử dụng công cụ lưu trữ duy nhất. Họ phải nâng cấp RDBMS lên phiên bản nhất để tận dụng tối đa công cụ lưu trữ được cải tiến. Việc hỗ trợ nhiều công cụ lưu trữ giusp MySQL ling hoạt hơn MS SQL Server.

**Lọc**

MySQl cho phép người dùng lọc ra các bảng, hàng, và người dùng theo một số cách. Nhưng nó lọc theo một các riêng lẻ. Trong qúa trình lọc dữ liệu, các nhà phát triển phải lọc từng bảng cơ sở dữ liệu bằng các chạy nhiều truy vấn. Ngược lại, SQL Server cho phép các nhà phát triển lọc theo hàng dựa trên hàng lọc cơ sở dữ liệu theo cơ sở dữ liệu. Ngoài ra, dữ liệu được lọc trong cơ sở dữ liệu được phân mảnh riêng. Do đó, các lập trình viên sẽ dễ dàng lọc nhiều hàng hơn mà không cần xem xét số lượng cơ sở dữ liệu.

**Sao lưu**

Trong khi sử dụng MySQL, nhà phát triển có thể sao lưu dữ liệu bằng các nén lại tất cả dữ liệu SQL bằng một số câu lệnh. Công cụ RDBMS cung cấp chặn cơ sở dữ liệu trong qúa trình sao lưa. Tính năng này làm giảm nguy cơ hỏng dữ liệu khi chuyển từ một phiên bản hoặc phiên bản MySQL sang phiên bản khác. Nhưng ngược lại, nó lại làm cho quá trình khôi phục dữ liệu tốn nhiều thời gian hơn do thực thi nhiều câu lệnh SQL. Khác với MySQL, SQL Server không chặn cơ sở dữ liệu trong khi sao lưu dữ liệu. Tính năng cho phép người dùng sao lưu và khôi phục lượng dữ liệu khổng lồ mà không mất thêm thời gian và công sức.

[\#VU_MINH_CUONG](#VU_MINH_CUONG)

nguồn: <https://medium.com/@mindfiresolutions.usa/a-comparison-between-mysql-vs-ms-sql-server-58b537e474be>
