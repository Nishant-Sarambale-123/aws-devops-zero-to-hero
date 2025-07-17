Here is a **complete and detailed note on AWS Lambda**, including **every important concept, architecture, use case, configuration, pricing, limitations, and interview questions**. These notes are useful for **real-world projects, certifications, and interviews**.

---

# 📘 **AWS Lambda – Complete Detailed Notes**

---

## ✅ **What is AWS Lambda?**

**AWS Lambda** is a **serverless compute service** that lets you run code **without provisioning or managing servers**. You simply upload your code, and Lambda handles everything required to run and scale it.

* **Event-driven**
* **Automatically scalable**
* **Pay-as-you-go**

---

## 🔹 **Key Benefits**

| Feature                         | Description                                                |
| ------------------------------- | ---------------------------------------------------------- |
| **Serverless**                  | No need to manage servers or infrastructure                |
| **Automatic Scaling**           | Scales in response to number of events                     |
| **High Availability**           | Built-in fault tolerance and redundancy                    |
| **Pay-per-use**                 | Charged based on execution time and memory                 |
| **Supports Multiple Languages** | Python, Node.js, Java, Go, Ruby, .NET, and custom runtimes |

---

## 🧠 **How AWS Lambda Works**

1. **Event Source** (e.g., S3, API Gateway, CloudWatch)
2. **Triggers** the Lambda Function
3. **Lambda Executes the Code**
4. Returns response or triggers another service (e.g., S3, DynamoDB)

---

## 🔸 **Core Components**

### 1. **Function**

* The actual code to execute

### 2. **Runtime**

* Language-specific environment to run code (e.g., Python 3.11, Node.js 20)

### 3. **Handler**

* Entry point for function execution

  * Example (Python): `lambda_function.lambda_handler`

### 4. **Event**

* JSON-formatted input that triggers the function

### 5. **Context Object**

* Provides metadata (memory, timeout, request ID)

---

## 🔹 **Supported Languages**

| Runtime            | Versions                          |
| ------------------ | --------------------------------- |
| Node.js            | 14.x, 16.x, 18.x, 20.x            |
| Python             | 3.8, 3.9, 3.10, 3.11              |
| Java               | 8, 11, 17                         |
| Go                 | 1.x                               |
| .NET               | 6, 7                              |
| Ruby               | 2.7, 3.2                          |
| **Custom Runtime** | Bring your own using Amazon Linux |

---

## 🔸 **Trigger/Event Sources**

| Service                       | Use Case                             |
| ----------------------------- | ------------------------------------ |
| **API Gateway**               | Build serverless REST APIs           |
| **S3**                        | Trigger on file upload/delete        |
| **DynamoDB Streams**          | React to table changes               |
| **CloudWatch Events**         | Scheduled tasks (cron jobs)          |
| **SNS/SQS**                   | Messaging and queuing                |
| **EventBridge**               | Event-driven architecture            |
| **Step Functions**            | Workflow orchestration               |
| **Application Load Balancer** | Lambda as target for HTTP(S) traffic |

---

## 🔹 **Invocation Types**

| Type                     | Description                                      |
| ------------------------ | ------------------------------------------------ |
| **Synchronous**          | Waits for function to finish (e.g., API Gateway) |
| **Asynchronous**         | Queued and retried if failed (e.g., S3, SNS)     |
| **Event Source Mapping** | Poll-based (e.g., SQS, DynamoDB Streams, Kafka)  |

---

## 🔸 **Deployment Options**

* **Console**
* **AWS CLI**
* **CloudFormation / SAM / CDK**
* **CI/CD Tools** (e.g., CodePipeline, GitHub Actions)

---

## 🔸 **Environment Variables**

* Used to pass configuration values (e.g., DB URL, secrets).
* Can be encrypted using **AWS KMS**.

---

## 🔸 **Lambda Layers**

* Shared libraries or dependencies across functions.
* Max of **5 layers** per function.
* Reduces function size.

---

## 🔸 **Resource Limits (Quotas)**

| Resource              | Limit                                       |
| --------------------- | ------------------------------------------- |
| Memory                | 128 MB – 10,240 MB                          |
| Timeout               | Max 15 minutes                              |
| Package Size (Zipped) | 50 MB (via console), 250 MB (via S3)        |
| Temp Storage (/tmp)   | 512 MB (up to 10 GB with Ephemeral Storage) |
| Concurrent executions | Default: 1,000 (can be increased)           |

---

## 🔹 **Security**

* Lambda runs inside a **VPC managed by AWS**, but can be configured to connect to your custom VPC.
* IAM Roles:

  * **Execution Role**: Grants permissions to access other AWS services (e.g., S3, DynamoDB).
  * **Resource-based policies**: Control who can invoke the function.

---

## 🔸 **Logging and Monitoring**

* Integrated with:

  * **Amazon CloudWatch Logs** (default logging)
  * **CloudWatch Metrics** (invocations, duration, errors, throttles)
  * **AWS X-Ray** (tracing, debugging, performance analysis)

---

## 🔸 **Pricing**

You are charged based on:

1. **Number of requests**

   * First 1M/month: Free
   * \$0.20 per 1M requests thereafter

2. **Duration (execution time × memory allocated)**

   * Free: 400,000 GB-seconds/month
   * Then charged based on GB-second

3. **Optional Costs**:

   * Provisioned Concurrency
   * Ephemeral storage
   * VPC networking

---

## 🔸 **Provisioned Concurrency vs Reserved Concurrency**

| Type            | Description                             |
| --------------- | --------------------------------------- |
| **Provisioned** | Pre-warms Lambda for low-latency        |
| **Reserved**    | Sets max concurrency limit for function |

---

## 🧠 **Best Practices**

* Use environment variables for configuration.
* Externalize heavy dependencies using **Lambda Layers**.
* Use **CloudWatch Logs Insights** for debugging.
* Set appropriate **timeouts** to avoid hanging.
* Use **Provisioned Concurrency** for low latency APIs.
* Secure with **least privilege IAM roles**.
* Clean up unused functions to save cost.

---

## 🔁 **Use Cases**

* Image/video processing on S3 upload
* REST APIs (via API Gateway + Lambda)
* Real-time data processing (Kinesis, DynamoDB Streams)
* Scheduled tasks (cron)
* Chatbots, ML inference
* Automation (EBS snapshot cleanup, notifications)

---

## 🧩 **Common AWS Lambda Interview Questions**

### 🔹 **Basic**

1. What is AWS Lambda?
2. What languages are supported by AWS Lambda?
3. What is the maximum execution timeout for a Lambda function?
4. What triggers can be used with Lambda?

### 🔹 **Intermediate**

5. How does Lambda scale automatically?
6. Difference between synchronous and asynchronous invocation?
7. What is a Lambda layer?
8. How do you monitor Lambda function performance?
9. How do you secure a Lambda function?
10. What is the difference between memory size and execution time?

### 🔹 **Advanced**

11. How do you connect a Lambda function to a VPC?
12. What is provisioned concurrency, and when should you use it?
13. How does error handling work in asynchronous Lambda?
14. How do you deploy Lambda functions using SAM or CDK?
15. What are cold starts in Lambda and how do you avoid them?

---

## 🔗 Official AWS Documentation

* [AWS Lambda Docs](https://docs.aws.amazon.com/lambda/latest/dg/welcome.html)
* [Lambda Pricing](https://aws.amazon.com/lambda/pricing/)
* [Lambda Limits](https://docs.aws.amazon.com/lambda/latest/dg/gettingstarted-limits.html)
* [Lambda Security](https://docs.aws.amazon.com/lambda/latest/dg/security.html)

---

Would you like a:

* ✅ **PDF of these notes**
* ✅ **Hands-on practice exercises**
* ✅ **Architecture diagram of Lambda**
* ✅ **Resume bullet points for Lambda experience**

Let me know!
