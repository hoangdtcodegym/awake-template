---
title: Hướng dẫn cách nâng cấp PHP của bạn lên 7.0 trên macOS Sierra
subtitle: làm thế nào để cài đặt PHP 7.0
category:
  - PHP
author: Đinh Thanh Tùng
date: 2019-12-22T17:00:00.000Z
featureImage: /uploads/screen-shot-2019-12-23-at-11.03.19.png
---
Thông thường, với phiên bản macOS Sierra mới, bạn đã cài đặt PHP 5.6 

Bạn 2 lựa chọn : Cài đặt BREW hoặc CURL

BREW

brew update && brew upgrade\
brew tap homebrew/dupes\
brew tap homebrew/versions\
brew tap homebrew/homebrew-php\
brew unlink php56\
brew*install*php70

Bạn có thể gặp lỗi nếu php chưa được cài đặt bởi BREW trước đó , nhưng đừng lo bạn vẫn có thẻ tiếp tục

CRUD

curl -s http://php-osx.liip.ch/install.sh | bash -s 7.0

Bạn có thể thay thế 7.0 bằng 7.1 với câu lệnh ở trên để cài PHP 7.1

Nếu đầu ra của PHP không có phiên bản 7, chỉ cần gõ câu lệnh này để cập nhật đường dẫn của bạn , một phép màu sẽ xảy ra, như đã nêu ở trên [php-osx.liip.ch website](https://php-osx.liip.ch/#faq).

export PATH=/usr/local/php5/bin:$PATH

Rõ ràng, ENV VAR có thể đã y đổi tuỳ thuộc vào môi trường của bạn.

Nếu một trong những lệnh trên không hoạt động, bạn có thể thử câu lệnh này:

export PATH=”$(brew — prefix /php/php70)/bin:$PATH”

Nguồn: <https://medium.com/zenchef-tech-and-product/how-to-upgrade-your-version-of-php-to-7-0-on-macos-sierra-e1bfdea55a63>
