Here are **detailed notes** on AWS **Security & Compliance** services — essential for interview prep, certification, and practical understanding.

---

## 🔐 **1. AWS KMS (Key Management Service)**

### 📌 **Purpose**

AWS KMS is a **fully managed encryption key service** that allows you to **create, manage, and control** cryptographic keys used to protect your data.

### 🔹 **Key Features**

* **Create Customer Managed Keys (CMK)** or use **AWS Managed Keys**.
* **Symmetric (AES-256)** and **Asymmetric** key support.
* Integrated with services like S3, EBS, RDS, Lambda, etc.
* Uses **envelope encryption** for better performance.
* **Audit** all key usage via **CloudTrail**.
* **Key rotation** can be automatic or manual.

### 🔹 **Use Cases**

* Encrypt S3 bucket objects.
* Encrypt EBS volumes and RDS snapshots.
* Encrypt sensitive environment variables in Lambda.

---

## 🛡️ **2. AWS Shield**

### 📌 **Purpose**

AWS Shield provides **DDoS (Distributed Denial of Service) protection** for your AWS applications.

### 🔹 **Tiers**

| Tier                | Description                                                                                   |
| ------------------- | --------------------------------------------------------------------------------------------- |
| **Shield Standard** | Free and automatically protects AWS infrastructure.                                           |
| **Shield Advanced** | Paid, offers enhanced detection, mitigation, 24/7 DDoS response team, and detailed reporting. |

### 🔹 **Key Features**

* Automatic protection against common Layer 3 & 4 attacks (UDP floods, SYN floods, etc.).
* Layer 7 attack detection with Shield Advanced.
* Integration with **AWS WAF**, **CloudFront**, and **Route 53**.
* **Attack diagnostics** and **cost protection** (credits for DDoS-related usage spikes).

### 🔹 **Use Cases**

* Protect public-facing applications (e.g., web servers, APIs).
* Ensure uptime and service availability.

---

## 🔥 **3. AWS WAF (Web Application Firewall)**

### 📌 **Purpose**

AWS WAF helps protect your web applications from **common web exploits** and **bot attacks**.

### 🔹 **Key Features**

* Works with **CloudFront**, **ALB**, **API Gateway**, and **App Runner**.
* Define custom **rules** to block SQL injection, XSS, etc.
* Managed **Rule Groups** provided by AWS and third parties.
* Real-time **metrics** and **logging** via CloudWatch.
* Set **rate-based rules** to limit traffic spikes.

### 🔹 **Use Cases**

* Block malicious IP addresses.
* Prevent common attacks like SQLi, XSS.
* Filter bots and scrapers.
* Add Layer 7 protection to APIs and websites.

---

## 🧪 **4. Amazon Inspector**

### 📌 **Purpose**

Amazon Inspector is an **automated vulnerability management service** that helps improve security and compliance of AWS workloads.

### 🔹 **Key Features**

* Scans **EC2 instances**, **ECR container images**, and **Lambda functions**.
* Detects vulnerabilities (CVE), outdated software, and security best-practice violations.
* Integrates with **AWS Systems Manager**, **Security Hub**, **EventBridge**.
* **Continuous scanning** or on-demand.
* Prioritized findings with severity levels (CVSS scoring).

### 🔹 **Use Cases**

* Scan container images in ECR before deployment.
* Identify vulnerable EC2 instances in production.
* Maintain compliance posture (e.g., CIS benchmarks).

---

## 🧠 **5. Amazon GuardDuty**

### 📌 **Purpose**

GuardDuty is a **threat detection service** that continuously monitors for **malicious activity** and **unauthorized behavior**.

### 🔹 **Key Features**

* Uses **machine learning**, anomaly detection, and threat intelligence feeds.
* Monitors:

  * VPC flow logs
  * AWS CloudTrail logs
  * DNS logs
* Detects threats like:

  * Unusual login patterns
  * Cryptocurrency mining
  * Communications with known malicious IPs/domains
* Integrates with **Security Hub**, **SNS**, and **Lambda** for automated response.

### 🔹 **Use Cases**

* Detect account compromise (e.g., unusual region access).
* Detect data exfiltration attempts.
* Monitor for malicious behavior inside your AWS environment.

---

## ✅ Summary Table

| Service       | Focus Area                 | Key Benefit                                   |
| ------------- | -------------------------- | --------------------------------------------- |
| **KMS**       | Encryption                 | Central key management, integrates across AWS |
| **Shield**    | DDoS protection            | Automatic defense for infrastructure & apps   |
| **WAF**       | Web application protection | Defends against SQLi, XSS, and bot attacks    |
| **Inspector** | Vulnerability management   | Finds CVEs in EC2, containers, Lambda         |
| **GuardDuty** | Threat detection           | Identifies suspicious behavior & attacks      |

---

Let me know if you want:

* Interview questions and answers for these services
* Architecture diagrams
* Scenario-based implementation examples

Here are **interview** and **scenario-based** questions and answers for key AWS **Security & Compliance** services: **KMS, Shield, WAF, Inspector, and GuardDuty**.

---

## 🔐 1. **AWS KMS (Key Management Service)**

### ✅ **Interview Questions**

**Q1: What is AWS KMS?**
**A:**
AWS KMS is a managed service to create and control encryption keys used to encrypt your data across AWS services like S3, EBS, and RDS.

**Q2: What is envelope encryption in AWS KMS?**
**A:**
Envelope encryption uses a master key to encrypt a data key, which is then used to encrypt the actual data. This improves performance and security.

**Q3: How is KMS integrated with CloudTrail?**
**A:**
All usage of KMS keys is logged in CloudTrail, providing an audit trail of who accessed which key and when.

---

### 🧩 **Scenario Question**

**Q: Your S3 bucket contains sensitive documents that must be encrypted using a customer-managed key. How would you implement this using KMS?**
**A:**

* Create a Customer Managed Key (CMK) in AWS KMS.
* Enable bucket default encryption and select this CMK.
* Apply IAM policies and KMS key policies to restrict access.
* Enable CloudTrail to audit key usage.

---

## 🛡️ 2. **AWS Shield**

### ✅ **Interview Questions**

**Q1: What is the difference between AWS Shield Standard and Advanced?**
**A:**

* **Shield Standard**: Free, automatic protection against common DDoS attacks.
* **Shield Advanced**: Paid, provides advanced detection, 24/7 support, and financial protection.

**Q2: Can Shield protect at Layer 7?**
**A:**
Shield Advanced integrates with AWS WAF to provide Layer 7 (application layer) protection.

---

### 🧩 **Scenario Question**

**Q: A DDoS attack is targeting your web app hosted behind an Application Load Balancer. How would AWS Shield help?**
**A:**

* **Shield Standard** auto-detects and mitigates the attack at the infrastructure level.
* For better visibility and response, **Shield Advanced** can be enabled to analyze and respond to complex attacks, and coordinate with AWS DDoS Response Team (DRT).

---

## 🌐 3. **AWS WAF (Web Application Firewall)**

### ✅ **Interview Questions**

**Q1: What can AWS WAF protect against?**
**A:**
It protects against common web exploits like SQL injection, XSS, bad bots, and allows IP whitelisting/blacklisting.

**Q2: How does AWS WAF integrate with other AWS services?**
**A:**
It can be deployed with CloudFront, ALB, API Gateway, and AWS App Runner.

---

### 🧩 **Scenario Question**

**Q: Your API Gateway is receiving malicious payloads. How can AWS WAF help?**
**A:**

* Attach AWS WAF to the API Gateway.
* Create rules to block specific patterns (e.g., SQLi, XSS).
* Use managed rule groups for standard protections.
* Enable logging and monitoring via CloudWatch.

---

## 🧪 4. **Amazon Inspector**

### ✅ **Interview Questions**

**Q1: What does Amazon Inspector do?**
**A:**
Inspector automatically scans EC2 instances, Lambda, and container images for vulnerabilities and security misconfigurations.

**Q2: What types of findings does Inspector generate?**
**A:**

* CVE vulnerabilities (OS and software packages)
* CIS benchmark violations
* Lambda security risks (publicly accessible, missing permissions)

---

### 🧩 **Scenario Question**

**Q: Your compliance team needs a monthly report of all vulnerabilities in EC2 and ECR. How would you automate this with Amazon Inspector?**
**A:**

* Enable Inspector and integrate with Systems Manager.
* Configure continuous scanning of EC2 and ECR.
* Set up EventBridge rules to forward findings to an SNS topic or Security Hub.
* Generate reports from Security Hub or export data to S3 for monthly review.

---

## 🧠 5. **Amazon GuardDuty**

### ✅ **Interview Questions**

**Q1: What is Amazon GuardDuty and what data sources does it analyze?**
**A:**
GuardDuty is a threat detection service that uses ML and threat intelligence. It analyzes CloudTrail logs, VPC flow logs, and DNS logs.

**Q2: What are some examples of threats GuardDuty can detect?**
**A:**

* Login attempts from unusual geolocations
* Crypto-mining malware
* Data exfiltration
* Communications with known malicious IPs

---

### 🧩 **Scenario Question**

**Q: You receive an alert from GuardDuty about an EC2 instance communicating with a known malware domain. What steps would you take?**
**A:**

* Investigate the alert in GuardDuty console.
* Isolate the EC2 instance (remove from load balancer or quarantine via security groups).
* Analyze CloudTrail logs to track commands or changes.
* Take a snapshot for forensic analysis.
* Terminate the instance if compromised and rotate IAM credentials.

---

## ✅ Summary Table of Focus Areas

| Service       | Focus                   | Typical Use Case                                     |
| ------------- | ----------------------- | ---------------------------------------------------- |
| **KMS**       | Encryption management   | Encrypting S3, EBS, RDS with centralized key control |
| **Shield**    | DDoS protection         | Protect apps from network-based attacks              |
| **WAF**       | Web layer protection    | Block XSS, SQLi, and bad bots                        |
| **Inspector** | Vulnerability detection | Scan EC2, ECR, Lambda for CVEs                       |
| **GuardDuty** | Threat detection        | Detect suspicious/malicious behavior                 |

---

Let me know if you’d like hands-on examples or how to implement automation with these services.

