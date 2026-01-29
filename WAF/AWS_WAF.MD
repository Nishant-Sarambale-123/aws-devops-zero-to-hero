Got it — I’ll clean this into **well-structured copy-paste friendly notes** (no links formatting breaking, no extra chat text, clean headings).

---

# AWS WAF Notes

---

## Instructor Details

Name: Moole Muralidhara Reddy
Email: [techworldwithmurali@gmail.com](mailto:techworldwithmurali@gmail.com)
Website: [https://www.techworldwithmurali.com](https://www.techworldwithmurali.com)
LinkedIn: [https://www.linkedin.com/in/moole-muralidhara-reddy](https://www.linkedin.com/in/moole-muralidhara-reddy)

---

## What is AWS WAF?

AWS WAF (Web Application Firewall) is a security service that protects web applications from common internet threats like hackers, bots, and malicious traffic. It allows you to define rules to allow or block HTTP/HTTPS requests to protect your applications from attacks that can slow them down, steal data, or exhaust resources.

It is a Layer 7 firewall designed specifically for web traffic.

---

## What AWS WAF Protects

AWS WAF can be attached to:

* Amazon CloudFront distributions
* Amazon API Gateway REST APIs
* Application Load Balancers (ALB)
* AWS AppSync GraphQL APIs
* Amazon Cognito user pools
* AWS App Runner services
* AWS Verified Access instances

---

## Key Features of AWS WAF

### 1. Managed Rulesets

AWS provides prebuilt managed rule groups to protect against common attacks such as:

* SQL Injection (SQLi)
* Cross-Site Scripting (XSS)
* Known bad bots
* OWASP Top 10 vulnerabilities

These rules are automatically updated by AWS.

---

### 2. Custom Rules

You can create your own rules based on:

* IP addresses
* HTTP headers
* URI strings
* Query parameters
* Request body
* Geographic location

Actions available:

* Allow
* Block
* Count
* CAPTCHA / Challenge

---

### 3. Integration with AWS Services

AWS WAF integrates with:

* CloudFront
* Application Load Balancer
* API Gateway
* AppSync

This enables centralized protection for applications.

---

### 4. Monitoring and Logging

AWS WAF integrates with CloudWatch to provide:

* Metrics
* Dashboards
* Alerts
* Logs for traffic analysis

---

### 5. Scalability and Performance

* Automatically scales with traffic
* Low latency
* Uses AWS global edge network

---

### 6. Rate Limiting and Bot Control

* Rate-based rules to block excessive requests
* Bot Control to detect automated traffic
* CAPTCHA challenges for suspicious users

---

## Creating and Managing Web ACL

### Steps to Create a Web ACL

1. Open AWS WAF Console
2. Click Create Web ACL
3. Enter name and description
4. Add rules (managed or custom)
5. Set actions (Allow / Block / Count)
6. Create Web ACL

---

## Applying Web ACL to an Application Load Balancer

1. Open AWS WAF Console
2. Select Web ACL
3. Go to Associations
4. Click Add association
5. Select ALB
6. Save

---

## Common AWS Managed Rule Groups

### AWS Core Rule Set (CRS)

Protects against OWASP Top 10 threats:

* SQL Injection
* XSS
* Command injection
* Local file inclusion
* HTTP violations

Use case: General web app security

---

### AWS Known Bad Inputs Rule Set

Blocks:

* Known malicious payloads
* Exploit attempts
* Parameter manipulation

Use case: Protection against frequent threats

---

### AWS SQL Injection Rule Set

Blocks SQL injection attempts in:

* Query strings
* POST bodies
* Headers

Use case: Database protection

---

### AWS XSS Rule Set

Blocks cross-site scripting attacks in:

* User input
* Forms
* Headers

Use case: Browser security

---

### AWS IP Reputation List Rule Set

Blocks traffic from known malicious IPs.

Use case: Bot and attacker mitigation

---

### AWS Anonymous IP List Rule Set

Blocks traffic from:

* VPN
* Tor
* Proxy networks

Use case: Prevent anonymous attacker traffic

---

### AWS Bot Control Rule Set

Features:

* Detect bad bots
* Allow good bots (Google, Bing)
* CAPTCHA verification

Use case: Stop scraping and credential stuffing

---

### AWS Account Takeover Prevention (ATP)

Detects:

* Credential stuffing
* Brute force login attempts
* Suspicious login behavior

Use case: Protect authentication systems

---

### AWS Managed DDoS Rule Set (Shield Advanced)

Protects against:

* Layer 7 floods
* Application DDoS

Use case: High-volume attack defense

---

### Third-Party Managed Rule Groups

Available from vendors:

* Fortinet
* F5
* Imperva
* Trend Micro

Use case: Advanced enterprise security

---

## Blocking a Specific IP Address

### Steps

1. Go to AWS WAF Console
2. Create IP Set
3. Add IP address
4. Create rule referencing IP set
5. Set action to Block
6. Attach rule to Web ACL

This blocks traffic from that IP.

---

## Monitoring and Logging AWS WAF

### Enable Logging

1. Open Web ACL
2. Go to Logging and Metrics
3. Enable logging
4. Send logs to:

   * Kinesis Firehose
   * S3
   * CloudWatch Logs

---

### CloudWatch Metrics

Tracks:

* Allowed requests
* Blocked requests
* Counted requests
* Rule match statistics

You can create dashboards and alarms.

---

### Log Data Includes

* Source IP
* Country
* User agent
* Matched rule
* Action taken

---

## Key Interview Points

* AWS WAF is Layer 7 protection
* Uses Web ACLs + rules
* Supports managed + custom rules
* Integrates with ALB / CloudFront / API Gateway
* Supports rate limiting and bot control
* Logs integrate with CloudWatch
* Works with AWS Shield for DDoS defense

---

If you want, I can also give:

✅ 1-page cheat sheet
✅ Interview Q&A
✅ Real architecture example
✅ CLI commands
✅ Terraform example
✅ Exam notes
✅ Production best practices

Just tell me what you want next.
