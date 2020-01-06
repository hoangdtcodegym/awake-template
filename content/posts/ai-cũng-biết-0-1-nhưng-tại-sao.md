---
title: Ai cũng biết 0! = 1 nhưng tại sao?
subtitle: >-
  Tại sao 0! = 1? Không có gì trên đời này xảy ra mà không có mục đích, nhưng
  mục đích của việc 0! = 1 là gì? Tại sao lại như thế? Bài viết này sẽ giải đáp
  thắc mắc này giúp bạn.
category:
  - Mathematic
author: Hai Tran
date: 2020-01-06T14:23:24.639Z
featureImage: /uploads/maxresdefault.jpg
---
Nếu như văn học là nơi bạn miêu tả, ca tụng thế giới hiện thực hay trong cả tưởng tượng bằng những câu chữ, hội họa là bằng những nét vẽ và màu sắc, thì toán học là nơi mà con người hiện thực hóa tất cả, tất cả mọi thứ bằng những con số. Thủa xa xưa, khi mà tổ tiên chúng ta còn đi bằng 4 chân, con người đã là một giống loài tò mò, chính sự tò mò muốn tìm hiểu và lí giải những thứ mà nó không hiểu đã giúp giống  loài ấy sáng tạo ra những con số và qua đó tìm hiểu và lí giải thế giới này qua chúng.

Toán học là một thứ rất thú vị và không hề khô khan như chúng ta nghĩ. Nó rất tươi mới, nhiều màu sắc và cực kì thú vị. Và khi bạn đủ yêu, đắm chìm vào nó đủ lâu, bạn sẽ thấy toán học vẫn rất thơ mộng và bay bổng không kém gì những vần thơ trong văn học. Chỉ là trường học của chúng ta hiện tại đang không thực sự diễn tả đúng về thứ được gọi là toán  học, chúng ta đôi khi được dạy những thứ đơn giản từ cộng trừ nhân chia đến các quy tắc cần ghi nhớ như 1 x 0 = 0, a^0 = 1 hay hằng tỉ những thứ khác một cách máy móc mà không hề biết taị sao chúng lại như thế và như thế để làm gì. Nếu như bạn đã từng không chỉ một lần thắc mắc câu hỏi: tại sao 0! = 1, taị sao a^0 = 1 thì bài viết này sẽ là nơi giải đáp thắc mắc này của bạn.

Bắt đầu bằng số mũ trước nhé. Ai cũng biết:\
 a^n = a\*a\*a\*.....\*a    tức lặp lại việc nhân a n lần.

Thế a^0 thì sao? Kết quả của việc nhân a với a với 0 lần? Đây có vẻ như là một câu hỏi khó có thể trả lời, nó nghe sai sai và cái gì khó bỏ qua, chúng ta nghĩ ngay đến việc kết quả là không xác định, a^0 = undefine . Nhưng không, toán học bắt chúng ta thừa nhận trường hợp đặc biệt rằng a^0 = 1. Thì, cũng được đi, các nhà toán học đi trước đã nói thế thì chắc là nó như thế rồi. Nhưng tại sao? Cơ sở nào cho việc a^0 lại bằng 1 được nhỉ?

Quay lại định nghĩa, chúng ta có a^n = a\*a\*....\*a (số a được nhân n lần) , và nó cũng tương đương với: a^n = a\*a^(n-1);

Ta có: 

a^n = a*a^(n-1)

a^(n-1) = a*a^(n-2)

...........

a^1=a*a^0;

a^0=a*a^-1=1



Và tương tự đối với n!, ta có: 

n! = 1\*2\*3\*....(n-1)\*n = n*(n-1)!

......

2!=2 * 1!

1!=1*0!=1

\=> 0! = 1

Hay với một cách giaỉ thích khác, đau đầu hơn, mà tôi đã được đọc đâu đấy trên mạng. Chúng ta biết n! là số các hoán vị có thể có được của n phần tử khác nhau. Vậy 0! sẽ là số các hoán vị có thể có của 0 phần tử khác nhau. Một tập rỗng không có phần tử nào , nghe như kết quả sẽ là 0. Nhưng không, nghĩ thoáng ra một chút, chúng ta sẽ thấy việc không thể thay đổi hoán vị nào của một tập rỗng, nghĩa là vốn dĩ nó đã có 1 hoán vị cho nó rồi. Điều này nghe có vẻ rối não, nhưng bạn có thể tưởng tượng nó ngang với việc chúng ta có 1 tập 1 phần tử chẳng hạn, vì nó có 1 phần tử nên chỉ có 1 hoán vị duy nhất cho chính nó, tập rỗng cũng tương tự vậy. Và điều đó có nghĩa là 0! = 1. 

Những điều ở phía trên thật sự thần kì. Nó làm cho toán học trở nên cực kì thú vị trong mắt tôi. Những điều này tạo nên một sự nhất quán cho các quy luật toán học. Nó mang lại rất nhiều ý nghĩa trong việc hiểu và vận dụng chúng trong các bài toán thực tế , và đương nhiên, thuận tiện nhiều cho việc tính toán của chúng ta.Điều tuyệt vời là với những thứ đơn giản. 

Albert Einstein - "If you can't explain it simply, you don't understand it well enough". Tạm dịch: nếu bạn không thể giải thích nó một cách đơn giản nghĩa là bạn chưa thực sự hiểu về nó. Và, hi vọng qua bài viết này bạn đã có thể đạt được đến trình độ hiểu cơ bản của Enstein về một vấn đề nhỏ trong toán học này và trở nên yêu thích toán học hơn.

[](<>)
