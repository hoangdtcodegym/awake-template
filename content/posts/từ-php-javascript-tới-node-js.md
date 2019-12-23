---
title: 'Từ PHP, JavaScript tới Node.js'
subtitle: Công nghệ thay đổi từng ngày. Chúng ta phải thích nghi với chúng
category:
  - Technology
author: Vincent Desmares
date: 2019-12-23T03:31:40.793Z
featureImage: /uploads/inside-glacier-cave-2.jpg
---
Tôi đã làm một PHP developer hơn 10 năm và gần đây tôi đã chuyển sang một môi trường khác - JS full stack. Tôi quen dần với JavaScript. Tôi học cú pháp jQuerry, rồi phần mềm Angular và cuối cùng bắt đầu sử dụng React.

Khi tôi chỉ là một người bắt đầu với PHP, tôi nhúng nó với files HTML. Những dòng code của tôi chỉ là một mớ lộn xộn. Do đó tôi bắt đầu sử dụng các frameworks để kiến thiết nó : ZF1 và ZF2. Thời gian dần trôi, bằng cách tiếp cận với API, tôi đã tạo ra được một server bao gồm một REST API được tạo ra với hàng trăm dòng code.

Vì chỉ là một phần nhỏ trong các dự án trong PHP, một câu hổi được đặt ra là: Liệu chúng tôi có thể  thoát ra khỏi nó ? Và nếu như chúng tôi có thể, gía trị và lợi ích thực sự là gì ? Trong bài viết này, tôi sẽ chia sẻ những kinh nghiệm đó, với những người giống tôi, những người muốn thoát khỏi thế giơí PHP và lao vào một JS Fullstack với những căn cứ vững chắc.

Tôi sẽ giới thiệu cuộc hành trình với các bạn một cuộc hành trình trên server từ PHP đến Node.js và đã làm chủ được các công nghệ như Webpack, React và các công nghệ frontend khác của JS.

![](/uploads/1_n3whc6qht89rh1gzarkepq.png "Biểu đồ giá trị")

Node.js là thành phần chính của stack mới của chúng tôi. Nó chạy các chương trình JavaScript với một tốc độ rất lớn

Nó làm các công việc đó rất tốt, vì có qúa nhiều những tôl được viết bằng ngôn ngữ cấp thấp bây giờ lại trở thành một phần trong JavaScript.Việc cài đặt chương trình gốc rất tẻ nhạt đến nỗi chúng tôi phải sử dụng Ansible để có thể triển khai stack của mình. Vì các công cụ lựa chọn mới của chúng tôi hiện chỉ phụ thuộc vào Node.js, điều duy nhất chúng tôi phải tự cài đặt trên máy chủ là NVM (Trình quản lý phiên bản Node): một công cụ dành riêng để cài đặt Node.js.

## **Cách cài đặt Node.js đúng cách với NVM**

Nếu dựa vào trình quản lý gói hệ điều hành hoặc cài đặt thủ công Node.js thì sẽ  nhanh chóng dẫn đến nhiều vấn đề khi chúng tôi cố gắng chuyển đổi các phiên bản. Vì vậy, chúng tôi đã sử dụng NVM.

Nó rất dễ để cài đặt với các câu lệnh sau

*wget -qO- https://raw.githubusercontent.com/creationix/nvm/v0.33.2/install.sh | bash*

*nvm install node*

*nvm use v6.9.1*

Sau khi cài đặt, chúng tôi có thể:

* Cài đặt các phiên bản Node.js khác nhau trên một hệ thống bằng một lệnh
* Chuyển đổi liền mạch giữa các phiên bản Node.js đó

Thậm chí  NVM hoạt động được trên cả Linux, Mac và Windows nhờ nvm-windows.

## **JavaScript trong năm 2017**

Khi bắt đầu học JavaScript trong quá trình học, nó được xem như một ngôn ngữ rác rưởi, "thật đáng buồn" khi bắt buộc phải làm cho các trang web trở nên bắt mắt và dễ dùng hơn. Do đó không bao giờ dành thời gian để nghiên cứu nó đúng cách. Hầu như tôi đã học về JavaScript trên những blog và những câu trả lời trên stack-overflow .**Tôi hối tiếc điều đó.**

Tôi chưa sẵn sàng để sử dụng các tools và framework hiện đại của JavaScript. JavaScript của năm 2017 là một ngôn ngữ rất khác, với các đặc điểm hiện đại nhuw:

* Classes
* Promises (hiện được tích hợp sẵn trong JS)
* Destructuring & spread operator
* Modules and module loaders
* Maps / Sets and their weak versions
* Async / Await

Vì vậy, phải mất thời gian để đi qua rất nhiều tài liệu để học Javascript đúng cách. Trang web Babeljs.io đã cho tôi cái nhìn tổng quan nhất về lập trình trong JavaScript hiện nay.

## Từ Composer tới Yarn

Composer là tool thật sự tốt nhưng lại chậm. NPM có cùng một vấn đề, vì vậy chúng tôi đã chọn Yarn thay thế. Nó là một sự thay thế nhanh hơn cho NPM. Trong dự án cuối cùng của tôi, chúng tôi có khoảng một trăm phụ thuộc. Trong số nhóm 10 developers của chúng tôi, chúng tôi đã có ít nhất 2 lần sửa đổi thư mục node*modules _mỗi ngày*.

(10 dev + 3 env) \* 2 install/day \* 60 days * 3 min/install = 78h

Thật vậy, hai tuần đã dành để xem các bộ tải và đọc Reddit. 3 phút là đủ lâu để thêm vào chi phí của dự án nhưng quá ngắn để chuyển sang một nhiệm vụ phát triển khác. Bằng cách giảm thời gian cài đặt từ 3 phút xuống còn 1 phút với Yarn, chúng tôi đã tiết kiệm được 46 giờ tập trung! Nếu như bạn hỏi tôi nó có đáng gía khoong ? Câu trả lời chắc chắn sẽ là có

## Cách tạo ra một API trong JavaScript

Những dòng code sẽ làm điều đó. Dưới đây là một ví dụ của một API. Dựa trên :

* Express, một JavaScript nhẹ tương đương với Zend Framework 2 / Symfony
* Sequelize, một thay thế cho Doctrine
* Epilogue, một sự thay thế cho Apigility

`const Sequelize = require('sequelize'),`

`epilogue = require('epilogue'),`

`express = require('express'),`

`bodyParser = require('body-parser');`

``

`// Define your models with Sequelize`

`// This is equivalent to defining Doctrine entities`

`let database = new Sequelize('database', 'root', 'password');`

`let User = database.define('User', {`

`username: Sequelize.STRING`

`});`

``

`// Create an Express server`

`let app = express();`

`app.use(bodyParser.json());`

`app.use(bodyParser.urlencoded({ extended: false }));`

``

`// Plug Epilogue into Express`

`epilogue.initialize({`

`app: app,`

`sequelize: database`

`});`

``

`// Configure a REST resource endpoint with Epilogue`

`let userResource = epilogue.resource({`

`model: User,`

`endpoints: ['/users', '/users/:id']`

`});`

``

`// And that's it, GET/POST and DELETE will be available for your user entity.`

`app.listen(() => {`

`console.log('Server started!');`

`});`

Với một vài dòng code, chúng tôi đã có API REST có thể định cấu hình và có thể mở rộng.

Sau khi đã tạo hơn 50 điểm cuối API với Apigility, chúng tôi đã bị thuyết phục rằng việc tạo các điểm cuối REST là có thể VÀ hiệu quả.

Phần kết tạo ra 10 điểm cuối của chúng tôi mà không có vấn đề gì. Chúng tôi có thể cắm một số custom code trong quy trình làm việc mặc định để xử lý các quy tắc phức tạp, như quyền user. Những gì có thể được tạo ra đã được phát triển như các điểm cuối RPC Express đơn giản với sự trợ giúp của Sequelize.

Đúng là Zend Framework 2 có nhiều tính năng hơn Express. Nhưng Express lại gọn nhẹ hơn và đủ cho tất cả các nhu cầu của chúng tôi. Chúng tôi đã không bỏ lỡ bất cứ điều gì.*(Còn nữa...)*

 ﻿*Dịch giả :Đỗ Huy Thắng (starnmoon)*                                           

*Nguồn: https://blog.matters.tech/migrating-from-php-to-javascript-with-node-js-155534498b58*
