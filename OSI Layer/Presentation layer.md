# 1.Tổng quan.
*  Hỗ trợ việc định nghĩa cho dạng dữ liệu truyền tải, cũng như xử lý bất kỳ mã hóa, nén hoặc các chuyển đổi khác đối với dữ liệu. 
* Ví dụ khi máy tính tải một file về, ở cuối file sẽ có đuôi để nhận biết đây là file gì (  .png .jpg .txt .mp4 ) để biết sử dụng chương trình gì để đọc, biên dịch được file.

* Phiên dịch (Translation): Tiến trình trên hai thiết bị trao đổi các thông tin dưới dạng chuỗi ký tự, số,... nhưng được mã hóa theo các hệ thống mã hóa khác nhau. Tầng trình diễn phía gửi có nhiệm vụ chuyển đổi các thông tin mã hóa đó thành khuôn dạng chung để gửi trên đường truyền. Tầng trình diễn tại phía nhận sẽ chuyển đổi khuyên dạng chung này thành thông tin theo khuôn dạng của máy nhận.
* Mã hóa: thực hiện mã hóa dữ liệu nhưng là mã hóa ở dạng ký tự chứ không phải mã hóa ở dạng bit như ở lớp vật lý. 
* Nén: Tầng trình diễn thực hiện nén dữ liệu làm giảm số lượng bit trên đường truyền đặc biệt là các dữ liệu đa phương tiện như âm thanh, hình ảnh.

# 2.Các giao thức.
* Apple Filing Protocol (AFP): Apple Filing Protocol là giao thức mạng độc quyền (giao thức truyền thông) cung cấp các dịch vụ cho macOS hoặc macOS cổ điển. Về cơ bản, đây là giao thức kiểm soát tệp mạng được thiết kế đặc biệt cho các nền tảng dựa trên Mac. cho phép máy Mac giao tiếp qua mạng cục bộ.
* Giao thức trình bày nhẹ (LPP- Lightweight Presentation Protocol): Giao thức trình bày nhẹ là giao thức được sử dụng để cung cấp dịch vụ trình bày ISO trên đầu các ngăn xếp giao thức dựa trên TCP / IP.
* NetWare Core Protocol (NCP): NetWare Core Protocol là giao thức mạng được sử dụng để truy cập tệp, in, thư mục, đồng bộ hóa đồng hồ, nhắn tin, thực thi lệnh từ xa và các chức năng dịch vụ mạng khác.
* Biểu diễn dữ liệu mạng (NDR - Network Data Representation ): Biểu diễn dữ liệu mạng về cơ bản là việc triển khai lớp trình bày trong mô hình OSI, lớp này cung cấp hoặc định nghĩa các kiểu dữ liệu nguyên thủy khác nhau, kiểu dữ liệu được xây dựng và một số kiểu biểu diễn dữ liệu.
* Biểu diễn dữ liệu bên ngoài (XDR- External Data Representation): Cho phép truyền dữ liệu giữa các loại hệ thống máy tính. Chuyển đổi từ biểu diễn cục bộ sang XDR được gọi là mã hóa . Chuyển đổi từ XDR sang biểu diễn cục bộ được gọi là giải mã. XDR được thực hiện như một thư viện phần mềm gồm các chức năng có thể di động giữa các hệ điều hành khác nhau và cũng độc lập với lớp truyền tải.
* Lớp cổng bảo mật (SSL- Secure Socket Layer): Giao thức Lớp cổng bảo mật cung cấp bảo mật cho dữ liệu đang được chuyển giữa trình duyệt web và máy chủ. SSL mã hóa liên kết giữa máy chủ web và trình duyệt, điều này đảm bảo rằng tất cả dữ liệu được truyền giữa chúng vẫn ở chế độ riêng tư và không bị tấn công. giao thức SSL gồm hai lớp con:
  * Giao thức SSL record: xác định các định dạng dùng để truyền dữ liệu
  * Giao thức SSL handshake (gọi là giao thức bắt tay) : sử dụng SSL record protocol để trao đổi một số thông tin giữa server và client vào lần đầu tiên thiết lập kết nối SSL.




