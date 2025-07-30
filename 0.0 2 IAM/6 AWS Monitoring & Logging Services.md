Here are detailed notes on **AWS Monitoring & Logging Services**: **CloudWatch** and **CloudTrail**, covering key points for understanding, exams, and interviews.

---

## 📈 **Amazon CloudWatch — Monitoring Service**

### 🔹 **Purpose**

CloudWatch is used to **monitor** AWS resources and custom applications in real-time.

---

### 🔹 **Key Features**

| Feature                  | Description                                                                    |
| ------------------------ | ------------------------------------------------------------------------------ |
| **Metrics**              | Numeric time-series data for AWS services (CPU %, memory, latency).            |
| **Alarms**               | Trigger actions (email, auto-scaling, Lambda) when a metric exceeds threshold. |
| **Dashboards**           | Visual representation of metrics from one or more services.                    |
| **Logs**                 | Collects, stores, and analyzes log data from EC2, Lambda, applications, etc.   |
| **Events (EventBridge)** | Respond to state changes like EC2 start/stop, instance termination.            |

---

### 🔹 **Metric Types**

* **AWS Default Metrics** (e.g., EC2 CPUUtilization, S3 BucketSizeBytes).
* **Custom Metrics** – Sent using CloudWatch Agent or `PutMetricData`.

---

### 🔹 **Alarm States**

* **OK** – Metric is within normal threshold
* **ALARM** – Threshold breached
* **INSUFFICIENT\_DATA** – No data available

---

### 🔹 **Use Cases**

* Trigger **Auto Scaling** based on CPU usage.
* Send **SNS email alert** when disk space is low.
* Create **dashboards** for system health monitoring.
* Analyze logs for errors, crashes, or throttling.

---

## 🧾 **AWS CloudTrail — Logging & Auditing Service**

### 🔹 **Purpose**

CloudTrail provides visibility into all **API activity** in an AWS account for **security**, **compliance**, and **audit** purposes.

---

### 🔹 **Key Features**

| Feature                              | Description                                         |
| ------------------------------------ | --------------------------------------------------- |
| **API Logging**                      | Logs every API call made via Console, CLI, SDKs.    |
| **Event History**                    | Shows last 90 days of API activities (read/write).  |
| **S3 Delivery**                      | Trails can deliver logs to a specified S3 bucket.   |
| **Integration with CloudWatch Logs** | Optional, for real-time alerts on specific actions. |

---

### 🔹 **Types of Events**

* **Management Events** – Create/Delete/Modify resources (e.g., launching EC2, creating S3 bucket).
* **Data Events** – Accessing the data itself (e.g., `GetObject` on S3).
* **Insight Events** – Detect anomalies (e.g., unusually high number of login attempts).

---

### 🔹 **Use Cases**

* Track **who deleted an EC2 or S3 bucket**.
* Detect **unauthorized IAM activity**.
* Monitor **compliance violations**.
* Set up **SIEM integrations** for audit trails.

---

### 🔹 **Storage**

* CloudTrail logs are stored in **S3**.
* Can be **encrypted using KMS**.
* Can be sent to **CloudWatch Logs** for real-time monitoring.

---

## 🔁 **CloudWatch vs CloudTrail: Summary**

| Feature          | **CloudWatch**                 | **CloudTrail**                         |
| ---------------- | ------------------------------ | -------------------------------------- |
| Purpose          | Performance monitoring         | Auditing API activity                  |
| Data Type        | Metrics & Logs                 | API call history                       |
| Real-time        | Yes                            | Near real-time (some delay)            |
| Log Source       | Applications, AWS services     | AWS Management Console, CLI, SDK, APIs |
| Retention        | User-defined                   | 90 days (default), longer in S3        |
| Storage Location | CloudWatch native, optional S3 | S3 (required)                          |
| Alerts           | Supports alarms                | Alerts when integrated with CloudWatch |

---

## 📝 Example Integration

* You can use **CloudTrail + CloudWatch Logs + SNS** to send alerts when:

  * An IAM user logs in from an unexpected IP.
  * A security group is modified.
  * A bucket is made public.
Here are detailed **interview questions with answers**, as well as **scenario-based questions** for AWS **Monitoring & Logging Services** — **CloudWatch** and **CloudTrail**.

---

## ✅ **1. Amazon CloudWatch**

### 🔹 **Interview Questions & Answers**

**Q1: What is Amazon CloudWatch?**
**A:** It’s a monitoring service that provides data and actionable insights for AWS, applications, and infrastructure through metrics, logs, and alarms.

---

**Q2: What are the key components of CloudWatch?**
**A:**

* **Metrics** – Time-series data like CPU, disk, memory, etc.
* **Alarms** – Trigger notifications/actions when metric thresholds are breached
* **Logs** – Central log storage from AWS services or custom apps
* **Dashboards** – Visual representation of data
* **Events** – Trigger actions based on changes in AWS environment

---

**Q3: How do you send custom metrics to CloudWatch?**
**A:** Using the AWS CLI, SDK, or CloudWatch agent by calling `PutMetricData`.

---

**Q4: What is the difference between CloudWatch Metrics and Logs?**
**A:**

* **Metrics** are numerical time-series values (e.g., CPU %, latency).
* **Logs** are text-based data like application logs, system logs, etc.

---

**Q5: Can you monitor non-AWS servers using CloudWatch?**
**A:** Yes, by installing the **CloudWatch Agent** on on-prem or non-AWS EC2 instances.

---

### 🔹 **Scenario-Based Q\&A**

**Q: You want to receive an alert when CPU utilization of an EC2 instance exceeds 80% for 5 minutes. What do you do?**
**A:**

1. Go to CloudWatch → Alarms → Create Alarm.
2. Select EC2 > CPUUtilization.
3. Set threshold (≥ 80% for 5 minutes).
4. Attach an SNS topic to notify via email/SMS.

---

**Q: How can you troubleshoot application errors using CloudWatch?**
**A:** Use **CloudWatch Logs** to view logs for errors, warnings, or exceptions, and correlate them with performance metrics.

---

## ✅ **2. AWS CloudTrail**

### 🔹 **Interview Questions & Answers**

**Q1: What is AWS CloudTrail?**
**A:** CloudTrail captures and stores a record of every API call made in an AWS account, including identity, time, IP address, and action.

---

**Q2: What kind of operations does CloudTrail record?**
**A:**

* Console logins
* CLI/SDK/API actions
* IAM user activities
* Resource creation/deletion/modification

---

**Q3: How is CloudTrail different from CloudWatch?**
**A:**

* **CloudTrail** is for **auditing and security** (API activity tracking).
* **CloudWatch** is for **operational monitoring** (performance and logs).

---

**Q4: Where is CloudTrail data stored?**
**A:** It is delivered to **S3 buckets** and can be optionally sent to **CloudWatch Logs**.

---

**Q5: Is CloudTrail enabled by default?**
**A:** Yes, the **management events** (read/write) for the last 90 days are recorded automatically in each AWS account.

---

### 🔹 **Scenario-Based Q\&A**

**Q: An S3 bucket was deleted unexpectedly. How do you identify who did it and when?**
**A:**

1. Go to **CloudTrail Console**.
2. Search for **DeleteBucket** events.
3. View details: IAM user, IP, time, region.

---

**Q: Your team suspects unauthorized access to an EC2 instance. How do you confirm the activity?**
**A:**

* Use **CloudTrail** to check `StartInstances` or `DescribeInstances` calls.
* Filter by user/role/IP address to trace access history.

---

**Q: You want to track all changes to IAM policies for compliance. What AWS service would you use?**
**A:** Use **CloudTrail** to record events like `PutRolePolicy`, `AttachPolicy`, etc., and store them in S3 for audit.

---

## ✅ **CloudWatch vs. CloudTrail Summary**

| Feature      | CloudWatch                         | CloudTrail                              |
| ------------ | ---------------------------------- | --------------------------------------- |
| Purpose      | Monitor performance, logs, metrics | Track user activity, API calls          |
| Type of Data | Metrics, logs, alarms              | Event history of AWS API calls          |
| Retention    | User-configurable                  | 90 days (default for management events) |
| Storage      | Native, optional S3                | S3 bucket                               |
| Best For     | Performance monitoring, alerting   | Security audits, compliance, tracing    |

---

Let me know if you’d like **dashboard setup steps**, **hands-on labs**, or **practice questions with explanations**!

---

Let me know if you want:

* CloudWatch dashboard setup steps
* CloudTrail configuration guide
* Practice Q\&A or diagram-based notes
