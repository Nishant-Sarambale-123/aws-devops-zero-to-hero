Here are **AWS DynamoDB Interview Notes (Very Detailed, Clean, Easy to Remember)** — perfect for DevOps, Cloud, or SRE interviews.

---

# ⭐ **AWS DynamoDB — Detailed Interview Notes**

## ✅ **What is DynamoDB?**

DynamoDB is a **fully managed, serverless, NoSQL key-value and document database** provided by AWS.
It offers **single-digit millisecond latency**, **automatic scaling**, and **built-in high availability** across multiple AZs.

---

# ⭐ 1. **Core Concepts**

## **1.1 Table**

* DynamoDB stores data in **tables**.
* No fixed schema — you only define **primary key**.

## **1.2 Item**

* A single record in a table.
* Similar to a row in RDBMS.

## **1.3 Attributes**

* Key–value pairs inside an item.
* Similar to columns.

---

# ⭐ 2. **Primary Keys**

## **2.1 Partition Key (HASH Key)**

* Only one key.
* All items with different PK go into different partitions.
* **Used for fast lookups**.
* Must be **unique**.

### Example:

```
UserID
```

## **2.2 Composite Key (Partition Key + Sort Key)**

Used when you want **multiple items** with same partition key.

### Example:

```
UserID (Partition Key)
OrderID (Sort Key)
```

Multiple orders from the same user are stored together.

---

# ⭐ 3. **Capacity Modes**

## **3.1 Provisioned Capacity**

You pre-define:

* **RCU**: Read Capacity Units
* **WCU**: Write Capacity Units

Use when workload is predictable.

## **3.2 On-Demand Capacity**

* You don’t specify capacity.
* DynamoDB auto-scales.
* Pay per request.
* Great for unpredictable workloads.

---

# ⭐ 4. **Consistency Models**

## **4.1 Eventually Consistent Reads** (Default)

* Cheaper, high performance.
* Data may take 1–2 seconds to reflect globally.

## **4.2 Strongly Consistent Reads**

* Guaranteed to return most recent data.
* Slightly slower + double RCU cost.

---

# ⭐ 5. **Indexes in DynamoDB**

## **5.1 Local Secondary Index (LSI)**

* Same Partition Key, different Sort Key.
* Must be created during table creation.
* Max 5 per table.
* **Strong consistency supported**.

## **5.2 Global Secondary Index (GSI)**

* Different Partition Key + Sort Key.
* Can be created anytime.
* Scales independently.
* **Eventually consistent only**.

---

# ⭐ 6. **DynamoDB Streams**

A time-ordered log of item-level changes (INSERT, MODIFY, REMOVE).

Used for:

* Serverless workflows (Lambda triggers)
* Replication
* Event-driven architecture
* Auditing

---

# ⭐ 7. **DynamoDB Accelerator (DAX)**

* Fully managed **in-memory cache**.
* Offers microsecond latency.
* Great for read-heavy workloads.
* Compatible with DynamoDB APIs.

---

# ⭐ 8. **Data Operations**

## **8.1 PutItem**

Create or fully replace an item.

## **8.2 UpdateItem**

Modify specific attributes without replacing whole item.

## **8.3 GetItem**

Fetch one item by Primary Key.

## **8.4 Query**

* Fetch multiple items based on Partition Key.
* Optional condition on Sort Key.

## **8.5 Scan**

* Reads entire table.
* Expensive + slow.
* Avoid in production.

---

# ⭐ 9. **Partitions**

DynamoDB automatically splits data into partitions based on:

* Item size
* Read/write throughput
* Growing dataset

Good partition key design is critical to avoid **hot partitions**.

---

# ⭐ 10. **TTL (Time-To-Live)**

Automatically deletes items after a specific timestamp.
Good for:

* Logs
* Sessions
* Temporary data

---

# ⭐ 11. **Backup & Restore**

DynamoDB provides:

* **On-demand backup**
* **Point-in-time recovery (PITR)** up to 35 days

Restores do NOT affect existing table performance.

---

# ⭐ 12. **Encryption**

DynamoDB supports:

* **Encryption at rest** (KMS-managed keys)
* Client-side encryption (optional)

All traffic uses **TLS in-transit**.

---

# ⭐ 13. **DynamoDB Global Tables**

* Multi-region, multi-master replication.
* Used for global applications.
* Automatic conflict resolution (last writer wins).

---

# ⭐ 14. **Transactions**

* ACID transaction support for up to 25 items or 4MB.
* Used for banking, financial systems, high-integrity apps.

---

# ⭐ 15. **Use Cases**

* Gaming profiles
* Shopping carts
* IoT device data
* Real-time analytics
* Session storage
* Leaderboards
* Mobile applications

---

# ⭐ **Quick Comparison Table**

| Feature | Description              |
| ------- | ------------------------ |
| Type    | NoSQL key-value/document |
| Scaling | Automatic                |
| HA      | Multi-AZ                 |
| Global  | Multi-region replication |
| Indexes | LSI, GSI                 |
| Cache   | DAX                      |
| Backup  | PITR, On-demand          |
| Pricing | RCU/WCU or On-demand     |

---

# ⭐ **Key Takeaway**

> DynamoDB is a high-performance, fully managed NoSQL database built for massive scale, microsecond reads (with DAX), and global replication — ideal for modern cloud applications.

---

If you want, I can also provide:

✅ Scenario-based DynamoDB interview questions
✅ DynamoDB FAQs
✅ DynamoDB cheat sheet (one page)
✅ DynamoDB YAML + CLI examples

Just tell me **“yes”**.
