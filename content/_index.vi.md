---
title : "Phát hiện bất thường AWS Backup cho ổ đĩa Amazon EBS"
date : "`r Sys.Date()`"
weight : 1
chapter : false
---
# Phát hiện bất thường AWS Backup cho ổ đĩa Amazon EBS


Bảo vệ dữ liệu của bạn khỏi các cuộc tấn công mạng và mã độc tống tiền là trách nhiệm quan trọng và việc thực hiện các bước cần thiết để phát hiện hoạt động bất thường ở mọi cấp trong tổ chức của bạn có thể giúp bạn giữ dữ liệu của mình an toàn nhất có thể. Lưu trữ dữ liệu là một lĩnh vực quan trọng mà bạn có thể và nên triển khai tính năng phát hiện bất thường.

Để bảo vệ bộ lưu trữ của bạn, xây dựng một serverless pipeline đơn giản để phát hiện các điểm bất thường xảy ra trên ổ đĩa Amazon Elastic Block Store (EBS). Chúng ta sử dụng AWS Backup cùng với một số dịch vụ do AWS quản lý khác để xây dựng giải pháp.

Khởi đầu của giải pháp là AWS Backup. Khi một ổ đĩa Amazon EBS được sao lưu, một snapshot sẽ được tạo. Bằng cách so sánh snapshot hiện tại này với snapshot đã tạo trước đó, có thể dễ dàng xác định số lượng khối đã thay đổi giữa hai snapshot. Giá trị khối đã thay đổi này được xuất bản lên Amazon CloudWatch dưới dạng chỉ số tùy chỉnh, trong đó cảnh báo Amazon CloudWatch được định cấu hình để phát hiện điểm bất thường trên chỉ số. Bằng cách sử dụng các khả năng máy học mạnh mẽ tích hợp sẵn của Amazon CloudWatch, các điểm bất thường sẽ được phát hiện và hiển thị khi dải ngưỡng của cảnh báo bị vi phạm. Khi điều này xảy ra, mọi thông báo cảnh báo được định cấu hình sẵn sẽ được kích hoạt.

Để xây dựng quy trình phát hiện bất thường, chúng ta sử dụng các dịch vụ sau:

- **AWS Backup**: Chúng tôi sẽ sử dụng **AWS Backup** để quản lý các bản sao lưu của ổ đĩa Amazon EBS. Chúng ta sẽ tạo một kế hoạch dự phòng để chọn khối lượng EBS dựa trên khóa thẻ bạn cung cấp trong quá trình thiết lập. Sau khi quá trình sao lưu bắt đầu, một snapshot sẽ được tạo và các sự kiện từ quy trình AWS Backup được xuất bản lên Amazon EventBridge.
- **Amazon EventBridge**: Amazon EventBridge là bus sự kiện không có máy chủ và nó nhận các sự kiện đến được xuất bản từ AWS Backup. Đối với các sự kiện sao lưu khớp với quy tắc được định cấu hình sẵn mà chúng tôi tạo, EventBridge sẽ kích hoạt một chức năng AWS Lambda.
- **AWS Lambda**: Tất cả các sự kiện AWS Backup phù hợp với quy tắc Amazon EventBridge đều được chuyển đến AWS Lambda. Từ sự kiện này, hàm AWS Lambda trích xuất khối lượng Amazon EBS  Amazon  Resource Name (ARN) và tên snapshot hiện tại. Sử dụng ARN làm khóa, chi tiết snapshot dự phòng trước đó được truy xuất từ ​​bảng Amazon DynamoDB. Nếu một mục snapshot trước đó được tìm thấy cho ARN đã cho, thì snapshot hiện tại và trước đó sẽ được so sánh để thay đổi. Giá trị thay đổi đã tính toán được chuyển đến Amazon CloudWatch dưới dạng số liệu tùy chỉnh. Nếu không tìm thấy mục snapshot trước đó trong bảng Amazon DynamoDB, thì một mục mới sẽ được tạo và cảnh báo Amazon CloudWatch được định cấu hình cho ARN.
- **Amazon DynamoDB**: Đối với mỗi sự kiện sao lưu đến chức năng AWS Lambda, một bảng Amazon DynamoDB được sử dụng để duy trì thông tin chi tiết về sự kiện. ARN từ sự kiện được sử dụng làm khóa phân vùng và tên snapshot được đính kèm làm thuộc tính cho mục.
- **Amazon CloudWatch**: Một số liệu tùy chỉnh được tạo trong hàm AWS Lambda và được gửi tới Amazon CloudWatch. Giá trị số liệu chứa số khối đã thay đổi giữa snapshot hiện tại và snapshot trước đó. Cảnh báo CloudWatch, đã được định cấu hình và tạo trước đó trong hàm AWS Lambda, được kích hoạt khi dải ngưỡng phát hiện bất thường bị vi phạm.
- **Amazon Simple Notification Service (Amazon SNS)**: Khi cảnh báo CloudWatch được kích hoạt, chủ đề Amazon SNS sẽ gửi thông báo đến địa chỉ email được định cấu hình trong quá trình thiết lập.

![EBS](/images/1/0007.png?featherlight=false&width=60pc)

#### Nội dung

- [Giới thiệu](1-Introduce/)
- [Chuẩn bị](2-Prerequiste/)
- [Kiểm tra tài nguyên](3-Checkresource/)
- [Tạo backup](4-Createbackup/)
- [Giám sát](5-Monitoring/)
- [Dọn dẹp tài nguyên](6-cleanup/)
