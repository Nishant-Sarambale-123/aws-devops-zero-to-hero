Perfect — this is a **very common DynamoDB interview question**. Let me give you a **clear, interview-ready answer** with simple explanation and a diagram-style description.

---

# ✅ How Data is Stored in DynamoDB

---

### 1️⃣ DynamoDB is a **Distributed, Partitioned, and Replicated NoSQL Database**

Key points:

* DynamoDB stores data **as items**, which are **key-value pairs (attributes)**.
* **Tables** are split into **partitions** for scalability.
* Each partition is stored on **SSD storage**.
* Data is **replicated across multiple Availability Zones (AZs)** for durability and high availability.

---

### 2️⃣ Partitioning

* DynamoDB uses the **partition key** to determine where data is stored.
* The **partition key is hashed** → hash determines which partition the item belongs to.
* This ensures **even distribution** and prevents hot spots.

**Simple example:**

| user_id | name    | age |
| ------- | ------- | --- |
| 101     | Nishant | 25  |
| 102     | Rahul   | 28  |

* `user_id` is partition key
* Hash of `101` → Partition A
* Hash of `102` → Partition B

---

### 3️⃣ Replication & Nodes

* Each partition has a **Primary Node** (handles writes)
* Data is **replicated to multiple Read Nodes** (for eventual consistency)
* Strongly consistent reads go to the primary node
* Eventually consistent reads can go to any replica

**Simple flow:**

```
Write request → Primary node → replicate to replicas → ACK to client
Read request → Primary node (strong) OR Replica node (eventual)
```

---

### 4️⃣ Secondary Index Storage

* Secondary indexes (GSI/LSI) **store a copy of the attributes** needed for the index
* GSI has **its own partitions and throughput**
* LSI shares partition with main table

---

### 5️⃣ Items & Attributes

* **Item = row** → collection of attributes
* **Attribute = name + value pair**
* Schema-less → items in the same table can have **different attributes**

---

### 6️⃣ Summary (Interview Ready)

> DynamoDB stores data as items (key-value pairs) in tables. Tables are partitioned based on the partition key and stored on SSDs. Each partition has a primary node for writes and multiple read replicas for high availability. Data is replicated across multiple AZs for durability, and secondary indexes maintain alternate access paths.

---

### Optional Diagram (Mental Image)

```
Table → Partition → Primary Node → Replicas
             |          \
             |           -> Eventually consistent reads
             -> Primary node handles writes (strong consistency)
```

---

If you want, I can make a **very simple step-by-step “data flow in DynamoDB” diagram** showing:

* Write → primary node → replica nodes
* Read → strong vs eventual
* Secondary index replication

It’s perfect for explaining in an interview.

Do you want me to make it?
