Here are **detailed notes on Amazon CloudFront**, covering every important concept and component with explanations, examples, and common interview points.

---

# 🌐 **Amazon CloudFront – Detailed Notes**

---

## ✅ **What is Amazon CloudFront?**

**Amazon CloudFront** is a **Content Delivery Network (CDN)** provided by AWS that delivers content (web pages, videos, images, APIs, etc.) to users globally **with low latency and high transfer speed**.

### 📌 Key Idea:

It caches content in **Edge Locations** around the world to serve content closer to the end users, improving performance and reducing the load on the origin server.

---

## 🧠 **Core Concepts**

### 1. **Edge Locations**

* These are the **datacenters** where content is cached.
* When a user requests content, CloudFront serves it from the **nearest edge location**.
* If the content is not already cached, CloudFront retrieves it from the origin.

### 2. **Origin**

* The **source** of your content.
* Can be:

  * **Amazon S3 bucket**
  * **Amazon EC2**
  * **Elastic Load Balancer**
  * **Any HTTP web server (even outside AWS)**

### 3. **Distribution**

* A CloudFront **distribution** is the configuration you create to tell CloudFront what to deliver and from where.
* **Two types:**

  * **Web distribution (Deprecated)**: for websites and HTTP(S) content.
  * **RTMP distribution (Deprecated)**: for streaming media using Adobe RTMP protocol.
  * Now replaced by **CloudFront Distributions with modern HTTP support**.

---

## ⚙️ **How CloudFront Works – Step by Step**

1. **User requests** a file (e.g., an image) from your website (e.g., `d12345.cloudfront.net/image.jpg`).
2. DNS routes the request to the **nearest edge location**.
3. If the file is **cached**, CloudFront serves it directly.
4. If not:

   * CloudFront **fetches** it from the origin.
   * **Caches it** at the edge location.
   * Serves it to the user.
5. On subsequent requests, the content is served from the **cache**.

---

## 📦 **Key Features of CloudFront**

### 🔐 1. **Security**

* **HTTPS Support** with **SSL/TLS encryption**
* **Custom SSL certificates** using AWS Certificate Manager (ACM)
* **Signed URLs and Signed Cookies** for restricted access
* **Origin Access Control (OAC)** or **Origin Access Identity (OAI)** for S3 private access

### 🔁 2. **Caching and TTL**

* You can control **cache duration** using **TTL (Time-To-Live)** settings.
* CloudFront respects cache headers (`Cache-Control`, `Expires`) from the origin.
* You can manually **invalidate** the cache.

### 📜 3. **Custom Error Pages**

* You can define **custom responses** for specific HTTP errors like 404, 403, etc.

### 📈 4. **Real-time Metrics**

* Integrated with **CloudWatch** for monitoring:

  * Requests
  * Cache hit/miss ratio
  * Latency
  * Error rates

### 🛡 5. **DDoS Protection**

* Built-in integration with **AWS Shield** and **AWS WAF**.

### 🚀 6. **Global Reach**

* Edge locations in **hundreds of cities and countries**, providing global low-latency delivery.

---

## 🔧 **Important Configurations**

| Config Option              | Description                                                                                 |
| -------------------------- | ------------------------------------------------------------------------------------------- |
| **Origin Settings**        | Set the source of content.                                                                  |
| **Cache Behavior**         | Define how CloudFront caches content (path patterns, TTL, headers, cookies, query strings). |
| **Viewer Protocol Policy** | Redirect HTTP to HTTPS, allow both, or HTTPS only.                                          |
| **Geo-restriction**        | Allow or block content by **country**.                                                      |
| **Lambda\@Edge**           | Run custom logic (e.g., header rewrites, redirects) **closer to users** at edge locations.  |
| **Field-Level Encryption** | Encrypt specific data before it reaches your application.                                   |

---

## 📂 **CloudFront with S3 Example**

1. Store a static website in S3.
2. Create a CloudFront distribution with S3 bucket as **origin**.
3. Restrict S3 bucket access to only **CloudFront** (using OAI or OAC).
4. Use CloudFront URL to access files globally.

---

## 🧪 **Use Cases**

* Static website hosting with S3 + CloudFront
* Video streaming
* API acceleration
* Dynamic and static content delivery
* Software downloads (large files)
* Secure content delivery with access control

---

## 🛡 **Security Options**

| Feature                 | Purpose                                  |
| ----------------------- | ---------------------------------------- |
| **Signed URLs/Cookies** | Restrict access to paid/premium content. |
| **WAF Integration**     | Block malicious IPs or user-agents.      |
| **Geo-restriction**     | Block users from specific countries.     |
| **HTTPS-only access**   | Enforce secure connections.              |

---

## 📉 **Pricing Overview**

* **Data Transfer Out to Internet** (varies by region)
* **Requests** (HTTP/HTTPS)
* **Invalidation Requests**: First 1,000/month free, then charged
* **Field-Level Encryption and Lambda\@Edge** are billed separately

💡 *Use AWS Free Tier for 1 TB of CloudFront data transfer per month (for the first 12 months).*

---

## 🔍 **Monitoring and Logging**

* **Access Logs**: Logs can be sent to **S3 buckets**.
* **CloudWatch Metrics**: Request count, error rate, bytes downloaded, etc.
* **AWS X-Ray**: For tracing requests through CloudFront + other AWS services

---

## 🧠 **Common Interview Questions**

### 1. What is Amazon CloudFront?

A CDN service that delivers content globally with low latency and high speed using edge locations.

### 2. What are Edge Locations?

Global datacenters where CloudFront caches content for faster delivery.

### 3. How does CloudFront cache content?

Based on path patterns, TTL, and cache headers. Content is stored at edge locations.

### 4. What is Origin Access Control (OAC)?

A mechanism to restrict S3 access only to CloudFront, replacing the older OAI method.

### 5. How can you restrict content access?

* Use **Signed URLs**
* Use **Geo-restriction**
* Use **AWS WAF rules**

### 6. Difference between S3 and CloudFront?

* **S3** stores data.
* **CloudFront** accelerates delivery of data globally.

---

## 📚 **Official AWS Documentation**

* [CloudFront Documentation](https://docs.aws.amazon.com/cloudfront/)
* [Using Signed URLs and Cookies](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/private-content-signed-urls.html)
* [CloudFront with S3](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/DownloadDistS3AndCustomOrigin.html)

---

Let me know if you want a **diagram**, **hands-on setup guide**, or **comparison with other CDNs (like Akamai, Azure CDN, Cloudflare)**.
