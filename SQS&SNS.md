Here you go — **full detailed SQS & SNS notes + interview questions & answers** in a clean, exam-ready format.

---

# ✅ **Amazon SQS & SNS – Detailed Notes + Interview Q&A**

---

# 🟦 **Amazon SQS (Simple Queue Service)**

## **1. What is SQS?**

SQS is a **fully managed message queueing service** that decouples application components and enables asynchronous communication.

### **Why it is used**

* Decouple microservices
* Remove tight coupling between producer & consumer
* Buffer bursts of traffic
* Ensure reliable message delivery

---

## 🟦 **2. Types of SQS Queues**

### **a) Standard Queue**

* **Unlimited throughput**
* **At-least-once** delivery
* **Best-effort ordering** (not strict)
* Suitable for high-volume background processing

### **b) FIFO Queue**

* **First-In-First-Out** guarantee
* **Exactly-once** processing
* **Limited throughput**

  * 3,000 messages/sec **with batching**
  * 300 messages/sec **without batching**
* Best for financial transactions, workflows, order processing

---

## 🟦 **3. Important SQS Features**

### ✔ Visibility Timeout

Time when a message becomes **invisible** after being picked up by a consumer.
If the consumer fails → message reappears for reprocessing.

Default = 30 sec
Max = 12 hours

---

### ✔ Dead Letter Queue (DLQ)

Stores messages that **cannot be processed** after *maxReceiveCount*.
Helpful for debugging, poison messages, retries.

---

### ✔ Message Retention Period

How long SQS stores messages.

Default = 4 days
Max = 14 days

---

### ✔ Long Polling (recommended)

Waits up to **20 sec** for a message → reduces empty responses and cost.

---

### ✔ Message Ordering With Message Groups (FIFO Only)

* Messages with same *MessageGroupId* are delivered in order.

---

### ✔ Delivery Delay

Delay message visibility for N seconds (0–900 sec).

---

### ✔ Batch Operations

Send/Delete messages in batches (up to 10 msgs).

---

---

# 🟩 **Amazon SNS (Simple Notification Service)**

## **1. What is SNS?**

SNS is a **pub/sub messaging service** used for broadcasting messages to many subscribers simultaneously.

### **Why it is used**

* Send notifications to multiple systems (fan-out)
* Push-based messaging
* Real-time alerts
* Event-driven designs

---

## 🟩 **2. SNS Components**

### ✔ **Topic**

Message channel for publishing events.

### ✔ **Publisher**

System sending messages.

### ✔ **Subscriber**

Who receives messages.

### ✔ Supported Subscription Types

* HTTP / HTTPS endpoints
* Email / Email-JSON
* SMS
* Lambda
* SQS
* Mobile push notifications (GCM/FCM, APNS)

---

## 🟩 **3. SNS Use Cases**

* Monitoring alerts
* Microservice event broadcast
* Fan-out patterns
* Push notifications
* Sending messages to multiple SQS queues

---

# 🚀 **SQS vs SNS (Quick Comparison)**

| Feature           | SQS              | SNS                     |
| ----------------- | ---------------- | ----------------------- |
| Model             | Queue            | Pub/Sub                 |
| Message Delivery  | Pull             | Push                    |
| Message Retention | Yes              | No                      |
| Subscribers       | Single           | Many                    |
| Ordering          | FIFO             | No ordering             |
| Use case          | Async processing | Real-time notifications |

---

# 🟪 **SQS + SNS Fan-Out Architecture**

SNS sends a message → fan-out to **multiple SQS queues** → each queue is processed independently.

Used in:

* Microservices
* Parallel processing
* Distributed systems

---

# 🔥 **SQS Interview Questions & Answers**

---

## **Q1. What is SQS and why is it used?**

### **Short answer:**

A managed message queue to decouple systems.

### **Detailed answer:**

SQS enables asynchronous, reliable communication between components. It helps handle burst traffic, retry failed messages, and ensure that producers and consumers do not depend on each other.

---

## **Q2. Difference between SQS Standard vs FIFO?**

### **Answer:**

* Standard = high throughput, at-least-once, best-effort order
* FIFO = exactly-once, ordered, limited throughput

---

## **Q3. What is visibility timeout?**

### **Answer:**

Period when a message is invisible after being read. If the consumer fails, message becomes visible again to be processed.

---

## **Q4. What is a Dead Letter Queue (DLQ)?**

### **Answer:**

Queue for messages that repeatedly fail processing. Used for debugging & avoiding message loss.

---

## **Q5. What is Long Polling?**

### **Answer:**

Waits for messages up to 20 sec instead of returning empty response → reduces costs and improves efficiency.

---

## **Q6. What happens if a consumer fails to delete a message?**

### **Answer:**

After visibility timeout expires → message becomes visible again → gets reprocessed.

---

## **Q7. Can SQS trigger Lambda directly?**

### ✔ Yes, but only FIFO & Standard queues both supported now.

AWS automatically polls SQS → invokes Lambda.

---

## **Q8. How do you achieve ordering in SQS Standard?**

You **cannot**.
Use **FIFO Queue** + MessageGroupId for ordered messages.

---

## **Q9. What is message retention period?**

### **Answer:**

4 days default, max 14 days.

---

## **Q10. How many messages can SQS batch?**

Up to **10 messages** per batch.

---

# 🔥 **SNS Interview Questions & Answers**

---

## **Q1. What is SNS?**

A fully managed pub/sub service that sends messages to multiple subscribers.

---

## **Q2. Can SNS deliver messages to SQS?**

✔ Yes
Used for **fan-out** architecture.

---

## **Q3. Difference between SNS & SQS?**

SNS = push, broadcast
SQS = pull, queue

---

## **Q4. What is SNS Fan-Out?**

Publishing to one SNS topic → replicates message to many SQS queues.

---

## **Q5. What are SNS protocols?**

HTTP/HTTPS, Email, SMS, SQS, Lambda, mobile push.

---

## **Q6. Does SNS store messages?**

No. SNS does not store messages (except for short retry buffer).

---

## **Q7. How does SNS retry delivery?**

Depending on protocol (HTTP retry policy, backoff).

---

## **Q8. When to use SNS vs SQS?**

* Use SNS when you need **broadcast**.
* Use SQS when you need **decoupling & reliability**.

---

# 🟥 **Scenario-Based Questions**

---

## **Scenario 1:**

You need to process orders **in order** and **only once**.

→ **Use SQS FIFO**

---

## **Scenario 2:**

One event must notify multiple microservices.

→ **SNS + Multiple SQS queues (fan-out)**

---

## **Scenario 3:**

Traffic spikes need buffering to avoid system overload.

→ **SQS Standard** with autoscaling consumers.

---

## **Scenario 4:**

Messages failing repeatedly should not block queue.

→ Configure **DLQ** with redrive policy.

---

## **Scenario 5:**

Mobile app notifications.

→ **SNS Mobile Push**

---

# ✅ Want Next?

I can also give you:

### ✔ SQS/SNS **diagram-based architecture notes**

### ✔ SQS/SNS **real-world DevOps interview questions**

### ✔ 50 MCQs for practice

### ✔ SQS/SNS cheat sheet (1-page)

Just tell me **"give more"** or specify the format.
