---
title: PHP không phải một ngôn ngữ lập trình
subtitle: program language
category:
  - PHP
author: Phạm Ngọc Diệu
date: 2020-01-24T04:10:39.781Z
featureImage: uploads/0_o_xt7o_1witozjx9.png
---
Trong những năm gần đây, PHP không đạt được một tiếng tăm tốt, thay vào đó nó luôn bị chỉ trích và nhận được những cái nhăn mặt. Một số đã đi xa tới mức không coi nó là một ngôn ngữ lập trình.

Chúng ta đều đã ở đó, bạn nghe từ PHP và thứ đầu tiên xuất hiện trong đầu bạn là một đoạn code lộn xộn, nơi mọi thứ được trộn lẫn với nhau. Hãy nhìn ví dụ sau:\
![Messed up PHP code](https://blog.spark-it.fr/wp-content/uploads/2018/07/screenshot-003.png)

Trong một file bạn có thể thấy các session , các thẻ HTML, định dạng CSS, và trong hầu hết trường hợp còn có các truy vấn SQL và cả quản lý hệ thống file. Nó có thể được gọi là bất cứ điều gì ngoại trừ là mã tốt, nó là một ác mộng trong thế giới web. 

Phần buồn là mọi người có xu hướng đổ lỗi cho PHP thay vì các lập tình viên.

PHP trở lên nổi tiếng vì nó yêu cầu đầu vào thấp, bất cứ lập trình viên mới nào có thể nhanh chóng code với nó nhờ vào phẩn hồi nhanh mà họ nhân được và cộng đồng lớn xung quanh nó, đồng thời cũng vì PHP không có nhiều yêu cầu các thứ các laaoj trình viên không thể có. Bạn có thể bắt đầu với bắt cứ *AMP nào mà bạn giỏi (LAMP, MAMP, WAMP tương ứng với Linux, MacOS, và Windows) . Và loại mã chúng ta vừa thấy có xu hướng là của một người vừa học PHP.

Vào 1/3/2012, một chương trình quản lý phụ thuộc PHP lấy cảm hứng từ NPM đã được công bố với tên gọi "Composer". Nó được phát triển bởi Nils Adermann và Jordi Boggiarno.

Trước sự xuất hiên của Composer, mọi lập trình viên PHP có một đống tệp và thư viện để nhúng trong mọi và mỗi dự án, theo cách này, nó phụ thuốc vào sự quản lý và hoàn toàn thủ công, và nó hoàn toàn hỗ loạn, rất ít khi tồn tại các phiên bản(version) trong quá trình thủ công, rất nhiều code thừa,..

Nhưng với sự xuất hiện của Composer, có rất nhiều thay đổi, bây giờ bạn có thể định nghĩa các yêu cầu chính xác của bạn trong phạm vi các phiên bản( rất quan trong trong các mội trường dựa trên SemVer) và có thể cài lại chính xác phiên bản bạn muỗn khi cần. composer quản lý tất cả các rắc rối của bạn và tự động tải tất cả các thu viện, tất cả những gì bạn cần được nhúng trong 1 file và bạn có thể tiếp tục công việc của mình mà không cần bạn tâm tới nó nữa.

Với ý nghĩa đó, PHP đang trở thành một ngôn ngữ được thiết lập tốt với công đồng lớn xung quanh nó và một bộ tiêu chuẩn rất nghiêm ngặt gọi là PSR.\
\
*PSR ( PHP standard Recommendation ) là một tiêu chuẩn code của PHP được công bố bởi PHP Framework Interop Group.  Nó tiêu chuẩn hóa các khái niệm, đối tượng lập trình trong PHP. Mục đích là cho phép khả năng tương tác giữa các thành phần và cung cấp một cơ sở kỹ thuật chung để thực hiện các khái niệm đã được chứng minh, để nhằm tối ưu việc lập trình và kiểm thử. PHP-FIG được tao ra bởi một số nhà sáng lập PHP Framework.*

Các lập trình viên không bị bắt buộc phải tuân thủ nghiêm ngặt các PSR, nó là một cố gắng để tránh làm mất hoặc thay đổi các code hiện tai. Nhưng nó được đề nghị cho các phiên bản mới và các dự án có số lượng quy tắc lớn. Ví có thể hơi khó để áp dụng tất cả, điều này phụ thuộc vào dự án, các lập trình viên, nhóm,...

Một vài quy tắc PSR có thể rất đơn giản, chúng thậm chí có thể thực hiện tự động, ví du như PSR-1 và PSR-2 miêu tả cách code nên được viết, các tiêu chuẩn này có thể được kiểm tra bẳng PHPCS ( PHP code sniffer) và lỗi có thể đươc sửa chữa tự động, nó được tích hợp tròn phần lớn IDE hiện nay.

Các quy tắc khác có một chút nâng cao và khó chuẩn hóa hơn, và đươc định hướng cho các nhà sáng tạo framework thay vì lập trình viên. Ví dụ như PSR-11, miêu tả một interface rất đơn giản với chỉ 2 phương thức để tạo ra một container, nhưng trước khi dùng nó bạn cần có kinh nghiệm về SOLID ( không phải chơi chữ) và hiểu sâu sắc các khai niệm về OOP và có kinh nghiệm , thực hành lập trình tốt. Chẳng hạn như tiệm sự phụ thuộc ( dependency injection) và đâỏ ngược kiểm soát (inversion of control),... ( nguyên tắc thiết kế S.O.L.I.D là một  điểm khởi đầu tốt mặc dù có chút vấn đề).

Vid thế ngày nay PHP framework được liên kết lại nhờ FIG và cộng đồng. Nó ngày càng có tổ chúc hơn và vẫn đnag phát triển nhanh chóng. Và chỉ để so sánh tôi xin giới thiệu cho các bạn một mẫu code PHP tốt sau:\
![Well written PHP code](https://blog.spark-it.fr/wp-content/uploads/2018/08/screenshot-001.png) 





Cuối năm hơi chán học, vừa hay thấy bài này nên dịch coi như kết thúc modul2, bắt đầu modul 3 vậy :)

Nguồn: <https://blog.spark-it.fr/en/2018/08/php-is-not-a-programming-language/>
