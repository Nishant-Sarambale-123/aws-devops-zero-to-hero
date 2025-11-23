Here are **AWS DynamoDB — INTERVIEW STYLE NOTES**
Short, crisp, direct — perfect for quick revision before interviews.

---

# ✅ **AWS DynamoDB – Interview Style Notes**

## **1. What is DynamoDB?**

* Fully managed **NoSQL** key-value + document database by AWS.
* Provides **single-digit millisecond latency**, **infinite scaling**, **serverless**, **high availability**.

---

# **2. DynamoDB Key Features**

* **Serverless** (no infra to manage)
* **Automatic scaling**
* **Built-in security** (IAM + KMS)
* **PITR** (Point-in-Time Recovery)
* **Streams** for change capture
* **TTL** for auto-expiring items
* **Global Tables** for multi-region active-active

---

# **3. DynamoDB Tables, Items, Attributes**

* **Table** – collection of items
* **Item** – individual record
* **Attribute** – key-value pairs
* **Max item size: 400 KB**

---

# **4. Primary Keys**

### **Partition Key (HASH KEY)**

* Must be unique
* Decides storage partition
* Bad choice → hot partition

### **Partition Key + Sort Key (HASH + RANGE)**

* PK can repeat
* SK maintains uniqueness
* Supports range queries (`BETWEEN`, `BEGINS_WITH`)

---

# **5. Capacity Modes**

### **Provisioned**

* Set read/write capacity units (RCU/WCU)
* Auto-scaling optional

### **On-Demand**

* Pay per request
* Best for unpredictable traffic
* No capacity planning

---

# **6. Reads**

### **Eventually Consistent**

* Default
* Faster, cheaper
* Replicated AP model

### **Strongly Consistent**

* Read latest data
* Available only in the same region

---

# **7. Writes**

* **Standard Writes**
* **Transactional Writes** (ACID, multi-item, multi-table)

---

# **8. Index Types**

### **LSI (Local Secondary Index)**

* Same Partition Key
* Different Sort Key
* Must be created during table creation
* Max 5 per table

### **GSI (Global Secondary Index)**

* Different PK and SK
* Most flexible
* Can be created anytime
* Scales independently

---

# **9. DynamoDB Streams**

* Captures item-level changes (INSERT, MODIFY, REMOVE)
* Used for:

  * Lambda triggers
  * Event sourcing
  * Replication
  * Audit logging

---

# **10. Time to Live (TTL)**

* Automatically deletes expired items using a TTL attribute
* Useful for session tokens, temp data, cache invalidation

---

# **11. Backups**

* **On-demand backup**
* **PITR** – recover to any second in last 35 days

---

# **12. Security**

* IAM policies
* KMS encryption (default encrypted)
* VPC endpoints for private access
* Conditional access based on item attributes

---

# **13. Global Tables**

* Multi-region, active-active replication
* Strong consistency across regions
* Automatic conflict resolution (last writer wins)

---

# **14. Hot Partitions**

Occurs when:

* Bad partition key design
* Low cardinality
* Too many reads/writes on same partition key

Fix:

* High-cardinality partition keys
* Randomization techniques
* Use GSIs

---

# **15. Best Practices**

* Use **high-cardinality partition keys**
* Minimize item size (< 400 KB)
* Prefer **queries** over scans
* Use **pagination**
* Avoid scanning large tables
* Prefer **GSI** for alternative query patterns
* Use **DAX** for read-heavy workloads

---

# **16. Common Use Cases**

* IoT device data
* User profiles
* Session management
* Gaming leaderboards
* Shopping carts
* Real-time analytics
* Serverless microservices

---

# 🎯 **One-Liner Summary**

**DynamoDB is a fully managed, highly scalable NoSQL database optimized for fast and predictable performance with seamless serverless integration.**

---

If you want, I can also create:
📌 **DynamoDB Scenario-Based Questions**
📌 **50+ DynamoDB Interview Q&A**
📌 **Quick Visual Architecture Diagram**

Just tell me!
