Here is a comprehensive list of **important AWS EC2 interview questions**, categorized by **level (basic to advanced)** and **with key points you should mention in answers**. These questions are commonly asked in interviews for roles like cloud engineer, DevOps engineer, AWS solution architect, etc.

---

## 🔰 **Basic EC2 Interview Questions**

### 1. **What is Amazon EC2?**

* **Ans:** EC2 (Elastic Compute Cloud) is a web service that provides **resizable compute capacity** in the cloud.
* Key Points: Elastic, scalable, virtual servers, pay-as-you-go model.

---

### 2. **What are the different types of EC2 instances?**

* **Ans:**

  * **General Purpose:** T4g, T3, T3a, M6g, M5
  * **Compute Optimized:** C7g, C6g, C5
  * **Memory Optimized:** R6g, R5, X2idn
  * **Storage Optimized:** I4i, D3, H1
  * **Accelerated Computing:** P4, Inf2, G5

---

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
