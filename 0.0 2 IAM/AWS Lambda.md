Great question 👍 Let’s cover **AWS Lambda** in detail with **notes + interview-style Q\&A** so you have a complete reference.

---

# 📘 AWS Lambda – Detailed Notes

### 🔹 Overview

* **AWS Lambda** is a **serverless compute service**.
* You run code **without managing servers**.
* You are charged only for **execution time (ms)** and the number of requests.

---

### 🔹 Key Features

1. **Event-driven** – Triggers from S3, DynamoDB, API Gateway, SNS, SQS, CloudWatch, etc.
2. **Automatic Scaling** – Handles thousands of requests concurrently.
3. **Pay-per-use** – Charged based on request count + execution duration.
4. **Multi-language support** – Python, Node.js, Java, Go, .NET, Ruby, custom runtimes.
5. **Stateless** – Each invocation is independent (use DynamoDB, S3, or RDS for state).
6. **Timeouts** – Max execution time = **15 minutes**.
7. **Memory + CPU** – Memory ranges from 128 MB to 10 GB. CPU scales with memory.
8. **Concurrency Control** – Configurable (reserved concurrency, provisioned concurrency).
9. **Deployment Package** – Code + dependencies zipped and uploaded, or via container images (up to 10 GB).
10. **Monitoring** – Integrated with CloudWatch Logs & X-Ray for tracing.

---

### 🔹 Typical Use Cases

* Real-time file processing (S3 triggers).
* APIs (with API Gateway + Lambda).
* Stream processing (Kinesis, DynamoDB Streams).
* Event-driven automation (CloudWatch, EventBridge).
* Chatbots, IoT backends, lightweight ML inference.

---

### 🔹 Lambda Lifecycle

1. **Event Triggered** (request arrives).
2. **Cold Start / Warm Start**:

   * Cold start → Container + runtime initialized.
   * Warm start → Reuses existing execution environment.
3. **Execution**: Function code runs.
4. **Shutdown**: Environment eventually destroyed after idle timeout.

---

# 🎯 AWS Lambda – Interview Questions & Answers

---

## 🔹 Basics

**Q1. What is AWS Lambda?**

* A serverless compute service where you run code without provisioning servers.
* Charged per execution and duration.

**Q2. Which languages does Lambda support?**

* Node.js, Python, Java, Go, Ruby, .NET, Custom runtimes, Container images.

**Q3. What is the max timeout for Lambda?**

* **15 minutes** per invocation.

---

## 🔹 Triggers & Integrations

**Q4. What are common Lambda triggers?**

* S3 (file upload), DynamoDB Streams, API Gateway, CloudWatch Events, SQS, SNS, Kinesis, EventBridge.

**Q5. Can Lambda be triggered by another Lambda?**

* Yes, indirectly via EventBridge, SQS, or direct SDK calls.

---

## 🔹 Scaling & Performance

**Q6. How does Lambda scale?**

* Automatically creates new instances of the function for concurrent requests.
* Can handle thousands of requests per second.

**Q7. What is concurrency in Lambda?**

* Number of executions running at the same time.
* Controlled with **Reserved Concurrency** (guarantees capacity) or **Provisioned Concurrency** (pre-warms environments to reduce cold starts).

**Q8. What is a Cold Start?**

* Delay when Lambda initializes a new execution environment (first run or after idle).
* Affects latency-sensitive apps.
* Mitigated using **Provisioned Concurrency**.

---

## 🔹 Limits

**Q9. What are Lambda limits?**

* Timeout: 15 minutes.
* Memory: 128 MB – 10 GB.
* Package size: 50 MB (zipped), 250 MB (unzipped), 10 GB (container image).
* Environment variables: 4 KB each.
* Concurrency: By default 1,000 per region (can be increased).

---

## 🔹 Storage & Networking

**Q10. Can Lambda connect to VPC?**

* Yes, it can be attached to a VPC to access private resources (like RDS).
* Needs ENI (Elastic Network Interface) setup in subnets.

**Q11. Where can Lambda store temporary data?**

* `/tmp` directory, with **ephemeral storage up to 10 GB**.
* Useful for caching between invocations.

---

## 🔹 Monitoring & Security

**Q12. How do you monitor Lambda?**

* **CloudWatch Logs** (function logs).
* **CloudWatch Metrics** (invocations, errors, duration, throttles).
* **X-Ray** (tracing & performance analysis).

**Q13. How is IAM used in Lambda?**

* Lambda runs with an **execution role (IAM role)** that defines access permissions (S3, DynamoDB, etc.).

---

## 🔹 Real-World Scenarios

**Q14. You need to process images uploaded to S3. How would you design it?**

* S3 bucket → Trigger Lambda → Lambda processes image (resize, watermark, etc.) → Store in another S3 bucket.

**Q15. How to reduce cold starts in a latency-critical app?**

* Use **Provisioned Concurrency**.
* Keep function warm with CloudWatch scheduled triggers.
* Reduce package size, use smaller runtimes (e.g., Node.js/Python).

**Q16. You need to build a serverless REST API. How?**

* Use **API Gateway** to expose endpoints.
* Each endpoint triggers a **Lambda function**.
* Responses returned to client via API Gateway.

**Q17. Can Lambda run a container image?**

* Yes, Lambda supports **container images up to 10 GB**, built using Docker.

---

✅ That covers both **theory + interview Q\&A + scenarios**.

Do you want me to also make a **comparison table (Lambda vs EC2 vs ECS/Fargate)** for interviews, since that’s a common question?
