## 1.Tổng quan.
* Tầng phiên sử dụng các dịch vụ được cung cấp bởi lớp vận chuyển, cho phép các ứng dụng thiết lập và duy trì các phiên và đồng bộ hóa các phiên.
## 2.Chức năng.
* Lớp phiên hoạt động như một bộ điều khiển hộp thoại, qua đó nó cho phép các hệ thống giao tiếp ở chế độ bán song công hoặc chế độ giao tiếp song công hoàn toàn.
* Chịu trách nhiệm quản lý mã thông báo, qua đó nó ngăn hai người dùng truy cập đồng thời hoặc cố gắng thực hiện cùng một hoạt động quan trọng.
* Cho phép đồng bộ hóa bằng cách cho phép quá trình thêm các điểm kiểm tra, được coi là điểm đồng bộ hóa các luồng dữ liệu.
* Chịu trách nhiệm kiểm tra và khôi phục phiên.
* Về cơ bản lớp này cung cấp cơ chế mở, đóng và quản lý một phiên giữa các quy trình ứng dụng của người dùng cuối.
  * Chịu trách nhiệm đồng bộ hóa thông tin từ các nguồn khác nhau. 
  * Kiểm soát các kết nối đơn hoặc nhiều kết nối cho từng ứng dụng của người dùng cuối và giao tiếp trực tiếp với cả hai lớp Presentation và Transport.
  * Tạo ra các thủ tục để kiểm tra, sau đó là hoãn, khởi động lại và kết thúc.
  * Chịu trách nhiệm tìm nạp hoặc nhận thông tin dữ liệu từ lớp trước của nó (lớp Transport) và tiếp tục gửi dữ liệu đến lớp sau nó (lớp Presentation).
## 3.Các giao thức.
## a)Netbios (Network Basic Input / Output System)
* Là một giao thức, công nghệ nối mạng. Nó được thiết kế trong môi trường mạng LAN để chia sẻ tài nguyên (như dùng chung các file, Folder, máy in…). Thông thường một mạng dùng giao thức Netbios thường là Netbios Datagram Service (Port 138) hoặc Netbios Session Service (Port 139) hoặc cả 2.
* Do đặc tính được thiết kế để dùng trong mạng LAN để chia sẻ tài nguyên nên nên tính bảo mật của Netbios rất thấp.

## b)Giao thức RPC (Remote Procedure Call).
* Là một mô hình mạng hay còn được biết đến là cơ chế giao tiếp giữa hai tiến trình. Đây là một loại giao thức yêu cầu phản hồi, có thể dễ dàng được giải thích sử dụng mô hình truyền thông máy khách/máy chủ. Quá trình gọi một được gọi là “máy khách” và quá trình trả lời lại yêu cầu này được gọi là “máy chủ”.

