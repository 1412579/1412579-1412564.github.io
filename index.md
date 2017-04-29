# Laravel Framework Version 5.4

## I. Thông tin nhóm

|   MSSV     |        Họ Tên         |    Nội Dung Đóng Góp | Đánh Giá              |
| :--------- | :-------------------- | :------------------- |  :------------------- | 
| 1412579    | Vũ Minh Trí           |                      |                       |
| 1412564    | Trần Thuỳ Bích Trâm   |                      |                       |          

## II. Nội dung tìm hiểu
1. MVC trong Laravel
2. Composer
3. Blade Template (tương tự view engine bên Nodejs)
4. Query Builder và Eloquent ORM
5. Form Request (khá tương tự body-parser bên Node) and Validation(khá tương tự Express-Validation)
6. Route/Restful API (khá tương tự Routing Express bên Node)
7. Truyền biến qua route, route share... (Still tương tự)
8. Một số tính năng đặc biệt: Tinker, Migration, Form in Laravel, Autopagination, CSRF_Token,...
9. Nói về các package open source của Laravel

## III. Tổng hợp nội dung tìm hiểu
### 1. MVC trong Laravel

![Mô hình MVC](/images/MVC.png)

* MVC là mô hình 3 lớp với ba thành phần chính:

	* Model là nơi chưa các nghiệp vụ logic, các phương thức thức xử lý, tuy nhiên đa phần model là nơi chúng ta sử dụng để truy xuất database.

	* View là hiển thị các giao diện của website dựa vào hành động của người dùng, là chính các file HTML của chúng ta. Trong Laravel cũng có một thư mục view riêng.

	* Controller chính là nơi nhận request của người dùng, từ đó có thể gửi lệnh cho Model hoặc View tùy vào request của người dùng.

* Có thể hiểu dễ hơn, Controller chính là nơi nhận lệnh từ người dùng, nếu người dùng thực hiện yêu cầu phải truy xuất xuống database, khi đó Controller sẽ gửi lệnh xuống Model, Model thực hiện yêu cầu của Controller sau đó lại ngược lại Controller, Controller nhận được dữ liệu và chuyển về View, từ đó View sẽ gửi thông tin dạng giao diện cho người dùng. Ngoài ra nếu yêu cầu không liên quan tới database thì Controller sẽ chuyển hướng thẳng về view mà không cần gửi lệnh cho Model.

* MVC giúp cho chúng ta quản lý mã nguồn dễ hơn, dễ nâng cấp và bảo trì source code của mình, tạo ra một chuẩn giúp cho teamwork tốt hơn, thống nhất trên một khuân khổ, tránh tình trạng "râu ông này cắm cằm bà kia" khi nhiều người code một project, và nhiều hơn thế nữa

### 2. MVC trong Laravel

* Về cơ bản, Laravel đã cung cấp cho ta một mô hình MVC quá tuyệt vời, chúng ta không phải làm quá nhiều việc khi chúng ta code "PHP thuần" nữa. Với các thành phần trong mô hình MVC được đặt rất rõ ràng và người dùng dễ dàng thao tác với mô hình MVC. 

![Mô hình MVC trong Laravel](/images/MVC-Laravel.png)

* Trong Laravel, chúng ta hãy chú ý tới những thư mục được Laravel tạo sẵn, nơi mà chúng ta sẽ thực hiện đúng mô hình MVC.
	* Thư mục __resources__: Đây là thư mục nơi mà chúng ta chứa các file giao diện, cụ thể là sẽ nằm trong thư mục view, Laravel cung cấp cho chúng ta thao tác gọi view rất đơn giản, nó được mặc định trong Laravel nên chúng ta không cần phải cấu hình một đường dẫn link tới thư mục này. Ngoài ra còn có các thư mục khác dùng để upload file, hoặc chứa thông tin giao diện đa ngôn ngữ và nơi chưa các file Front-end (tuy nhiên đa phần chúng ta đều để các file Front-end tại thư mục Public)
	![Mô hình MVC trong Laravel](/images/1.png)
	![Mô hình MVC trong Laravel](/images/2.png)
	![Mô hình MVC trong Laravel](/images/3.png)
	* Thư mục __public__: đây là thư mục đúng nghĩa như cái tên của nó, __public__ là nơi ta chứa các file cần thiết, chả hạn như đối với mình thì đây là nơi mình sử dụng để chứa các file _CSS_, _JS_, và một số hình ảnh upload được mình lưu tại đây.
	![Mô hình MVC trong Laravel](/images/4.png)
	![Mô hình MVC trong Laravel](/images/5.png)

	* Thư mục __app__ - nơi chưa đựng những gì tinh tuý nhất trong Laravel: quả thật vậy, đây chính là nơi nòng cốt của cả trang web, trong thư mục này, chúng chứa toàn bộ những những xử lý của chúng ta thông qua _Http\Controller_ cũng như chứa các file _Model_ giúp chúng ta thao tác cơ sở dữ liệu. Ngoài ra nó còn chứa các file Request - nơi chúng ta có thể sử dụng Validation mà Laravel cung cấp sẵn cũng như middleware giúp chúng ta thiết lập Authentication cho ứng dụng.
	![Mô hình MVC trong Laravel](/images/6.png)
	![Mô hình MVC trong Laravel](/images/7.png)
	![Mô hình MVC trong Laravel](/images/8.png)


* Laravel (phiên bản 5.4) cung cấp cho chúng thêm một thành phần khác đó chính là Route, nơi định tuyến, dẫn đường cho các HTTP Request được gửi tới nơi mà nó mong muốn. Với thư mục Route thì nó sẽ giúp cho việc quản lý các định tuyến được tốt hơn.

* Đối với phiên bản 5.4, Laravel đã đưa Route ra một thư mục riêng thay vì tích hợp nó vào thư mục App như phiên bản trước (cụ thể phiên bản 5.0), cùng với đó chia Route thành các file khác nhau thay vì gộp như cũ (api, channel, console, web), giúp quản lý tất cả các Route tốt hơn.


### 2. Composer và thao tác cmd trong Laravel

![Composer trong Laravel](/images/composer.jpg)

* _Composer_ là một công cụ cho phép chúng ta quản lý các thư viện của PHP tốt hơn, nó cho phép chúng ta tải về các gói thư viện cần thiết chỉ bằng các dòng lệnh, và sau đó nó sẽ giúp ta tải về mà không cần phải sử dụng quá nhiều thao tác. Phần này em thấy khá giống với NPM của Node, đều cho phép chúng ta tải các thư viện (module) nhanh và dễ dàng.

* Về cơ bản không có quá nhiều thứ để nói về _Composer_, chúng ta sử dụng nó để tải các thư viện của PHP, thay vì phải tải bằng tay, mỗi project ta sẽ phải tải về những thư viện khi chúng ta sử dụng, vì _Composer_ sẽ chỉ cài đặt tại chính thư mục chứa project đó. 


* Ngoài _composer_ thì Laravel cũng cung cấp cho chúng ta một thứ khác, đó chính là _artisan_. Đây là một CLI được Laravel tích hợp giúp Lập trình viên tạo những file cần thiết cực kỳ nhanh chóng và hữu dụng khi phát triển ứng dụng. 

* Ví dụ một cụ thể dễ dàng, bạn hoàn toàn có thể tạo ra các file _model_ hoặc _controller_ thông qua __artisan__ chả hạn. Hoặc thứ mà chúng ta hay dùng đến nhất mỗi khi phát triển một ứng dụng web đó chính là _database_, __artisan__ cũng giúp chúng ta những thao tác thông qua _Migration_ để tạo và phát triển _database_ nhanh hơn. 
Dưới đây là một số các câu lệnh __artisan__ hỗ trợ, bạn có thể kiểm tra danh sách câu lệnh này thông qua cú pháp _**php artisan list**_

<p align="center">
![Mô hình MVC trong Laravel](/images/9.png)
</p>

### 3. Blade Templade

#### Templade Engine là gì?

* Đơn giản Template đó chính là một mẫu ngôn ngữ trình bày, giúp chúng ta tách biệt code PHP ra khỏi code HTML.

#### Blade Templates trong Laravel

* Blade là một _templating engine_ đơn giản và được Laravel tích hợp vào cho mình. Ngoài việc nó cung cấp những câu lệnh trong view, nó không cấm bạn sử dụng PHP trong view như các _template engine_ khác. Tất cả các views của _Blade_ sẽ được compile thành mã PHP thuần, cho nên nó sẽ không làm tăng quá nhiều chi phí của ứng dụng. 

##### Mặc định chúng ta sẽ đặt tên cho các file dạng đuôi _*.blade.php_ (với * là tên file của bạn)

#### Chúng ta có thể làm gì với __Blade__?

* Blade giúp ta quản lý các file view tốt hơn, khi chúng ta thiết kế view, có rất nhiều đoạn code bị lặp lại, vì vậy khi chúng ta chỉnh sửa lại một file nào đó, chúng ta buộc phải chỉnh sửa lại tất cả các view chứa nó.

* Vì vậy Blade cung cấp cho chúng ta cơ chế _thừa kế template_, chúng ta có thể tách những đoạn code bị trùng lắp ra một file mới và bạn chỉ cần gọi file đó tại các view chúng ta sử dụng. Khi cần chỉnh sửa, ta chỉ cần chỉnh một file và tất cả các view đều được update thay vì phải chỉnh sửa toàn bộ các view.

* Xét một ví dụ cơ bản về Blade Templade.

<p align="center">
![Blade Templade trong Laravel](/images/10.png)
</p>

* Như hình ảnh phía trên, mình đã tách _header_ và _footer_ của website chính ra riêng, với view _index.blade.php_ đơn giản nó chỉ chứa lời gọi đến 2 file trên và _@yield('content')_ là nơi được sử dụng để hiển thị dữ liệu ở một vị trí đặt trước. Chả hạn như tại view _home.blade.php_ hình kế thừa view cha là _index.blade.php_, sau đó mình chỉ cần inject một nội dụng vào _@section_. Ở trên mình đã nói là _@yield_ sẽ là nơi nội dụng của những section này được hiển thị.

<p align="center">
	![Blade Templade trong Laravel](/images/11.png)
</p>


