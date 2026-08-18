# 🌐 AWS Networking Services

AWS networking services provide the connectivity, routing, traffic
distribution, DNS, content delivery, and secure communication required
to build reliable and scalable cloud architectures.

## 🗂️ Services Covered

  Service                      Purpose
  ---------------------------- ------------------------------------------
  **Amazon VPC**               Isolated virtual network
  **Amazon Route 53**          DNS and domain routing
  **Elastic Load Balancing**   Traffic distribution
  **Amazon CloudFront**        Global content delivery
  **NAT Gateway**              Private subnet outbound internet access
  **Internet Gateway**         VPC internet connectivity
  **AWS VPN**                  Encrypted network connectivity
  **AWS Direct Connect**       Dedicated connectivity to AWS
  **VPC Endpoints**            Private access to supported AWS services

------------------------------------------------------------------------

# 🏗️ Amazon VPC

Amazon Virtual Private Cloud (VPC) is a logically isolated virtual
network in AWS.

### Core Concepts

-   VPC
-   CIDR blocks
-   Public and private subnets
-   Route tables
-   Internet Gateway
-   NAT Gateway
-   Security Groups
-   Network ACLs
-   VPC Endpoints

### Typical Architecture

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
                ALB                   NAT
                 │                     │
          ┌──────┴──────┐              │
          │             │              │
    Private Subnet  Private Subnet     │
          │             │              │
         EC2          Application ◄────┘
```

A public subnet generally has a route to an Internet Gateway. A private
subnet does not have a direct route to the Internet Gateway.

------------------------------------------------------------------------

# 🌐 Amazon Route 53

Route 53 is AWS's DNS and domain management service.

### Common Uses

-   Domain name resolution
-   DNS records
-   Health checks
-   Routing traffic to applications
-   Failover and latency-based routing

``` text
User
 │
 ▼
example.com
 │
 ▼
Route 53
 │
 ▼
Application Load Balancer
 │
 ▼
Application
```

**Think:** `Route 53 → DNS`

------------------------------------------------------------------------

# ⚖️ Elastic Load Balancing

Elastic Load Balancing distributes incoming traffic across healthy
targets.

### Main Types

  Type       Best For
  ---------- ----------------------------------------
  **ALB**    HTTP/HTTPS applications
  **NLB**    High-performance TCP/UDP/TLS workloads
  **GWLB**   Network and security appliances

``` text
                 Users
                   │
                   ▼
                  ALB
              ┌────┼────┐
              ▼    ▼    ▼
             EC2  EC2  EC2
              │    │    │
              └────┴────┘
                Application
```

**Think:** `ELB → Distribute Traffic`

------------------------------------------------------------------------

# 🌍 Amazon CloudFront

CloudFront is AWS's global Content Delivery Network (CDN).

It delivers content from locations closer to users to reduce latency.

### Common Uses

-   Static websites
-   Images
-   Videos
-   APIs
-   Web applications
-   Software downloads

``` text
User
 │
 ▼
CloudFront
 │
 ├────► S3
 │
 └────► ALB
```

**Think:** `CloudFront → Deliver Content Globally`

------------------------------------------------------------------------

# 🚪 NAT Gateway

A NAT Gateway allows resources in a private subnet to initiate outbound
connections to the internet.

``` text
Private EC2
    │
    ▼
Route Table
    │
    ▼
NAT Gateway
    │
    ▼
Internet Gateway
    │
    ▼
Internet
```

### Example Uses

-   Download software updates
-   Access external APIs
-   Pull packages
-   Reach public services from private workloads

**Important:** NAT Gateway does not make a private instance directly
reachable from the internet.

**Think:** `NAT Gateway → Private Subnet → Internet`

------------------------------------------------------------------------

# 🌐 Internet Gateway

An Internet Gateway provides a path between a VPC and the internet.

``` text
Internet
   │
   ▼
Internet Gateway
   │
   ▼
VPC
   │
   ▼
Public Subnet
   │
   ▼
EC2 / ALB
```

**Think:** `Internet Gateway → VPC ↔ Internet`

------------------------------------------------------------------------

# 🔐 AWS VPN

AWS VPN provides encrypted connectivity between networks.

### Site-to-Site Example

``` text
On-Premises Network
        │
        │ Encrypted VPN
        ▼
    AWS VPN
        │
        ▼
       VPC
        │
        ▼
 AWS Resources
```

### Common Uses

-   Hybrid cloud
-   Connecting corporate networks to AWS
-   Secure remote connectivity
-   Private resource access

**Think:** `VPN → Encrypted Network Connection`

------------------------------------------------------------------------

# 🔌 AWS Direct Connect

AWS Direct Connect provides a dedicated network connection between an
organization's network and AWS.

``` text
Corporate Network
       │
       │ Dedicated Connection
       ▼
AWS Direct Connect
       │
       ▼
AWS Network
       │
       ▼
VPC
```

### VPN vs Direct Connect

  Feature      VPN                   Direct Connect
  ------------ --------------------- ------------------------------------
  Connection   Internet-based        Dedicated connection
  Encryption   Encrypted tunnel      Additional encryption can be used
  Setup        Generally quicker     Requires connectivity provisioning
  Common Use   Hybrid connectivity   Enterprise connectivity

------------------------------------------------------------------------

# 🛡️ Network Security

## Security Groups

Security Groups are stateful virtual firewalls associated with supported
AWS resources.

``` text
Internet
   │
   ▼
ALB Security Group
   │
   ▼
EC2 Security Group
   │
   ▼
Database Security Group
```

A common design is:

``` text
Internet → ALB : 443
ALB → Application : App Port
Application → Database : DB Port
```

The database should generally remain in private subnets and should not
be directly exposed to the public internet.

## Network ACLs

Network ACLs provide stateless traffic filtering at the subnet level.

### Security Group vs NACL

  Feature       Security Group            Network ACL
  ------------- ------------------------- ------------------------
  Level         Resource                  Subnet
  Stateful      Yes                       No
  Rules         Allow rules               Allow and deny rules
  Typical Use   Resource-level security   Subnet-level filtering

------------------------------------------------------------------------

# 🛣️ Route Tables

Route tables determine where network traffic is sent.

### Public Route

``` text
Destination       Target
0.0.0.0/0    →    Internet Gateway
```

### Private Outbound Route

``` text
Destination       Target
0.0.0.0/0    →    NAT Gateway
```

A subnet's routing configuration determines whether it has direct
internet connectivity.

------------------------------------------------------------------------

# 🔗 VPC Endpoints

VPC Endpoints allow private connectivity from a VPC to supported AWS
services.

``` text
Private EC2
    │
    ▼
VPC Endpoint
    │
    ▼
AWS Service
```

This can reduce internet exposure when accessing supported AWS services
privately.

------------------------------------------------------------------------

# 🏛️ Typical 3-Tier Architecture

``` text
                         INTERNET
                            │
                            ▼
                         Route 53
                            │
                            ▼
                       CloudFront
                            │
                            ▼
                  Application Load Balancer
                     ┌──────┴──────┐
                     │             │
               Public Subnet   Public Subnet
                     │             │
                     └──────┬──────┘
                            │
                  ┌─────────┴─────────┐
                  │                   │
            Private Subnet       Private Subnet
                  │                   │
              EC2 / ECS            EC2 / ECS
                  │                   │
                  └─────────┬─────────┘
                            │
                       RDS / Aurora
```

### Private Subnet Outbound Access

``` text
Private Application
       │
       ▼
  Route Table
       │
       ▼
  NAT Gateway
       │
       ▼
Internet Gateway
       │
       ▼
Internet
```

------------------------------------------------------------------------

# 🔄 How Networking Services Work Together

A typical web application request can flow like this:

``` text
User
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
 ▼
EC2 / ECS / EKS
 │
 ├────► S3
 │
 └────► RDS / DynamoDB
```

### Hybrid Connectivity

``` text
On-Premises
    │
 ┌──┴──────────────┐
 ▼                 ▼
VPN          Direct Connect
 │                 │
 └───────┬─────────┘
         ▼
        VPC
```

------------------------------------------------------------------------

# ⚖️ Quick Comparison

  Service                Main Purpose
  ---------------------- ----------------------------------
  **VPC**                Build an isolated AWS network
  **Route 53**           DNS
  **ALB**                HTTP/HTTPS traffic distribution
  **NLB**                High-performance network traffic
  **GWLB**               Network/security appliances
  **CloudFront**         Global content delivery
  **NAT Gateway**        Private subnet outbound internet
  **Internet Gateway**   VPC internet connectivity
  **VPN**                Encrypted network connectivity
  **Direct Connect**     Dedicated AWS connectivity
  **VPC Endpoint**       Private AWS service access

------------------------------------------------------------------------

# 🧠 Quick Decision Guide

Need an isolated AWS network → **VPC**

Need DNS → **Route 53**

Need web traffic distribution → **ALB**

Need high-performance TCP/UDP traffic → **NLB**

Need global content delivery → **CloudFront**

Need private subnet outbound internet → **NAT Gateway**

Need VPC internet connectivity → **Internet Gateway**

Need encrypted hybrid connectivity → **VPN**

Need dedicated connectivity → **Direct Connect**

Need private AWS service access → **VPC Endpoint**

------------------------------------------------------------------------

# 🎯 Interview Questions

### What is a VPC?

A VPC is a logically isolated virtual network where you control IP
addressing, routing, and network security.

### Public vs Private Subnet?

A public subnet generally has a route to an Internet Gateway. A private
subnet does not have a direct route to the Internet Gateway.

### NAT Gateway vs Internet Gateway?

An Internet Gateway provides a VPC path to the internet. A NAT Gateway
enables private resources to initiate outbound internet connections.

### Security Group vs NACL?

Security Groups are stateful and operate at the resource level. NACLs
are stateless and operate at the subnet level.

### ALB vs NLB?

ALB is designed for HTTP/HTTPS application traffic. NLB is designed for
high-performance TCP/UDP/TLS workloads.

### VPN vs Direct Connect?

VPN uses an encrypted connection over the internet. Direct Connect
provides dedicated network connectivity to AWS.

### Route 53 vs CloudFront?

Route 53 provides DNS and domain routing. CloudFront is a CDN for
delivering content closer to users.

------------------------------------------------------------------------

# 📚 Learning Path

1.  Networking fundamentals
2.  IP addressing and CIDR
3.  VPC
4.  Public and private subnets
5.  Route tables
6.  Internet Gateway
7.  NAT Gateway
8.  Security Groups
9.  Network ACLs
10. Route 53
11. Elastic Load Balancing
12. CloudFront
13. VPN
14. Direct Connect
15. VPC Endpoints
16. Build a highly available VPC
17. Secure application and database tiers

------------------------------------------------------------------------

# 🛠️ Skills Covered

`AWS` `VPC` `Networking` `Route53` `ALB` `NLB` `CloudFront`
`NAT Gateway` `Internet Gateway` `VPN` `Direct Connect` `VPC Endpoints`
`CIDR` `Subnets` `Route Tables` `Security Groups` `NACL`
`Cloud Architecture` `DevOps`

------------------------------------------------------------------------

## ⭐ Key Takeaway

``` text
VPC            → Your AWS Network
Route 53       → DNS
ALB/NLB        → Traffic Distribution
CloudFront     → Global Content Delivery
NAT Gateway    → Private → Internet
Internet GW    → VPC ↔ Internet
VPN            → Encrypted Connectivity
Direct Connect → Dedicated Connectivity
VPC Endpoint   → Private AWS Service Access
```

Strong AWS architectures combine **networking, security, compute,
storage, databases, and monitoring** rather than treating each service
independently.

This section is part of my broader AWS learning repository:

**Compute → Storage → Networking → DevOps → AI/ML → Security →
Monitoring**

**Learn → Implement → Document → Revise → Build Projects 🚀**
