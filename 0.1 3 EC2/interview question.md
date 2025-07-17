### 🟢 Basic EC2 Interview Questions

#### 1. What is Amazon EC2?

**Answer:**
Amazon EC2 (Elastic Compute Cloud) is a web service provided by AWS that offers scalable and resizable compute capacity in the cloud. It eliminates the need to invest in hardware upfront, so you can develop and deploy applications faster.

**Key Points:**

* Elastic and scalable virtual servers
* Pay-as-you-go pricing model
* Supports Windows and Linux
* Full control over instances (start, stop, reboot, terminate)

---

#### 2. What are the different EC2 instance families, and how do you choose between them?

**Answer:**
EC2 instance families are categorized based on specific workload characteristics:

* **General Purpose (T4g, T3, T3a, M6g, M5):** Balanced compute, memory, and networking. Ideal for web servers, app servers, dev/test environments.
* **Compute Optimized (C7g, C6g, C5):** High performance for compute-intensive tasks such as scientific modeling, batch processing, and gaming.
* **Memory Optimized (R6g, R5, X2idn):** Designed for memory-intensive workloads like in-memory databases, caching, and real-time big data analytics.
* **Storage Optimized (I4i, D3, H1):** High, sequential read/write access to large datasets. Great for data warehouses and Hadoop clusters.
* **Accelerated Computing (P4, G5, Inf2):** Use hardware accelerators (GPU/FPGA) for ML inference/training, high-performance computing.

**Choosing:** Based on workload type, architecture (x86 vs ARM), and cost-performance balance.

---

#### 3. What is the difference between an EBS volume and an Instance Store?

**Answer:**

* **EBS (Elastic Block Store):** Persistent block storage. Data survives instance stop/start. Can be detached/attached to multiple instances.
* **Instance Store:** Ephemeral storage located on disks that are physically attached to the host. Data lost on stop/terminate.

---

#### 4. What are the types of EBS volumes?

**Answer:**
Amazon EBS offers five volume types:

1. **gp3 (General Purpose SSD):**

   * Baseline 3,000 IOPS and 125 MB/s throughput, scalable to 16,000 IOPS/1,000 MB/s
   * Ideal for general-purpose workloads, boot volumes

2. **gp2 (General Purpose SSD - Legacy):**

   * IOPS tied to volume size (3 IOPS/GB)
   * Use for dev/test, smaller workloads

3. **io1/io2 (Provisioned IOPS SSD):**

   * io2 is more durable and provides 99.999% durability
   * Up to 64,000 IOPS
   * Ideal for large relational/NoSQL databases

4. **st1 (Throughput Optimized HDD):**

   * Low cost, good for large, sequential workloads like big data
   * Cannot be used as boot volume

5. **sc1 (Cold HDD):**

   * Lowest-cost, infrequent access workloads
   * Suitable for archives and backups

---

#### 5. What are EC2 pricing models?

**Answer:**

1. **On-Demand:**

   * Pay per second (or hour for Windows)
   * No long-term commitment
2. **Reserved Instances:**

   * 1- or 3-year commitment
   * Up to 75% cheaper
3. **Spot Instances:**

   * Up to 90% discount
   * Can be terminated with 2-minute warning
4. **Savings Plans:**

   * Flexible pricing model, commit to compute usage (not instance type)

---

### ⚙️ Intermediate EC2 Interview Questions

#### 6. What is a security group in EC2?

**Answer:**
Security Groups act as virtual firewalls for EC2 instances.

* Control inbound and outbound traffic
* Stateful: Return traffic is automatically allowed
* Default: All inbound traffic denied, outbound allowed

---

#### 7. Difference between a Security Group and Network ACL

| Feature    | Security Group | Network ACL  |
| ---------- | -------------- | ------------ |
| Level      | Instance-level | Subnet-level |
| Rules      | Allow only     | Allow/Deny   |
| Stateful   | Yes            | No           |
| Applies To | EC2            | Subnets      |

---

#### 8. What is a Key Pair in EC2?

**Answer:**
Key pairs enable secure SSH access to Linux instances. AWS stores the public key, and you download the private key (`.pem` or `.ppk`).

---

#### 9. EC2 Instance Lifecycle States

* Pending
* Running
* Stopping
* Stopped
* Terminated

---

#### 10. How do you connect to an EC2 Linux instance?

**Answer:**
Using SSH:

```bash
ssh -i "your-key.pem" ec2-user@<public-ip>
```

Ensure port 22 is open in the security group.

---

#### 11. What is an Elastic IP?

**Answer:**
A static IPv4 address designed for dynamic cloud computing. It persists even if you stop/start an instance.

---

#### 12. How to resize an EC2 instance?

1. Stop instance
2. Modify instance type
3. Start instance

---

#### 13. How to secure data on EC2?

* Use encrypted EBS volumes
* Use SSL/TLS for secure data transmission
* Use IAM roles instead of static credentials
* Restrict access using Security Groups and NACLs

---

#### 14. How to automate EC2 provisioning?

* AWS CloudFormation
* Terraform
* Launch Templates and Auto Scaling Groups
* AWS CLI/SDK

---

### 🚀 Advanced EC2 Interview Questions

#### 15. Difference between Launch Template and Launch Configuration

| Feature         | Launch Template | Launch Configuration |
| --------------- | --------------- | -------------------- |
| Versioning      | Yes             | No                   |
| Modern Features | Supported       | Limited              |
| Flexibility     | More            | Less                 |

---

#### 16. What is EC2 Auto Scaling?

Automatically adjusts number of EC2 instances based on:

* CPU usage
* Schedules
* CloudWatch custom metrics

---

#### 17. What is an EC2 Placement Group?

Logical group of instances:

* **Cluster:** Same AZ, low latency/high throughput
* **Spread:** Different racks, fault-tolerant
* **Partition:** Logical divisions, ideal for large-scale workloads like Hadoop

---

#### 18. Spot Instance Interruption Handling

* AWS provides 2-minute warning before reclaiming
* Use interruption notice script to shutdown gracefully

---

#### 19. What is EC2 Hibernation?

Preserves instance RAM to EBS when stopped. On restart, instance boots faster with same state.
Useful for dev, training, analytics environments.

---

#### 20. What is EC2 User Data?

User data is a script that runs at launch.
Example:

```bash
#!/bin/bash
yum update -y
yum install httpd -y
systemctl start httpd
```

---

#### 21. Difference Between Stop and Terminate

| Operation | Instance | EBS Volume |
| --------- | -------- | ---------- |
| Stop      | Retained | Retained   |
| Terminate | Deleted  | Optional   |

---

#### 22. Can EC2 Have Multiple EBS Volumes?

Yes, up to 27 EBS volumes can be attached per instance (depends on instance type).

---

#### 23. How IAM Roles Work With EC2?

* Attach IAM roles to EC2 to access other AWS services securely.
* No need to hardcode credentials.

---

#### 24. What is an ENI (Elastic Network Interface)?

A virtual network interface attached to EC2.

* Used for failover, multi-homed networking, or application segregation

---

#### 25. How to Troubleshoot EC2 Connectivity?

1. Check security group rules
2. Ensure subnet has route to IGW (if public)
3. Verify NACL allows traffic
4. Instance has a public IP
5. OS-level firewall (iptables/ufw) not blocking

---

### 📘 Bonus Scenario-Based Questions

**Scenario:** Your EC2 web server is not accessible via HTTP.
**Troubleshooting Steps:**

* Security Group allows port 80
* Instance is in Running state
* Web service is installed and active (e.g., Apache, Nginx)
* NACL and route tables correctly configured
* Instance in a public subnet with IGW

**Scenario:** Recover data from a terminated instance?

* Only possible if EBS volume was not deleted
* Attach volume to another EC2 instance

**Scenario:** How to ensure high availability in EC2?

* Use Auto Scaling Groups
* Deploy across multiple Availability Zones
* Use Elastic Load Balancer (ELB)

### 📚 Official Documentation & Links

* EC2 Overview: [https://docs.aws.amazon.com/ec2/index.html](https://docs.aws.amazon.com/ec2/index.html)
* EC2 Pricing: [https://aws.amazon.com/ec2/pricing/](https://aws.amazon.com/ec2/pricing/)
* Launch Templates: [https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-launch-templates.html](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-launch-templates.html)
* EC2 Auto Scaling: [https://docs.aws.amazon.com/autoscaling/ec2/userguide/what-is-amazon-ec2-auto-scaling.html](https://docs.aws.amazon.com/autoscaling/ec2/userguide/what-is-amazon-ec2-auto-scaling.html)
