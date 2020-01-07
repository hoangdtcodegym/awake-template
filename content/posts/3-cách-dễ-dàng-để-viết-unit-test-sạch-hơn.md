---
title: 3 cách dễ dàng để viết unit test sạch hơn.
subtitle: unit test
category:
  - Technology
  - Algorithm
author: Phạm Ngọc Diệu
date: 2020-01-07T16:09:27.902Z
featureImage: /uploads/0_o_xt7o_1witozjx9.png
---
Chúng ta đều biết rằng rất khó để viết những unit test tốt. Mọi người cùng gặp vấn đề tại một số điểm. Nhưng điều đó không có nghĩa là những bài test tầm thường của bạn khó đọc. Đây là 3 lời khuyên có thể tạo ra điều khác biệt và giúp những bài test bình thường được đơn giản, sạch và thông minh hơn.

1. One test, one function. 

   Đừng lồng nhiều test vào một function như thế này:

   ```
   public void testBasicStuff() {
      Bar bar = makeBar(); 
      Bar expectedBar = makeBar().setBuzzer(3); 
      runBuzzProgram(bar); 
      assertThat(bar).isEqualTo(expectedBar); 
      Bar expectedBar2 = makeBar().setBuzzer(6); 
      runBuzzProgram(bar); 
      assertThat(bar).isEqualTo(expectedBar2); 
      Bar expectedBarFinal = makeBar().setBuzzer(0);
      runBuzzShutdownProgram(bar);
      assertThat(bar).isEqualTo(expectedBarFinal);
      }
   ```

   Kết hợp 3 bài test với nhau là không thuận tiện vì:

* Nó sẽ làm bài test trở lên mơ hồ, liệu chất liệu, thành phẩn của bài test thứ nhất có ảnh hưởng tới bài test thứ hai và thứ ba không.
* Trạng thái bắt đầu của test thứ hai va thứ ba không rõ ràng, như kiểu “ Bất cứ trạng thái nào sau khi test thứ nhất kết thúc”. Điều này làm nó khó hiểu hơn. Để khắc phục, rõ ràng phải thiết lập rõ trạng thái bắt đầu cho test thứ 2 và thứ 3.

  ```
   public void testOne() {
      Bar bar = makeBar();\
      Bar expectedBar = makeBar().setBuzzer(3);\
      runBuzzProgram(bar);\
      assertThat(bar).isEqualTo(expectedBar);\
    }
    
    public void testTwo() {   // Here, we set up the same state that test #1 ended in.
      Bar bar = makeBar().setValue(3);
      Bar expectedBar2 = makeBar().setBuzzer(6);\
      runBuzzProgram(bar);\
      assertThat(bar).isEqualTo(expectedBar2);  
      }
      
    public void testThree() {\
      // Here, we set up the same state that test #2 ended in.   Bar bar = makeBar().setValue(6);
      Bar expectedBarFinal = makeBar().setBuzzer(0);
      runBuzzShutdownProgram(bar);
      assertThat(bar).isEqualTo(expectedBarFinal);
    }
  ```

    Lưu ý là cách để làm cho trạng thái bắt đầu của bài test rõ ràng hơn cũng sẽ làm cho bài test đơn giản , dễ hiểu hơn, và để đọc mỗi test, chúng ta chỉ cần nhìn vào 4 dòng code thôi.  Bạn  muốn đọc phiên bản này hay không ?

2. Good test name.

   ```
   public void testBasicFunctionality() {
   ```

    Thật xấu hổ khi nhìn thấy những test có tên như trên. Khi mà bạn có thể  thấy chúng như sau:

   ```
   public void testMyFunc_updatesBar_inExpectedGeneralCase() {
        ...
      }

   public void testMyFunc_updatesBar_whenFooServiceReturnsError() {
        ...
      }
   ```

Ở đây tôi không cần đọc đầy đủ bài test để biết chúng ta đang test cái gì , bời vì chúng ta đã cho bài test một cái tên rõ nghĩa. Cá nhân tôi thích đặt tên bài test theo cấu trúc như sau:

```
public void testSYSTEM_BEHAVIOR_CONDITION() {
```

Ví dụ

```
public void testAuthenticate_rejectsUser_whenBadCredentialsProvided() {
```

3.AAA: Arrange , Act, Assert

Arrange: Thiết lập test, giả lập RPGs, điền giữ diệu giả,…

Act: Chạy các chức năng được kiểm thử.

Assert: Kiểm tra các trạng thái dự kiến.

```
public void testMyFunc_updatesBar() {
Bar bar;
Bar expectedBar = makeBar().setBuzzer(3);
myFunc(bar);
assertThat(bar).isEqualTo(expectedBar);
}
```

Đoạn code trên, mặc dù chỉ có 4 dòng, vẫn có thể gây nhầm lẫn, mơ hồ một chút.  Bời vì AAA không tách rời. Tại sao `expectedBar`được khai báo ở đầu? Có phải nó được dùng trong `myFunc()` ? Khi nào thiết lập hoàn thành và khi nào thì bài test thực sự chạy.? Bạn có thể ngăn chặn tất cả những mơ hồ đó bằng cách tách thành 3 bước riêng biệt trong code của bạn:

```
public void testMyFunc_updatesBar() {
  Bar bar;  myFunc(bar);  Bar expectedBar = makeBar().setBuzzer(3);
  assertThat(bar).isEqualTo(expectedBar);
}
```

Đây là một ví dụ khác, lần này trên Python,:

```
class MyTestCase(unittest.TestCase):

  testFoo_ShouldUpdateBarService_ForUserWithExistingBaz(self):
    # foo calls the Garble service internally, so we mock the response.
    supposeGarbleServiceReturns(EXPECTED_GARBLE_RESPONSE);
    user = makeSimpleUserWithExistingBaz();
  
    foo(user);
  
    # Ensure Bar was updated to contain the recent user.
    self.assertIn(user.id, (u.id for u in bar_service.recentUsers()));
```

Chúng ta không thể thấy`foo ()` làm gì hay `supposeGarbleServiceReturns()` làm cái gì và cả `makeSimpleUserWithExistingBaz ()`nữa, nhưng bạn có thể ngay lập tức nhận ra cái gì đang diễn ra ở đây vì bài test có một cái tên rõ nghĩa.  Đó là 3 bước riêng biệt và nó là những chú thích phù hợp.

Không cách  nào trong 3 cách trên  yêu cầu bất kỳ loại refactor hay debugging nào để thực hiện. Ngay cả trong các code hiện tại.Tuy nhiên tác động của chúng đến việc đọc và bảo trì của các bộ test lớn có thể rất lớn. Vậy nên vì lợi ích của đồng nghiệp hay ai đó một ngày nào đó sẽ kế thừa code của bạn, làm ơn hãy định dạng lại unit test của bạn.

Nguồn: <!--StartFragment-->

<https://blog.usejournal.com/3-easy-ways-to-write-cleaner-unit-tests-2ec04ca6b9df>

<!--EndFragment-->
