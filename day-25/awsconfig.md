Here are **detailed notes on AWS Config**, including key concepts, features, use cases, pricing, and interview questions.

---

# 📘 AWS Config – Detailed Notes

---

## 🔹 What is AWS Config?

**AWS Config** is a service that **enables you to assess, audit, and evaluate the configurations** of your AWS resources. It provides a **detailed view of resource configuration history and compliance over time**.

---

## 🔹 Key Features

| Feature                                | Description                                                                                         |
| -------------------------------------- | --------------------------------------------------------------------------------------------------- |
| **Resource Configuration History**     | Tracks historical changes to AWS resource configurations.                                           |
| **Configuration Snapshot**             | Captures the current state of your AWS resources at a specific point in time.                       |
| **Configuration Timeline**             | Visual timeline showing configuration changes and relationships over time.                          |
| **Compliance Checks**                  | Uses AWS Config **Rules** to evaluate whether resource configurations comply with defined settings. |
| **Relationships**                      | Tracks relationships between resources (e.g., EC2 instance → security group → VPC).                 |
| **Integration with AWS Organizations** | Centralized config tracking across multiple AWS accounts.                                           |
| **Supports multi-region setup**        | AWS Config can track resources in multiple regions.                                                 |
| **Aggregator**                         | Centralized view of resource compliance and config history across accounts and regions.             |

---

## 🔹 How AWS Config Works

1. **Set up AWS Config** for an account or organization.
2. Choose:

   * Resources to record (All resources or specific types)
   * Delivery method (S3 bucket for snapshots, SNS for notifications)
3. AWS Config:

   * Records config changes.
   * Stores snapshots in S3.
   * Sends notifications via SNS.
4. Use **AWS Config Rules** to evaluate resources against desired configurations.

---

## 🔹 Supported Resources

AWS Config supports most AWS resources like:

* EC2 instances
* VPCs, Subnets, Route Tables, Security Groups
* S3 Buckets
* IAM Users, Groups, Policies
* RDS Instances
* Lambda functions
* CloudTrail Trails
* Elastic Load Balancers
* And many more...

📌 [Supported resources list (official)](https://docs.aws.amazon.com/config/latest/developerguide/resource-config-reference.html)

---

## 🔹 AWS Config Rules

Rules evaluate the compliance of AWS resources. There are 2 types:

| Rule Type         | Description                                                               |
| ----------------- | ------------------------------------------------------------------------- |
| **Managed Rules** | Pre-built by AWS (e.g., check-s3-bucket-public-read-prohibited)           |
| **Custom Rules**  | Written by user using AWS Lambda (e.g., validate a custom tagging policy) |

### 📌 Examples of Managed Rules

* `s3-bucket-public-read-prohibited`
* `iam-password-policy`
* `ec2-instance-no-public-ip`
* `rds-storage-encrypted`

---

## 🔹 Delivery Channel

A delivery channel tells AWS Config **where to send** the configuration snapshots and compliance results.

* **S3 Bucket** → stores configuration snapshots and history.
* **SNS Topic** → sends notifications for config changes and compliance checks.

---

## 🔹 AWS Config Aggregator

Allows viewing configuration and compliance data **across multiple accounts and regions**.

* Useful for centralized governance in **multi-account architecture** (e.g., AWS Organizations).
* Requires permission delegation to access data from member accounts.

---

## 🔹 Pricing

### AWS Config charges for:

1. **Configuration Items (CIs)** – Each recorded configuration of a supported resource.
2. **Custom Rule evaluations** – Per evaluation.
3. **Conformance Packs** – Collections of rules (pricing per evaluation too).
4. **Recording Global Resources** (e.g., IAM resources).

📌 Pricing link: [https://aws.amazon.com/config/pricing/](https://aws.amazon.com/config/pricing/)

---

## 🔹 Common Use Cases

* **Auditing and Compliance** (PCI, HIPAA, CIS Benchmarks)
* **Governance** of multi-account environments
* **Security posture tracking** – identify non-compliant resources
* **Troubleshooting** resource changes (e.g., who modified security group rules?)
* **Resource inventory** – view all resources and their metadata

---

## 🔹 Integration with Other Services

| Service               | Integration Purpose                               |
| --------------------- | ------------------------------------------------- |
| **CloudTrail**        | Shows who made changes to resource configurations |
| **AWS Organizations** | Centralize Config across accounts                 |
| **AWS Security Hub**  | Shares compliance data                            |
| **Amazon S3**         | Stores config snapshots                           |
| **Amazon SNS**        | Notification delivery                             |
| **AWS Lambda**        | Custom rule logic                                 |

---

## 🔹 Conformance Packs

* A collection of AWS Config rules and remediation actions.
* Used to **audit AWS environments against industry standards**.
* Example: `Operational Best Practices for NIST`, `CIS Benchmark`.

---

## 🔹 AWS Config vs CloudTrail

| Feature    | AWS Config                        | AWS CloudTrail                  |
| ---------- | --------------------------------- | ------------------------------- |
| Focus      | Resource configuration changes    | API call history                |
| Stores     | What changed in resource config   | Who made what API call          |
| Useful for | Auditing resource state           | Auditing actions and access     |
| Retention  | Stored in S3 as per configuration | 90 days (default), export to S3 |

---

# 🧠 Interview Questions on AWS Config

### 🔸 Basic

1. **What is AWS Config? How is it used?**
2. **What kind of resources can AWS Config track?**
3. **What is a configuration item?**
4. **What are the delivery channels in AWS Config?**
5. **What is the use of the AWS Config timeline?**

### 🔸 Intermediate

6. **What are AWS Config Rules? How are custom rules different from managed rules?**
7. **How do AWS Config and CloudTrail complement each other?**
8. **How does AWS Config Aggregator help in an enterprise environment?**
9. **What is a conformance pack?**
10. **Can AWS Config detect changes in IAM policies?**

### 🔸 Advanced

11. **How would you ensure all S3 buckets are not public using AWS Config?**
12. **How do you remediate a non-compliant resource automatically using Config and Lambda?**
13. **How do you optimize the cost of AWS Config in a large organization?**
14. **Explain how AWS Config supports security compliance audits.**
15. **How do you troubleshoot sudden security group changes using Config?**

---

## 🔹 Best Practices

* Enable AWS Config in **all regions** (some resources are regional).
* Use **aggregators** for centralized compliance view.
* Regularly review **compliance reports** and alerts.
* Combine with **CloudTrail** for full traceability (what changed & who did it).
* Set up **S3 bucket lifecycle policies** to manage old snapshots and reduce cost.
* Use **Conformance Packs** for quick compliance setups.

---

Would you like me to create a mind map, notes PDF, or visual architecture of AWS Config setup across AWS Organizations?
