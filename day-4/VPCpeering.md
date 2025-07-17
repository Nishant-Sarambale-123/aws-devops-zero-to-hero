Here are **detailed notes on AWS VPC Peering**, covering **all concepts, use cases, limitations, and examples** — very useful for interviews, hands-on practice, and understanding cloud networking.

---

# 🌐 **AWS VPC Peering - Full Detailed Notes**

---

## 🔹 What is VPC Peering?

**VPC Peering** is a **network connection** between two VPCs that enables you to **route traffic privately** using **private IP addresses**.

It allows resources (e.g., EC2 instances) in one VPC to communicate with resources in another **as if they are in the same network**, without traversing the public internet.

---

## 🔹 Key Features

| Feature                         | Description                                                    |
| ------------------------------- | -------------------------------------------------------------- |
| **Private Communication**       | Uses private IP addresses to route traffic.                    |
| **Cross-account Support**       | Can peer VPCs in **same or different AWS accounts**.           |
| **Cross-Region Support**        | Can peer VPCs in **different regions** (inter-region peering). |
| **No transitive peering**       | Peering is point-to-point only; no chaining of peers.          |
| **Low Latency, High Bandwidth** | Utilizes AWS backbone network infrastructure.                  |
| **One-to-One Relationship**     | Peering is established between 2 VPCs at a time.               |

---

## 🔹 VPC Peering Use Cases

1. **Shared services VPC** (e.g., centralized logging, DNS, AD)
2. **Application-tier separation** across VPCs (web, app, DB tiers)
3. **VPCs in different AWS accounts** (e.g., mergers, multi-team environments)
4. **Cross-region VPC access** (cost-effective alternative to Direct Connect in some cases)
5. **Hybrid network topologies** with hub-and-spoke models

---

## 🔹 Components Required

* Two VPCs (Peering is initiated from one VPC — the **requester**)
* **CIDR blocks must not overlap**
* Peering connection is **accepted** by the **accepter VPC**
* **Routing tables** must be updated in both VPCs
* **Security groups and NACLs** must allow traffic

---

## 🔹 Steps to Create VPC Peering

1. **Initiate peering request** from VPC-A (requester)
2. **Accept request** from VPC-B (accepter)
3. **Update route tables** in both VPCs to allow traffic
4. **Configure security groups** to allow traffic between resources

---

## 🔹 Example Scenario

| VPC   | CIDR             | Region    |
| ----- | ---------------- | --------- |
| VPC-A | `10.0.0.0/16`    | us-east-1 |
| VPC-B | `192.168.0.0/16` | us-east-1 |

Steps:

* Create a VPC peering connection from A to B
* Accept the peering in B
* Add routes in VPC-A:

  * `Destination: 192.168.0.0/16 → Target: pcx-xxxxxxx`
* Add routes in VPC-B:

  * `Destination: 10.0.0.0/16 → Target: pcx-xxxxxxx`
* Allow traffic in security groups

---

## 🔹 Transitive Routing Limitation (⚠️ Important)

**Transitive routing is not supported.**

Example:

```
VPC-A <-- Peered --> VPC-B <-- Peered --> VPC-C
```

* VPC-A **cannot communicate** with VPC-C through VPC-B.
* To allow communication, you must peer A ↔ B, B ↔ C, and A ↔ C explicitly.

---

## 🔹 DNS Resolution Across Peered VPCs

* You can enable **DNS resolution** across VPC peering.
* Must enable **DNS hostnames and DNS resolution** in both VPCs.
* In peering options: enable **"Allow DNS resolution from peer VPC"**.

---

## 🔹 Cross-Region Peering

Supported for **inter-region** communication.

### Additional notes:

* Uses AWS backbone → **encrypted and low latency**
* Costs: **data transfer charges** apply for inter-region traffic
* Must use **Inter-region Peering IDs** (cannot attach IGWs across regions)

---

## 🔹 Limitations

| Limitation                      | Detail                                     |
| ------------------------------- | ------------------------------------------ |
| No overlapping CIDRs            | CIDR blocks of both VPCs must be unique    |
| No transitive routing           | Cannot route through one VPC to another    |
| No security group referencing   | Cannot use SGs from peered VPCs            |
| 125 peering connections per VPC | (Soft limit, can be increased via support) |
| Manual route table update       | You need to update routes in both VPCs     |
| Only works for IPv4             | IPv6 support is limited                    |

---

## 🔹 Pricing

* **No cost for creating a peering connection**
* **Data transfer charges** apply:

  * Intra-region: **lower cost**
  * Inter-region: **higher cost**

---

## 🔹 VPC Peering vs Transit Gateway (Interview Insight)

| Feature            | VPC Peering          | Transit Gateway                |
| ------------------ | -------------------- | ------------------------------ |
| Setup              | Point-to-point       | Central hub                    |
| Transitive routing | ❌ No                 | ✅ Yes                          |
| Management         | Complex as VPCs grow | Easier                         |
| Max connections    | 125 per VPC          | Thousands via TGW              |
| Use case           | Few VPCs             | Large-scale network topologies |

---

## 🔹 Troubleshooting VPC Peering

* Check that:

  * CIDR blocks do not overlap
  * Peering connection is **active**
  * **Route tables are updated** correctly
  * **Security groups** allow traffic
  * **NACLs** are not blocking the traffic

---

## 🔹 Terraform Example

```hcl
resource "aws_vpc_peering_connection" "peer" {
  vpc_id        = aws_vpc.vpc1.id
  peer_vpc_id   = aws_vpc.vpc2.id
  auto_accept   = true

  tags = {
    Name = "VPC Peering Example"
  }
}
```

---

## 🔹 CLI Command to Create Peering

```bash
aws ec2 create-vpc-peering-connection \
  --vpc-id vpc-aaa111 \
  --peer-vpc-id vpc-bbb222
```

---

Would you like **a diagram** and **hands-on scenario** using AWS Console or CLI to practice this?
