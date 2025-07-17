Here are **important CDN (Content Delivery Network) interview questions** with detailed answers, especially focused on **Amazon CloudFront**, but also applicable to general CDN concepts.

---

# 📄 **CDN Interview Questions and Answers (Beginner to Advanced)**

---

### 🔹 **1. What is a CDN?**

**Answer:**
A **Content Delivery Network (CDN)** is a globally distributed network of servers that delivers content (web pages, images, videos, scripts, APIs) to users based on their geographic location, the origin of the content, and a content delivery server.

**Key Benefits:**

* Reduces latency
* Improves website load time
* Reduces load on origin servers
* Enhances availability and performance

---

### 🔹 **2. What are the main components of a CDN like Amazon CloudFront?**

**Answer:**

* **Edge Locations**: Datacenters for caching and delivering content closer to users.
* **Origin**: The actual source of the content (e.g., S3 bucket, EC2, external HTTP server).
* **Distribution**: CloudFront configuration for content delivery.
* **Cache Behavior**: Rules for how CloudFront caches and serves content.
* **TTL (Time To Live)**: Controls cache duration for content.
* **Invalidation**: Manually removes content from edge caches.

---

### 🔹 **3. How does a CDN improve website performance?**

**Answer:**

* **Reduces latency** by serving content from the nearest edge location.
* **Decreases server load** by caching static content.
* **Improves availability** by distributing load across global edge servers.
* Enables **faster failover** in case of origin failure.

---

### 🔹 **4. What is the difference between a CDN and a Load Balancer?**

| CDN                       | Load Balancer                              |
| ------------------------- | ------------------------------------------ |
| Delivers content globally | Distributes traffic across backend servers |
| Caches static content     | Doesn’t cache, just forwards requests      |
| Improves performance      | Improves availability and scaling          |
| Edge locations used       | Used at the application layer (e.g., ALB)  |

---

### 🔹 **5. What types of content are typically delivered through a CDN?**

**Answer:**

* Static assets: HTML, CSS, JS, images, fonts
* Video and audio streaming
* Software downloads
* API responses
* Dynamic content (to some extent using caching strategies)

---

### 🔹 **6. What is caching in CDN and how does it work?**

**Answer:**
CDNs cache content at **edge locations** to reduce the need to fetch data from the origin server every time.

**Caching Behavior:**

* Controlled by **TTL**, `Cache-Control`, and `Expires` headers.
* CloudFront allows you to cache based on:

  * Path patterns
  * Query strings
  * Cookies
  * Headers

---

### 🔹 **7. What is TTL in CDN?**

**Answer:**
**TTL (Time to Live)** determines how long a cached object stays in the CDN edge server before it’s considered stale and revalidated with the origin.

**Example:**

* TTL = 3600 seconds → cached for 1 hour

---

### 🔹 **8. How do you invalidate cache in CloudFront?**

**Answer:**

* Use the **"Invalidations"** feature in CloudFront to remove specific files from the cache.
* AWS CLI:

  ```bash
  aws cloudfront create-invalidation \
    --distribution-id YOUR_DISTRIBUTION_ID \
    --paths "/index.html"
  ```

---

### 🔹 **9. How does CloudFront handle HTTPS/SSL?**

**Answer:**

* CloudFront supports **HTTPS** with **SSL/TLS encryption**.
* You can use:

  * **Default CloudFront SSL certificate**
  * **Custom domain with ACM certificate**
* Supports **TLS 1.2** (modern browsers)

---

### 🔹 **10. How can you restrict access to content in CloudFront?**

**Answer:**

* **Signed URLs and Signed Cookies**: For paid/premium content
* **Geo-restriction**: Block users from specific countries
* **Origin Access Control (OAC)**: Restrict S3 content to only CloudFront
* **WAF rules**: Block IPs, user agents, SQL injection, etc.

---

### 🔹 **11. What is Origin Access Identity (OAI) and OAC in CloudFront?**

**Answer:**

* **OAI (Legacy)**: Allows CloudFront to access private S3 buckets.
* **OAC (Newer)**: More flexible and secure method to restrict access from CloudFront to S3. Supports advanced IAM role-based access.

---

### 🔹 **12. What is the difference between Signed URL and Signed Cookie?**

| Feature   | Signed URL                        | Signed Cookie                   |
| --------- | --------------------------------- | ------------------------------- |
| Access to | One specific object               | Multiple objects (or folders)   |
| Best for  | Single-file downloads             | Streaming/video sites           |
| Usage     | URL includes policy and signature | Browser receives secure cookies |

---

### 🔹 **13. What is Lambda\@Edge?**

**Answer:**
Lambda\@Edge allows you to **run serverless functions at AWS edge locations** without managing servers.

**Use Cases:**

* URL rewriting
* A/B testing
* Header modification
* User-based authentication

---

### 🔹 **14. Can CloudFront be used with dynamic content?**

**Answer:**
Yes. CloudFront can cache dynamic content **based on query strings, headers, or cookies**. However, for highly dynamic content, it simply forwards the request to the origin.

---

### 🔹 **15. How is CloudFront priced?**

**Answer:**
Charges are based on:

* **Data transfer out to the internet**
* **Number of requests**
* **Invalidation requests** (first 1,000 free/month)
* **Additional charges** for Lambda\@Edge, field-level encryption

---

## ⚡️ BONUS Questions (Advanced Level)

### 🔸 16. How does CloudFront handle DDoS protection?

* Built-in integration with **AWS Shield** (free)
* Add **AWS WAF** for more advanced protections

---

### 🔸 17. What happens when content is updated in S3? Will CloudFront reflect it immediately?

**Answer:**
No. CloudFront will continue to serve the cached version until the TTL expires or a **manual invalidation** is issued.

---

### 🔸 18. What is field-level encryption in CloudFront?

**Answer:**
Encrypts specific sensitive fields (like credit card info) in HTTP requests before they reach your backend, using **public key encryption** at the edge.

---

### 🔸 19. Can CloudFront deliver content from non-AWS origins?

**Answer:**
Yes, you can configure CloudFront to fetch and cache content from **any HTTP/HTTPS web server**, not just AWS origins.

---

### 🔸 20. Difference between CloudFront and S3 Static Website?

| Feature         | S3 Static Website        | CloudFront                      |
| --------------- | ------------------------ | ------------------------------- |
| Latency         | Higher (no edge caching) | Low latency with edge locations |
| SSL Support     | No custom domain HTTPS   | Full HTTPS with custom domains  |
| DDoS Protection | None                     | Built-in AWS Shield/WAF         |

---

Let me know if you'd like a **mock interview**, **CloudFront architecture diagram**, or **hands-on lab questions** for deeper practice.
