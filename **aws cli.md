Here are **clean, practical, interview-oriented AWS CLI notes** — short, crisp, and perfect for revision.

---

# ✅ **AWS CLI Notes (Quick + Comprehensive)**

## **1. Installation & Setup**

### **Install**

* Windows: MSI installer
* Linux: `curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" …`

### **Configure**

```bash
aws configure
```

Sets:

* **AWS Access Key**
* **AWS Secret Key**
* **Default Region**
* **Default Output Format (json/text/table)**

To view config:

```bash
aws configure list
aws configure list-profiles
```

---

# ✅ **2. AWS CLI Profile Management**

Use multiple accounts:

```bash
aws configure --profile dev
aws configure --profile prod
```

Run a command with a profile:

```bash
aws s3 ls --profile dev
```

Switch profile temporarily:

```bash
export AWS_PROFILE=dev
```

---

# ✅ **3. S3 (Most Used)**

### **List buckets**

```bash
aws s3 ls
```

### **Upload file**

```bash
aws s3 cp file.txt s3://my-bucket/
```

### **Download**

```bash
aws s3 cp s3://my-bucket/file.txt .
```

### **Sync directory**

```bash
aws s3 sync ./data s3://my-bucket/data
```

### **Delete object**

```bash
aws s3 rm s3://my-bucket/file.txt
```

---

# ✅ **4. EC2**

### **List Instances**

```bash
aws ec2 describe-instances
```

Filter running only:

```bash
aws ec2 describe-instances --filters "Name=instance-state-name,Values=running"
```

### **Start / Stop**

```bash
aws ec2 start-instances --instance-ids i-12345
aws ec2 stop-instances --instance-ids i-12345
```

### **Create Key Pair**

```bash
aws ec2 create-key-pair --key-name mykey --query "KeyMaterial" --output text > mykey.pem
```

### **Get Public IP**

```bash
aws ec2 describe-instances --instance-ids i-12345 --query "Reservations[].Instances[].PublicIpAddress" --output text
```

---

# ✅ **5. IAM**

### **List Users**

```bash
aws iam list-users
```

### **Create User**

```bash
aws iam create-user --user-name devuser
```

### **Attach Policy**

```bash
aws iam attach-user-policy \
  --user-name devuser \
  --policy-arn arn:aws:iam::aws:policy/AmazonS3ReadOnlyAccess
```

---

# ✅ **6. Lambda**

List functions:

```bash
aws lambda list-functions
```

Invoke:

```bash
aws lambda invoke --function-name MyFunction out.json
```

---

# ✅ **7. CloudWatch**

### **Get Logs**

```bash
aws logs describe-log-groups
```

Download last 20 log events:

```bash
aws logs get-log-events \
  --log-group-name "/aws/lambda/test" \
  --log-stream-name "2023/01/01/stream" \
  --limit 20
```

---

# ✅ **8. VPC**

List VPCs:

```bash
aws ec2 describe-vpcs
```

List subnets:

```bash
aws ec2 describe-subnets
```

List route tables:

```bash
aws ec2 describe-route-tables
```

---

# ✅ **9. EKS**

List clusters:

```bash
aws eks list-clusters
```

Update kubeconfig:

```bash
aws eks update-kubeconfig --region ap-south-1 --name mycluster
```

---

# ✅ **10. CloudFormation**

List stacks:

```bash
aws cloudformation list-stacks
```

Deploy:

```bash
aws cloudformation deploy --stack-name mystack --template-file template.yaml --capabilities CAPABILITY_IAM
```

---

# ✅ **11. STS**

Get caller identity:

```bash
aws sts get-caller-identity
```

Assume Role:

```bash
aws sts assume-role \
  --role-arn arn:aws:iam::123456789:role/Admin \
  --role-session-name AdminSession
```

---

# ✅ **12. Useful Querying with JMESPath**

Extract fields:

```bash
aws ec2 describe-instances --query "Reservations[].Instances[].InstanceId"
```

Pretty output:

```bash
--output table
```

---

# ✅ **13. Debugging**

Add debug logs:

```bash
aws s3 ls --debug
```

---

# ✅ **14. AWS CLI vs AWS S3 vs S3API**

### **aws s3**

* High-level (sync, cp, mv)
* Easier and user-friendly

### **aws s3api**

* Low-level
* Full control (e.g., bucket encryption, versioning)

Example:

```bash
aws s3api get-bucket-versioning --bucket mybucket
```

---

# 📌 **15. Must-Know CLI Interview Points**

* Difference between `aws s3` vs `aws s3api`
* How to use IAM roles with CLI
* How to assume role using STS
* How to use filters + queries
* Why CLI is better for automation
* How to update kubeconfig for EKS

---

If you want, I can also give:

✅ **AWS CLI cheat sheet (one page PDF style)**
✅ **AWS CLI 50 real-world commands**
✅ **Scenario-based interview questions using AWS CLI**

Just tell me!


Here is a **clean, crisp, one-page AWS CLI Cheat Sheet** — perfect for interviews, quick revision, and daily usage.

---

# 🌟 **AWS CLI CHEAT SHEET (One Page)**

---

# 🔧 **1. Setup & Configuration**

```bash
aws configure
aws configure list
aws configure list-profiles
```

Use a profile:

```bash
aws s3 ls --profile dev
```

Switch temporarily:

```bash
export AWS_PROFILE=dev
```

---

# 🗂️ **2. S3 Commands**

List buckets:

```bash
aws s3 ls
```

Upload / Download:

```bash
aws s3 cp file.txt s3://my-bucket/
aws s3 cp s3://my-bucket/file.txt .
```

Sync folders:

```bash
aws s3 sync . s3://my-bucket
```

Delete object:

```bash
aws s3 rm s3://my-bucket/file.txt
```

S3API (low-level):

```bash
aws s3api get-bucket-versioning --bucket my-bucket
```

---

# 🖥️ **3. EC2 Commands**

List instances:

```bash
aws ec2 describe-instances
```

Filter running:

```bash
aws ec2 describe-instances \
  --filters "Name=instance-state-name,Values=running"
```

Start/Stop:

```bash
aws ec2 start-instances --instance-ids i-123
aws ec2 stop-instances --instance-ids i-123
```

Get public IP:

```bash
aws ec2 describe-instances \
  --instance-ids i-123 \
  --query "Reservations[].Instances[].PublicIpAddress" \
  --output text
```

Create key pair:

```bash
aws ec2 create-key-pair --key-name mykey \
  --query "KeyMaterial" --output text > mykey.pem
```

---

# 👤 **4. IAM**

List:

```bash
aws iam list-users
aws iam list-roles
aws iam list-policies
```

Create user:

```bash
aws iam create-user --user-name devuser
```

Attach policy:

```bash
aws iam attach-user-policy \
  --user-name devuser \
  --policy-arn arn:aws:iam::aws:policy/AmazonS3ReadOnlyAccess
```

---

# 📡 **5. VPC**

Describe:

```bash
aws ec2 describe-vpcs
aws ec2 describe-subnets
aws ec2 describe-route-tables
aws ec2 describe-security-groups
```

---

# 📦 **6. EKS**

List clusters:

```bash
aws eks list-clusters
```

Update kubeconfig:

```bash
aws eks update-kubeconfig --name cluster --region ap-south-1
```

---

# 📝 **7. CloudWatch**

List log groups:

```bash
aws logs describe-log-groups
```

Get logs:

```bash
aws logs get-log-events \
  --log-group-name "/aws/lambda/test" \
  --log-stream-name "2024/11/11/stream"
```

---

# ⚡ **8. Lambda**

List:

```bash
aws lambda list-functions
```

Invoke:

```bash
aws lambda invoke \
  --function-name MyFn \
  out.json
```

---

# 🧱 **9. CloudFormation**

List stacks:

```bash
aws cloudformation list-stacks
```

Deploy:

```bash
aws cloudformation deploy \
  --stack-name mystack \
  --template-file template.yaml \
  --capabilities CAPABILITY_IAM
```

---

# 🔐 **10. STS (Assume Role)**

Who am I?

```bash
aws sts get-caller-identity
```

Assume role:

```bash
aws sts assume-role \
  --role-arn arn:aws:iam::123:role/Admin \
  --role-session-name AdminSession
```

---

# 🎯 **11. Querying (JMESPath)**

Filter output:

```bash
aws ec2 describe-instances \
  --query "Reservations[].Instances[].InstanceId"
```

Output formats:

```bash
--output json
--output table
--output text
```

---

# 🐞 **12. Debugging AWS CLI**

```bash
aws s3 ls --debug
```

---

# ⚡ **13. Most Important Differences**

| Command     | Purpose                      |
| ----------- | ---------------------------- |
| `aws s3`    | High-level (cp, sync, mv)    |
| `aws s3api` | Low-level API control        |
| `aws ec2`   | Instance/network details     |
| `aws sts`   | Security tokens, assume-role |

---

If you want, I can provide:

📌 **Printable PDF Cheat Sheet**
📌 **Advanced AWS CLI Commands (50+)**
📌 **Scenario-based AWS CLI questions**

Just tell me!

