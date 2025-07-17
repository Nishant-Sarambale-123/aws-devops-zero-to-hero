Here are **detailed notes on Amazon EKS (Elastic Kubernetes Service)** — including key concepts, architecture, setup process, integrations, features, and interview questions.

---

# ☸️ **Amazon EKS (Elastic Kubernetes Service) – Full Notes**

---

## ✅ **What is Amazon EKS?**

**Amazon EKS** is a **fully managed Kubernetes service** by AWS that makes it easy to run Kubernetes without needing to install, operate, or maintain your own control plane or nodes.

📌 **Kubernetes = container orchestration**, EKS = managed Kubernetes on AWS.

---

## 🧱 **EKS Architecture Overview**

```
+-----------------------------+
|        EKS Control Plane   |  (Managed by AWS)
|  - API Server              |
|  - etcd                    |
|  - Scheduler               |
+-------------+-------------+
              |
              v
+-------------+--------------+
|   EKS Worker Nodes (EC2/Fargate)  |
| - Run your container workloads   |
+-------------------------------+
```

### Components:

* **Control Plane**: Managed by AWS, includes API server, etcd (state store), controller manager, scheduler.
* **Worker Nodes**: EC2 instances or Fargate to run Kubernetes pods.
* **Node Group**: A group of EC2 instances managed as a unit.

---

## 🧠 **Key Concepts in EKS**

| Term                                      | Description                                               |
| ----------------------------------------- | --------------------------------------------------------- |
| **Cluster**                               | A Kubernetes cluster with control plane and worker nodes  |
| **Node Group**                            | Group of EC2 instances (nodes) registered to the cluster  |
| **Fargate Profile**                       | Serverless compute option to run pods                     |
| **IAM Roles for Service Accounts (IRSA)** | Fine-grained permissions for pods                         |
| **kubeconfig**                            | File used by `kubectl` to access the cluster              |
| **EKS Add-ons**                           | AWS-managed installation of CoreDNS, kube-proxy, VPC CNI  |
| **Security Groups**                       | Control traffic to nodes                                  |
| **VPC/Subnets**                           | EKS must be deployed in a VPC with private/public subnets |

---

## ⚙️ **EKS Setup Process (High-level)**

### ✅ **Step-by-Step (EC2-based worker nodes)**

1. **Create EKS Cluster**

   * Use Console / CLI / eksctl
   * Choose VPC, subnets, control plane config

2. **Launch Worker Nodes**

   * Create managed/unmanaged node groups (EC2)
   * Configure IAM roles for EC2

3. **Configure `kubectl`**

   * Update kubeconfig:

     ```bash
     aws eks update-kubeconfig --region <region> --name <cluster-name>
     ```

4. **Deploy Workloads**

   * Use standard `kubectl` commands or Helm charts
   * Deploy pods, services, deployments, etc.

5. **Add IAM Permissions (IRSA)**

   * Create IAM role
   * Annotate Kubernetes service account with role ARN

6. **Monitor with CloudWatch, Prometheus, Grafana**

---

## 🖥️ **EKS Node Options**

| Type                       | Description                                                   |
| -------------------------- | ------------------------------------------------------------- |
| **EC2 Managed Node Group** | AWS handles provisioning, scaling, and lifecycle of EC2 nodes |
| **EC2 Unmanaged Nodes**    | You manage EC2 instance lifecycle manually                    |
| **Fargate**                | Serverless compute; no need to manage EC2 instances           |

---

## 🔐 **EKS Security Features**

| Feature                    | Purpose                                    |
| -------------------------- | ------------------------------------------ |
| **IAM for authentication** | IAM users and roles map to Kubernetes RBAC |
| **RBAC**                   | Kubernetes-level access control            |
| **IRSA**                   | Assign IAM roles to pods securely          |
| **KMS encryption**         | Encrypt secrets stored in etcd             |
| **VPC Security Groups**    | Restrict inbound/outbound traffic          |

---

## 🔄 **EKS Add-Ons**

Add-ons are **AWS-managed deployments** of common Kubernetes components:

| Add-on             | Function                          |
| ------------------ | --------------------------------- |
| **VPC CNI**        | Enables pod networking inside VPC |
| **CoreDNS**        | Internal DNS for Kubernetes       |
| **kube-proxy**     | Handles service networking        |
| **Amazon EBS CSI** | Provision EBS volumes dynamically |

Install via:

```bash
aws eks create-addon --cluster-name my-cluster --addon-name vpc-cni --addon-version v1.12.0
```

---

## 📦 **Storage in EKS**

* **Amazon EBS**: Block storage for persistent volumes
* **Amazon EFS**: Shared file system for multiple pods
* **FSx for Lustre**: High-performance file system for ML/HPC workloads
* Use **Kubernetes CSI drivers** for provisioning

---

## 🔁 **Autoscaling in EKS**

| Component                           | Purpose                                                       |
| ----------------------------------- | ------------------------------------------------------------- |
| **Cluster Autoscaler**              | Scales worker nodes (EC2) based on pod demand                 |
| **HPA (Horizontal Pod Autoscaler)** | Scales number of pods based on CPU/memory                     |
| **Karpenter**                       | Open-source auto scaler replacing Cluster Autoscaler (faster) |

---

## 🧪 **Monitoring and Logging**

* **CloudWatch Container Insights**
* **Amazon Managed Prometheus**
* **Grafana (Amazon Managed or self-hosted)**
* **Fluent Bit** for log forwarding

---

## 🚀 **EKS vs ECS**

| Feature        | Amazon EKS                             | Amazon ECS                    |
| -------------- | -------------------------------------- | ----------------------------- |
| Orchestrator   | Kubernetes (open-source standard)      | AWS proprietary               |
| Learning Curve | Higher                                 | Easier                        |
| Flexibility    | Very high (portable, vendor-agnostic)  | AWS-native                    |
| Ecosystem      | Helm, Kustomize, K8s Operators, etc.   | ECS-specific tools            |
| Use Case       | Complex, multi-cloud, open-source apps | Simpler AWS-centric workloads |

---

## 💰 **EKS Pricing**

* **EKS Control Plane**: \$0.10/hour per cluster
* **EC2 / Fargate**: Billed separately
* **Add-ons / Storage / Networking**: Billed based on usage
* **No cost for Kubernetes itself**

---

## 🔗 **Integrations**

| AWS Service                  | Purpose                                     |
| ---------------------------- | ------------------------------------------- |
| **IAM**                      | Authentication and pod-level access control |
| **CloudWatch**               | Logging and metrics                         |
| **ALB/ELB**                  | Ingress controllers for HTTP/S              |
| **Route 53**                 | DNS integration                             |
| **CodePipeline / CodeBuild** | CI/CD deployments                           |
| **Secrets Manager / SSM**    | Secret injection in pods                    |

---

## 🧠 **Common EKS Interview Questions**

### 🔹 1. What is Amazon EKS?

A fully managed Kubernetes service that allows you to run Kubernetes clusters on AWS without managing the control plane.

---

### 🔹 2. What is the difference between EKS managed and unmanaged node groups?

| Managed Node Group               | Unmanaged Node Group     |
| -------------------------------- | ------------------------ |
| AWS manages EC2 lifecycle        | You manage EC2 lifecycle |
| Auto-scaling, patching supported | Manual setup required    |
| Easier and integrated            | More customizable        |

---

### 🔹 3. What is IAM Role for Service Accounts (IRSA)?

**Answer:**
IRSA allows you to **assign IAM permissions to specific Kubernetes pods** using **OIDC identity provider integration**. This gives fine-grained access control without exposing credentials.

---

### 🔹 4. How do you scale workloads in EKS?

**Answer:**

* Use **HPA** to scale pods based on CPU/memory.
* Use **Cluster Autoscaler** or **Karpenter** to scale EC2 nodes.
* Use **Fargate** for serverless scaling of pods.

---

### 🔹 5. How do you expose services in EKS?

**Answer:**

* Use **LoadBalancer type service** to expose externally.
* Use **Ingress + ALB Ingress Controller** for routing traffic to multiple services.
* Use **NodePort** for basic external access (less common in production).

---

### 🔹 6. How is the EKS control plane secured?

**Answer:**

* IAM + Kubernetes RBAC
* API server endpoint can be private or public with authorized IPs
* Data in etcd is encrypted using AWS KMS

---

### 🔹 7. What is Karpenter?

**Answer:**
**Karpenter** is an open-source Kubernetes node autoscaler that **provisions and scales worker nodes** dynamically based on pod demand. It's faster and more flexible than the traditional Cluster Autoscaler.

---

### 🔹 8. How do you update an EKS cluster?

**Answer:**

* Use AWS Console, CLI, or eksctl to upgrade the control plane.
* Then upgrade node groups and Kubernetes components (CoreDNS, kube-proxy, etc.)

---

## 📚 **Official Docs and Resources**

* [EKS Home](https://aws.amazon.com/eks/)
* [EKS User Guide](https://docs.aws.amazon.com/eks/latest/userguide/)
* [EKS Best Practices](https://aws.github.io/aws-eks-best-practices/)
* [eksctl CLI Tool](https://eksctl.io/)

---

Let me know if you'd like:

✅ Hands-on labs
✅ Architecture diagrams
✅ Comparison with GKE/AKS
✅ CI/CD pipelines for EKS (with GitHub Actions or CodePipeline)
✅ EKS security best practices

I'm happy to help build your complete EKS learning path!
