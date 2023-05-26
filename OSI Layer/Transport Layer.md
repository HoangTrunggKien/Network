# 1.Nhiệm vụ tầng giao vận.
## 1.1 Xử lí gói tin.
* Tại phía gửi, dữ liệu tại tầng này được cắt ra thành nhiều Segment, mỗi Segment được chèn thêm các thông tin về phương thức vận chuyển (header ) và đẩy chúng xuống tầng mạng.
 
![Imgur](https://i.imgur.com/Ov87cwi.png)

* Tại phía nhận, tầng giao vận làm nhiệm vụ bóc tách header rồi sắp xếp theo các thứ tự Segment thành dữ liệu rồi chuyển chúng lên tầng trên.

![Imgur](https://i.imgur.com/KFhZo12.png)

## 1.2 Cung cấp kết nối.
* Về mặt dịch vụ, tầng giao vận tạo ra một kết nối logic giữa hai cổng đầu cuối, tất cả các gói dữ liệu của cùng một thông điệp được truyền theo đường kết nối đó.
* Có ba giai đoạn kết nối: Thiết lập kết nối, truyền dữ liệu, giải phóng kết nối.

## 1.3 Kiểm soát kết nối.
* Dữ liệu truyền trên tầng này có thể truyền theo hai cách đó là hướng kết nối hoặc không hướng kết nối.
 * Truyền kiểu hướng kết nối: Tầng giao vận của máy gửi phải thực hiện bắt tay kết nối với tầng giao vận của máy nhận trước. Sau khi bắt tay thành công thì mới bắt đầu truyền dữ liệu.
 * Truyền kiểu phi kết nối: Tầng giao vận phía gửi không thực hiện bắt tay hỏi trước mà xử lý dữ liệu rồi sẽ truyền luôn.

## 1.4 Kiểm soát lưu lượng và lỗi.
* Trong thực tế, không có đường truyền nào vận chuyển dữ liệu không có lỗi 100%. Do đó, các giao thức của lớp truyền tải được thiết kế để cung cấp khả năng truyền không có lỗi.
*	Lớp liên kết dữ liệu cũng cung cấp cơ chế xử lý lỗi, nhưng nó chỉ đảm bảo phân phối không có lỗi từ nút này sang nút khác. Tuy nhiên, độ tin cậy của từng nút không đảm bảo độ tin cậy của đầu cuối.
*	Lớp liên kết dữ liệu kiểm tra lỗi giữa mỗi mạng. Nếu một lỗi được đưa vào bên trong một trong các bộ định tuyến, thì lỗi này sẽ không bị lớp liên kết dữ liệu bắt được. Nó chỉ phát hiện những lỗi đã được đưa vào giữa phần đầu và phần cuối của liên kết. Do đó, tầng vận chuyển thực hiện việc kiểm tra lỗi từ đầu đến cuối để đảm bảo rằng gói tin đã đến một cách chính xác.

# 2.Các dịch vụ tầng giao vận.
## 2.1 Truyền thông giữa tiến trình với tiến trình.
* Một máy tính có thể vừa chơi game vừa nghe nhạc cùng một lúc. Nếu chỉ sử dụng địa chỉ IP sẽ không thể giúp định danh cho tiến trình nào đang được xử lý trên một máy trạm. Vì vậy, lớp giao vận cung cấp dịch vụ truyền thông tiến trình để giải quyết vấn đề này.
*	Có một số cách để thực hiện truyền thông tiến trình - tiến trình, nhưng thông dụng nhất là thực hiện thông qua mô hình client - server. Để truyền thông tiến trình - tiến trình, ta cần xác định các thông số sau:
 * Địa chỉ IP: Dùng để định danh các máy trạm.
 * Địa chỉ cổng: Để định danh các tiến trình. Có 3 loại cổng là: Cổng thông dụng, cổng đăng ký, cổng động.
* Cổng thông dụng: Là các cổng nằm trong khoảng từ 0 đến 1023, những cổng này được gán và giám sát bởi IANA (Tổ chức cấp phát số liệu Internet). Dưới đây là một số cổng khá thông dụng trong hệ thống mạng:

|Cổng|Giao thức|Miêu tả|
|-|-|-|
|20|FTP, data|Giao thức truyền tệp. (kết nối dữ liệu)|
|21|FTP, control|Giao thức truyền tệp. (kết nối điều khiển)|
|23|Telnet|Giao thức đăng nhập từ xa.|
|25|SMTP|Giao thức truyền thư điện tử đơn giản.|
|53|DNS|Hệ thống tên miền.|
|80|HTTP|Giao thức truyền siêu văn bản.|
|110|POP3|Giao thức nhận thư điện tử.|




