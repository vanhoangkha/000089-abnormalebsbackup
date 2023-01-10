---
title : "Creating resources with CloudFormation"
date : "`r Sys.Date()`"
weight : 3
chapter : false
pre : " <b> 2.3 </b> "
---
#### Create resources with CloudFormation

1. Perform resource creation with **CloudFormation**. Select **Create stack**.

![CloudFormation](/images/3/0001.png?featherlight=false&width=90pc)

2. Configure **Create stack**

   - Select **Template is ready**
   - Select **Upload a template file**
   - Upload file **anomaly-detection-cfn.json**
   - Select **Next**

![CloudFormation](/images/3/0002.png?featherlight=false&width=90pc)

3. Enter **Stack name** as **AnomalyDetectionStack**

   - Complete the information, enter email to receive notifications.
   - Enter EBS's TagKey.
   - Enter the created S3 bucket name.
   - Select **Next**

![CloudFormation](/images/3/0003.png?featherlight=false&width=90pc)

4. Select **Next**

![CloudFormation](/images/3/0004.png?featherlight=false&width=90pc)

5. Select **I acknowledge that AWS CloudFormation might create IAM resources**. Then select **Submit**.

![CloudFormation](/images/3/0005.png?featherlight=false&width=90pc)

6. Wait about 5 minutes, stack created successfully.

![CloudFormation](/images/3/0006.png?featherlight=false&width=90pc)

7. Check the entered email will receive a notification.

- Note that the mail may be sent to the spam folder.
- Select **Confirm subscription**

![CloudFormation](/images/3/0007.png?featherlight=false&width=90pc)

8. After **Subscription confirmed!**

![CloudFormation](/images/3/0008.png?featherlight=false&width=90pc)