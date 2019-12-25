---
title: 5 điều quan trọng trong PHP
subtitle: PHP
category:
  - PHP
author: Daniel Kelly
date: 2019-12-25T08:50:08.230Z
featureImage: /uploads/cat-1045782_1920.jpg
---
Nếu bạn nghĩ rằng một người độc thân sau đó bị sa thải. Người độc thân không còn nữa , và thậm chí còn bị ghét bỏ



Chúng ta hãy xem 5 mẫu thiết kế hay nhất của PHP hiện nay.



Nhà máy

Bạn nên sử dung các nhà máy để xây dựng một đối tượng. Đúng rồi-xây dựng và không khởi tạo. Bạn không muốn có một nhà máy để tạo một nhà máy. Khi bạn xây dựng đối tượng bạn cần phải khởi tạo nó. Luôn luôn, nó đòi hỏi áp dụng nhiều bước và nhất định. Với nó đối tượng xây dựng cùng một cách. Về cơ bản, đó là điểm cơ bản của một nhà máy.

Nó là 1 cái tuyệt vời để có một giao diện cho nhà máy của bạn và có mã của bạn vào nó chứ không phải một nhà máy bê tông. Cùng với đó bạn có thể thay thês nhà máy này bằng nhà máy khác.

interface FriendFactoryInterface {

public function create() : Friend

}

Tierpe, chúng tôi thực hiện giao diện của nhà máy với các bước sau:

class FriendFactory implements FriendFactoryInterface {

public function create() : Friend {



$friend = new Friend();

return $friend;

}

}



Đó là khá đơn giản và mẫu thiết kế đẹp!

Chiến lươc

Nó là đã sử dụng đến ẩn chi tiết thực hiện các thuật toán cần thiết để thực hiện của hoạt động. Có chiến lược, một người có thể chọn cần thiết thuật toán biết thực hiện nó

Hãy nói khách hàng cần đọc một thư viện chuyển dữ liệu từ nguồn thư viện này sang nguồn thư viện khác.Ví dụ, bạn cần chuyển dữ liệu trong cơ sở dữ liệu trong file csv, hoặc từ bảng tính đến tập json. Bạn hãy làm điều đó ?

Bắt đầu, bạn nên đọc chiến lược tương ứng. Hãy để cho họ gọi là độc giả. Tiếp theo họ nên đọc chiến lược va viết dữ liệu đến kho. Hãy gọi là nhà văn.

Vi thế 2 độc giả đọc dữ liệu trong cấu trúc dữ liệu hoặc trong bảng tính.Theo đó, họ có 2 nhà văn dữ liệu trong flie csv hoặc file json.

Quan trọng một khách hàng làm việc với chiến lược của chúng tôi và không quan tâm triển khai của họ.VÌ thế ,chúng ta nên xác định giao diện chiến lược cho họ. Theo cách đó, một khách hàng chỉ biết được phương thức giao diện chiến lược với chúng, và những điều xảy ra hiện trường và không là của nó.

Cuối cùng, chúng ta tạo một ứng dụng khách hàng ở trong tuy nhiên nó cần truyền dữ liệu.

Chúng ta hãy xem những hoạt động:

interface ReaderInterface {

public function start() : void;

public function read() : array;

public function stop() : void;

}

interface WriterInterface {

public function start() : void;

public function write(array $data) : void;

public function stop() : void;

}

class DatabaseReader implements ReaderInterface {

...

}

class SpreadsheetReader implements ReaderInterface {

...

}

class CsvWriter implements WriterInterface {

...

}

class JsonWriter implements WriterInterface {

...

}

class Transformer {



...

public function transform(string $from, string $to) : void {

$reader = $this->findReader($from);

$writer = $this->findWriter($to);



$reader->start();

$writer->start();

try {

foreach ($reader->read() as $row) {

$writer->write($row);

}

} finally {

$writer->stop();

$reader->stop();

}

}

...

}



Bạn có thể thấy, máy biến áp là một khách hàng chiến lược của chúng tôi không thực sự quan tâm đến việc triển khai thực hiện. Tất cả những gì nó quan tâm là phương pháp giao diện chiến lược của chúng tôi.

Nó được sử dụng biến giao diện một giao diện. Hãy giả sử rằng dự án của bạn được dữ liệu từ một số lưu trữ bằng cách sử dụng lớp sau

class Storage {

private $source;



public function __constructor(AdapterInterface $source) {

$this->source = $source;

}

public function getOne(int $id) : ?object {

return $this->source->find($id);

}



public function getAll(array $criteria = \[]) : Collection {

return $this->source->findAll($criteria);

}

}

Lưu ý lưu trữ không hành động trực tiếp với các nguồn nhưng nó hoạt động với bộ vận chuyển mã nguồn

Hơn thế nữa, lưu trữ không biết bất kì thứ gì về bộ điều khiển cụ thể .Nó điều khiển đến bộ giao diện cụ thể. Như vậy,Việc triển khai cụ thể bộ điều hợp được cung cấp là một hộp đen hoàn chỉnh cho nó.

Đây là bộ giao diện

interface AdapterInterface{

pulic function find(int $id ) : ?object;

public function findAll (array $criteria = \[ ]) :

Collection;

}

Hiện nay, hãy giả sử rằng chúng tôi sử dụng một thư viện để truy cập cơ sở dữ liệu MySQL

$row = $mysql->fetchRow(...);

$data = $mysql->fetchAll(...);

Như bạn có thể thấy, chúng tôi không thể tích hợp thư viện này giống như vậy vào bộ lưu trữ của chúng tôi. Chúng ta cần tạo một bộ chuyển đổi cho nó như dưới đây:

class MySqlAdapter implements AdapterInterface {



...

public function find(int $id) : ?object {



$data = $this->mysql->fetchRow(\['id' => $id]);

// some data transformation

}

public function findAll(array $criteria = \[]) : Collection {



$data = $this->mysql->fetchAll($criteria);

// some data transformation

}



...

}

Observer

Nó được sử dụng để thông báo cho phần còn lại của hệ thống về một số sự kiện ở một số nơi nhất định. Để hiểu rõ hơn về lợi ích của mẫu này, hãy xem xét hai giải pháp cho cùng một vấn đề.

class Theater {



public function present(Movie $movie) : void {



$this->getEventManager()

\->notify(new Event(Event::START, $movie));

$movie->play();



$movie->pause(5);

$this->getEventManager()

\->notify(new Event(Event::PAUSE, $movie));

$movie->finish();



$this->getEventManager()

\->notify(new Event(Event::END, $movie));

}

}

$theater = new Theater();

$theater

\->getEventManager()

\->listen(Event::START, new MessagesListener())

\->listen(Event::START, new LightsListener())

\->listen(Event::PAUSE, new BreakListener())

\->listen(Event::PAUSE, new AdvertisementListener())

\->listen(Event::END, new FeedbackListener())

\->listen(Event::END, new CleaningListener());

$theater->present($movie);

As you can see, the present method becomes extremely straightforward. It doesn’t care about what happens outside of the class. It just does what it is supposed to do and notifies the rest of the system about the facts. Whatever is interested in those facts can listen to the respective events and be notified about them and do what it has to do.

With this approach, it also becomes pretty easy to add additional complexity. All you have to do is to create a new listener and put the needed logic there.

Hope you found the Observer pattern useful.

Decorator

It is used when you want to adjust the behavior of an object at run-time, and with that, reduce redundant inheritances and the number of classes. You might ask why do I need that at all? Well, it could be better explained with examples.

Let’s say we have classes Window and Door, and they both implement OpenerInterface.

interface OpenerInterface {

public function open() : void;

}

class Door implements OpenerInterface {

public function open() : void {

// opens the door

}

}

class Window implements OpenerInterface {

public function open() : void {

// opens the window

}

}

Cả cửa sổ và cửa ra vào đều có cùng một hành vi để mở. Bây giờ, chúng ta cần các cửa ra vào và cửa sổ khác với chức năng bổ sung sẽ cho người dùng biết nhiệt độ bên ngoài khi họ mở cửa hoặc cửa sổ. Chúng ta có thể giải quyết vấn đề này bằng sự kế thừa như thế này

class SmartDoor extends Door {

public function open() : void {

parent::open();

$this->temperature();

}

}

class SmartWindow extends Window {

public function open() : void {

parent::open();

$this->temperature();

}

}

Tất cả trong tất cả, chúng tôi có tổng cộng 4 lớp. Tuy nhiên, với mẫu Decorator chúng ta chỉ có thể giải quyết vấn đề này với 3 lớp. Đây là cách thực hiện:

class SmartOpener implements OpenerInterface {



private $opener;

public function __construct(OpenerInterface $opener) {

$this->opener = $opener;

}



public function open() : void {

$this->opener->open();

$this->temperature();

}

}

$door = new Door();

$window = new Window();

$smartDoor = new SmartOpener($door);

$smartWindow = new SmartOpener($window);

Chúng tôi đã giới thiệu một loại công cụ mở mới hoạt động như một proxy nhưng có chức năng bổ sung ở trên nó. Đó là những gì lừa. Hy vọng bạn tìm thấy bài viết này hữu ích và thú vị. Nếu vậy, đừng ngần ngại vỗ tay và chia sẻ nó trên mạng xã hội. Chúc mừng mã hóa! :)
