---
title: SQL vs NoSQL. Chúng khác nhau thế nào
subtitle: SQL vs NoSQL
category:
  - MySQL
author: Phạm Ngọc Diệu
date: 2019-12-23T03:45:31.381Z
featureImage: /uploads/about-hero.jpg
---
Khi chọn cơ sở dữ liệu, một trong những quyết định quan trọng nhất là chọn loại cơ sở dữ liệu dùng cấu trúc kiểu quan hệ (SQL) hay các loại cơ sở dữ liệu không dùng cấu trúc dữ liệu quan hệ (NoSQL). Trong khi cả hai đều là những lựa chọn khả thi, có những khác biệt giữa chúng người dùng cần nhớ khi đưa ra chọn lựa.\
Ở đây chúng ta sẽ đưa ra những điểm khác biệt quan trọng nhất giữa chúng.\
**Những điểm khác biệt lớn nhất giữa SQL và NoSQL.**\
**Ngôn ngữ**Hãy nghĩa về một thành phố ( tạm gọi là A), nơi tất cả mọi người nói chung một ngôn ngữ, tất cả các doanh nghiệp được xây dựng quanh nó, các hoạt động giao tiếp đều dùng nó. Nói ngắn gọn đó là cách duy nhất để các cư dân có thể hiểu và tương tác với thế giới xung quanh.Thay đổi ngôn ngữ tại một nơi nào đó sẽ gây xáo trộn và rắc rối cho mọi người.\
Giờ hãy nghĩ về một thành phố khác ( thành phố B) , nơi mỗi gia đình, nói một loại ngôn ngữ khác, mọi người tương tác với thế giới theo cách khác nhau, và không có một ngôn ngữ, một sự thấu hiểu hay thiết lập một cách tổ chức chung. Nếu một gia đình khác đi, nó sẽ không ảnh hưởng đến bất kỳ ai.\
***Cơ sở dữ liệu SQL*:**sử dụng ngôn ngữ truy vấn cấu trúc (SQL) để dịnh nghĩa và thao tác với dữ liệu. Một mặt nó vô cùng hiệu quả: SQL là một trong những lựa chọn tiện lợi, được sử dụng rộng rãi và đa năng nhất. Điều đó làm cho nó thành một lựa chọn an toàn, đặc biệt trong những truy vẫn phức tạp. Mặt khác, nó có những hạn chế. SQL yêu cầu bạn sử dụng các lược đồ, cấu trúc được xác định trước để xác định cấu trúc dữ liệu của bạn trước khi bạn làm việc với nó. Ngoài ra tất cả dữ liệu của bạn cần theo cùng một cấu trúc. Điều này có thể yêu cầu rất nhiều chuẩn bị trước, và ở thành phố A, điều này có nghĩa là thay đổi cấu trúc sẽ vừa rất khó vừa gây rối thậm chí đổ vỡ toàn bộ hệ thống.\
***Cơ sở dữ liêu NoSQL :***No SQL một mặt có cấu trúc động cho dữ liệu phi cấu trúc, và dữ liệu được lưu theo nhiều cách. Cúng có thể là theo hướng côt ( column-oriented, hướng tại liệu (document – orient ) hoặc theo kiểu đồ thị (graph-based), hoặc tổ chức thành dạng KeyValue (KeyValue Store). Sự linh hoạt này cho phép:\
- Bạn có thể tạo các tài liệu mà không cần định nghĩa cấu trúc của chúng trước.\
- Mỗi tài liệu có thể có cấu trúc riêng củ nó.\
- Cú pháp có thể thay đổi từ cơ sử dữ liệu này tới cơ sở dữ liệu khác\
- Và bạn có thể add thêm các trước khác nếu muốn.

**Khả năng mở rộng.**Trong hầu hết các trường hợp, cơ sở dữ liệu SQL có thể mở rộng theo chiều dọc, nó có nghĩa là bạn có thể tăng tải của mộ server bằng cách tăng những thứ như CPU, RAM, hoặc SSD. Cơ sở dữ liệu NoSQL mặt khác có khả năng mở rộng theo chiều ngang. Nó nghĩa là bạn có thể xử lý lưu lượng nhiều hơn bằng cách tách hoặc tăng thêm server cho cơ sở dữ liệu NoSQL của bạn.Nó giống như thêm các tàng cho cùng một tòa nhà và thêm các tòa nhà cho một khu phố vậy. Cái sau có thể trở nên lớn và mạnh hơn. Điều đó khiến chó NoSQL thành lựa chọn ưu tiên cho các tập dữ liệu lớn hoặc dễ thay đổi.\
**Cấu trúc**

Cơ sở dữ liệu quan hệ được tổ trức theo dang bảng, trong khi NoSQL theo các kiểu như dựa trên văn bản, các cặp key-value, cơ sở dữ liệu đồ thị, hoặc các cột rộng. Nó làm cho cơ sở dữ liệu quan hệ SQL là một lựa chọn tốt hơn cho các ứng dụng yêu cầu các phiên làm việc với nhiều nhiều hàng , ví dụ như hệ thống kế toán hoặc các hệ thống được xây dựng từ cấu trúc quan hệ.\
Một vài ví dụ về SQL có thể kể tới như: MySQL.,Oracle, PostgreSQL, và Microsoft SQL server. Ví dụ về các hệ thống NoSQL như : MonGoDB, BigTable, Redis, RavenDB, Cassandra, Hbase, Neo4j và CouchDB.\
Bài viết còn khá dài nhưng phần sau là giới thiệu thêm về các hệ thống trên + do lười nên ai có nhu cầu vào link xem nhé.\
Nguồn: <https://www.xplenty.com/blog/the-sql-vs-nosql-difference/>
