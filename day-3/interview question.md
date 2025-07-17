Here is a comprehensive list of **important AWS EC2 interview questions**, categorized by **level (basic to advanced)** and **with key points you should mention in answers**. These questions are commonly asked in interviews for roles like cloud engineer, DevOps engineer, AWS solution architect, etc.

---

## 🔰 **Basic EC2 Interview Questions**

### 1. **What is Amazon EC2?**

* **Ans:** EC2 (Elastic Compute Cloud) is a web service that provides **resizable compute capacity** in the cloud.
* Key Points: Elastic, scalable, virtual servers, pay-as-you-go model.

---

1. What are the different EC2 instance families, and how do you choose between them?
Answer:
AWS EC2 instance families are categorized based on the type of workload:

General Purpose (T4g, T3, M6g, M5): Balanced CPU, memory, and network. Good for web servers, small databases.

Compute Optimized (C7g, C6g, C5): High CPU-to-memory ratio. Ideal for CPU-bound workloads like batch processing or gaming servers.

Memory Optimized (R6g, R5, X2idn): High memory-to-CPU ratio. Best for in-memory databases like Redis or SAP HANA.

Storage Optimized (I4i, D3, H1): Designed for high disk I/O. Useful for big data and NoSQL.

Accelerated Computing (P4, G5, Inf2): Use GPUs or custom chips for ML/AI, inference, rendering.

Follow-up Tip: Always evaluate performance requirements, cost efficiency, and instance architecture (Intel/Graviton) when choosing.

### 3. **What is the difference between an EBS volume and an instance store?**

* **Ans:**

  * **EBS (Elastic Block Store):** Persistent storage, survives stop/start.
  * **Instance Store:** Temporary storage, data lost on stop/terminate.

---

### 4. **What are the types of EBS volumes?**

* **Ans:**

  * gp3, gp2 – General purpose SSD
  * io2/io1 – Provisioned IOPS SSD
  * st1 – Throughput optimized HDD
  * sc1 – Cold HDD
Here is a **complete interview-style answer** to the question:

---


**Q: What are the types of Amazon EBS volumes, and when would you use each?**

---

### **Answer:**

Amazon EBS (Elastic Block Store) provides **five types of volumes**, each designed for different use cases based on performance and cost requirements:

---

#### 🔹 1. **gp3 – General Purpose SSD (Latest Generation)**

* **Description:**

  * Default EBS volume type.
  * Offers **baseline performance of 3,000 IOPS** and **125 MB/s throughput**, scalable up to **16,000 IOPS** and **1,000 MB/s**.
  * IOPS and throughput are **independent** of volume size.
* **Use Cases:**

  * Boot volumes
  * General-purpose workloads
  * Web/application servers
  * Small to medium databases

---

#### 🔹 2. **gp2 – General Purpose SSD (Legacy)**

* **Description:**

  * Older SSD volume type.
  * **IOPS is tied to size** (3 IOPS per GB, up to 16,000 IOPS).
  * Performance bursts for short periods.
* **Use Cases:**

  * Development/testing
  * Boot volumes
  * Low to moderate workload apps

---

#### 🔹 3. **io1 / io2 – Provisioned IOPS SSD**

* **Description:**

  * Designed for **high-performance, I/O-intensive** workloads.
  * Supports up to **64,000 IOPS (Nitro instances)**.
  * **io2** is more durable and reliable than io1 (99.999% durability).
* **Use Cases:**

  * Large databases like Oracle, MySQL, PostgreSQL
  * Critical transactional systems
  * Applications requiring consistent low-latency I/O
  * SAP HANA, NoSQL DBs like MongoDB

---

#### 🔹 4. **st1 – Throughput Optimized HDD**

* **Description:**

  * Spinning disk HDD optimized for **large, sequential I/O**.
  * Good throughput but **lower IOPS**.
  * Cannot be a boot volume.
* **Use Cases:**

  * Big data processing (Hadoop, Spark)
  * Data warehouses
  * Log processing and streaming workloads

---

#### 🔹 5. **sc1 – Cold HDD**

* **Description:**

  * Lowest cost HDD storage.
  * Designed for **infrequently accessed** data.
  * Very low IOPS and throughput.
* **Use Cases:**

  * Backup and archival
  * Disaster recovery
  * Large volumes of rarely used data

---

### 📌 **Summary Table:**

| Volume Type | Category | Max IOPS | Use Case                           |
| ----------- | -------- | -------- | ---------------------------------- |
| **gp3**     | SSD      | 16,000   | General workloads, better than gp2 |
| **gp2**     | SSD      | 16,000   | Boot volumes, dev/test             |
| **io1/io2** | SSD      | 64,000   | High-performance DBs               |
| **st1**     | HDD      | \~500    | Big data, logs                     |
| **sc1**     | HDD      | \~250    | Archival, backup                   |

---

### 🔚 Final Tip for Interviews:

Always relate EBS volume choice to **cost, performance, and durability needs**. For example, mention `io2` for high durability in production DBs and `gp3` for everyday scalable workloads.

---

Would you like me to format this answer into a **1-page printable interview sheet or PDF**?


---

### 5. **What are EC2 pricing models?**

* **Ans:**

  * **On-Demand:** Pay per hour/second
  * **Reserved:** 1/3-year commitment, up to 75% discount
  * **Spot Instances:** Up to 90% cheaper, can be interrupted
  * **Savings Plans:** Flexible pricing model

---

## ⚙️ **Intermediate EC2 Questions**

### 6. **What is a security group in EC2?**

* **Ans:** Virtual firewall attached to EC2 instances.

  * **Inbound/outbound rules**
  * **Stateful**
  * **Default deny all**

---

### 7. **What is the difference between a security group and a network ACL?**

| Feature    | Security Group | NACL         |
| ---------- | -------------- | ------------ |
| Type       | Instance-level | Subnet-level |
| Rules      | Allow only     | Allow/deny   |
| Stateful   | Yes            | No           |
| Applied To | EC2            | Subnets      |

---

### 8. **What is a key pair in EC2?**

* **Ans:** A public-private key used to SSH into Linux EC2 instances.
* AWS stores the **public key**, user keeps **private key (.pem/.ppk)**.

---

### 9. **What are EC2 instance states?**

* Pending → Running → Stopping → Stopped → Terminated

---

### 10. **How do you connect to an EC2 Linux instance?**

* SSH using:

  ```bash
  ssh -i "your-key.pem" ec2-user@<public-ip>
  ```

---

### 11. **What is an Elastic IP?**

* Static public IPv4 address assigned to an EC2.
* Stays the same across stop/start.

---

### 12. **How do you resize an EC2 instance?**

* Stop the instance → Change instance type → Start again

---

### 13. **How can you protect data in EC2?**

* **Use encrypted EBS volumes**
* **Enable SSL/TLS for apps**
* **Use IAM roles**
* **Restrict access via security groups**

---

### 14. **How to automate EC2 provisioning?**

* Use **Launch Templates**, **Auto Scaling Groups**, **CloudFormation**, or **Terraform**.

---

## 🚀 **Advanced EC2 Interview Questions**

### 15. **What is the difference between a Launch Template and Launch Configuration?**

| Feature            | Launch Template | Launch Configuration |
| ------------------ | --------------- | -------------------- |
| Versioning         | Yes             | No                   |
| Newer AWS services | Supported       | Limited              |
| Flexibility        | More flexible   | Less flexible        |

---

### 16. **What is EC2 Auto Scaling?**

* Automatically increases or decreases the number of EC2 instances based on:

  * **CPU Utilization**
  * **Custom CloudWatch metrics**
  * **Schedules**

---

### 17. **What is an EC2 placement group?**

* Logical group of instances for workload placement.

  * **Cluster:** Same AZ – low latency
  * **Spread:** Different hardware – high availability
  * **Partition:** Logical groups, used for Hadoop, etc.

---

### 18. **How does Spot Instance interruption work?**

* AWS can reclaim spot instances with **2-minute warning**.
* Use **Spot Instance interruption notice** to gracefully shut down.

---

### 19. **What is hibernation in EC2?**

* Pauses an instance and saves RAM contents to EBS.
* Fast boot-up, useful for dev environments.

---

### 20. **What is EC2 user data?**

* Script executed at instance launch.
* Example: Installing Apache

  ```bash
  #!/bin/bash
  yum update -y
  yum install httpd -y
  systemctl start httpd
  ```

---

### 21. **What’s the difference between stop and terminate?**

* **Stop:** Instance can be restarted; EBS data retained.
* **Terminate:** Instance is deleted; data lost unless EBS is kept.

---

### 22. **Can we attach multiple EBS volumes to one EC2?**

* Yes, EC2 can have **multiple EBS volumes** (up to 27 in most cases).

---

### 23. **How do IAM roles work with EC2?**

* Attach role to EC2 to allow access to other AWS services without storing credentials.

---

### 24. **What is ENI (Elastic Network Interface)?**

* A **virtual network interface** that can be attached to EC2 instances.
* Useful for:

  * Dual-homed instances
  * Failover

---

### 25. **How do you troubleshoot EC2 instance connectivity issues?**

* Check:

  * Security group
  * NACLs
  * Route tables
  * Public IP
  * Key pair
  * OS-level firewall (iptables, ufw)

---

## 📘 **Bonus Scenario-Based Questions**

### ✅ **Q: Your web server is not accessible over HTTP. How would you troubleshoot?**

* Check:

  * Security group has port 80 open
  * Instance is running
  * Web service is installed and started
  * NACL and route table settings
  * Internet Gateway attached (if public subnet)

---

### ✅ **Q: How do you recover data from a terminated instance?**

* Only possible if:

  * EBS volume is not deleted on termination
  * Then: Attach volume to another EC2

---

### ✅ **Q: How to make EC2 highly available?**

* Use:

  * **Auto Scaling Groups**
  * **Elastic Load Balancer (ELB)**
  * **Instances in multiple AZs**

---

## 📚 Official Documentation & Further Learning

* 🔗 EC2 Overview: [https://docs.aws.amazon.com/ec2/index.html](https://docs.aws.amazon.com/ec2/index.html)
* 🔗 EC2 Pricing: [https://aws.amazon.com/ec2/pricing/](https://aws.amazon.com/ec2/pricing/)
* 🔗 Launch Templates: [https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-launch-templates.html](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-launch-templates.html)
* 🔗 EC2 Auto Scaling: [https://docs.aws.amazon.com/autoscaling/ec2/userguide/what-is-amazon-ec2-auto-scaling.html](https://docs.aws.amazon.com/autoscaling/ec2/userguide/what-is-amazon-ec2-auto-scaling.html)

---

Would you like these compiled into a **PDF**, or should I continue with **scenario-based or real-time troubleshooting questions** for EC2?
