Here are **clear, structured, interview-ready + practical notes on DynamoDB** — written like DevOps/cloud study material.

---

# ✅ Amazon DynamoDB – Detailed Notes

## 1. What is DynamoDB?

Amazon DynamoDB is a **fully managed NoSQL key-value and document database** that provides:

* Single-digit millisecond latency
* Automatic scaling
* High availability
* Serverless architecture
* Built-in security and backup

👉 You don’t manage servers, OS, storage, or patching.

---

## 2. Core Features

### 🔹 Serverless

* No infrastructure management
* AWS automatically handles scaling and maintenance

### 🔹 High Performance

* Designed for low latency
* Handles millions of requests per second

### 🔹 Auto Scaling

* Automatically adjusts throughput
* Handles traffic spikes

### 🔹 Highly Available

* Data replicated across multiple AZs
* Built-in fault tolerance

### 🔹 Durable

* Data stored redundantly
* 99.999% durability

### 🔹 Security

* Encryption at rest
* Encryption in transit
* IAM access control

---

## 3. DynamoDB Data Model

DynamoDB is schema-less (NoSQL).

### Table Structure

A table contains:

* Items → rows
* Attributes → columns

Example:

| UserID (PK) | Name    | Age |
| ----------- | ------- | --- |
| 101         | Nishant | 25  |


Sure — simplest possible definitions 👇

👉 Item:
A complete record in a DynamoDB table (like one row in a database).

👉 Attribute:
A single field inside an item (like one column value).

Even simpler:

Item = full row
Attribute = one piece of data in that row

---

## 4. Primary Keys

DynamoDB requires a primary key.

### 🔹 Simple Primary Key

* Partition Key only
* Example: UserID

Each value must be unique.

---

### 🔹 Composite Primary Key

Consists of:

* Partition Key
* Sort Key

Example:

| UserID (PK) | OrderDate (SK) | Amount |
| ----------- | -------------- | ------ |
| 101         | 2026-01-01     | 200    |
| 101         | 2026-01-05     | 300    |

👉 Allows multiple items with same partition key.

---

## 5. Partition Key Concept

Partition key determines:

* Data distribution
* Load balancing
* Storage location

DynamoDB hashes partition key → decides where data is stored.

⚠️ Bad partition key = hot partition = throttling.

Good key:

* High cardinality
* Even distribution

---

## 6. Secondary Indexes

Indexes allow alternate query patterns.

### 🔹 Global Secondary Index (GSI)

* Different partition key
* Optional sort key
* Separate throughput

Example:
Query by email instead of UserID.

---

### 🔹 Local Secondary Index (LSI)

* Same partition key
* Different sort key
* Created at table creation
* Shares table throughput

---

## 7. Read & Write Capacity

Two modes:

Now the simple breakdown:

👉 RCU (Read Capacity Unit):
How many reads per second your table supports.

👉 WCU (Write Capacity Unit):
How many writes per second your table supports.
---

### 🔹 Provisioned Mode

You specify:

* Read Capacity Units (RCU)
* Write Capacity Units (WCU)

Cheaper for predictable workloads.

---

### 🔹 On-Demand Mode

Auto scaling built-in.

* Pay per request
* Best for unpredictable traffic

---

## 8. Consistency Models

### 🔹 Eventually Consistent (default)

* Faster
* May return stale data

### 🔹 Strongly Consistent

* Always latest data
* Slightly slower
* Higher cost

DynamoDB Read & Write Capacity Types
📖 Read Capacity (RCU types)
Read Type	RCU cost	Meaning	Use case
Eventually consistent read	0.5 RCU	May return slightly old data	Default apps
Strongly consistent read	1 RCU	Always latest data	Critical reads
Transactional read	2 RCU	ACID guaranteed read	Payments/orders

👉 All values are for up to 4 KB item size

✍️ Write Capacity (WCU types)
Write Type	WCU cost	Meaning	Use case
Standard write	1 WCU	Normal write/update	Most apps
Transactional write	2 WCU	ACID guaranteed write	Banking/orders

👉 All values are for up to 1 KB item size

If item size increases:

2 KB write = 2 WCU

3 KB write = 3 WCU

---

## 9. DynamoDB Operations

### Basic operations:

* PutItem → Insert/update
* GetItem → Read single item
* UpdateItem → Modify item
* DeleteItem → Remove item
* Query → Fetch by key
* Scan → Read entire table (expensive)

⚠️ Avoid Scan in production.

---

## 10. DynamoDB Streams

Streams capture changes in table:

* Insert
* Modify
* Delete

Used for:

* Triggers
* Event-driven apps
* Lambda processing
* Auditing

---

## 11. DynamoDB + Lambda Integration

Common pattern:

DynamoDB Stream → Lambda → Process event

Used for:

* Notifications
* Data pipelines
* Real-time analytics

---

## 12. Backup & Recovery

### 🔹 On-demand backup

Manual snapshots

### 🔹 Point-in-time recovery (PITR)

Restore table to any second in last 35 days

---

## 13. TTL (Time to Live)

Auto delete expired items.

Example:

* Session storage
* Logs
* Temporary data

---

## 14. Transactions

DynamoDB supports ACID transactions:

* All succeed or all fail
* Across multiple items/tables

Useful for:

* Banking
* Orders
* Inventory

---

## 15. DynamoDB Accelerator (DAX)

In-memory cache for DynamoDB.

Benefits:

* Microsecond latency
* Reduces read load

Good for:

* Read-heavy apps

---

## 16. Global Tables

Multi-region replication.

Features:

* Active-active replication
* Low latency global access
* Disaster recovery

---

## 17. Pricing Model

You pay for:

* Read/write requests
* Storage
* Backups
* Streams
* Data transfer

On-demand → per request billing
Provisioned → reserved capacity billing

---

## 18. Best Practices

✅ Use high-cardinality partition keys
✅ Avoid hot partitions
✅ Prefer Query over Scan
✅ Use On-demand for unpredictable traffic
✅ Use DAX for caching
✅ Enable PITR backup
✅ Use TTL for temp data
✅ Design access patterns first

---

## 19. Use Cases

* Gaming leaderboards
* IoT data ingestion
* Real-time analytics
* Shopping carts
* User sessions
* Microservices backend
* Serverless apps

---

## 20. DynamoDB vs RDS

| Feature  | DynamoDB      | RDS             |
| -------- | ------------- | --------------- |
| Type     | NoSQL         | Relational SQL  |
| Scaling  | Automatic     | Manual/limited  |
| Schema   | Flexible      | Fixed           |
| Latency  | Milliseconds  | Higher          |
| Joins    | Not supported | Supported       |
| Best for | Massive scale | Complex queries |

---

## Interview One-Liner

👉 *“DynamoDB is a fully managed, serverless NoSQL database designed for high performance, automatic scaling, and low-latency applications at any scale.”*

---

If you want, I can give:

✅ DynamoDB interview questions
✅ Real-world architecture examples
✅ Terraform DynamoDB setup
✅ DynamoDB design patterns
✅ DynamoDB vs MongoDB
✅ DynamoDB capacity calculations
✅ AWS exam notes
✅ Production best practices
✅ Common mistakes

Just tell me what you want next.
