# I. Lớp liên kết dữ liệu.
## 1. Chức năng.
* Cung cấp một giao diện dịch vụ được định nghĩa rõ với lớp mạng.
* Kiểm soát và xử lí các lỗi đường truyền.
* Điều khiển luồng dữ liệu để tương thích được tốc độ của máy phát và
máy thu. <br/>
 Để thực hiện được các chức năng này, lớp liên kết dữ liệu nhận các gói tin gửi xuống từ lớp mạng và đóng chúng và các khung (frame) để truyền đi. Mỗi khung chứa phần tiêu đề (header), tải trọng (payload) và phần đuôi (trailer)
 
 ![Imgur](https://i.imgur.com/SXS8yx4.png)
 
 ## 2. Các dịch vụ.
 ### a) Đóng gói dữ liệu và truy cập đường truyền.
 * Đóng gói dữ liệu: Các giao thức tầng liên kết dữ liệu đặt gói dữ liệu tầng mạng vào trong gói dữ liệu tầng liên kết dữ liệu:

![Imgur](https://i.imgur.com/3Ns7TqE.png)

  * Tạo khung: lớp liên kết dữ liệu chuẩn bị một gói để vận chuyển qua các phương tiện cục bộ bằng một tiêu đề và một đoạn giới thiệu để tạo khung, khung này bao gồm:
  * Data: là dữ liệu chuyển từ lớp mạng
  * Header: chứa thông tin điều khiển như địa chỉ MAC đích, địa chỉ MAC nguồn. Các trường Header điển hình bao gồm:
    * Start Frame field: là trường cho biết phần bắt đầu của khung.
    * Source and Destination address fields: cho biết nút nguồn và nút đích
   * Type: cho biết dịch vụ lớp trên 
   * Logical connection control field: dùng để thiết lập kết nối logic giữa các nút.
   * Physical link control field: thiết lập kết nối vật lý
   * Flow control field: Trường điều khiển luồng
    * Congestion control field: Trường kiểm soát tắc nghẽn
  * Trailer: chứa thông tin xác định lỗi được thêm vào cuối PDU.

* Truy cập đường truyền: cung cấp các giao thức đa truy cập cho phép các nút điều chỉnh việc truyền thông của mình trên một kênh truyền chung tránh sự xung đột.
  * Giao thức phân chia theo thời gian (TDM): giao thức này phân chia thời gian thành các khoảng thời gian độc lập sau đó lại chia các khoảng thời gian thành các khe thời gian, mỗi khe được cấp cho một nút. Khi có dữ liệu cần gửi nút sẽ truyền các bit trong khe thời gian mà mình được cấp phát.
  * Giao thức phân chia theo tần số (FDM): giao thức này tạo ra kênh truyền gồm các dải tần số, mỗi nút được cấp phát một tần số riêng biệt.
  * Giao thức phân chia theo mã (CDMA): CDMA cấp phát cho mỗi nút một mã duy nhất để mã hoá dữ liệu gửi đi.
  * Giao thức truy cập ngẫu nhiên: trong giao thức này nút truyền luôn truyền dữ liệu với một tốc độ cao nhất. Khi xảy ra xung đột, các nút liên quan đến xung đột sẽ ngay lập tức dừng truyền và sau thực hiện  truyền lại frame sau một khoảng thời gian nhất định. 
  
 ### b) Kiểm soát lưu lượng.
 * Một chức năng quan trọng khác trong lớp liên kết dữ liệu là kiểm soát tốc độ truyền giữa nguồn và đích, tránh các trường hợp máy thu gửi nhanh nhưng máy nhận chậm bằng cách đệm thêm các bit bổ sung được cung cấp bởi điều khiển luồng.

### c) Phát hiện và sửa lỗi.
* Việc phát hiện lỗi được thực hiện bằng cách phía gửi sẽ thiết lập chèn một số bit phát hiện lỗi, sau đó phía nhận thực hiện tính toán để xác định chính xác vị trí lỗi sau đó sẽ thực hiện sửa các bit lỗi đó.

## 3. Lớp con trong lớp Liên kết dữ liệu.
### a) Lớp con điều khiển liên kết (LLC)
* Lớp con LLC giao tiếp với tầng network, nó quan tâm đến khía cạnh như: truyền lại dữ liệu, xác nhận việc nhận dữ liệu.

### b) Lớp con điều khiển truy phương tiện MAC
* Lớp con MAC liên quan đến các chức năng phụ thuộc phần cứng mạng. Trong một mạng LAN mỗi máy tính có một địa chỉ MAC riêng biệt duy nhất. Địa chỉ này được sử dụng để xác định nguồn và đích đến của mỗi khung trên kênh quảng bá. Nhờ có địa chỉ MAC, các máy tính có thể kết nối điểm - điểm thông qua một kênh quảng bá được chia sẻ bởi nhiều kết nối điểm.

# II. Công nghệ Ethernet.
## 1. Giới thiệu.
*  Ethernet là một dạng công nghệ mạng, sử dụng kết nối các mạng lại với nhau trong mạng cục bộ. Đây là nơi để các thiết bị điện tử kết nối với nhau thông qua một giao thức. Ethernet là nơi giúp máy tính, laptop, tivi,... có thể kết nối với mạng, kết nối dữ liệu với các thiết bị khác. Trong Ethernet sẽ có khung, để chia luồng dữ liệu thành các gói gồm địa chỉ nguồn và đích, có chức năng phát hiện lỗi trong dữ liệu được truyền và yêu cầu truyền lại. Chính vì thế, Ethernet có tốc độ bảo mật, độ tin cậy cao nên được sử phổ biến trong cuộc sống ngày nay như văn phòng, trường học, công ty,...
* Một mạng Ethernet bao gồm các nút mạng và các phương tiện kết nối. Các nút mạng được chia làm 2 loại:
  * Thiết bị đầu cuối dữ liệu (DTE – Data Terminal Equipment): Là các thiết bị đóng vai trò là nguồn hoặc đích của các khung dữ liệu. DTE thường là máy tính, máy trạm, máy chủ,... thường được gọi là trạm cuối.
   * Thiết bị truyền thông dữ liệu (DCE – Data Communication Equipment): Là các thiết bị mạng trung gian có nhiệm vụ nhận và chuyển tiếp các gói tin trong mạng. DCE có thể là các thiết bị độc lập như hub, switch, bộ định tuyến hoặc các giao diện truyền thông như card mạng, modem, v.v.
  * Các phương tiện kết nối thông dụng trong Ethernet là cáp xoắn đôi (bọc hoặc không bọc) và một số loại cáp quang.

## 2. Cấu trúc khung Ethernet.

![Imgur](https://i.imgur.com/EgYuPSW.png)

* PRE (Preamable): Gồm 7 bytes, là 1 chuỗi các bit 0 và 1 để đánh dấu
điểm đầu khung và đồng bộ khung.
* SFD (Start-of-Frame Delimiter): Gồm 1 byte, là 1 chuỗi các bit 0 và 1,
kết thúc bằng 2 bit 1 liên tiếp, cho biết bit tiếp theo là bit ngoài cùng bên trái trong byte ngòai cùng bên trái của trường địa chỉ.
* DA/SA (Destination Address/Source Address): Địa chỉ đích và địa chỉ
nguồn. Mỗi trường có độ rộng 6 bytes.
* Length/Type: Gồm 2 bytes. Nếu giá trị của trường này lớn hơn hoặc bằng 1500 thì đó là số byte dữ liệu trong phần Data. Nếu giá trị đó lớn hơn 1536 thì nó là 1 giá trị cho biết kiểu của khung.
* Data: Chứa dữ liệu của khung (<= 1500 bytes). Nếu số byte dữ liệu nhỏ
hơn 46, một phần bù sẽ được thêm vào để kích thước tăng lên thành 46 bytes.
* Frame Check Sequence (FCS): Gồm 4 bytes. Trường này chứa 1 mã kiểm tra lỗi CRC được tạo bởi bên gửi. Giá trị này sẽ được tính lại bởi bên nhận và khớp với giá trị trên xem các khung có bị lỗi trong quá trình truyền hay không. Giá trị này được tạo ra từ các trường DA, SA, Length/Type, và Data.
này được tạo ra từ các trường DA, SA, Length/Type, và Data.

## 3. Quá trình truyền khung và nhận khung.
### a) Truyền khung.
* Khi tầng con MAC của một trạm cuối nhận được yêu cầu truyền khung cùng với các thông tin về địa chỉ và dữ liệu cần truyền từ tầng con LLC, tầng con MAC bắt đầu quá trình truyền bằng cách chuyển đổi các thông tin từ LLC vào vùng đệm khung MAC.
  * Giá trị của các trường PRE và SOF được chèn vào vị trí tương ứng.
  * Địa chỉ đích và nguồn được đưa vào các trường DA, SA.
  * Số byte dữ liệu LLC được tính toán và đưa vào trường Length/Type.
  * Dữ liệu LLC được chèn vào trường Data. Nếu số byte dữ liệu <46, phần bù được thêm vào để số byte thành 46.
  * Giá trị kiểm lỗi CRC được tính toán dựa trên các trường DA, SA, Length/Type, Data và được chèn vào trường FCS ngay sau trường Data.
  * Sau khi khung được đóng gói, nó sẽ được truyền đi (thường là sử dụng phương pháp truy nhập đường truyền CSMA/CD
### b) Nhận khung.
* Khi trạm đích nhận được khung gửi tới cho nó, đầu tiên nó sẽ kiểm tra xem địa chỉ đích của gói tin có trùng với địa chỉ của nó không (hoặc có thể trùng với địa chỉ nhóm hay địa chỉ quảng bá) để xác định xem nó có nhận gói tin đó không. Nếu trùng một trong các địa chỉ đó, nó sẽ kiểm tra độ dài khung, tiến hành tính toán mã kiểm lỗi CRC và khớp với mã thu được từ khung. Nếu độ dài khung là đúng và 2 giá trị kiểm lỗi khớp với nhau, nó sẽ xác định kiểu của khung dựa trên kích thước trường Length/Type. Cuối cùng, khung được phân tách và chuyển cho giao thức phù hợp ở tầng trên.



       
       
       
       
       
       
       
       
       
       
       
       
       
       
       
       
       
       
       
       
       
       
       
       


