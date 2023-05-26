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

* Cổng đăng kí: Các cổng nằm trong khoảng từ 1024 đến 49151, để có thể sử dụng các cổng này cần phải đăng ký với IANA.
* Cổng động: Là các cổng ngẫu nhiên nằm trong khoảng từ 49152 đến 65535. Các tiến trình máy khách sử dụng các cổng này để định danh cho mình.
 * Địa chỉ socket: Là một cặp địa chỉ bao gồm địa chỉ IP và địa chỉ port. Sự kết hợp hai cặp địa chỉ này dùng để tránh trong trường hợp hay máy tính có cùng địa chỉ port (vì giá trị port là ngẫu nhiên trong khoảng từ 49152 đến 65535 nên vấn đề trùng lặp là có thể xảy ra).

## 2.2 Truyền thông tin cậy TCP.
* TCP là một giao thức hướng kết nối, nó có trách nhiệm thiết lập một kết nối với phía nhận chia dữ liệu thành các đơn vị vận chuyển, đánh số cho chúng và sau đó gửi lần lượt.
*	TCP được sử dụng khi cần truyền thông tin cậy, tức là dữ liệu yêu cầu phải được gửi đến đầy đủ không được mất mát một gói tin nào.

### 2.2.1 Tiêu đề gói tin TCP.	
* Khi hai thiết bị truyền thông tin cậy, lớp transport sau khi phân mảnh gói tin từ tầng phiên chúng sẽ gắn thêm 1 tiêu đề TCP rồi mới chuyển xuống để lớp mạng xử lý.

![Imgur](https://i.imgur.com/vgZjMUX.png)

* Tiêu đề TCP có chiều dài từ 20 byte đến 60 byte và chứa các trường như sau:
 * Source Port: Địa chỉ port nguồn.
 * Destination Port: Địa chỉ port đích.
 * Sequence number: Xác định số được gán cho byte dữ liệu đầu tiên chứa trong segment. 
Ví dụ:  Đầu tiên trong giai đoạn thiết lập kết nối, mỗi phía sử dụng một bộ tạo số ngẫu nhiên để tạo một trình tự khởi đầu (ISN). Giả sử số ISN là 2367 và gói thứ nhất mạng 1000 byte dữ liệu thì số trình tự sẽ là 2369 vì ( 2367 và 2368 sử dụng để thiết lập kết nối), segment tiếp theo mạng 500 byte sẽ có số trình tự là (2369 + 1000 = 3369), segment tiếp theo sẽ có số trình tự là (3369 + 500 = 3869),...	
 * Acknowledgment Number: Số này xác định số hiệu byte mà trạm gửi segment đang chờ để nhận. Số này sẽ tăng lên 1 nếu nó nhận thành công giá trị đang chờ.
 * HL - Header Length: Số lượng từ trong TCP Header.
 * Reserved: Để dành chưa sử dụng tới, để dùng cho tương lai.
 * Flags: xác định bit điều khiển, có 6 cờ bit lần lượt là:
   * ACK: được đặt để cho biết tính chính xác của trường Acknowledgment.
	  * RST, SYN, FIN: dùng để thiết lập và hủy kết nối.
	  * PSH và URG không được sử dụng trong thực tế.
 * Window Size: là số lượng dữ liệu tối đa bên nhận có thể nhận.
 * Checksum: Chứa mã kiểm tra lỗi theo phương pháp (CRC), tính toán và kiểm tra sự toàn vẹn của Header và dữ liệu.
 * Urgent Pointer: trường này hợp lệ khi cờ URG được đặt, tuy nhiên thì trường này thường để trống vì URG không được sử dụng.
 * Options: chứa các thông tin tùy chọn.\

### 2.2.2 Cơ chế điều khiển luồng trong TCP.
* Điều khiển luồng là cơ chế cho biết lượng dữ liệu mà nguồn có thể gửi đi. Thông thường TCP có thể gửi một byte dữ liệu và sau đó chờ xác nhận rồi mới gửi byte tiếp theo.

![Imgur](https://i.imgur.com/TIuJbUg.png)

* Tuy nhiên làm như vậy thì quá trình gửi tin sẽ diễn ra rất chậm, vì vậy để tăng tốc độ truyền TCP sẽ gửi theo cách gửi nhiều dữ liệu với kích thước được quy định bằng giá trị Window size.
 * Window size trượt cố định: TCP sẽ gửi một loạt dữ liệu được bao phủ bởi một kích thước Window size cố định, khi trạm gửi nhận được ACK nó sẽ trượt cửa số lên vị trí bằng với giá trị của ACK rồi tiếp tục gửi với kích thước Window size đã đặt trước.

![Imgur](https://i.imgur.com/YVINq14.png)

 * Window size thay đổi: giá trị Window size sẽ được phía nhận tính toán dựa trên kích thước bộ đệm của nó.
   Ví dụ: phía gửi truyền một segment với kích thước 4000 byte, Seq number = 1001. Tuy nhiên bộ đệm phía nhận sau khi nhận 4000 byte thì bị đầy, lúc này nó gửi ACK đã nhận được dữ liệu và kèm theo giá trị Window size = 0 (muốn báo là bộ đệm đã đầy không thể nhận thêm được). Bên gửi phải đợi cho đến khi nhận được thông báo kích thước cửa sổ lớn hơn 0 thì mới được tiếp tục truyền. Ở đây sau khi nhận được thông báo kích thước cửa sổ bằng 1000 bên gửi mới tiếp tục gửi với window size = 1000.
   
![Imgur](https://i.imgur.com/8oVrEzr.png)

### 2.2.3 Điều khiển lỗi. 
* Cơ chế sửa lỗi của TCP là TCP nguồn đặt một bộ định thời cho mỗi Segment được gửi đi và bộ định thời này được kiểm tra định kỳ.
#### a)Bộ định thời truyền lại.
* Dùng để điều khiển một Segment mất hoặc bị hỏng. Khi TCP gửi một Segment, nó tạo một bộ định thời truyền lại cho phân đoạn đó.
 * Nếu xác nhận của Segment này được xác nhận trước khi bộ định thời tắt thì bộ định thời mất hiệu lực. 
 * Nếu bộ định thời tắt trước khi xác nhận đến, Segment sẽ được truyền lại và bộ định thời được reset lại. 

![Imgur](https://i.imgur.com/wFTmqQw.png)

#### b) Bộ định thời kiên nhẫn.
* Dùng để xử lý vấn đề liên quan đến Window size bằng 0. Nếu bên gửi nhận được thông báo một Window size = 0, nó sẽ ngừng truyền cho tới khi bên nhận gửi xác nhận thông báo kích thước Window size lớn hơn 0.
* TCP không có cơ chế ACK lại các ACK vừa nhận và nếu  xác nhận thông báo kích thước Window size lớn hơn 0 bị mất trên đường truyền, phía nhận nghĩ mình đã làm xong nhiệm vụ gửi ACK và ngồi đợi bên gửi truyền tiếp dữ liệu. Lúc này cả hai bên sẽ ngồi đợi nhau vô hạn.
* Bộ định thời kiên nhẫn được đặt khi bên gửi nhận được một ACK Window size = 0, khi bộ định thời này hết hạn nó sẽ gửi cho bên nhận một Segment probe cảnh báo rằng ACK Window size đã bị mất và cần gửi lại. Giá trị của bộ định thời kiên nhẫn sẽ được nhân đôi nếu một Segment probe gửi đi không được phản hồi lại và nó sẽ nhân đến tối đa là 60 giây. Sau khi đạt ngưỡng 60 giây, thì cứ 60 giây một bên phát gửi một Segment probe cho đến khi cửa sổ được mở lại.

![Imgur](https://i.imgur.com/10FG0xr.png)

#### c) Bộ định thời keepalive.
* Bộ định thời này được sử dụng để tránh tình trạng một kết nối giữa hai trạm ở trạng thái rỗi quá lâu. Máy chủ sẽ quy định thời gian rỗi tối đa là 2 giờ. Sau 2 giờ mà không thấy máy khách phản hồi, nó sẽ gửi một Segment probe và sau 10 probe ( 75 giây gửi một probe) mà không thấy máy khách trả lời nó sẽ đóng kết nối.
#### d) Bộ định thời time-waited.
* Được sử dụng trong giai đoạn kết thúc kết nối. Khi TCP đóng một kết nối, nó không coi như là kết nối đã thực sự đóng. Nó sẽ giữ kết nối trong tình trạng lấp lửng sau một khoảng thời gian bằng hai lần thời gian tồn tại của một Segment mới đóng hoàn toàn.

### 2.2.4 Thiết lập và giải phóng kết nối.
#### a) Thiết lập kết nối.
* Việc thiết lập kết nối được thực hiện thông qua thủ tục bắt tay 3 bước:
 * Bước 1: Máy khách gửi một segment yêu cầu kết nối chứa cờ  SYN = 1 và giá trị Seq bắt đầu của mình tới máy chủ. Ngoài ra nếu máy khách cũng có thể thêm vào trường tùy chọn giá trị MSS (Maximum Segment Size) nếu muốn định nghĩa kích thước của Segment mong muốn nhận.
 * Bước 2: Phía máy chủ sau khi nhận được thông báo kết nối của máy khách, nó thực hiện xác nhận ACK lại bằng cách cộng thêm 1 vào giá trị Seq ban đầu của máy khách đồng thời phía máy chủ cũng tạo một Seq bắt đầu rồi gửi lại cho máy khách.
 * Bước 3: Khi nhận được segment chấp nhận kết nối, máy khách khởi tạo bộ đệm và các biến để phục vụ kết nối đồng thời cũng gửi lại segment thứ 3 (gồm ACK = giá trị Seq bắt đầu của máy chủ + 1 và giá trị Seq bắt đầu nhận) cho máy chủ. Lúc này phía máy khách cũng đặt cờ SYN = 0 thông báo quá trình bắt tay hoàn tất, có thể trao đổi các segment chứa dữ liệu.

![Imgur](https://i.imgur.com/6MKsCHw.png)

####b) Giải phóng kết nối.
* Việc giải phóng kết nối có thể xuất phát từ một phía bất kỳ. 
 * Bước 1: Máy khách gửi thông báo FIN = 1.
 * Bước 2: Máy chủ gửi lại ACK biên nhận thông báo FIN của máy khách. Tại thời điểm này, máy chủ vẫn có thể tiếp tục gửi nhưng dữ liệu chưa gửi.
 * Bước 3: Khi không còn dữ liệu để gửi nữa, máy chủ gửi 1 Segment chứa cờ FIN.
 * Bước 4: Máy khách thực hiện biên nhận ACK lại thông báo FIN. Tại thời điểm này thì tất cả tài nguyên phục vụ kết nối đều được giải phóng.

## 2.3 Truyền thông không tin cậy UDP.
* Là giao thức truyền thông phi kết nối và không tin cậy, được dùng thay thế TCP theo yêu cầu của ứng dụng ( kết nối nhanh, không đòi hỏi độ tin cậy cao như hội nghị truyền hình, Voice IP, livestream,..)
* Gói tin UDP datagram:

![Imgur](https://i.imgur.com/s07aMvm.png)

* Cổng nguồn (Source Port): xác định số cổng của chương trình ứng dụng
* Cổng đích (Destination Port): xác định số cổng của chương trình ứng dụng nhận.
* Độ dài tổng (Total length): xác định độ dài tổng tiêu đề và dữ liệu của UDP datagram.
* Checksum: chứa mã kiểm tra lỗi theo phương pháp CRC cho toàn bộ Segment.

## 2.4 So sánh TCP và UDP.
* Giao thức UDP có một số ưu điểm hơn so với TCP:
 * Không có giai đoạn thiết lập kết nối: điều này giúp UDP không phải mất thời gian thiết lập đường truyền làm giảm độ trễ của mạng.
 * Không duy trì trạng thái kết nối: việc duy trì không duy trạng thái kết nối làm giảm tiêu tốn các tài nguyên của ứng dụng 
 * Tiêu đề gói dữ liệu nhỏ: tiêu đề của UDP chỉ có 8 byte rất nhỏ so với 20 byte của TCP
 * Không kiểm soát tốc độ gửi: tốc độ truyền của UDP không bị giới hạn bởi các cơ chế điều khiển luồng hay tắc nghẽn mà chỉ bị ảnh hưởng bởi tốc độ sinh dữ liệu của ứng dụng và tốc độ truy cập mạng.

|Đặc trưng|UDP|TCP|
|-|-|-|
|Tốc độ truyền|Nhanh hơn|Chậm hơn|
|Dung lượng gói tin|Nặng|Nhẹ|
|Hướng liên kết|Không|Có|
|Sử dụng phiên|Không|Có|
|Độ tin cậy|Không|Có|
|Xác thực|Không|Có|
|Đánh thứ tự|Không|Có|
|Điều khiển luồng|Không|Có|
|Bảo mật|Ít hơn TCP|Hơn UDP|

























