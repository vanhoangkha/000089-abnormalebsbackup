---
title : "Tạo backup"
date :  "`r Sys.Date()`" 
weight : 4
chapter : false
pre : " <b> 4. </b> "
---

#### Tạo backup

1. Trong phần này, chúng ta sẽ tạo **On-demand backup**.

   - Truy cập vào giao diện **AWS Backup**
   - Chọn **Create on-demand backup**

![Create backup](/images/5/0001.png?featherlight=false&width=90pc)

2. Hoàn thành thông tin tạo **backup**

   - Đối với **Resource type**, chọn **EBS**
   - Chọn **Volume ID** đã tạo.
   - Sau đó thực hiện chọn **Backup window** là **Create backup now** (Bắt đầu sau 1 giờ tạo)
   - Chọn **Always** cho **Retention period**
   - Chọn **Backup vault** đã tạo.
   - Sử dụng **IAM role** mặc định.
   - Chọn **Create on-demand backup**

![Create backup](/images/5/0002.png?featherlight=false&width=90pc)

3. Bạn sẽ thấy job backup đang trong trạng thái **Running**


![Create backup](/images/5/0003.png?featherlight=false&width=90pc)

4. Xem chi tiết backup job.

![Create backup](/images/5/0004.png?featherlight=false&width=90pc)

5. Khoảng 5 phút sau, backup job sẽ hoàn thành.

![Create backup](/images/5/0005.png?featherlight=false&width=90pc)





