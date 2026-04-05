# Amazon S3 - Advance

# Requester Pay

**S3 Requester Pays** is like putting a vending machine in front of your shared data: **you keep owning the data**, but **the person taking it pays** for the request and download. It’s useful when you want to share large datasets publicly or across accounts **without paying for everyone else’s access costs**.

**Key Use Case:**

- Choose **Requester Pays** when you want to **share large S3 data sets** but make the **consumer pay for access/downloads**, while **you still pay for storage**.

**Exam Tip:**

If you see **“share large dataset with external users, but avoid paying access/download costs”**, think **S3 Requester Pays**.

**Main Difference:**

**Normal S3 bucket:** owner pays for requests/downloads.

**Requester Pays bucket:** **requester** pays for **requests + data transfer**, but **owner still pays for storage**.

**Gotchas:**

- **Anonymous access is not allowed** on Requester Pays buckets.
- The requester must explicitly acknowledge charges, such as with `-request-payer requester` in CLI/API requests.

**Visual Logic (Mermaid):**

![requester-pay.png](Amazon%20S3%20-%20Advance/requester-pay.png)

# Event Notification

**S3 Event Notifications** are like putting a **doorbell** on an S3 bucket: when something happens—like a file being uploaded, deleted, or restored—S3 immediately sends a message to another service. This lets your architecture **react automatically** instead of waiting for someone to check the bucket.

**Key Use Case:**

- Choose it when you need to **trigger downstream actions automatically** after an S3 event, like image processing, alerts, or queue-based workflows.

**Exam Tip:**

If you see **“when a file is uploaded to S3, automatically trigger something”**, think **S3 Event Notifications**.

**Main Difference:**

**S3 Event Notifications** = direct bucket event trigger to **SNS, SQS, Lambda, or EventBridge**.

**S3 Event Notifications vs EventBridge:** use **EventBridge** when you need **more routing flexibility** or want to reach **SQS FIFO**; direct S3 notifications do **not support SQS FIFO**.

**Visual Logic (Mermaid):**

![event-notification.png](Amazon%20S3%20-%20Advance/event-notification.png)

# **S3 Storage Lens**

**S3 Storage Lens** is like a **warehouse dashboard** for all your S3 buckets—it shows what you store, how it’s growing, and whether you’re following good practices. Instead of checking buckets one by one, you get a **big-picture view** across accounts, buckets, and even an AWS Organization.

**Key Use Case:**

- Choose it when you need **organization-wide visibility** into **S3 usage, activity, cost optimization, and data protection**.

**Exam Tip:**

If you see **“analyze S3 usage across many buckets/accounts and get optimization insights”**, think **S3 Storage Lens**.

**Main Difference:**

**S3 Storage Lens** = **analytics + visibility** for S3 storage and activity.

**CloudWatch S3 metrics** = more **traditional operational monitoring**; Storage Lens is built for **storage insights and recommendations**. Storage Lens metrics can also be published to **CloudWatch** when advanced metrics are enabled.

**Visual Logic (Mermaid):**

![storage-lens.png](Amazon%20S3%20-%20Advance/storage-lens.png)

# **Storage Lens Metrics**

**Storage Lens metrics** are the **numbers behind the dashboard**—things like storage size, object count, request trends, and protection settings. Think of them as the **gauges on your car dashboard** telling you how your S3 environment is behaving.

**Key Use Case:**

- Choose them when you want **daily metrics** to spot **growth, inefficiencies, and risky bucket settings**.

**Exam Tip:**

If you see **“daily S3 analytics metrics for storage trends and best-practice insights”**, think **Storage Lens metrics**.

**Main Difference:**

**Free metrics** give core visibility.

**Advanced metrics** add more detail, including extra cost/data-protection insights, CloudWatch publishing, and more granular troubleshooting data like detailed status-code metrics.

**Visual Logic (Mermaid):**

![storage-lens-metrics.png](Amazon%20S3%20-%20Advance/storage-lens-metrics.png)

# Storage Lens Metrics Categories

The **metrics categories** are like labeled sections in a business report—they group related insights so you can quickly focus on the problem you care about. AWS organizes them around use cases such as **cost optimization**, **data protection**, **access management**, **performance**, and **events**, plus **summary** metrics.

**Key Use Case:**

- Choose categories when you want to quickly answer a question like **“Where am I wasting money?”** or **“Which buckets are poorly protected?”**

**Exam Tip:**

If you see **“find cost-saving opportunities or weak protection settings in S3 at scale”**, think **Storage Lens metric categories**.

**Main Difference:**

- **Cost optimization** = saving money
- **Data protection** = backup/encryption/versioning posture
- **Access management** = ownership/ACL-style visibility
- **Performance** = request behavior and troubleshooting
- **Event** = event-related trends
- **Summary** = high-level overview

**Visual Logic (Mermaid):**

![storage-lens-metrics-categories.png](Amazon%20S3%20-%20Advance/storage-lens-metrics-categories.png)

**Fast memory hook:**

**Storage Lens** = the dashboard.

**Metrics** = the numbers.

**Metric categories** = the labeled buckets of insight.

# Storage Lens Default Dashboard

The **S3 Storage Lens default dashboard** is the **automatic built-in dashboard** AWS gives you for your account, like a **default health report** for all your S3 storage. It shows **summarized insights and trends for your entire account**, updates **daily**, and helps you spot storage growth, cost issues, and protection gaps without building a custom dashboard first.

**Key Use Case:**

- Choose it when you want **instant account-wide S3 visibility** with **no custom setup**.

**Exam Tip:**

If you see **“default, account-wide S3 analytics dashboard created by AWS”**, think **Storage Lens default dashboard**.

**Main Difference:**

**Default dashboard** = automatic, **entire account scope**, **scope cannot be changed**.

**Custom Storage Lens dashboard** = you choose **specific Regions, buckets, or organization scope**.

**Extra exam trigger:**

You can **upgrade** the default dashboard from **free metrics** to **advanced metrics**, and you can **disable** it, but you **cannot delete it**.

**Visual Logic (Mermaid):**

![default-dashboard.png](Amazon%20S3%20-%20Advance/default-dashboard.png)

```

```