# ⚙️ AWS DevOps & CI/CD Services

AWS DevOps services help automate the software development lifecycle — from **source code and builds to testing, deployment, infrastructure provisioning, and operations**.

## 🗂️ Services Covered

| Service | Purpose |
|---|---|
| **AWS CodePipeline** | CI/CD workflow orchestration |
| **AWS CodeBuild** | Build and test applications |
| **AWS CodeDeploy** | Automated application deployments |
| **AWS CodeCommit** | Source control service |
| **AWS CloudFormation** | Infrastructure as Code |
| **AWS Systems Manager** | Infrastructure operations and management |
| **Amazon ECR** | Container image registry |

> **Note:** AWS CodeCommit availability and capabilities can change over time. GitHub and other source-control platforms can also be integrated into AWS CI/CD workflows.

---

# 🔄 CI/CD

### Continuous Integration
Developers frequently merge code into a shared repository, with automated builds and tests detecting issues early.

### Continuous Delivery
Validated changes are automatically prepared for release, with production deployment optionally requiring approval.

### Continuous Deployment
Validated changes are automatically deployed to production.

```text
Code → Build → Test → Package → Deploy → Monitor
```

---

# 🔧 AWS CodePipeline

CodePipeline orchestrates CI/CD stages.

```text
Source
  │
  ▼
Build
  │
  ▼
Test
  │
  ▼
Deploy
  │
  ▼
Production
```

**Think:** `CodePipeline → CI/CD Orchestration`

---

# 🏗️ AWS CodeBuild

CodeBuild is a managed build and test service.

### Common Tasks
- Install dependencies
- Compile code
- Run tests
- Build Docker images
- Create build artifacts
- Run quality/security checks

```text
Source Code
    │
    ▼
CodeBuild
    │
    ▼
Docker Build
    │
    ▼
Amazon ECR
```

**Think:** `CodeBuild → Build & Test`

---

# 🚀 AWS CodeDeploy

CodeDeploy automates application deployments to supported compute environments.

### Deployment Strategies
- In-place deployment
- Blue/green deployment

```text
Code → Build → CodeDeploy → Production
```

**Think:** `CodeDeploy → Automated Deployment`

---

# 📦 AWS CodeCommit

CodeCommit is a managed Git-based source control service for hosting private repositories.

```text
Developer
    │
    ▼
CodeCommit / GitHub
    │
    ▼
CI/CD Pipeline
```

**Think:** `CodeCommit → Source Control`

---

# 🏗️ AWS CloudFormation

CloudFormation is an **Infrastructure as Code (IaC)** service.

```text
CloudFormation Template
          │
          ▼
        Stack
          │
     ┌────┼────┐
     ▼    ▼    ▼
    VPC   EC2  S3
```

### Benefits
- Repeatable infrastructure
- Automation
- Version control
- Consistent environments
- Reduced manual configuration

**Think:** `CloudFormation → Infrastructure as Code`

---

# 🛠️ AWS Systems Manager

Systems Manager helps manage and operate AWS and hybrid infrastructure.

### Common Capabilities
- Session Manager
- Run Command
- Patch management
- Parameter Store
- Automation
- Inventory

```text
Administrator
      │
      ▼
Systems Manager
      │
 ┌────┼────┐
 ▼    ▼    ▼
EC2  EC2  EC2
```

**Think:** `Systems Manager → Operate & Manage`

---

# 🗄️ Amazon ECR

Amazon ECR is a managed container image registry.

```text
Developer
    │
    ▼
Docker Build
    │
    ▼
Amazon ECR
    │
 ┌──┴─────┐
 ▼        ▼
ECS      EKS
```

**Think:** `ECR → Store Container Images`

---

# 🧰 External DevOps Tools

### Source Control
- Git
- GitHub

### CI/CD
- GitHub Actions
- Jenkins

### Containers
- Docker
- Kubernetes

### Infrastructure as Code
- Terraform
- Ansible
- AWS CloudFormation

---

# 🚀 Complete CI/CD Workflow

```text
Developer
    │
    ▼
GitHub
    │
    ▼
CI/CD Pipeline
    │
    ▼
Build & Test
    │
    ▼
Docker Build
    │
    ▼
Amazon ECR
    │
    ▼
ECS / EKS
    │
    ▼
Production
    │
    ▼
CloudWatch
```

### AWS-Native Example

```text
GitHub / Source
       │
       ▼
CodePipeline
       │
       ▼
CodeBuild
       │
       ├──► Tests
       │
       └──► Docker Build
                 │
                 ▼
                ECR
                 │
                 ▼
              ECS / EKS
                 │
                 ▼
             Production
                 │
                 ▼
             Monitoring
```

---

# 🏗️ Infrastructure as Code Workflow

```text
Developer
    │
    ▼
Terraform / CloudFormation
    │
    ▼
Version Control
    │
    ▼
CI/CD Pipeline
    │
    ▼
Validate / Plan
    │
    ▼
Apply
    │
    ▼
AWS Infrastructure
```

---

# 🐳 Docker + Kubernetes Workflow

```text
Application Code
      │
      ▼
Dockerfile
      │
      ▼
Docker Image
      │
      ▼
Amazon ECR
      │
      ▼
ECS / EKS
      │
      ▼
Containers
```

---

# 🔐 DevSecOps

Security should be integrated throughout the development lifecycle.

```text
Code
 │
 ▼
Security Scan
 │
 ▼
Build
 │
 ▼
Test
 │
 ▼
Container Scan
 │
 ▼
Deploy
 │
 ▼
Monitor
```

### Practices
- Least-privilege IAM
- Secrets management
- Dependency scanning
- Container image scanning
- Infrastructure security checks
- Secure CI/CD credentials
- Audit logging

---

# 📊 Deployment Strategies

### Rolling Deployment

Gradually replace the old application version with the new version.

### Blue/Green Deployment

Run two environments and shift traffic from the old version to the new version.

```text
Users
  │
  ▼
Load Balancer
  │
  ├──► Blue  → Current
  │
  └──► Green → New Version
```

### Canary Deployment

Release the new version to a small percentage of traffic before expanding the rollout.

```text
Users
  │
  ▼
Load Balancer
  │
  ├──► 95% → Stable
  └──► 5%  → New Version
```

---

# 📈 Monitoring in DevOps

Deployment does not end when the application reaches production.

```text
Deploy
  │
  ▼
Production
  │
  ▼
CloudWatch
  │
 ┌┴─────────────┐
 ▼              ▼
Metrics        Logs
 │              │
 └──────┬───────┘
        ▼
      Alerts
```

---

# 🧠 Core DevOps Concepts

- Continuous Integration
- Continuous Delivery
- Continuous Deployment
- Git Workflows
- Build Automation
- Automated Testing
- Docker
- Kubernetes
- Infrastructure as Code
- Configuration Management
- Blue/Green Deployment
- Rolling Deployment
- Canary Deployment
- Secrets Management
- Container Registry
- Monitoring
- Observability
- Deployment Automation
- DevSecOps

---

# ⚖️ Quick Comparison

| Service | Main Purpose |
|---|---|
| **CodePipeline** | CI/CD orchestration |
| **CodeBuild** | Build and test |
| **CodeDeploy** | Application deployment |
| **CodeCommit** | Source control |
| **CloudFormation** | Infrastructure as Code |
| **Systems Manager** | Infrastructure operations |
| **ECR** | Container image registry |

---

# 🧠 Quick Decision Guide

Need CI/CD orchestration → **CodePipeline**

Need build and test → **CodeBuild**

Need automated application deployment → **CodeDeploy**

Need AWS-managed Git → **CodeCommit**

Need AWS Infrastructure as Code → **CloudFormation**

Need infrastructure operations → **Systems Manager**

Need container image storage → **ECR**

Need external CI/CD → **GitHub Actions / Jenkins**

Need containerization → **Docker**

Need container orchestration → **ECS / EKS**

Need Infrastructure as Code → **Terraform / CloudFormation**

---

# 🎯 Interview Questions

### CodePipeline vs CodeBuild
**CodePipeline** orchestrates the delivery workflow. **CodeBuild** performs build and test operations.

### CodeBuild vs CodeDeploy
**CodeBuild** builds and tests the application. **CodeDeploy** automates application deployment.

### What is Infrastructure as Code?
IaC defines infrastructure using machine-readable configuration instead of manually creating resources.

Examples: **Terraform, CloudFormation**

### What is Blue/Green Deployment?
Two environments are maintained and traffic is shifted from the old version to the new version.

### What is Canary Deployment?
A new version is initially released to a small percentage of users before expanding the rollout.

### Why use ECR?
ECR provides managed storage for container images used by platforms such as ECS and EKS.

---

# 📚 Learning Path

1. Linux fundamentals
2. Git and GitHub
3. Git workflows
4. CI/CD fundamentals
5. GitHub Actions
6. Jenkins
7. AWS CodePipeline
8. AWS CodeBuild
9. AWS CodeDeploy
10. Docker
11. Amazon ECR
12. ECS and EKS
13. Infrastructure as Code
14. CloudFormation
15. Terraform
16. Ansible
17. DevSecOps
18. Deployment strategies
19. Monitoring and observability
20. End-to-end CI/CD projects

---

# 🛠️ Skills Covered

`AWS` `DevOps` `CI/CD` `CodePipeline` `CodeBuild` `CodeDeploy` `CodeCommit` `CloudFormation` `Systems Manager` `ECR` `Git` `GitHub` `GitHub Actions` `Jenkins` `Docker` `Kubernetes` `ECS` `EKS` `Terraform` `Ansible` `DevSecOps` `Infrastructure as Code`

---

## ⭐ Key Takeaway

```text
GitHub
   │
   ▼
CI/CD
   │
   ▼
Build & Test
   │
   ▼
Docker
   │
   ▼
ECR
   │
   ▼
ECS / EKS
   │
   ▼
Production
   │
   ▼
Monitoring
```

DevOps is about creating a repeatable path from **code → build → test → package → deploy → monitor → improve**.

This section is part of my broader AWS learning repository:

**Compute → Storage → Networking → DevOps → AI/ML → Security → Monitoring**

**Learn → Implement → Automate → Document → Improve 🚀**
