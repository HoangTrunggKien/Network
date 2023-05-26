# I.Tổng quan.
## 1.Chức năng.
* Xác định các đối tác truyền thông: Application xác định tính khả dụng của các đối tác truyền thông cho một ứng dụng có dữ liệu để truyền.
* Xác định tính khả dụng của tài nguyên: Application Layer xác định xem có đủ tài nguyên mạng cho giao tiếp được yêu cầu hay không.
* Đồng bộ hóa giao tiếp: tất cả giao tiếp xảy ra giữa các ứng dụng yêu cầu sự hợp tác được quản lý bởi một Application Layer.

## 2.Dịch vụ.
* Network Virtual Terminal: một Application cho phép người dùng đăng nhập vào một máy chủ từ xa.
* Truyền, truy cập và quản lý tệp: ứng dụng cho phép người dùng truy cập tệp trong máy tính từ xa, truy xuất tệp từ máy tính và quản lý tệp trong máy tính từ xa.
* Định địa chỉ: để có giao tiếp giữa máy khách và máy chủ, cần có địa chỉ. Khi một máy khách thực hiện yêu cầu đến máy chủ, yêu cầu này chứa địa chỉ của máy chủ và của chính nó. Phản hồi của máy chủ đối với yêu cầu của máy khách, yêu cầu chứa địa chỉ đích tức là địa chỉ của máy khách. Để đạt được kiểu địa chỉ này, DNS được sử dụng.
* Dịch vụ thư: một Application Layer cung cấp chuyển tiếp và lưu trữ Email.
* Dịch vụ thư mục: một ứng dụng chứa cơ sở dữ liệu phân tán cung cấp quyền truy cập thông tin toàn cầu về các đối tượng và dịch vụ khác nhau.

# II.Các giao thức.
## 1.Telnet.
* Telnet là viết tắt của  telecommunications network, là một giao thức dòng lệnh được sử dụng để quản lý các thiết bị khác nhau như PC, máy chủ, router, switch, camera, tường lửa từ xa… Hoặc Telnet là một giao thức máy tính cung cấp khả năng giao tiếp tương tác hai chiều cho các máy tính trên internet và mạng cục bộ LAN.
* Telnet có nhiệm vụ cung cấp các kết nối từ xa, đảm nhiệm việc các lệnh hoặc dữ liệu đến kết nối mạng từ xa nên chúng rất phổ biến trong hệ thống mạng.
* Cấu trúc telnet: Trong cấu trúc của Telnet bao gồm khách hàng (Client) và máy chủ (Server). Ở phía Server sẽ cung cấp dịch vụ Telnet. Dịch vụ này sẽ đưa đến và kết nối các ứng dụng của Client.
* Tính năng của Telnet: 
1. Hiển thị thông tin kết nối nhưng khác chậm chạp và thô sơ.
2. Kết nối nhanh.
3. Giao thức Telnet không an toàn, không bảo mật cao vì nó không được mã hóa nên các thông tin lưu lượng của giao thức Telnet có thể bị lộ bất cứ lúc nào.

* Các thiết bị thường sử dụng Telnet: Linux, Router, Switch, Camera, Windows, …
* Ngoài ra giao thức này còn có thể được dùng để ping một cổng và kiểm tra xem cổng đó có đang mở hay không. 

## 2.FTP (File Transfer Protocol).
* FTP là giao thức truyền tải tập tin được dùng trong việc trao đổi dữ liệu qua mạng thông qua giao thức TCP/IP, thường hoạt động trên hai port 20 và port 21.
* Với giao thức FTP, các client trong mạng có thể truy cập đến máy chủ FTP để gửi hoặc lấy dữ liệu. Điểm nổi bật là người dùng có thể truy cập đến máy chủ FTP để truyền và nhận dữ liệu dù đang ở xa.

![Imgur](https://i.imgur.com/ysUvj7q.png)

* Control Connection: đây là phiên làm việc TCP logic đầu tiên được tạo ra khi quá trình truyền dữ liệu bắt đầu. Quá trình sẽ được duy trì trong suốt quá trình phiên làm việc diễn ra.
* Data Connection: là một kết nối dữ liệu TCP được tạo ra với mục đích chuyên biệt là truyền tải dữ liệu giữa máy Client và Server. Kết nối sẽ tự động ngắt khi quá trình truyền tải dữ liệu hoàn tất.
* Các giao thức truyền dữ liệu trong giao thức FTP.
  * Stream mode: phương thức này hoạt động dựa vào tính tin cậy trong việc truyền dữ liệu trên giao thức TCP. Dữ liệu sẽ được truyền đi dưới dạng các byte có cấu trúc không liên tiếp.
  * Block mode: dữ liệu được chia thành nhiều khối nhỏ và được đóng gói thành các FTP Blocks. Mỗi Block sẽ chứa thông tin về khối dữ liệu đang được gửi.
  * Compressed mode: các đoạn dữ liệu bị lặp sẽ được phát hiện và loại bỏ để giảm chiều dài của toàn bộ thông điệp khi gửi đi (nén dữ liệu).

## 3.SNMP (Simple Network Management Protocol).
* SNMP được sử dụng để trao đổi thông tin quản lý giữa các thiết bị mạng. Nó là một phần của TCP/IP.
* Các thành phần của SNMP:
 * SNMP Manager có các chức năng:
   * Agent truy vấn.
   * Nhận các response từ agent.
   * Đặt các biến trong agent.
   * Xác nhận các sự kiện không đồng bộ từ các agent.
 *  Các thiết bị được SNMP quản lý: router, switch, máy trạm, máy in, …
 * SNMP Agent: là một chương trình được đóng gói trong các thiết bị mạng. Việc kích hoạt agent cho phép nó thu thập cơ sở dữ liệu thông tin quản lý từ thiết bị cục bộ và cung cấp nó cho SNMP manager khi được truy vấn.
	* Các chức năng của SNMP Agent:
	  * Thu thập thông tin quản lý về các chỉ số hoạt động của thiết bị.
  	  * Lưu trữ và truy xuất thông tin quản lý.
   	  * Báo hiệu sự kiện cho trình quản lý.
  	  * Hoạt động như một Proxy cho một số nút mạng không quản lý được.
	


