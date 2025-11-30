Here are **clean, simple, and point-wise notes** on **AWS Secrets Manager** and **AWS Systems Manager Parameter Store**, along with a comparison.

---

# **AWS Secrets Manager — Point-Wise Notes**

### **Basics**

* Used to store **highly sensitive secrets** like passwords, DB creds, API keys, tokens.
* Automatically integrates with AWS services like RDS, Lambda, EC2.

### **Key Features**

* **Automatic secret rotation** without downtime.

  * Works with RDS MySQL/PostgreSQL/Aurora natively.
* Stores secrets in **encrypted form** using AWS KMS.
* Provides **fine-grained access control** using IAM.
* Maintains **secret versions** and history.
* Supports **cross-account access**.
* Can store secrets up to **64 KB**.

### **Costs**

* Secret Manager is a **paid service**.

  * Charges per secret per month + per 10,000 API calls.

### **Use Cases**

* Database passwords
* Third-party API keys
* OAuth tokens
* Rotation of credentials
* Storing private TLS keys (secure)

---

# **AWS Parameter Store — Point-Wise Notes**

### **Basics**

* Part of **AWS Systems Manager (SSM)**.
* Used for storing **configuration data** and **non-critical secrets**.
* Two types of parameters:

  * **Standard** (free)
  * **Advanced** (paid, higher limits)

### **Key Features**

* Stores values as **PlainText**, **SecureString**, or **StringList**.
* SecureString uses **KMS encryption** for secrets.
* No built-in automatic rotation (handled manually or via Lambda).
* Works well with EC2, Lambda, ECS, CodePipeline, and CloudFormation.
* Supports hierarchical structure like `/dev/app/db/password`.

### **Cost**

* **Standard tier is free**.
* Advanced parameters cost extra.

### **Use Cases**

* App configuration variables
* Environment variables
* Feature flags
* Non-rotating secrets
* Storing AMI IDs, API endpoint URLs, etc.

---

# **Secrets Manager vs Parameter Store — Comparison Table**

| Feature                  | Secrets Manager                 | Parameter Store                      |
| ------------------------ | ------------------------------- | ------------------------------------ |
| **Primary Purpose**      | Store and rotate secrets        | Store config + basic secrets         |
| **Rotation Support**     | **Built-in automatic rotation** | **No built-in rotation**             |
| **Cost**                 | **Paid**                        | **Standard = Free**, Advanced = Paid |
| **Max Size**             | 64 KB                           | 4 KB (Standard), 8 KB (Advanced)     |
| **Versioning**           | Yes                             | Yes                                  |
| **KMS Encryption**       | Yes                             | Yes (SecureString)                   |
| **Secrets Type**         | High-sensitive secrets          | App configs + basic secrets          |
| **Cross-account Access** | Supported                       | Supported                            |
| **Best For**             | DB creds, API keys, tokens      | App settings, env variables          |

---

# **Simple Explanation**

* **Secrets Manager** = for **high-security secrets with automatic rotation**.
* **Parameter Store** = for **general configuration + non-critical secrets**; cheaper or free.

---

If you want, I can also give:
✔ Real-world scenario examples
✔ Interview Q&A format
✔ Architecture diagrams (text-based)
