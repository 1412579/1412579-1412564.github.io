# Laravel Framework Version 5.4

## I. Thông tin nhóm

|   MSSV  |        Họ Tên      | Nội Dung Đóng Góp | Đánh Giá |
| :--------- | :-------------------- | :------------------- | :---------- |
| 1412579 | Vũ Minh Trí |                   |          |
| 1412564 | Trần Thuỳ Bích Trâm     |                   |          |

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
## 1. MVC trong Laravel
![Mô hình MVC](/images/MVC.png)

* MVC là mô hình 3 lớp với ba thành phần chính:

	* Model là nơi chưa các nghiệp vụ logic, các phương thức thức xử lý, tuy nhiên đa phần model là nơi chúng ta sử dụng để truy xuất database.

	* View là hiển thị các giao diện của website dựa vào hành động của người dùng, là chính các file HTML của chúng ta. Trong Laravel cũng có một thư mục view riêng.

	* Controller chính là nơi nhận request của người dùng, từ đó có thể gửi lệnh cho Model hoặc View tùy vào request của người dùng.

* Có thể hiểu dễ hơn, Controller chính là nơi nhận lệnh từ người dùng, nếu người dùng thực hiện yêu cầu phải truy xuất xuống database, khi đó Controller sẽ gửi lệnh xuống Model, Model thực hiện yêu cầu của Controller sau đó lại ngược lại Controller, Controller nhận được dữ liệu và chuyển về View, từ đó View sẽ gửi thông tin dạng giao diện cho người dùng. Ngoài ra nếu yêu cầu không liên quan tới database thì Controller sẽ chuyển hướng thẳng về view mà không cần gửi lệnh cho Model.

* MVC giúp cho chúng ta quản lý mã nguồn dễ hơn, dễ nâng cấp và bảo trì source code của mình, tạo ra một chuẩn giúp cho teamwork tốt hơn, thống nhất trên một khuân khổ, tránh tình trạng "râu ông này cắm cằm bà kia" khi nhiều người code một project, và nhiều hơn thế nữa

## 2. MVC trong Laravel