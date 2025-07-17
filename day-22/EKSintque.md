Here are **detailed AWS EKS (Elastic Kubernetes Service) interview questions and answers**, ranging from beginner to advanced levels, covering concepts, configurations, and real-world scenarios.

---

### ✅ **Basic EKS Interview Questions**

---

**1. What is Amazon EKS?**
**Answer:**
Amazon EKS (Elastic Kubernetes Service) is a fully managed service that makes it easy to run Kubernetes on AWS without having to manage the Kubernetes control plane or etcd nodes. EKS automatically manages control plane availability and scalability.

---

**2. What are the components managed by AWS in EKS?**
**Answer:**

* Kubernetes control plane
* etcd (key-value store for cluster state)
* API server, scheduler, and controller manager

---

**3. What are the components you manage in EKS?**
**Answer:**

* Worker nodes (EC2 or Fargate)
* Node Groups (via managed/unmanaged)
* Kubernetes resources (Pods, Deployments, Services, etc.)

---

**4. What is a Node Group in EKS?**
**Answer:**
A node group is a set of EC2 instances that are part of your cluster and used to run Kubernetes workloads. It can be:

* **Managed Node Group** (AWS manages lifecycle)
* **Self-managed Node Group** (You manage manually)

---

**5. What is the difference between ECS and EKS?**

| Feature       | ECS                 | EKS                                 |
| ------------- | ------------------- | ----------------------------------- |
| Orchestration | AWS proprietary     | Kubernetes                          |
| Complexity    | Easier to set up    | More complex (K8s expertise needed) |
| Flexibility   | Less (AWS specific) | More (Kubernetes-native)            |

---

**6. How do you authenticate users in EKS?**
**Answer:**

* IAM authentication using `aws-auth` ConfigMap
* `kubectl` uses IAM roles for authentication
* `aws-iam-authenticator` is used under the hood

---

**7. How do you scale EKS nodes?**
**Answer:**

* Use **Cluster Autoscaler** (for EC2)
* Use **Karpenter** (newer, more efficient autoscaler)
* Configure Auto Scaling Groups for EC2 nodes

---

**8. What are Fargate Profiles in EKS?**
**Answer:**
Fargate profiles allow you to run Kubernetes pods without managing EC2 nodes. EKS automatically provisions compute for the pods based on namespace or labels.

---

### ✅ **Intermediate EKS Interview Questions**

---

**9. How is networking handled in EKS?**
**Answer:**

* Uses **Amazon VPC CNI plugin**
* Each pod gets an ENI and a private IP address
* Allows native VPC networking and security group support

---

**10. What are the different deployment strategies in EKS?**
**Answer:**

* Rolling Updates (default)
* Blue/Green deployments (with manual routing)
* Canary deployments (with metrics-based promotion)

---

**11. How do you monitor an EKS cluster?**
**Answer:**

* **CloudWatch Container Insights**
* **Prometheus and Grafana** (via Helm)
* **Kube-State-Metrics** for Kubernetes objects
* **FluentBit/FluentD** for logging

---

**12. What are Add-ons in EKS?**
**Answer:**
Add-ons are native Kubernetes components managed by EKS, such as:

* VPC CNI
* CoreDNS
* kube-proxy
  They can be updated and installed via the EKS console or CLI.

---

**13. How do you upgrade an EKS cluster?**
**Answer:**

1. Upgrade the **control plane** via AWS CLI or Console.
2. Upgrade **node groups** (managed/unmanaged).
3. Upgrade **Kubernetes resources** (e.g., Deployments).
4. Upgrade add-ons (CoreDNS, kube-proxy).

---

**14. What are the security best practices for EKS?**
**Answer:**

* Use IAM roles for service accounts (IRSA)
* Use Kubernetes RBAC for fine-grained access
* Restrict `kubectl` access via IAM
* Use private EKS endpoint if needed

---

**15. How do you provision an EKS cluster using infrastructure as code?**
**Answer:**

* **Terraform** (with EKS modules)
* **AWS CloudFormation**
* **eksctl** (CLI tool from Weaveworks)

---

### ✅ **Advanced EKS Interview Questions**

---

**16. How does IAM for Service Accounts (IRSA) work in EKS?**
**Answer:**

* IRSA allows Kubernetes service accounts to assume IAM roles.
* It uses OIDC tokens issued by EKS to authenticate to AWS.
* Safer than attaching IAM roles to EC2 nodes.

---

**17. How does EKS handle multi-tenancy?**
**Answer:**

* Namespace isolation
* Kubernetes RBAC
* Network policies (e.g., Calico)
* Pod security policies or OPA Gatekeeper

---

**18. What is Karpenter and how is it used in EKS?**
**Answer:**

* Karpenter is an open-source autoscaler that provisions nodes quickly based on pod resource requests.
* It dynamically chooses instance types and placement.
* More efficient than Cluster Autoscaler.

---

**19. How do you configure private access for EKS?**
**Answer:**

* Disable public endpoint
* Use private VPC endpoint
* Route traffic through bastion/jump host or VPN

---

**20. What tools are commonly used with EKS in production?**
**Answer:**

* **Helm** – for managing Kubernetes applications
* **ArgoCD** or **Flux** – for GitOps-based deployment
* **Prometheus + Grafana** – for monitoring
* **AWS Load Balancer Controller** – for ALB/NLB

---

### ✅ Behavioral & Scenario-Based Questions

---

**21. How do you troubleshoot a pod stuck in `Pending` in EKS?**
**Answer:**

* Check pod events: `kubectl describe pod <name>`
* Look for:

  * Insufficient resources
  * Taints/tolerations mismatch
  * NodeSelector or affinity issues

---

**22. How do you handle zero-downtime deployments in EKS?**
**Answer:**

* Use readiness and liveness probes
* Ensure proper rolling updates strategy
* Use horizontal pod autoscaler
* Use pod disruption budgets

---

**23. How do you ensure security of secrets in EKS?**
**Answer:**

* Use **Secrets Manager** or **Parameter Store** (via IRSA)
* Enable **encryption at rest** using KMS
* Limit access via RBAC

---

### ✅ Useful Commands

```bash
# Create cluster using eksctl
eksctl create cluster --name my-cluster --region us-west-2

# Get nodes
kubectl get nodes

# View cluster info
kubectl cluster-info

# View AWS-auth config
kubectl get configmap aws-auth -n kube-system
```

---

### ✅ Official Docs & Resources

* [EKS Overview – AWS Docs](https://docs.aws.amazon.com/eks/latest/userguide/what-is-eks.html)
* [EKS Best Practices Guide](https://aws.github.io/aws-eks-best-practices/)
* [EKS Troubleshooting Guide](https://docs.aws.amazon.com/eks/latest/userguide/troubleshooting.html)

---

Would you like a **PDF export** or also want the same for **`eksctl`, `Fargate`, or Karpenter\` in detail?**
