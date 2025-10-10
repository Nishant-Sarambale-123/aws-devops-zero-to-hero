Let’s go step-by-step clearly 👇

---

### 📘 Scenario:

You **bought a domain from a third-party registrar** (like GoDaddy, Namecheap, BigRock, etc.)
You want to **use Amazon Route 53** to manage DNS (hosted zone, records, etc.)

---

## 🪜 Steps to set up DNS on Route 53 for a third-party domain:

---

### **Step 1️⃣: Create a Hosted Zone in Route 53**

1. Go to **AWS Console → Route 53**.
2. Click on **“Hosted zones” → “Create hosted zone”**.
3. Enter your **domain name** (exactly as registered, e.g., `example.com`).
4. Select **Public hosted zone** (so it’s accessible on the internet).
5. Click **Create hosted zone**.

---

### **Step 2️⃣: Get the Route 53 Nameservers**

After creating the hosted zone, AWS will automatically create 4 **NS (Name Server)** records and 1 **SOA** record.

* Example NS record might look like:

  ```
  ns-123.awsdns-01.com
  ns-456.awsdns-22.net
  ns-789.awsdns-33.org
  ns-012.awsdns-44.co.uk
  ```

---

### **Step 3️⃣: Update Name Servers in Your Domain Registrar**

Now go to your **domain registrar (external website where you bought the domain)** — for example, GoDaddy, Namecheap, BigRock, etc.

1. Login to your registrar account.
2. Open **DNS Settings** or **Manage Nameservers**.
3. **Replace the existing nameservers** with the 4 Route 53 ones you got in step 2.
4. Save/Apply changes.

✅ This step delegates DNS management to AWS Route 53.

---

### **Step 4️⃣: Add DNS Records in Route 53**

In Route 53 hosted zone, add required DNS records — for example:

| Record Type | Name  | Value               | Purpose                   |
| ----------- | ----- | ------------------- | ------------------------- |
| A           | `@`   | Public IP / ELB DNS | To map domain to website  |
| CNAME       | `www` | `example.com`       | To redirect www to root   |
| MX          | `@`   | Mail server         | For emails                |
| TXT         | `@`   | Verification / SPF  | For Google, AWS SES, etc. |

Example:
If your application is hosted on an EC2 or Load Balancer, you’ll create an **A record** pointing to its public IP or ELB DNS name.

---

### **Step 5️⃣: Verify Propagation**

DNS changes can take some time (usually up to 24–48 hours) to propagate globally.

You can check using:

* [https://dnschecker.org](https://dnschecker.org)
* Or CLI:

  ```bash
  nslookup example.com
  dig example.com NS
  ```

If the nameservers match the ones from Route 53 → ✅ success!

---

### 🧭 Summary:

| Step | Action                | Where                       |
| ---- | --------------------- | --------------------------- |
| 1    | Create hosted zone    | Route 53                    |
| 2    | Copy AWS name servers | Route 53                    |
| 3    | Update nameservers    | Domain registrar (external) |
| 4    | Add DNS records       | Route 53                    |
| 5    | Verify DNS            | DNS checker / CLI           |

---

If you tell me which **registrar** (like GoDaddy, Namecheap, etc.) you used, I can give **exact UI steps** for that site.
Would you like that?
