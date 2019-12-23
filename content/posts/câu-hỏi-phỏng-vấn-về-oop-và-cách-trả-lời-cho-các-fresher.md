---
title: Câu hỏi phỏng vấn về OOP và cách trả lời cho các Fresher.
subtitle: >-
  Bạn sắp đi phỏng vấn hoặc đơn giản là chỉ muốn biết khi phỏng vấn người ta sẽ
  hỏi những gì? Đọc ngay bài viết để có thể trang bị những câu trả lời cần thiết
  về OOP cho các fresher cần.
category:
  - PHP
author: HaiTran
date: 2019-12-23T03:06:58.800Z
featureImage: /uploads/about-hero.jpg
---
## 1. OOP là gì?

\- OOP là từ viết tắt của Object Oriented Programing , một phương pháp lập trình mà ở đó các chương trình được coi là tập hợp các đối tượng. Mỗi đối tượng là thể hiện của một lớp (class).

## 2. Các đặc tính cơ bản của OOP?

\- Các đặc tính cơ bản của OOP là:

* Tính trừu tượng.
* Tính kế thừa.
* TÍnh đóng gói.
* Tính đa hình.

## 3. Lớp là gì?

\- Lớp có thể hiểu đơn giản là đại diện của một loại đối tượng. Nó là một bản kế hoạch, một bản mẫu hay bản thiết kế diễn tả đối tượng.

## 4. Đối tượng là gì?

\- Đối tượng là một thể hiện của lớp và nó có thuộc tính, hành vi và bản sắc riêng.

## 5. Tính đóng gói là gì?

\- Tính đóng gói là một đặc tính của OOP, nó đảm bảo cho thông tin của đối tượng luôn được che giấu. Các thông tin được ẩn giấu ấy bị giới hạn sử dụng trong phạm vi các thành viên của lớp ấy.

\- Có các mức độ che giấu là: public, protected, private, internal và protected internal.

## 6. Tính đa hình là gì?

\- Tính đa hình là việc các hành vi , thuộc tính của lớp con có thể thay đổi, không còn rập khuôn trong một khuôn mẫu của lớp cha khi các hành vi và phương thức ấy không còn phù hợp.

Hiểu đơn giản, tính đa hình làm cho các đối tượng không bị rập khuôn trong một khuôn mẫu giống nhau.

## 7. Tính kế thừa là gì?

\- Tính kế thừa là một khái niệm chỉ việc một lớp có thể chia sẻ kiến trúc, phương thức và thuộc tính cho một class khác. Nếu việc kế thừa chỉ được thực hiện trên một class thì nó được gọi là kế thừa đơn , còn nếu nó có thể được thực hiện trên nhiều class khác nhau thì nó được gọi là đa kế thừa.

## 8. Manipulator là gì?

\- Manipulator là các hàm có thể được sử dụng kết hợp với các toán tử “<<” và “>>” trên một đối tượng. Ví dụ như endl và setw.

## 9. Định nghĩa một phương thức khởi tạo trong OOP?

\- Phương thức khởi tạo (constructor) là một phương thức được sử dụng để khởi tạo các thuộc tính của một đối tượng và được gọi ngay khi đối tượng được tạo ra. Các quy định cho phương thức khởi tạo là:

* Tên của phương thức khởi bạo phải là tên của một lớp.
* Phương thức khởi tạo không thể là một phương thức có trả về.

## 10. Định nghĩa một phương thức hủy?

\- Phương thức hủy là một phương thức được tự động gọi khi một đối tượng đã được sử dụng xong hoặc bị hủy bỏ. Tên của phương thức hủy cũng phải trùng với tên class nhưng với dấu ngã “~” ở phía trước tên.

## 11. Nội hàm (Inline function) là gì?

\- Nội hàm là một kĩ thuật được sử dụng bởi trình biên dịch và “” để chèn nội dung của hàm vào hàm được sử dụng trong mã nguồn chương trình.

## 12. Nạp chồng là gì?

\- Nạp chồng là việc một phương thức, thuộc tính có tên giống nhau nhưng khác nhau về số lượng và loại tham số. Toán tử “-” , “*” có thể được sử dụng để nhảy qua các phương thức và nó có một làn ưu tiên thực hiện riêng.

## 13. Lớp trừu tượng là gì?

\- Một lớp trừu tượng là một lớp không thể được khởi taọ. Việc khởi tạo đối tượng từ một lớp trừu tượng là bất khả thi, nhưng nó lại có thể được kế thừa. Một lớp trừu tượng có thể chỉ chứa duy nhất một phương thức trừu tượng. Java chỉ cho phép các phương thức trừu tượng được ở bên trong lớp trừu tượng trong khi các ngôn ngữ khác vẫn có thể cho phép các phương thức không phải là trừu tượng ở bên trong nó.

## 14. Thế nào là interface?

\- Một interface có thể hiểu là một tập hợp các phương thức trừu tượng. Nếu lớp thực thi một interface thì nó sẽ kế thừa tất cả các phương thức trừu tượng trong interface đấy.

## 15. Xử lí ngoại lệ là gì?

\- Xử lí ngoại lệ là một sự kiện xảy ra trong suốt quá trình thực thi chương trình. Các xử lí ngoại lệ có hai loại: Ngoại lệ thời gian chạy và ngoại lệ lỗi. Những ngoại lệ này được xử lí thông qua các cơ chế xử lí ngoại lệ như try, catch và throw.

## 16. Thế nào là thực thi đa hình?

\- Thực thi đa hình (Run time polymorphism) cũng được biết đến như việc ghi đè phương thức trong lúc được gọi đến một phương thức bị ghi đè được giải quyết trong suốt thời gian thực thi, không phải trong thời gian biên dịch. Điều này có nghĩa là có hai hoặc nhiều phương thức cùng tên, cùng chữ kí nhưng khác thực thi.

## 18. Phương thức khởi tạo sao chép là gì?

\- Đây là một phương thức khởi tạo đặc biệt cho việc tạo một bản copy của đối tượng từ một đối tượng đã tồn tại. Sẽ luôn chỉ có một phương thức khởi tạo sao chép được xác định bởi hệ thống hoặc người dùng.

## 19. Sự khác nhau giữa lớp và đối tượng?

\- Một đối tượng là thể hiện của một lớp. Các đối tượng nắm giữ tất cả các thông tin trong khi class thì không. Các thuộc tính và phương thức được định nghĩa trong class được thực thi và sử dụng trong các đối tượng.

\-Các lớp có thể có các lớp con kế thừa trong khi đối tượng thì không.

## 20. Khác biệt giữa cấu trúc (structure) và lớp?

\- Quyền truy cập của cấu trúc được mặc định là public nhưng loại truy cập của lớp là private. Một cấu trúc được sử dụng cho một nhóm các dữ liệu nơi các lớp có thể sử dụng cho nhóm dữ liệu và các phương thức. Các cấu trúc duy nhất được sử dụng cho dữ liệu và nó không đòi hỏi sự nghiêm ngặt trong việc xác nhận truy cập nhưng các lớp lại được sử dụng để đóng gói và kế thừa dữ liệu, thứ đòi hỏi sự nghiêm ngặt trong việc này.

\#Translate from https://medium.com/dot-net-tutorial/oops-interview-questions-with-answers-for-freshers-b2a568ed364b
