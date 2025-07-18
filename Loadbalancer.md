Here are **detailed notes on Load Balancers**, including types, components, working, benefits, and AWS-specific implementation (like ELB):

---

## 📘 What is a Load Balancer?

A **Load Balancer** is a device or software that distributes incoming network traffic across multiple servers (targets) to ensure:

* No single server is overwhelmed
* High availability
* Reliability
* Performance optimization

---

## 🔧 How Load Balancers Work

1. **Client sends request** to a public endpoint.
2. **Load balancer receives** the request.
3. It chooses a **healthy backend server** using a configured algorithm.
4. **Forwards** the request to that server.
5. Returns the server’s response to the client.

---

## 🎯 Benefits of Load Balancer

| Feature              | Description                                       |
| -------------------- | ------------------------------------------------- |
| High Availability    | If one server fails, traffic is rerouted          |
| Scalability          | Easily distribute traffic among multiple servers  |
| Fault Tolerance      | Health checks detect and remove unhealthy servers |
| Improved Performance | Uses algorithms to reduce latency                 |
| SSL Termination      | Handles SSL decryption                            |
| Security             | Acts as a single point to apply security policies |

---

## 📚 Types of Load Balancers

### 1. **Layer 4 (Transport Layer)**

* Works on TCP/UDP protocols
* Balances traffic based on IP address and port
* Example: TCP Load Balancer

### 2. **Layer 7 (Application Layer)**

* Works on HTTP/HTTPS
* Supports content-based routing
* Can inspect headers, cookies, URLs
* Example: HTTP Load Balancer

---

## 🧠 Load Balancing Algorithms

| Algorithm            | Description                                            |
| -------------------- | ------------------------------------------------------ |
| Round Robin          | Distributes requests sequentially                      |
| Least Connections    | Sends to the server with the fewest active connections |
| IP Hash              | Uses client IP to determine the server                 |
| Weighted Round Robin | Assigns more traffic to powerful servers               |
| Random               | Chooses server randomly                                |

---

## 💡 Components of Load Balancer

1. **Listeners** – Defines protocol and port (e.g., HTTP:80, HTTPS:443)
2. **Target Group** – Group of servers (EC2, containers, IPs)
3. **Health Checks** – Periodic check to remove unhealthy targets
4. **Rules (Layer 7)** – Conditional routing logic (e.g., path-based)
5. **Backend Pool** – Actual servers handling the requests

---

## 🛡️ AWS Elastic Load Balancer (ELB)

### Types of ELB:

| Type                                | Layer       | Use Case                     |
| ----------------------------------- | ----------- | ---------------------------- |
| **Application Load Balancer (ALB)** | Layer 7     | HTTP/HTTPS, advanced routing |
| **Network Load Balancer (NLB)**     | Layer 4     | TCP/UDP, high throughput     |
| **Gateway Load Balancer (GWLB)**    | Layer 3     | Used for security appliances |
| **Classic Load Balancer (CLB)**     | Layer 4 & 7 | Legacy use only              |

---

### 🔍 Application Load Balancer (ALB) – Layer 7

* Content-based routing (host/path)
* Supports WebSockets
* Works well with containers and microservices
* Supports HTTP/2 and SSL offloading

### 🔌 Network Load Balancer (NLB) – Layer 4

* High performance, low latency
* Static IP support
* TLS offloading
* Can handle millions of requests per second

### 🧭 Gateway Load Balancer (GWLB)

* Deploy third-party virtual appliances (e.g., firewall, IDS)
* Integrates with VPC traffic mirroring
* Uses Geneve protocol for tunneling

---

## ✅ Health Checks

* ELB performs periodic checks
* Unhealthy targets are deregistered
* Healthy ones continue serving traffic
* Configurable parameters:

  * Path (e.g., `/health`)
  * Timeout
  * Interval
  * Thresholds

---

## 🧩 Use Cases of Load Balancer

* Distribute traffic across multiple EC2 instances
* Blue-Green deployment
* Zero downtime application updates
* Autoscaling backend targets
* TLS/SSL termination point
* Multi-AZ HA architecture

---

## ⚙️ Load Balancer vs API Gateway

| Feature        | Load Balancer    | API Gateway                   |
| -------------- | ---------------- | ----------------------------- |
| Layer          | L4 or L7         | L7                            |
| Routing        | Based on IP/path | Path, query, header           |
| Rate Limiting  | No               | Yes                           |
| Authentication | Limited          | Built-in                      |
| Monitoring     | CloudWatch       | CloudWatch, Detailed API logs |

---

## 📎 Interview Questions

1. **What is a Load Balancer?**

   * A system to distribute traffic among multiple backend servers.

2. **Difference between ALB, NLB, and CLB in AWS?**

   * ALB: HTTP/HTTPS routing
   * NLB: TCP/UDP, low latency
   * CLB: Legacy, not recommended for new apps

3. **What is path-based routing?**

   * Directing requests based on URI path (e.g., `/login` to one service, `/images` to another).

4. **What is SSL termination in load balancer?**

   * Load balancer handles SSL decryption, reducing backend load.

5. **What happens when a target fails a health check?**

   * Load balancer removes it from the pool temporarily.

6. **Can a load balancer have a static IP?**

   * Only NLB supports Elastic IPs.

7. **Does ALB support WebSocket?**

   * Yes.

8. **Can you use a load balancer with Lambda?**

   * ALB supports Lambda targets for HTTP(S) traffic.

---

## 📘 Summary

* Load Balancer = Traffic Distributor
* Types: ALB (L7), NLB (L4), GWLB (L3), CLB (legacy)
* Key features: HA, fault tolerance, security, SSL, autoscaling
* AWS ELB simplifies implementation of scalable architectures

---

Would you like a diagram or YAML/CloudFormation sample for creating an ELB in AWS?
