---
title : "Giám sát"
date :  "`r Sys.Date()`" 
weight : 5
chapter : false
pre : " <b> 5. </b> "
---

#### Giám sát

1. Truy cập vào **AWS CloudWatch**

   - Chọn **All alarms**
   - Bạn sẽ thấy có 1 **alarm** xuất hiện (2-3 phút kể từ lần backup đầu tiên)

![Review result](/images/6/0001.png?featherlight=false&width=90pc)

2. Cảnh báo (Alarm) được tạo bởi hàm AWS Lambda mà chúng ta đã triển khai và được định cấu hình để phát hiện các điểm bất thường dựa trên chỉ số tùy chỉnh (custom metrics) của Amazon CloudWatch sẽ được gửi trong các lần sao lưu (backup) tiếp theo.

   - Chọn alarm xuất hiện, bạn sẽ xem các thông số chi tiết.

![Review result](/images/6/0002.png?featherlight=false&width=90pc)

3. Tại thời điểm này, chúng ta không có bất kỳ dữ liệu số liệu nào nên cảnh báo hiển thị không đủ dữ liệu. Trên thực tế, để đào tạo đúng cách mô hình phát hiện điểm bất thường của Amazon CloudWatch, chúng ta sẽ cần trải qua khá nhiều lần lặp lại sao lưu trước khi có thể thiết lập một mẫu.

![Review result](/images/6/0003.png?featherlight=false&width=90pc)

4. Kiểm tra ngay bây giờ, một số lượng đáng kể các bản sao lưu đã diễn ra và bạn sẽ nhận thấy một dải màu xám trải dài trên màn hình. Đây là dải phát hiện bất thường và khi các snapshot hiện tại và trước đó được so sánh và có quá nhiều khối bị thay đổi, ngưỡng của dải màu xám bị phá vỡ và báo động được kích hoạt.

- Cuối cùng, hãy xem số liệu tùy chỉnh thực tế của Amazon CloudWatch. Nếu nhấp vào nút Xem trong chỉ số ở phần phía trên bên phải của biểu đồ, thì bạn sẽ được chuyển hướng đến trang chỉ số, nơi bạn có thể xem tất cả các điểm dữ liệu chỉ số, cũng như chỉ số và cấu hình phát hiện điểm bất thường của nó.

![Review result](/images/6/0004.png?featherlight=false&width=90pc)
