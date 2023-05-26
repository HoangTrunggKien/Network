# 1.Nhiệm vụ tầng giao vận.
## 1.1 Xử lí gói tin.
* Tại phía gửi, dữ liệu tại tầng này được cắt ra thành nhiều Segment, mỗi Segment được chèn thêm các thông tin về phương thức vận chuyển (header ) và đẩy chúng xuống tầng mạng.
 
![Imgur](https://i.imgur.com/Ov87cwi.png)

* Tại phía nhận, tầng giao vận làm nhiệm vụ bóc tách header rồi sắp xếp theo các thứ tự Segment thành dữ liệu rồi chuyển chúng lên tầng trên.
![Imgur](https://i.imgur.com/KFhZo12.png)


