---
title : "Tạo tài nguyên bằng CloudFormation"
date :  "`r Sys.Date()`" 
weight : 3
chapter : false
pre : " <b> 2.3 </b> "
---
#### Tạo tài nguyên bằng CloudFormation

1. Thực hiện tạo tài nguyên bằng **CloudFormation**. Chọn **Create stack**.

![CloudFormation](/images/3/0001.png?featherlight=false&width=90pc)

2. Cấu hình **Create stack**

   - Chọn **Template is ready**
   - Chọn **Upload a template file**
   - Upload file **anomaly-detection-cfn.json**
   - Chọn **Next**

![CloudFormation](/images/3/0002.png?featherlight=false&width=90pc)

3. Nhập **Stack name** là **AnomalyDetectionStack**

   - Hoàn thành các thông tin, nhập email để nhận thông báo.
   - Nhập TagKey của EBS.
   - Nhập S3 bucket name đã tạo.
   - Chọn **Next**

![CloudFormation](/images/3/0003.png?featherlight=false&width=90pc)

4. Chọn **Next**

![CloudFormation](/images/3/0004.png?featherlight=false&width=90pc)

5. Chọn **I acknowledge that AWS CloudFormation might create IAM resources**. Sau đó chọn **Submit**.

![CloudFormation](/images/3/0005.png?featherlight=false&width=90pc)

6. Đợi khoảng 5 phút sau, stack tạo thành công.

![CloudFormation](/images/3/0006.png?featherlight=false&width=90pc)

7. Kiểm tra email đã nhập sẽ nhận được thông báo.

- Lưu ý có thể mail được gửi đến trong thư mục spam.
- Chọn **Confirm subscription**

![CloudFormation](/images/3/0007.png?featherlight=false&width=90pc)

8. Sau khi **Subscription confirmed!**

![CloudFormation](/images/3/0008.png?featherlight=false&width=90pc)