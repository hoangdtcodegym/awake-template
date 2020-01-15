---
title: 'PSR-1: Chuẩn viết code cơ bản'
subtitle: series về chuẩn viết code cơ bản trong php
category:
  - PHP
author: ca_map_trang
date: 2020-01-15T14:42:41.775Z
featureImage: uploads/anhdep01.jpg
---
# **PSR-1: Chuẩn viết code cơ bản**

# Tóm tắt nội dung chính:

* Các file PHÁI dùng các thẻ`<?php`và`<?=`.
* Các file PHẢI dùng duy nhất UTF-8 không BOM cho code PHP .
* Các file NÊN*hoặc*định nghĩa kí hiệu (lớp, hàm, hằng số, vv.)*hoặc*đưa ra tác dụng (e.g. sinh ra output, thay đổi .ini settings, vv.) nhưng KHÔNG NÊN làm cả 2.
* Các namespace và các class PHẢI tuân theo các chuẩn PSR "autoloading": \[[PSR-0],[PSR-4](https://viblo.asia/p/psr-4-trinh-tai-tu-dong-07LKXNxJlV4)].
* Tên class PHẢI được định nghĩa ở dạng`StudlyCaps`.
* Hằng số của phải PHẢI được định nghĩa bằng chữ cái in hoa và cách nhau bằng dấu gạch dưới.
* Các phương thức PHẢI đặt tên dạng`camelCase`.

Còn cụ thể về chuẩn PSR-1 sẽ được giải thích tiếp ở các mục dưới đây

# Các files

## Thẻ PHP

PHP code PHẢI dùng thẻ dài`<?php ?>`hoặc dạng ngắn`<?= ?>`; KHÔNG ĐƯỢC dùng các thẻ khác(tuy nhiên 1 số framework tuy có các thẻ khác nhưng khi biên dịch đều quay về đúng thẻ chuẩn).

## Encoding

Các file PHẢI dùng duy nhất UTF-8 không BOM cho code PHP .

## thành phần phụ

Các file nên định nghĩa kí hiệu (lớp, hàm, hằng số, vv.) *hoặc* đưa ra tác dụng (e.g. sinh ra output, thay đổi .ini settings, vv.) nhưng KHÔNG NÊN làm cả 2.

Cụm từ "thành phần phụ " có nghĩa là thực hiện logic không liên quan trực tiếp đến việc khai báo các lớp, hàm, hằng số, vv., chỉ đơn thuần là bao gồm

"Tác dụng phụ" bao gồm nhưng không giới hạn: tạo đầu ra, sử dụng rõ ràng yêu cầu hoặc bao gồm, kết nối với các dịch vụ bên ngoài, sửa đổi cài đặt ini, phát ra lỗi hoặc ngoại lệ, sửa đổi biến toàn cầu hoặc tĩnh, đọc hoặc ghi vào tệp và những thứ khác.

Ví dụ sau đây là ví dụ về trường hợp bao gồm cả định nghĩa lẫn tác dụng phụ, là ví dụ không  nên làm theo

```none
<?php
// side effect: change ini settings
ini_set('error_reporting', E_ALL);

// side effect: loads a file
include "file.php";

// side effect: generates output
echo "<html>\n";

// declaration
function foo()
{
    // function body
}
```

Còn đây là ví dụ nên làm theo:

```none
<?php
// declaration
function foo()
{
    // function body
}

// conditional declaration is *not* a side effect
if (! function_exists('bar')) {
    function bar()
    {
        // function body
    }
}
```

# Các Namespace và tên class

Các namespace và các class phải tuân theo các chuẩn PSR "autoloading": \[[PSR-0], \[PSR-4]].

Về chuẩn PSR-0 đã bị bỏ và thay thế bằng PSR-4. PSR-4 mình sẽ đề cập trong các bài viết sau.

Điều này có nghĩa là mỗi lớp trong một tập tin của chính nó, và nằm trong một namespace của ít nhất một mức là tên vendor cấp cao nhất.

Tên class phải được định nghĩa ở dạng`StudlyCaps(viết hoa các chữ cái đầu tiên)`.

Với PHP 5.3 trở về sau, code phải dùng namespace bình thường:

```none
<?php
// PHP 5.3 and later:
namespace Vendor\Model;

class Foo
{
}
```

Với các phiên bản 5.2.x trở về trước, nên đặt tên class với tên vendor đằng trước như sau

```none
<?php
// PHP 5.2.x and earlier:
class Vendor_Model_Foo
{
}
```

# Các hằng số, thuộc tính và phương thức của class

Ở đây Class là dùng chung cho các class, interface và method.

## Hằng

Hằng số phải được định nghĩa bằng chữ cái in hoa và cách nhau bằng dấu gạch dưới.

```none
<?php
namespace Vendor\Model;

class Foo
{
    const VERSION = '1.0';
    const DATE_APPROVED = '2012-06-01';
}
```

## Thuộc tính

Bạn có thể đặt ra quy ước đặt tên tùy ý, theo`$StudlyCaps`,`$camelCase`, hoặc`$under_score`

Tuy nhiên, bất kỳ quy ước đặt tên nào được sử dụng NÊN được áp dụng nhất quán trong phạm vi hợp lý. Phạm vi đó có thể là cấp vendor, package, class hoặc method.

## Phương thức

Các phương thức PHẢI đặt tên dạng`camelCase`.

Source: <https://www.php-fig.org/psr/psr-1/>
