Here are the **most important AWS CloudWatch interview questions** with brief explanations to help you answer them confidently. These questions are grouped from **basic to advanced levels**, and are frequently asked in **DevOps, Cloud Engineer, and SRE** interviews.

---

# ✅ **AWS CloudWatch Interview Questions and Answers**

---

## 🟢 **Basic Level**

### 1. **What is Amazon CloudWatch?**

CloudWatch is a monitoring and observability service used to collect and track metrics, collect and monitor log files, set alarms, and automatically react to changes in your AWS environment.

---

### 2. **What is the difference between CloudWatch Metrics and Logs?**

| Feature  | CloudWatch Metrics       | CloudWatch Logs            |
| -------- | ------------------------ | -------------------------- |
| Type     | Numeric time-series data | Raw log data (text)        |
| Use      | Monitor performance      | Debugging, troubleshooting |
| Examples | CPUUtilization, Latency  | App logs, error logs       |

---

### 3. **What are CloudWatch Alarms?**

Alarms monitor CloudWatch metrics and trigger actions like:

* Sending notifications via SNS
* Starting/stopping EC2
* Triggering Auto Scaling

---

### 4. **What are the different states of a CloudWatch Alarm?**

* **OK** – metric is within threshold
* **ALARM** – metric breached threshold
* **INSUFFICIENT\_DATA** – not enough data

---

### 5. **What is a CloudWatch Dashboard?**

A customizable interface to visualize CloudWatch metrics using graphs and widgets. Dashboards are region-specific.

---

### 6. **What are the default metrics collected by CloudWatch for EC2?**

* CPUUtilization
* DiskReadOps / DiskWriteOps
* NetworkIn / NetworkOut
* StatusCheckFailed

> ⚠ Memory and Disk space require CloudWatch Agent.

---

## 🟡 **Intermediate Level**

### 7. **What is the CloudWatch Agent?**

An agent installed on EC2 or on-prem servers to collect system-level metrics like memory, disk space, and custom logs.

---

### 8. **How can you monitor memory utilization of EC2?**

Install and configure **CloudWatch Agent**, as memory usage is not captured by default metrics.

---

### 9. **What is a Log Group and Log Stream in CloudWatch Logs?**

| Term       | Definition                                                       |
| ---------- | ---------------------------------------------------------------- |
| Log Group  | Container for logs (e.g., per application/service)               |
| Log Stream | Sequence of log events from a single source (e.g., EC2 instance) |

---

### 10. **What is CloudWatch Logs Insights?**

An analytics tool to query logs using SQL-like queries for debugging and analysis.

📌 Example:

```sql
fields @timestamp, @message
| filter @message like /ERROR/
| sort @timestamp desc
```

---

### 11. **How is CloudWatch different from CloudTrail?**

| Feature | CloudWatch              | CloudTrail           |
| ------- | ----------------------- | -------------------- |
| Purpose | Metrics/logs monitoring | API call history     |
| Level   | Resource/infra          | Account-level events |
| Example | CPU usage alert         | Who stopped EC2      |

---

### 12. **Can CloudWatch trigger automated actions?**

Yes. Alarms can trigger:

* Auto Scaling
* EC2 instance recovery
* Lambda functions
* SNS notifications

---

### 13. **How do you reduce costs in CloudWatch Logs?**

* Set appropriate **retention** period
* Use **filter patterns** to reduce ingestion
* Store long-term logs in **S3**
* Use **CloudWatch Logs Insights** efficiently (pay per GB scanned)

---

## 🔴 **Advanced Level**

### 14. **What is CloudWatch Contributor Insights?**

It analyzes log data to identify top contributors causing high traffic or errors. Great for anomaly detection.

---

### 15. **How can you monitor an application hosted on-prem using CloudWatch?**

Use **CloudWatch Agent** or **PutMetricData API** to send custom metrics/logs from on-prem infrastructure to AWS.

---

### 16. **What is the difference between Standard and Detailed Monitoring in EC2?**

| Type     | Interval  | Cost |
| -------- | --------- | ---- |
| Standard | 5 minutes | Free |
| Detailed | 1 minute  | Paid |

Use Detailed Monitoring for real-time dashboards or Auto Scaling.

---

### 17. **What is the retention period for metrics in CloudWatch?**

* 1-minute resolution: 15 days
* 5-minute: 63 days
* 1-hour: 455 days

---

### 18. **How can you monitor AWS Lambda using CloudWatch?**

Lambda automatically pushes metrics and logs to CloudWatch:

* **Metrics**: Invocations, Duration, Errors
* **Logs**: Captured via `console.log()`

---

### 19. **Can CloudWatch collect metrics from custom applications?**

Yes. Use:

* **PutMetricData API**
* **CloudWatch Agent**
* **StatsD or collectd plugins**

---

### 20. **What is the use of CloudWatch EventBridge?**

EventBridge (formerly CloudWatch Events) allows:

* Scheduling tasks (cron)
* Reacting to state changes (e.g., EC2 instance stopped → trigger Lambda)

---

## 🔁 **Scenario-Based Questions**

### 21. **Your EC2 instance is running out of disk space. How do you monitor and get notified?**

* Install **CloudWatch Agent**
* Monitor disk space metric
* Create an **Alarm**
* Send notification using **SNS**

---

### 22. **You want to trigger a Lambda function every 12 hours. How?**

Use **CloudWatch Events (EventBridge)** with a scheduled rule (`cron`) to trigger the Lambda function.

---

### 23. **You want to debug why your app failed last night. What tool in CloudWatch will help?**

* Use **CloudWatch Logs** and **Logs Insights** to filter logs based on time and error messages.

---

## 🔗 Official AWS Docs for Reference

* [CloudWatch Docs](https://docs.aws.amazon.com/cloudwatch/)
* [CloudWatch Logs](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/)
* [Alarms Guide](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/AlarmThatSendsEmail.html)
* [Logs Insights](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/AnalyzingLogData.html)

---

Would you like me to create a **PDF of these questions**, or include **hands-on labs** for each concept?
