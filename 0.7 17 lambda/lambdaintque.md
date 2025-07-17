Here is a **complete list of AWS Lambda interview questions**, ranging from **basic to advanced levels**, including **scenario-based** and **real-world use cases**. Each question is followed by a brief explanation or keyword to help you prepare strong answers.

---

# ✅ **AWS Lambda Interview Questions & Answers**

---

## 🟢 **Basic Level Questions**

---

### 1. **What is AWS Lambda?**

AWS Lambda is a serverless compute service that lets you run code without provisioning or managing servers. It's event-driven and automatically scales.

---

### 2. **Which languages are supported in AWS Lambda?**

* Node.js
* Python
* Java
* Go
* Ruby
* .NET (C#)
* Custom runtimes (using Lambda Runtime API)

---

### 3. **What are some AWS services that can trigger a Lambda function?**

* Amazon S3
* Amazon DynamoDB (Streams)
* Amazon API Gateway
* Amazon EventBridge (CloudWatch Events)
* Amazon SQS
* AWS Step Functions
* ALB (Application Load Balancer)

---

### 4. **What is a Lambda function handler?**

The entry point of your Lambda function.
Example (Python):

```python
def lambda_handler(event, context):
```

---

### 5. **What is the maximum execution timeout for a Lambda function?**

15 minutes (900 seconds)

---

### 6. **What is an event in AWS Lambda?**

The data that triggers the Lambda function, passed in JSON format.

---

### 7. **Where are Lambda logs stored?**

In **Amazon CloudWatch Logs**, automatically by default.

---

## 🟡 **Intermediate Level Questions**

---

### 8. **What is a Lambda Layer?**

A package of libraries or dependencies you can attach to Lambda functions. Max 5 layers per function.

---

### 9. **What is the difference between synchronous and asynchronous invocation in Lambda?**

| Type             | Description                                         |
| ---------------- | --------------------------------------------------- |
| **Synchronous**  | Waits for the result (e.g., API Gateway)            |
| **Asynchronous** | Event is queued; retries on failure (e.g., S3, SNS) |

---

### 10. **How does AWS Lambda scale automatically?**

Lambda runs a new instance for each concurrent request, up to account limits (default 1,000 concurrent executions).

---

### 11. **What is the `/tmp` directory in AWS Lambda?**

Temporary storage available during execution.

* Default: 512 MB
* Can be increased up to 10 GB using **ephemeral storage**

---

### 12. **How can you pass environment-specific configurations to Lambda?**

Using **Environment Variables** (can be encrypted with AWS KMS)

---

### 13. **What is the role of IAM in AWS Lambda?**

Lambda assumes an **execution role** to access other AWS resources like S3, DynamoDB, etc.

---

### 14. **What is the difference between Reserved Concurrency and Provisioned Concurrency?**

| Type            | Description                                     |
| --------------- | ----------------------------------------------- |
| **Reserved**    | Limits function concurrency                     |
| **Provisioned** | Pre-warms Lambda instances to avoid cold starts |

---

### 15. **What is cold start in Lambda?**

The latency when a new container is initialized for the first time. Happens more with VPC-enabled or rarely used functions.

---

### 16. **How can you reduce cold start in Lambda?**

* Use **Provisioned Concurrency**
* Avoid heavy dependencies
* Keep packages lightweight
* Avoid VPC unless necessary

---

## 🔴 **Advanced Level Questions**

---

### 17. **Can a Lambda function access resources in a VPC?**

Yes. It must be configured with:

* VPC ID
* Subnet IDs
* Security Group

---

### 18. **What is the maximum size for deployment package and layers in AWS Lambda?**

* Deployment package (zipped): 50 MB (console), 250 MB (via S3)
* Unzipped: 250 MB
* Layer: 50 MB (unzipped)

---

### 19. **How can you monitor Lambda function metrics?**

Using **Amazon CloudWatch**, which includes:

* Invocations
* Duration
* Errors
* Throttles
* IteratorAge (for streams)

---

### 20. **Can Lambda functions run in parallel?**

Yes. Lambda scales out automatically with multiple concurrent executions (default soft limit: 1,000)

---

### 21. **How is AWS Lambda billed?**

| Item          | Billing                                |
| ------------- | -------------------------------------- |
| **Requests**  | \$0.20 per million                     |
| **Duration**  | Based on memory x execution time (ms)  |
| **Free tier** | 1M requests + 400,000 GB-seconds/month |

---

### 22. **How do you handle exceptions in Lambda?**

* **Synchronous**: Return a structured error
* **Asynchronous**: Retries automatically; can send to **DLQ** (Dead Letter Queue)
* Use try-catch (in code), **CloudWatch Logs** for debugging

---

### 23. **What is Lambda\@Edge?**

Run Lambda functions closer to users at **CloudFront Edge Locations** for low-latency response (used for modifying HTTP requests/responses).

---

### 24. **What is the difference between Lambda and EC2?**

| Feature           | Lambda        | EC2                      |
| ----------------- | ------------- | ------------------------ |
| Server Management | No            | Yes                      |
| Scaling           | Auto          | Manual/Auto Scaling      |
| Use Case          | Event-driven  | Stateful apps, databases |
| Billing           | Per execution | Per hour/second          |

---

## 🔁 **Scenario-Based Questions**

---

### 25. **You need to resize images automatically when users upload them to S3. How will you do it?**

* Configure **S3 PUT trigger** for Lambda
* Lambda processes the image (e.g., using PIL in Python)
* Store resized image in another S3 bucket

---

### 26. **You need to schedule a Lambda to run every day at 9 AM. How?**

* Use **EventBridge rule** (cron job)
* Target: Lambda function

---

### 27. **You want to store processed data into DynamoDB. How will Lambda access it securely?**

* Attach **IAM Role with DynamoDB permissions** to Lambda
* Use AWS SDK in function to put items into DynamoDB

---

### 28. **How can you debug a failed Lambda function?**

* Use **CloudWatch Logs**
* Check error message and stack trace
* Add logging statements in function
* Use **AWS X-Ray** for tracing

---

### 29. **What will you do if your Lambda function is throttled?**

* Increase **reserved concurrency**
* Check and raise **account concurrency limits**
* Implement **backoff and retry**

---

### 30. **Can you run Lambda functions on-premise?**

Not directly. But with **AWS Lambda Runtime Interface Emulator (RIE)** or **Greengrass**, some capabilities are supported.

---

## 🔗 AWS Official Docs

* [Lambda Docs](https://docs.aws.amazon.com/lambda/)
* [Lambda Pricing](https://aws.amazon.com/lambda/pricing/)
* [Lambda Quotas](https://docs.aws.amazon.com/lambda/latest/dg/gettingstarted-limits.html)

---

Would you like:

* ✅ PDF version of these questions
* ✅ Flashcards
* ✅ Diagram of Lambda architecture
* ✅ Resume keywords for Lambda-based projects?

Let me know!
