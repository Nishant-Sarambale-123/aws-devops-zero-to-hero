Here are **detailed notes on NACL (Network Access Control List)** in AWS, along with **important interview questions and answers** to help you prepare:

---

## 🛡️ AWS NACL (Network Access Control List) – Detailed Notes

---

### 🔹 What is a NACL?

* A **Network Access Control List (NACL)** is a **stateless firewall** that controls **inbound and outbound traffic** at the **subnet level** in a **VPC (Virtual Private Cloud)**.
* Unlike **Security Groups** (which are **stateful** and operate at the instance level), NACLs apply rules to **all resources within a subnet**.

---

### 🔹 Key Characteristics of NACLs

| Feature     | NACL                                                                        |
| ----------- | --------------------------------------------------------------------------- |
| Scope       | Subnet-level                                                                |
| Type        | Stateless                                                                   |
| Rules       | Allow & Deny                                                                |
| Evaluation  | Rule Number Order (Lowest to Highest)                                       |
| Default     | One default NACL per VPC                                                    |
| Association | Can associate with multiple subnets, but only one NACL per subnet at a time |

---

### 🔹 Default vs Custom NACL

| Feature   | Default NACL                | Custom NACL                            |
| --------- | --------------------------- | -------------------------------------- |
| Rules     | Allows all inbound/outbound | Denies all inbound/outbound by default |
| Editable  | Yes                         | Yes                                    |
| Deletable | No                          | Yes                                    |

---

### 🔹 NACL Rule Components

Each rule in a NACL contains:

1. **Rule Number**: Evaluated from lowest to highest (e.g., 100, 200…).
2. **Protocol**: E.g., TCP, UDP, ICMP, or ALL.
3. **Port Range**: E.g., 80 for HTTP, 22 for SSH, etc.
4. **CIDR Block**: Source/destination IP range.
5. **Allow/Deny**: Action for the traffic.

📝 **Important**: As soon as a rule matches, it's applied, and no further rules are evaluated.

---

### 🔹 Inbound and Outbound Rules

* **Inbound** rules: Control incoming traffic.
* **Outbound** rules: Control outgoing traffic.
* **Stateless** nature: You must explicitly allow both directions of communication (unlike security groups).

🧠 **Example**:
If you allow **incoming HTTP (port 80)**, you must also allow **outbound ephemeral ports (1024-65535)** for the response.

---

### 🔹 Rule Evaluation Order

* NACLs process rules **in order (by rule number)**.
* The first matching rule **is applied**, and the evaluation **stops**.
* A **"DENY" rule overrides any "ALLOW"** that comes later.

---

### 🔹 AWS NACL Use Cases

* **Block IP ranges** (e.g., known malicious IPs).
* Provide **coarse-grained** subnet-level security.
* Prevent access to specific ports (e.g., block port 23 for Telnet).
* Add an extra layer of security with **Security Groups**.

---

### 🔹 Comparison: NACL vs Security Group

| Feature          | NACL                    | Security Group                 |
| ---------------- | ----------------------- | ------------------------------ |
| Scope            | Subnet level            | Instance level                 |
| Stateful         | ❌ No                    | ✅ Yes                          |
| Allow Rules      | ✅                       | ✅                              |
| Deny Rules       | ✅                       | ❌                              |
| Rule Evaluation  | By Rule Number          | All rules are evaluated        |
| Default Behavior | Default NACL allows all | Default SG allows none inbound |

---

### 🔹 AWS Best Practices for NACLs

* Use NACLs to **deny known bad traffic**.
* Allow only required traffic (principle of least privilege).
* Combine NACLs with Security Groups for layered security.
* Keep rule numbers spaced (e.g., 100, 200...) for easy updates.

---

## 💡 Common Interview Questions on NACL (with Answers)

---

### **1. What is the difference between NACL and Security Group?**

✅ **Answer**:

* **NACLs** are **stateless**, work at the **subnet level**, and support both **Allow and Deny** rules.
* **Security Groups** are **stateful**, work at the **instance level**, and support **only Allow** rules.

---

### **2. Can a subnet be associated with more than one NACL?**

✅ **Answer**:
No, a subnet can only be associated with **one NACL** at a time. However, one NACL can be **associated with multiple subnets**.

---

### **3. What happens if no rule matches in a NACL?**

✅ **Answer**:
If traffic does not match any NACL rule, it is **implicitly denied**.

---

### **4. Are NACLs evaluated in order?**

✅ **Answer**:
Yes, NACL rules are evaluated in **ascending order by rule number**. Once a match is found, the rule is applied, and **no further rules** are evaluated.

---

### **5. Why are NACLs considered stateless?**

✅ **Answer**:
Because **each request and response is evaluated independently**, even for return traffic. You must explicitly allow both inbound and outbound traffic.

---

### **6. How does default NACL behave?**

✅ **Answer**:
The **default NACL** allows **all inbound and outbound traffic**.

---

### **7. Can you block a specific IP address using NACL?**

✅ **Answer**:
Yes, NACLs support **Deny** rules and can be used to **block traffic from specific IP addresses or CIDR blocks**.

---

### **8. If you allow inbound port 80 in a NACL, is return traffic automatically allowed?**

✅ **Answer**:
No, because NACLs are **stateless**, you also need to explicitly allow the **outbound ephemeral port range** (typically 1024–65535) for the return traffic.

---

### **9. What happens when you delete a custom NACL associated with a subnet?**

✅ **Answer**:
The subnet is automatically **reassociated with the default NACL**.

---

### **10. Can a NACL be attached to multiple subnets?**

✅ **Answer**:
Yes, **a single NACL can be associated with multiple subnets**, but **a subnet can only have one NACL**.

---

## 📌 Tips for Interviews

* Always mention **stateless vs stateful**.
* Emphasize **subnet-level vs instance-level** control.
* Highlight **Allow + Deny** capability of NACLs.
* Give real-world scenarios (e.g., blocking external Telnet traffic).
* Know **default NACL behavior**.

---

If you'd like, I can also provide **diagram-based explanation** or **practice scenarios with rules** (like: allow SSH, deny ICMP, etc.).

Would you like that?
