# AWS-Cloud
# ☁️ AWS Cloud & DevOps Learning Repository

Welcome to my **AWS Cloud & DevOps learning repository**.

This repository is a structured collection of my learning notes, service
overviews, architectures, practical examples, diagrams, and hands-on
work across the major areas of AWS Cloud.

The goal is to build a strong understanding of **cloud infrastructure,
DevOps, security, monitoring, and AI/ML services** and to document the
journey in a way that is useful for both learning and revision.

------------------------------------------------------------------------

## 🎯 Repository Objective

This repository focuses on understanding AWS services from both a
**theoretical and practical perspective**.

For each major AWS domain, I aim to document:

-   What the service does
-   Why it is used
-   Key features
-   Architecture and workflow
-   Common use cases
-   Service comparisons
-   Important concepts
-   CLI examples where applicable
-   DevOps and real-world implementation scenarios
-   Interview preparation notes

------------------------------------------------------------------------

# 🗂️ AWS Learning Areas

``` text
                         AWS CLOUD
                            │
        ┌───────────────────┼───────────────────┐
        │                   │                   │
     COMPUTE             STORAGE            NETWORKING
        │                   │                   │
   EC2, Lambda          S3, EBS, EFS       VPC, Route 53
   ECS, EKS             Glacier            ELB, CloudFront
   Fargate              Storage Gateway    NAT, VPN
   Beanstalk                                Direct Connect
        │                   │                   │
        └───────────────────┼───────────────────┘
                            │
              ┌─────────────┼─────────────┐
              │             │             │
            DEVOPS       SECURITY      MONITORING
              │             │             │
          CodePipeline      IAM         CloudWatch
          CodeBuild         KMS         CloudTrail
          CodeDeploy        WAF         Config
          CodeCommit        Secrets     X-Ray
          CloudFormation    GuardDuty
          Systems Manager   Security Hub
              │             │             │
              └─────────────┼─────────────┘
                            │
                          AI / ML
                            │
                 ┌──────────┼──────────┐
                 │          │          │
               SageMaker  Bedrock   Rekognition
               Comprehend  Textract  Transcribe
```

------------------------------------------------------------------------

# 🚀 1. Compute Services

AWS compute services provide the infrastructure required to run
applications, workloads, containers, and serverless functions.

### Services Covered

  Service                     Purpose
  --------------------------- ------------------------------------
  **Amazon EC2**              Resizable virtual servers
  **AWS Lambda**              Serverless event-driven compute
  **AWS Fargate**             Serverless container compute
  **Amazon ECS**              AWS-native container orchestration
  **Amazon EKS**              Managed Kubernetes
  **AWS Elastic Beanstalk**   Simplified application deployment
  **Amazon ECR**              Container image registry

### Core Concepts

-   EC2 Instances
-   AMIs
-   Instance Types
-   EBS
-   Auto Scaling
-   Load Balancers
-   Serverless Computing
-   Docker Containers
-   ECS
-   EKS
-   Kubernetes
-   Fargate
-   Container Registries

### Typical Architecture

``` text
Developer
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
Fargate / EC2
    │
    ▼
Application Load Balancer
    │
    ▼
Users
```

------------------------------------------------------------------------

# 💾 2. Storage Services

AWS storage services provide scalable and durable solutions for
application data, files, databases, backups, and archives.

### Services Covered

  Service                   Purpose
  ------------------------- -----------------------------
  **Amazon S3**             Object storage
  **Amazon EBS**            Block storage for EC2
  **Amazon EFS**            Managed shared file storage
  **S3 Glacier**            Long-term archival storage
  **AWS Storage Gateway**   Hybrid cloud storage

### Core Concepts

-   S3 Buckets
-   Objects
-   Storage Classes
-   Versioning
-   Lifecycle Policies
-   Bucket Policies
-   Encryption
-   EBS Volumes
-   EBS Snapshots
-   EFS File Systems
-   Backup and Archiving

### Simple Comparison

``` text
S3       → Object Storage
EBS      → Block Storage
EFS      → Shared File Storage
Glacier  → Archive Storage
```

### Example Architecture

``` text
Application
    │
    ├──────────► EBS
    │             │
    │          EC2 Storage
    │
    ├──────────► EFS
    │             │
    │       Shared File Storage
    │
    └──────────► S3
                  │
              Object Storage
                  │
               Glacier
```

------------------------------------------------------------------------

# 🌐 3. Networking Services

AWS networking services provide secure communication between users,
applications, AWS services, and on-premises environments.

### Services Covered

  Service                      Purpose
  ---------------------------- -----------------------------------------
  **Amazon VPC**               Isolated virtual network
  **Amazon Route 53**          DNS and domain routing
  **Elastic Load Balancing**   Traffic distribution
  **CloudFront**               Content delivery network
  **NAT Gateway**              Private subnet outbound internet access
  **Internet Gateway**         Internet connectivity for VPC
  **AWS VPN**                  Secure network connectivity
  **AWS Direct Connect**       Dedicated private connectivity

### Core Concepts

-   VPC
-   CIDR
-   Subnets
-   Route Tables
-   Internet Gateway
-   NAT Gateway
-   Security Groups
-   Network ACLs
-   Public and Private Subnets
-   Load Balancers
-   DNS
-   CDN
-   VPN
-   Hybrid Networking

### Typical VPC Architecture

``` text
                         Internet
                            │
                            ▼
                    Internet Gateway
                            │
                 ┌──────────┴──────────┐
                 │         VPC         │
                 │                     │
          Public Subnet          Public Subnet
                 │                     │
              ALB / NAT              ALB
                 │
          ┌──────┴──────┐
          │             │
    Private Subnet  Private Subnet
          │             │
        EC2           Application
```

------------------------------------------------------------------------

# ⚙️ 4. DevOps & CI/CD Services

AWS DevOps services help automate software development, testing,
deployment, infrastructure provisioning, and operational workflows.

### Services Covered

  Service                   Purpose
  ------------------------- -----------------------------
  **AWS CodePipeline**      CI/CD orchestration
  **AWS CodeBuild**         Build and test applications
  **AWS CodeDeploy**        Automated deployments
  **AWS CodeCommit**        Source control
  **AWS CloudFormation**    Infrastructure as Code
  **AWS Systems Manager**   Infrastructure operations
  **Amazon ECR**            Container image management

### External Tools Also Covered

-   Git
-   GitHub
-   GitHub Actions
-   Jenkins
-   Docker
-   Kubernetes
-   Terraform
-   Ansible

### CI/CD Workflow

``` text
Developer
    │
    ▼
GitHub
    │
    ▼
CI Pipeline
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
Monitoring
```

### DevOps Concepts

-   Continuous Integration
-   Continuous Delivery
-   Continuous Deployment
-   Git Workflows
-   Build Automation
-   Testing
-   Docker
-   Kubernetes
-   Infrastructure as Code
-   Blue/Green Deployment
-   Rolling Deployment
-   Canary Deployment
-   Secrets Management
-   Deployment Automation

------------------------------------------------------------------------

# 🤖 5. AI & Machine Learning Services

AWS provides managed services for building, deploying, and consuming AI
and machine learning capabilities.

### Services Covered

  Service                  Purpose
  ------------------------ --------------------------------------
  **Amazon SageMaker**     Build, train, and deploy ML models
  **Amazon Bedrock**       Build generative AI applications
  **Amazon Rekognition**   Image and video analysis
  **Amazon Comprehend**    Natural language processing
  **Amazon Textract**      Extract text and data from documents
  **Amazon Transcribe**    Speech-to-text
  **Amazon Translate**     Machine translation
  **Amazon Polly**         Text-to-speech

### Core Concepts

-   Machine Learning
-   Generative AI
-   Foundation Models
-   LLM Applications
-   Model Training
-   Model Deployment
-   Inference
-   Prompt Engineering
-   Embeddings
-   Vector Search
-   RAG
-   Computer Vision
-   NLP
-   Speech Processing

### AI/ML Workflow

``` text
Data
 │
 ▼
Data Preparation
 │
 ▼
Model / Foundation Model
 │
 ├───────────────┐
 ▼               ▼
SageMaker       Bedrock
 │               │
 ▼               ▼
Training       GenAI App
 │               │
 └───────┬───────┘
         ▼
      Inference
         │
         ▼
    Application
```

------------------------------------------------------------------------

# 🔐 6. Security Services

AWS security services help protect identities, infrastructure,
applications, data, and workloads.

### Services Covered

  Service                   Purpose
  ------------------------- ---------------------------------
  **AWS IAM**               Identity and access management
  **AWS KMS**               Encryption key management
  **AWS Secrets Manager**   Secure secret storage
  **AWS WAF**               Web application firewall
  **AWS Shield**            DDoS protection
  **Amazon GuardDuty**      Threat detection
  **AWS Security Hub**      Security posture management
  **AWS Config**            Resource configuration tracking
  **Amazon Inspector**      Vulnerability management
  **AWS CloudTrail**        API activity auditing

### Core Concepts

-   IAM Users
-   IAM Groups
-   IAM Roles
-   IAM Policies
-   Least Privilege
-   MFA
-   Encryption at Rest
-   Encryption in Transit
-   KMS
-   Secrets
-   Network Security
-   WAF
-   DDoS Protection
-   Threat Detection
-   Compliance

### Security Model

``` text
                    AWS SECURITY
                         │
        ┌────────────────┼────────────────┐
        │                │                │
     Identity           Data          Network
        │                │                │
       IAM              KMS             WAF
       MFA           Encryption       Shield
       Roles          Secrets         Security Groups
        │                │                │
        └────────────────┼────────────────┘
                         │
                    Monitoring
                         │
              CloudTrail / GuardDuty
```

------------------------------------------------------------------------

# 📊 7. Monitoring & Observability

Monitoring services help understand the health, performance, security,
and behavior of AWS resources and applications.

### Services Covered

  Service                                     Purpose
  ------------------------------------------- -----------------------------------
  **Amazon CloudWatch**                       Metrics, logs, dashboards, alarms
  **AWS CloudTrail**                          API and account activity auditing
  **AWS Config**                              Resource configuration tracking
  **AWS X-Ray**                               Application tracing
  **Amazon Managed Service for Prometheus**   Metrics monitoring
  **Amazon Managed Grafana**                  Visualization and dashboards

### Core Concepts

-   Metrics
-   Logs
-   Alarms
-   Dashboards
-   Log Groups
-   Log Streams
-   Application Monitoring
-   Distributed Tracing
-   Auditing
-   Observability
-   Alerting

### Observability Flow

``` text
Application
    │
    ├──────────► Metrics ──────► CloudWatch
    │
    ├──────────► Logs ─────────► CloudWatch Logs
    │
    ├──────────► API Activity ─► CloudTrail
    │
    └──────────► Traces ───────► X-Ray
                                   │
                                   ▼
                              Dashboards
                                   │
                                   ▼
                                 Alerts
```

------------------------------------------------------------------------

# 🏛️ End-to-End AWS Architecture

The concepts in this repository can be combined into a complete cloud
architecture:

``` text
                             USERS
                               │
                               ▼
                         Route 53
                               │
                               ▼
                         CloudFront
                               │
                               ▼
                     Application Load Balancer
                               │
                         ┌─────┴─────┐
                         │           │
                      ECS/EKS      Lambda
                         │
                    Fargate / EC2
                         │
              ┌──────────┼──────────┐
              │          │          │
             S3        EFS         EBS
              │
           Database
              │
              ▼
          Application
              │
        ┌─────┴───────────────┐
        │                     │
   CloudWatch             CloudTrail
        │                     │
        └──────────┬──────────┘
                   │
                Security
                   │
       IAM / KMS / WAF / GuardDuty
                   │
                   ▼
             AWS Environment
```

------------------------------------------------------------------------

# 🔄 How the AWS Services Connect

A practical DevOps workflow may look like:

``` text
                 SOURCE CODE
                      │
                      ▼
                    GitHub
                      │
                      ▼
                 CI/CD Pipeline
                      │
              ┌───────┴───────┐
              ▼               ▼
          Build/Test       Security Scan
              │               │
              └───────┬───────┘
                      ▼
                 Docker Build
                      │
                      ▼
                    ECR
                      │
              ┌───────┴───────┐
              ▼               ▼
             ECS             EKS
              │               │
           Fargate          EC2/Fargate
              │               │
              └───────┬───────┘
                      ▼
                   VPC
                      │
                      ▼
              Load Balancer
                      │
                      ▼
                  Users
                      │
          ┌───────────┴───────────┐
          ▼                       ▼
     CloudWatch              CloudTrail
          │                       │
          └───────────┬───────────┘
                      ▼
                  Monitoring
                      │
                      ▼
                   Alerts
```

------------------------------------------------------------------------

# 📚 Learning Roadmap

My planned learning progression for this repository:

### Phase 1 --- Cloud Fundamentals

-   AWS Regions
-   Availability Zones
-   AWS Global Infrastructure
-   Shared Responsibility Model
-   IAM Fundamentals
-   AWS Pricing Basics

### Phase 2 --- Compute

-   EC2
-   AMI
-   EBS
-   Auto Scaling
-   Load Balancing
-   Lambda
-   ECS
-   EKS
-   Fargate
-   Elastic Beanstalk
-   ECR

### Phase 3 --- Storage

-   S3
-   EBS
-   EFS
-   Glacier
-   Storage Classes
-   Lifecycle Policies
-   Versioning
-   Backup

### Phase 4 --- Networking

-   VPC
-   CIDR
-   Subnets
-   Route Tables
-   Internet Gateway
-   NAT Gateway
-   Security Groups
-   NACLs
-   Route 53
-   Load Balancers
-   CloudFront
-   VPN

### Phase 5 --- DevOps

-   Git
-   GitHub
-   Linux
-   Docker
-   CI/CD
-   GitHub Actions
-   Jenkins
-   AWS CodePipeline
-   Terraform
-   CloudFormation
-   Kubernetes
-   Helm
-   Deployment Strategies

### Phase 6 --- Security

-   IAM
-   IAM Roles
-   IAM Policies
-   KMS
-   Secrets Manager
-   WAF
-   Shield
-   GuardDuty
-   Inspector
-   Security Hub
-   CloudTrail

### Phase 7 --- Monitoring

-   CloudWatch
-   Logs
-   Metrics
-   Alarms
-   Dashboards
-   CloudTrail
-   X-Ray
-   Prometheus
-   Grafana
-   Observability

### Phase 8 --- AI/ML

-   Machine Learning Fundamentals
-   SageMaker
-   Bedrock
-   Generative AI
-   Foundation Models
-   RAG
-   Prompt Engineering
-   NLP
-   Computer Vision
-   AI-powered applications

------------------------------------------------------------------------

# 🗃️ Suggested Repository Structure

``` text
AWS-Cloud/
│
├── README.md
│
├── Compute/
│   ├── EC2/
│   ├── Lambda/
│   ├── ECS/
│   ├── EKS/
│   ├── Fargate/
│   ├── Elastic-Beanstalk/
│   └── ECR/
│
├── Storage/
│   ├── S3/
│   ├── EBS/
│   ├── EFS/
│   └── Glacier/
│
├── Networking/
│   ├── VPC/
│   ├── Route53/
│   ├── Load-Balancer/
│   ├── CloudFront/
│   ├── NAT-Gateway/
│   └── VPN/
│
├── DevOps/
│   ├── Git/
│   ├── GitHub-Actions/
│   ├── Jenkins/
│   ├── Docker/
│   ├── Kubernetes/
│   ├── Terraform/
│   └── CI-CD/
│
├── AI-ML/
│   ├── SageMaker/
│   ├── Bedrock/
│   ├── Rekognition/
│   ├── Comprehend/
│   └── Textract/
│
├── Security/
│   ├── IAM/
│   ├── KMS/
│   ├── WAF/
│   ├── GuardDuty/
│   ├── Security-Hub/
│   └── Secrets-Manager/
│
└── Monitoring/
    ├── CloudWatch/
    ├── CloudTrail/
    ├── X-Ray/
    ├── Prometheus/
    └── Grafana/
```

------------------------------------------------------------------------

# 🧪 Hands-On Projects

As the repository grows, practical projects will connect multiple AWS
services together.

### Project 1 --- Highly Available Web Application

``` text
Route 53
   │
CloudFront
   │
ALB
   │
EC2 Auto Scaling
   │
Application
   │
RDS / S3
```

### Project 2 --- Containerized Application

``` text
GitHub
   │
GitHub Actions
   │
Docker
   │
ECR
   │
ECS
   │
Fargate
   │
ALB
```

### Project 3 --- Kubernetes Deployment

``` text
GitHub
   │
CI/CD
   │
Docker
   │
ECR
   │
EKS
   │
Pods
   │
ALB
```

### Project 4 --- Serverless Application

``` text
API Gateway
     │
   Lambda
     │
DynamoDB
     │
    S3
```

### Project 5 --- Secure AWS Architecture

``` text
IAM
 │
VPC
 │
Private Subnets
 │
Security Groups
 │
WAF
 │
KMS
 │
Secrets Manager
 │
GuardDuty
 │
Security Hub
```

------------------------------------------------------------------------

# 🎯 Interview Preparation

This repository will also be used for AWS Cloud and DevOps interview
preparation.

Important topics include:

### AWS

-   EC2
-   S3
-   VPC
-   IAM
-   Lambda
-   ECS
-   EKS
-   RDS
-   CloudWatch
-   CloudTrail

### DevOps

-   Git
-   Linux
-   Docker
-   Kubernetes
-   CI/CD
-   Jenkins
-   GitHub Actions
-   Terraform
-   Ansible

### Networking

-   TCP/IP
-   DNS
-   HTTP/HTTPS
-   CIDR
-   Subnets
-   Routing
-   NAT
-   Load Balancing
-   VPN

### Security

-   IAM
-   Least Privilege
-   Encryption
-   KMS
-   Secrets
-   WAF
-   Security Groups
-   Network ACLs

------------------------------------------------------------------------

# 🛠️ Tools & Technologies

### Cloud

`AWS`

### DevOps

`Git` `GitHub` `GitHub Actions` `Jenkins` `Docker` `Kubernetes`
`Terraform` `Ansible`

### AWS Services

`EC2` `S3` `VPC` `Lambda` `ECS` `EKS` `Fargate` `ECR` `Route 53`
`CloudFront` `CloudWatch` `CloudTrail` `IAM` `KMS` `WAF` `GuardDuty`
`SageMaker` `Bedrock`

### Operating Systems

`Linux` `Ubuntu`

### Programming / Scripting

`Python` `Bash` `YAML`

------------------------------------------------------------------------

# 📈 Learning Philosophy

I am using this repository to follow a **learn → implement → document →
revise** approach.

``` text
          LEARN
            │
            ▼
        UNDERSTAND
            │
            ▼
        IMPLEMENT
            │
            ▼
        DOCUMENT
            │
            ▼
          REVISE
            │
            ▼
         PROJECTS
            │
            ▼
        INTERVIEWS
```

The objective is not just to memorize AWS services, but to understand
**how and why they are used together to build secure, scalable, highly
available, and cost-effective cloud solutions.**

------------------------------------------------------------------------

# ⭐ Repository Highlights

This repository will continuously grow with:

-   📘 AWS service notes
-   🏗️ Architecture diagrams
-   💻 AWS CLI examples
-   🐳 Docker examples
-   ☸️ Kubernetes manifests
-   ⚙️ CI/CD pipelines
-   🏗️ Terraform configurations
-   🔐 Security best practices
-   📊 Monitoring examples
-   🤖 AI/ML experiments
-   🧪 Hands-on projects
-   🎯 Interview questions
-   📝 Learning summaries

------------------------------------------------------------------------

# 📌 Disclaimer

This is a personal learning and documentation repository created to
understand AWS Cloud, DevOps, Security, Monitoring, and AI/ML concepts
through practical exploration.

AWS service capabilities, pricing, limits, and best practices can change
over time. Always refer to the official AWS documentation when
implementing services in production.

------------------------------------------------------------------------

# 👨‍💻 About This Repository

This repository represents my ongoing journey toward becoming a **Cloud
/ DevOps Engineer**, with a focus on AWS, Linux, networking, containers,
Kubernetes, automation, Infrastructure as Code, security, monitoring,
and AI/ML.

**Learn. Build. Automate. Document. Improve. 🚀**

------------------------------------------------------------------------

## 🔖 Topics

`aws` `amazon-web-services` `cloud-computing` `devops`
`cloud-engineering` `aws-cloud` `docker` `kubernetes` `terraform`
`linux` `cicd` `security` `monitoring` `aiml` `machine-learning`
`generative-ai` `cloud-security` `infrastructure-as-code`
