# 1. Giới thiệu.
* Lớp vật lý truyền tải luồng bit 0 1, xung điện, tín hiệu ánh sáng hoặc radio thông qua mạng ở cấp độ điện tử và cơ học. Lớp này cung cấp các tài nguyên phần cứng để gửi và nhận dữ liệu trên một carrier, bao gồm xác định cáp, card và các thành phần vật lý.
#2. Đặc điểm vật lý của môi trường.
* Hub: Là thiết bị dùng để kết nối nhiều máy tính hay các thiết bị mạng khác lại với nhau. Hub được coi là một điểm kết nối chung cho các thiết bị trong mạng và thường được sử dụng để kết nối các phân đoạn của mạng LAN. Khi một gói dữ liệu đến một cổng, nó được sao chép và gửi tới tất cả các cổng khác.

![Imgur](https://i.imgur.com/0UH7g3V.png)

* Bộ lặp ( Repeater ): Là bộ khuếch đại giúp truyền tín hiệu đi xa và ổn định hơn.

![Imgur](https://i.imgur.com/jr0ZH0t.png)

* Converter: Là một thiết bị chuyển đổi dạng tín hiệu này sang dạng tín hiệu khác để phù hợp với môi trường truyền.

![Imgur](https://i.imgur.com/q7ZeEYI.png)

* Network Adapter: Được gọi là bộ điều hợp mạng hay card mạng(NIC), chúng bao gồm card Ethernet, chip Wifi bên trong và bộ phát Wifi không dây bên ngoài. 

![Imgur](https://i.imgur.com/HPZpkgn.png)

* Host Bus Adapter (HBA): Là bảng mạch hay bộ điều hợp mạch tích hợp kết nối hệ thống chủ với thiết bị lưu trữ hoặc mạng. HBA cũng cung cấp xử lý đầu vào/ra để giảm tải cho bộ xử lý của máy chủ khi lưu trữ và truy xuất dữ liệu, giúp cải thiện hiệu xuất tổng thể của máy chủ.

![Imgur](https://i.imgur.com/CDKvNqZ.png)

# 3. Topology vật lý.
## a) Mạng hình sao.
* Là một mô hình mạng gồm thiết bị làm trung tâm và các nút thông tin chịu sự điều khiển của trung tâm đó. Các nút ở đây có thể là máy trạm, các thiết bị đầu cuối hay các thiết bị khác trong mạng LAN.

![Imgur](https://i.imgur.com/fTPqYyo.png)

* Ưu điểm:
  * Khi có lỗi xảy ra ở một trạm nào đó thì cả hệ thống vẫn hoạt động bình thường.
  * Tốc độ mạng khá nhanh.
  * Cấu trúc mạng khá đơn giản giúp dễ dàng kiểm tra, sửa chữa khi gặp sự cố.
  * Có thể thu hẹp hay mở rộng theo ý muốn của người dùng.
* Nhược điểm:
  * Thiết bị trung tâm là thiết bị chính của cả hệ thống, nếu nó gặp sự cố thì tất cả các thiết bị khác không thể giao tiếp được với nhau.
  * Khoảng cách kết nối hạn chế.
  * Tốn kém chi phí dây mạng và thiết bị trung gian.

## b) Bus topology:
* Là kiểu kết nối mà tất cả các thiết bị như máy chủ máy trạm, các nút thông tin đều được liên kết với nhau trên một đường dây cáp chính để truyền dữ liệu. Các dữ liệu và tín hiệu truyền qua dây cáp đều đến được tất cả điểm đến.

![Imgur](https://i.imgur.com/uyKi51D.png)

* Ưu điểm: Dễ lắp đặt và không bị giới hạn độ dài dây cáp.
* Nhược điểm: 
  * Khi có một trạm xảy ra lỗi, cần phải tạm dừng toàn bộ hệ thống để kiểm tra và khắc phục.
	* Rất dễ gặp tình trạng tắc nghẽn khi dữ liệu được truyền với lưu lượng lớn.

## c) Mạng hình vòng.
* Các thiết bị được kết nối thành vòng tròn khép kín thông qua dây cáp. Tín hiệu sẽ được truyền đi theo một chiều cố định. Tại một thời điểm, chỉ có một nút được truyền tin qua một nút khác.

![Imgur](https://i.imgur.com/HiFsRTE.png)

* Ưu điểm:
  * Dễ dàng mở rộng hệ thống mạng LAN ra xa hơn.  
  * Tiếu kiệm được chiều dài dây cáp.
  * Tốc độ mạng nhanh hơn mạng Bus.
* Nhược điểm: Thiết bị được kết nối khép kín nên khi một thiết bị nào đó gặp sự cố thì hệ thống cũng sẽ ngừng hoạt động.

## d) Mạng hình lưới.
* Một máy tính sẽ được liên kết với tất cả các máy còn lại trong hệ thống mà không cần phải thông qua Hub hay Switch.
* Ưu điểm:
  * Các máy tính sẽ hoạt động độc lập, sẽ không bị ảnh hưởng khi các máy khác gặp sự cố.
  * Dễ dàng mở rộng với phạm vi lớn.
* Nhược điểm: Việc quản lý hệ thống sẽ khá phức tạp và gây tốn tài nguyên bộ nhớ và về việc xử lý của các máy trạm.

![Imgur](https://i.imgur.com/lJyed2T.png)




























