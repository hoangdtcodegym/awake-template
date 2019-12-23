---
title: Refactor PHP
subtitle: tái cấu trúc trong php
category:
  - PHP
author: Hoàn Nguyễn
date: 2019-12-23T09:34:11.068Z
featureImage: /uploads/anhdep01.jpg
---
<!--StartFragment-->

**Các nhà phát triển tốt được xác định bởi chất lượng mã của họ**.Trong ngành công nghiệp phần mềm, viết mã tốt có nghĩa là tiết kiệm tiền có thể được đầu tư vào thử nghiệm, cập nhật, mở rộng hoặc sửa lỗi. Trong bài viết này, tôi sẽ cho bạn thấy các ví dụ thực tế về một số kỹ thuật và ý tưởng sẽ giúp bạn viết mã sạch của mình và tái cấu trúc lại nó để làm cho nó mạnh mẽ hơn và mô đun hóa. Những kỹ thuật này không chỉ giúp bạn tái cấu trúc mã cũ mà còn cung cấp cho bạn những ý tưởng tuyệt vời về cách viết mã sạch từ bây giờ.

**Tái cấu trúc là gì và tại sao chúng ta cần nó?** Tái cấu trúc đề cập đến các kỹ thuật và các bước giúp bạn viết mã sạch. Điều này rất quan trọng đối với các nhà phát triển khác, những người sau đó sẽ có thể đọc, mở rộng và sử dụng lại mã mà không cần phải chỉnh sửa nhiều.

Các dòng tiếp theo sẽ cho bạn thấy một số ví dụ về tái cấu trúc mã kế thừa và làm cho nó tốt hơn. Không bao giờ tái cấu trúc lại mã mà không có kiểm thử

Lời khuyên đầu tiên của tôi là đừng bao giờ bắt đầu tái cấu trúc mà không có kiểm thử.

**Tôi đoán lý do rất rõ ràng:** Bạn sẽ kết thúc với các chức năng bị hỏng rất khó khắc phục vì bạn sẽ không thể tìm ra những gì bị hỏng. Do đó, nếu bạn cần cấu trúc lại nó, hãy bắt đầu với thử nghiệm nó trước. Hãy chắc chắn rằng phần bạn sẽ tái cấu trúc được bao phủ bởi các bài kiểm tra. Kiểm tra phân tích mã PHPUnit.

\
**Bắt đầu tái cấu trúc từ mã của bạn.**Hãy nhìn vào bức ảnh tiếp theo. Đây là một dự án thực sự cho một hệ thống quản lý khách sạn mà tôi tìm thấy trên Github. Đây là một dự án nguồn mở thực sự thực sự code tệ nhất.

![](/uploads/0_o_xt7o_1witozjx9.png)

Như bạn có thể thấy trong phương pháp này, có ba cấp độ được đánh dấu màu đỏ. cnhất phải là câu lệnh if / other lồng trong điều kiện if đầu tiên. Thông thường, điểm sâu nhất là tập trung vào một logic duy nhất giúp dễ dàng cấu trúc lại.



**Như bạn có thể thấy trong phương pháp này,** có ba cấp độ được đánh dấu màu đỏ. Cấp độ bên trong phải là câu lệnh if/else lồng trong điều kiện if đầu tiên. Thông thường, cấp độ cuối là tập trung vào một logic duy nhất giúp dễ dàng cấu trúc lại.



**Làm cho các phương thức của bạn ngắn hơn bằng** cách chia chúng thành các phương thức nhỏ hơn hoặc các tệp cấu hình file/DB table

Có thể, trong trường hợp này, chúng ta có thể trích xuất nó thành một phương thức riêng tư như sau:

![](/uploads/1.png)

Bây giờ, hãy xem phương thức add () sau khi tái cấu trúc các phần khác. Nó là nhiều sạch hơn, có thể đọc và kiểm tra.

![](/uploads/2.png)

Luôn sử dụng {} trong câu lệnh if..else

**Hầu hết các ngôn ngữ lập trình đều hỗ trợ** một câu lệnh if và một số nhà phát triển sử dụng nó vì nó đơn giản, tuy nhiên, nó không thể đọc được và dễ gây ra sự cố do chỉ một dòng trống có thể phá vỡ điều kiện và bắt đầu gặp sự cố. Xem sự khác biệt giữa hai ví dụ:

![](/uploads/3.png)

**Không sử dụng số magic number & magic string.**

Trong ví dụ tiếp theo, bạn nhận thấy nếu có hơn 250, nó sẽ trả về một thông báo lỗi. Trong trường hợp này, 250 được coi là một con số ma thuật. Nếu bạn không phải là nhà phát triển đã viết nó, sẽ rất khó để tìm ra những gì nó đại diện.

![](/uploads/5.png)

\
**Để tái cấu trúc lại phương pháp này, chúng ta có** thể hình dung ra 250 là số phòng tối đa. Do đó, thay vì mã hóa nó, chúng ta có thể trích xuất nó thành biến $maxAvAvailableRooms. Bây giờ, nó dễ hiểu hơn đối với các nhà phát triển khác.

![](/uploads/6.png)

**Không sử dụng các câu lệnh khác nếu bạn không cần:** Trong cùng một hàm availablerooms () bạn nhận thấy câu lệnh if, trong đó chúng ta có thể dễ dàng loại bỏ phần khác và logic vẫn sẽ giống nhau.

![](/uploads/7.png)

**Sử dụng tên có ý nghĩa cho các phương thức,** biến và kiểm tra của bạn Trong ví dụ sau, bạn có thể thấy rằng có hai phương thức từ hệ thống quản lý khách sạn có tên là "index () và room_m ()". Đối với tôi, tôi không thể xác định mục đích của họ là gì. Tôi nghĩ sẽ dễ hiểu hơn nếu tên của họ được mô tả.

![](/uploads/8.png)

**Sử dụng các khả năng tối đa của ngôn ngữ lập trình của bạn** Nhiều nhà phát triển không sử dụng toàn bộ khả năng của ngôn ngữ lập trình họ sử dụng. Nhiều trong số các tính năng này có thể giúp bạn tiết kiệm rất nhiều nỗ lực và làm cho mã của bạn mạnh mẽ hơn. Hãy xem các ví dụ tiếp theo và chú ý làm thế nào có thể dễ dàng đạt được kết quả tương tự với ít mã hơn bằng cách chỉ sử dụng gợi ý loại.

![](/uploads/9.png)

![](/uploads/10.png)

**Nguồn từ:** <https://medium.com/hackernoon/refactor-your-php-legacy-code-real-projects-examples-da9edf03ff4b>

<!--EndFragment-->
