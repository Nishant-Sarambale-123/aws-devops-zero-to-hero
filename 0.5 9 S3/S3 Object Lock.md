Here’s a **clear, interview-style explanation of S3 Object Lock** 👆

---

## ☁️ **S3 Object Lock — Interview Notes**

### 🔹 **1. What is S3 Object Lock?**

> **S3 Object Lock** protects objects from being **deleted or overwritten** for a fixed period or indefinitely.
> It is primarily used to meet **compliance, regulatory, or legal requirements** (WORM – Write Once, Read Many).

✅ **Interview answer:**

> “S3 Object Lock prevents accidental or malicious deletion/overwriting of S3 objects by enforcing retention periods or legal holds.”

---

### 🔹 **2. Key Features**

| Feature                          | Description                                                              |
| -------------------------------- | ------------------------------------------------------------------------ |
| **Retention Mode**               | Prevents deletion for a specific period (Compliance or Governance mode). |
| **Governance Mode**              | Users with special permissions can override retention.                   |
| **Compliance Mode**              | Nobody can delete or overwrite until retention expires.                  |
| **Legal Hold**                   | Indefinite protection until manually removed, regardless of retention.   |
| **WORM (Write Once, Read Many)** | Ensures data immutability for regulatory compliance.                     |

---

### 🔹 **3. Modes Explained**

1. **Governance Mode**

   * Default retention applies, but admins with special permissions can **override retention**.
   * Use case: Internal compliance with flexibility.

2. **Compliance Mode**

   * Retention **cannot be overridden**, even by root/admin.
   * Use case: Legal or regulatory requirements (e.g., SEC, FINRA).

3. **Legal Hold**

   * Can be applied at any time, no retention period required.
   * Use case: Ongoing litigation where deletion must be prevented.

---

### 🔹 **4. How to Enable Object Lock**

* Must enable **Object Lock at bucket creation** (cannot enable later).
* Enable **Default retention** for the bucket (optional).
* Apply **per object** when uploading or later using PUT object retention.

📘 **CLI Example:**

```bash
aws s3api put-object-retention \
  --bucket my-bucket \
  --key important-file.txt \
  --retention '{"Mode": "COMPLIANCE","RetainUntilDate":"2026-01-01T00:00:00"}'
```

---

### 🔹 **5. Use Cases**

* Regulatory compliance (financial, healthcare, legal records)
* Protect backups from accidental deletion
* Prevent ransomware or malicious deletion

---

### 💬 **Sample Interview Q&A**

**Q1:** What is S3 Object Lock used for?

> To enforce immutability of S3 objects, preventing deletion or overwriting for compliance or legal reasons.

**Q2:** Can you delete an object in Compliance mode before retention expires?

> No, Compliance mode cannot be overridden until the retention period ends.

**Q3:** Difference between Governance and Compliance mode?

> Governance → Admins can override retention with permissions.
> Compliance → Nobody can override retention until expiration.

**Q4:** Can Object Lock be enabled on an existing bucket?

> No, it must be enabled **at bucket creation**.

---

### 🧠 **One-line Interview Summary:**

> “S3 Object Lock ensures S3 objects are **immutable** for a retention period or legal hold, protecting data from deletion or tampering.”

---

If you want, I can also create **a single-page S3 interview sheet** covering **Keys, Prefixes, Select, Access Points, Object Lock, Versioning, Lifecycle, Storage Classes** — everything **concise for interview prep**.

Do you want me to prepare that?
