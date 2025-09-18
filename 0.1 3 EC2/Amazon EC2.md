Here’s a **detailed set of notes on Amazon EC2 (Elastic Compute Cloud)**, organized so you can use them for **study, reference, and interviews**:

---

# **Amazon EC2 (Elastic Compute Cloud) – Detailed Notes**

## 1. **Introduction**

* **Amazon EC2 (Elastic Compute Cloud)** is a **scalable virtual server service** in AWS.
* Provides **resizable compute capacity** in the cloud – you can launch virtual machines called **EC2 instances**.
* Pay-as-you-go pricing model → pay only for compute you use.
* Used for hosting applications, databases, microservices, testing environments, ML workloads, and more.

---

## 2. **Key Features**

1. **Elasticity** → Scale instances up or down quickly.
2. **Wide Instance Types** → Optimized for compute, memory, storage, GPU, HPC, etc.
3. **Pay-as-you-go & Reserved Pricing**.
4. **Integration with AWS Services** → S3, RDS, VPC, ELB, Auto Scaling.
5. **Customizable AMIs** → Create pre-configured machine images.
6. **Security** → Security Groups (firewalls), Key Pairs (SSH), IAM Roles.
7. **High Availability** → Multi-AZ deployment.
8. **Multiple OS Support** → Linux, Windows, custom OS.

---

## 3. **Core Components**

* **AMI (Amazon Machine Image)**
  Template for launching instances (OS + Software + Config).

* **Instance Type**
  Defines hardware (vCPU, RAM, network, storage).
  Categories:

  * General Purpose (T, M series)
  * Compute Optimized (C series)
  * Memory Optimized (R, X series)
  * Storage Optimized (I, D, H series)
  * Accelerated Computing (P, G, Inf series – GPU/AI workloads)

* **EBS (Elastic Block Store)**
  Persistent block-level storage volumes attached to EC2.
  Volumes are **AZ-specific** but replicated within the AZ.

* **Instance Store (Ephemeral Storage)**
  Temporary storage physically attached to host → lost on stop/terminate.

* **Security Groups**
  Virtual firewall at **instance level** → allow/deny inbound & outbound traffic.

* **Key Pairs**
  SSH/RDP authentication → Private key stays with you, public key with AWS.

* **Elastic IPs**
  Static IPv4 addresses that can be remapped to another instance.

* **Placement Groups**
  Control how instances are placed:

  * **Cluster** – low latency, high throughput.
  * **Spread** – instances spread across hardware.
  * **Partition** – distributed across logical partitions (big data, Hadoop).

---

## 4. **Lifecycle of an EC2 Instance**

* **Pending** → Initializing.
* **Running** → Available for use.
* **Stopping/Stopped** → Preserves root EBS volume, instance not billed.
* **Terminated** → Instance permanently deleted.

---

## 5. **Networking in EC2**

* Instances run inside a **VPC (Virtual Private Cloud)**.
* **Private IP** (within VPC) + **Public IP** (if required).
* Can attach **Elastic IP** for fixed public IP.
* Use **ENI (Elastic Network Interfaces)** for multiple network interfaces.
* **Security Layers**:

  * Security Groups (instance level firewall)
  * NACLs (subnet-level firewall)

---

## 6. **Storage Options**

* **EBS Volumes** (persistent block storage)
  Types:

  * gp3/gp2 → General Purpose SSD
  * io2/io1 → Provisioned IOPS SSD (high performance)
  * st1 → Throughput Optimized HDD
  * sc1 → Cold HDD (low cost)

* **Instance Store** → Temporary storage tied to instance lifecycle.

* **EFS (Elastic File System)** → Network file storage, shared across instances.

* **S3 Integration** → Store backups, AMIs, logs, etc.

---

## 7. **EC2 Purchasing Options**

1. **On-Demand** → Pay by second/hour (no commitment). Best for short-term.
2. **Reserved Instances (RIs)** → 1–3 year commitment → up to 75% cheaper.
3. **Savings Plans** → Flexible pricing model (compute savings).
4. **Spot Instances** → Bid for unused capacity (up to 90% cheaper). Can be interrupted.
5. **Dedicated Hosts** → Physical servers dedicated to you.
6. **Dedicated Instances** → Run on isolated hardware.
7. **Capacity Reservations** → Guarantee capacity for specific AZ.

---

## 8. **Scaling with EC2**

* **Manual Scaling** → Start/stop/terminate manually.
* **Auto Scaling** → Automatically add/remove instances based on demand.
* **Elastic Load Balancing (ELB)** → Distributes traffic across multiple EC2s.
* **HPC (High Performance Computing)** → Cluster placement for low-latency workloads.

---

## 9. **Monitoring & Management**

* **Amazon CloudWatch** → Monitor metrics (CPU, memory, network).
* **EC2 Instance Connect** → Browser-based SSH access.
* **Systems Manager (SSM)** → Manage instances at scale.
* **CloudTrail** → Logs API activity.

---

## 10. **Security Best Practices**

* Use **IAM roles** instead of embedding credentials.
* Restrict SSH/RDP access (use Security Groups wisely).
* Keep AMIs updated & patched.
* Encrypt EBS volumes (KMS).
* Enable CloudWatch alarms & GuardDuty for monitoring.

---

## 11. **Use Cases**

* Web hosting & application servers.
* Databases (RDS alternative for custom DBs).
* Development & testing environments.
* Machine Learning & Big Data (GPU/High Memory instances).
* Batch processing (using Spot Instances).
* Gaming servers.

---

## 12. **Interview-Level Key Points**

* **Difference between Security Groups & NACLs**.
* **EBS vs Instance Store**.
* **EC2 vs Lambda vs ECS/EKS**.
* **Spot vs Reserved vs On-Demand Instances**.
* **Placement Groups types**.
* **How EC2 integrates with Auto Scaling & ELB**.
* **EC2 Monitoring using CloudWatch**.

---

✅ That’s a **complete EC2 notes package** — from basics to advanced topics.

Do you want me to also create a **tabular cheat sheet (quick revision format)** for EC2 (pricing, storage, instance types, networking) so you can revise before interviews?
