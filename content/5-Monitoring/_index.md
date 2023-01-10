---
title : "Create backup"
date : "`r Sys.Date()`"
weight : 4
chapter : false
pre : " <b> 4. </b> "
---

#### Create backup

1. In this section, we will create **On-demand backup**.

   - Access to **AWS Backup** interface
   - Select **Create on-demand backup**

![Create backup](/images/5/0001.png?featherlight=false&width=90pc)

2. Complete information to create **backup**

   - For **Resource type**, select **EBS**
   - Select the created **Volume ID**.
   - Then select **Backup window** as **Create backup now** (Starts after 1 hour of creation)
   - Select **Always** for **Retention period**
   - Select the created **Backup vault**.
   - Use default **IAM role**.
   - Select **Create on-demand backup**

![Create backup](/images/5/0002.png?featherlight=false&width=90pc)

3. You will see that the backup job is in **Running** status


![Create backup](/images/5/0003.png?featherlight=false&width=90pc)

4. View backup job details.

![Create backup](/images/5/0004.png?featherlight=false&width=90pc)

5. About 5 minutes later, the backup job will complete.

![Create backup](/images/5/0005.png?featherlight=false&width=90pc)