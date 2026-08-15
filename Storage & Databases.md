# 💾 AWS Storage & Database Services

AWS provides scalable services for storing objects, files, block data,
backups, archives, transactional data, NoSQL workloads, caching, and
analytics.

## 🗂️ Services Covered

### Storage

  Service                   Purpose
  ------------------------- -----------------------------
  **Amazon S3**             Object storage
  **Amazon EBS**            Block storage for EC2
  **Amazon EFS**            Shared managed file storage
  **Amazon S3 Glacier**     Long-term archival
  **AWS Storage Gateway**   Hybrid cloud storage

### Databases

  Service                  Type             Purpose
  ------------------------ ---------------- ------------------------------
  **Amazon RDS**           Relational       Managed SQL databases
  **Amazon Aurora**        Relational       AWS cloud-optimized SQL
  **Amazon DynamoDB**      NoSQL            Key-value/document workloads
  **Amazon ElastiCache**   In-memory        Caching
  **Amazon Redshift**      Data Warehouse   Analytics
  **Amazon DocumentDB**    Document         Document workloads
  **Amazon Neptune**       Graph            Relationship-based workloads

------------------------------------------------------------------------

# 🪣 Amazon S3

Amazon S3 is scalable **object storage**.

### Core Concepts

-   Buckets
-   Objects
-   Storage Classes
-   Versioning
-   Lifecycle Policies
-   Bucket Policies
-   Encryption
-   Replication
-   Access Control

### Best For

Backups, images, videos, application assets, logs, data lakes, static
websites, and archives.

**Think:** `S3 → Object Storage`

------------------------------------------------------------------------

# 💽 Amazon EBS

Amazon EBS provides persistent **block storage** for EC2 instances.

### Core Concepts

-   EBS Volumes
-   Volume Types
-   IOPS
-   Throughput
-   Snapshots
-   Encryption

``` text
EC2 Instance
     │
     ▼
 EBS Volume
     │
  OS / Data
```

**Think:** `EBS → Virtual Disk for EC2`

------------------------------------------------------------------------

# 📁 Amazon EFS

Amazon EFS provides a managed, elastic **shared file system**.

``` text
          EFS
       ┌───┼───┐
       ▼   ▼   ▼
      EC2 EC2 EC2
       └───┴───┘
       Shared Files
```

**Think:** `EFS → Shared File Storage`

------------------------------------------------------------------------

# ❄️ Amazon S3 Glacier

S3 Glacier storage classes are designed for low-cost, long-term
archival.

### Best For

-   Compliance records
-   Historical data
-   Backups
-   Disaster recovery archives

**Think:** `Glacier → Long-Term Archive`

------------------------------------------------------------------------

# 🔌 AWS Storage Gateway

Storage Gateway connects on-premises environments with AWS storage.

### Use Cases

-   Hybrid cloud
-   Backup
-   Disaster recovery
-   Cloud migration

------------------------------------------------------------------------

# 🗄️ Database Services

Storage services and database services solve different problems.

``` text
STORAGE
 ├── S3       → Objects
 ├── EBS      → Blocks
 └── EFS      → Files

DATABASES
 ├── RDS      → Relational SQL
 ├── Aurora   → Cloud-optimized SQL
 ├── DynamoDB → NoSQL
 ├── ElastiCache → In-memory
 ├── Redshift → Data Warehouse
 ├── DocumentDB → Documents
 └── Neptune  → Graph
```

------------------------------------------------------------------------

# 🐘 Amazon RDS

Amazon RDS is a managed **relational database service**.

Supported engines include PostgreSQL, MySQL, MariaDB, Oracle, and SQL
Server.

### Best For

-   Web applications
-   Transactional workloads
-   Business applications
-   Traditional SQL databases

**Think:** `RDS → Managed Relational Database`

------------------------------------------------------------------------

# ⚡ Amazon Aurora

Amazon Aurora is a cloud-optimized relational database compatible with
MySQL and PostgreSQL.

### Best For

-   Production SQL workloads
-   High availability
-   Applications requiring scalable relational databases

**Think:** `Aurora → AWS-optimized Relational Database`

------------------------------------------------------------------------

# 🟦 Amazon DynamoDB

DynamoDB is a fully managed **NoSQL key-value and document database**.

### Core Concepts

-   Tables
-   Items
-   Attributes
-   Partition Keys
-   Sort Keys
-   Secondary Indexes
-   On-demand / Provisioned capacity

### Best For

-   Serverless applications
-   APIs
-   Gaming
-   IoT
-   High-scale applications
-   Low-latency workloads

**Think:** `DynamoDB → Scalable NoSQL`

------------------------------------------------------------------------

# 🚀 Amazon ElastiCache

ElastiCache provides managed **in-memory caching**.

``` text
Application
    │
    ▼
ElastiCache
    │
 ┌──┴──────────┐
 │             │
Hit           Miss
 │             │
 ▼             ▼
Return       Database
```

### Benefits

-   Lower latency
-   Reduced database load
-   Faster access to frequently used data
-   Session storage

**Think:** `ElastiCache → Fast Cached Data`

------------------------------------------------------------------------

# 🚀 Amazon ElastiCache — Redis / Valkey

Amazon ElastiCache is AWS's managed **in-memory caching service**. It supports **Valkey, Redis OSS, and Memcached** engines. citeturn0search0turn0search11

For Redis-based workloads, ElastiCache can provide managed Redis OSS caches, while Valkey is also available as an engine.

### What is Redis?

**Redis** is an in-memory data store commonly used for:

- Caching
- Session management
- Real-time applications
- Counters and rate limiting
- Pub/Sub
- Frequently accessed application data

Redis keeps data primarily in memory, which makes it useful when applications need very fast reads and writes.

### Redis / ElastiCache Architecture

```text
Application
     │
     ▼
ElastiCache
(Redis OSS / Valkey)
     │
 ┌───┴───────────┐
 │               │
Cache Hit      Cache Miss
 │               │
 ▼               ▼
Return Data    Database
                  │
                  ▼
             Store Result
                  │
                  ▼
             Update Cache
```

### Common Redis Use Cases

**1. Application Caching**

Frequently requested data can be stored in Redis so the application does not query the primary database every time.

**2. Session Management**

User sessions can be stored centrally so multiple application servers can access the same session data.

**3. Rate Limiting**

Redis counters can help control how many requests a user or API client can make within a time window.

**4. Real-Time Applications**

Redis can support low-latency workloads such as leaderboards, counters, and real-time state.

**5. Pub/Sub**

Redis-compatible publish/subscribe functionality can be used for messaging between application components.

### Redis vs Database

```text
                    Application
                         │
                         ▼
                      Redis
                  ┌──────┴──────┐
                  │             │
             Cache Hit      Cache Miss
                  │             │
                  ▼             ▼
             Fast Response   RDS / Aurora
                                │
                                ▼
                             Database
```

Redis should generally be treated as a **cache or fast data layer**, while RDS/Aurora or another primary database remains the source of durable application data unless a specific architecture requires otherwise.

### Redis vs ElastiCache

| Technology | Meaning |
|---|---|
| **Redis** | In-memory data store / caching technology |
| **Redis OSS** | Open-source Redis engine supported by ElastiCache |
| **Amazon ElastiCache** | AWS managed service for Valkey, Redis OSS, and Memcached |
| **ElastiCache Serverless** | Managed serverless cache deployment option |

AWS documentation currently lists **Valkey, Redis OSS, and Memcached** as supported ElastiCache engines. citeturn0search0turn0search11

### Key Benefits

- Very low-latency data access
- Reduces load on primary databases
- Supports session storage
- Useful for real-time workloads
- Managed scaling and infrastructure through ElastiCache
- Serverless and node-based deployment options are available citeturn0search11

### Security

ElastiCache for Valkey and Redis OSS supports encryption in transit and authentication options. IAM authentication can also be used with supported Valkey/Redis OSS versions, providing short-lived authentication tokens. citeturn0search7turn0search8

**Think:** `ElastiCache + Redis/Valkey → Fast In-Memory Data Layer`

# 📊 Amazon Redshift

Amazon Redshift is a cloud data warehouse for large-scale analytics.

### Best For

-   Business intelligence
-   Reporting
-   Data analytics
-   Data warehouse workloads

``` text
Transactional DB
      │
      ▼
 Data Pipeline
      │
      ▼
   Redshift
      │
      ▼
 Analytics / BI
```

**Think:** `Redshift → Analytics & Data Warehouse`

------------------------------------------------------------------------

# 📄 Amazon DocumentDB

Amazon DocumentDB is a managed document database designed for
MongoDB-compatible workloads.

**Think:** `DocumentDB → Document Data`

------------------------------------------------------------------------

# 🕸️ Amazon Neptune

Amazon Neptune is a managed graph database.

### Best For

-   Social networks
-   Recommendation systems
-   Knowledge graphs
-   Fraud detection
-   Relationship analysis

**Think:** `Neptune → Graph Relationships`

------------------------------------------------------------------------

# ⚖️ Storage Comparison

  Service           Type      Best For
  ----------------- --------- ----------------------------
  S3                Object    Files, backups, data lakes
  EBS               Block     EC2 disks
  EFS               File      Shared files
  Glacier           Archive   Long-term storage
  Storage Gateway   Hybrid    On-prem + AWS

# ⚖️ Database Comparison

  Service       Type             Best For
  ------------- ---------------- -----------------------------
  RDS           Relational       SQL applications
  Aurora        Relational       Scalable production SQL
  DynamoDB      NoSQL            High-scale low-latency apps
  ElastiCache   In-memory        Caching
  Redshift      Data Warehouse   Analytics
  DocumentDB    Document         Document workloads
  Neptune       Graph            Relationship data

------------------------------------------------------------------------

# 🧠 Quick Decision Guide

**Need to store files?** → S3

**Need a disk for EC2?** → EBS

**Need shared files?** → EFS

**Need long-term archival?** → Glacier

**Need managed SQL?** → RDS / Aurora

**Need highly scalable NoSQL?** → DynamoDB

**Need caching / fast in-memory data?** → ElastiCache (Redis/Valkey)

**Need analytics/data warehouse?** → Redshift

**Need document data?** → DocumentDB

**Need graph relationships?** → Neptune

------------------------------------------------------------------------

# 🏗️ Example Architecture

``` text
                         Users
                           │
                           ▼
                    Load Balancer
                           │
                           ▼
                     Application
                  ┌────────┼────────┐
                  │        │        │
                  ▼        ▼        ▼
                 S3       EFS   ElastiCache
                  │                 │
                  │                 │
                  ▼                 ▼
              Glacier            RDS/Aurora
                                    │
                                    ▼
                               Application DB
                                    │
                                    ▼
                               Backups → S3
                                         │
                                         ▼
                                      Glacier
```

------------------------------------------------------------------------

# 🔐 Storage & Database Security

Important practices:

-   IAM least privilege
-   S3 Block Public Access
-   Encryption at rest
-   Encryption in transit
-   KMS
-   EBS encryption
-   RDS encryption
-   Private subnets for databases
-   Security Groups
-   Secrets Manager
-   Automated backups
-   Versioning
-   Disaster recovery

A common secure design is:

``` text
Internet
   │
   ▼
   ALB
   │
   ▼
Application Subnet
   │
   ▼
Private Database Subnet
   │
   ▼
RDS / Aurora
```

------------------------------------------------------------------------

# 🎯 Redis / ElastiCache Interview Questions

### What is Redis?

Redis is an in-memory data store commonly used for caching, sessions, counters, rate limiting, and real-time workloads.

### Redis vs RDS

**Redis** is primarily used as a fast in-memory data layer, while **RDS** provides managed relational databases for durable SQL workloads.

### Why use Redis in front of a database?

Redis can serve frequently requested data from memory, reducing database queries and improving application latency.

### What is Amazon ElastiCache?

ElastiCache is AWS's managed caching service supporting Valkey, Redis OSS, and Memcached. citeturn0search0

### Redis Cache Flow

```text
Request
   │
   ▼
Redis / ElastiCache
   │
   ├── Hit  → Return immediately
   │
   └── Miss → Query Database
                 │
                 ▼
             Save in Redis
```

# 🎯 Interview Questions

### S3 vs EBS

**S3** is object storage accessed through APIs. **EBS** provides block
storage attached to EC2.

### EBS vs EFS

**EBS** is generally attached as block storage to an instance, while
**EFS** provides shared file storage that multiple resources can access.

### RDS vs DynamoDB

**RDS** uses relational SQL models and structured schemas. **DynamoDB**
is a NoSQL key-value/document database designed for scalable,
low-latency workloads.

### S3 vs Database

S3 stores objects/files, while databases provide structured data
storage, queries, indexes, and application transactions.

### Why use ElastiCache?

To reduce database load and improve response times by keeping frequently
accessed data in memory.

------------------------------------------------------------------------

# 📚 Learning Path

1.  S3 fundamentals
2.  S3 storage classes
3.  Versioning and lifecycle policies
4.  EBS and snapshots
5.  EFS
6.  Backup and archival
7.  RDS
8.  Aurora
9.  DynamoDB
10. ElastiCache
11. Redshift
12. DocumentDB and Neptune
13. Storage/database security
14. Backup and disaster recovery
15. Build integrated AWS architectures

------------------------------------------------------------------------

# 🛠️ Skills Covered

`AWS` `S3` `EBS` `EFS` `Glacier` `Storage Gateway` `RDS` `Aurora`
`DynamoDB` `ElastiCache` `Redis` `Valkey` `Redshift` `DocumentDB` `Neptune` `Databases`
`Cloud Storage` `Cloud Architecture` `DevOps`

------------------------------------------------------------------------

## ⭐ Key Takeaway

``` text
S3          → Object Storage
EBS         → Block Storage
EFS         → Shared File Storage
Glacier     → Archive Storage

RDS         → Relational Database
Aurora      → Cloud-Optimized SQL
DynamoDB    → NoSQL Database
ElastiCache → In-Memory Cache (Redis/Valkey)
Redshift    → Data Warehouse
DocumentDB  → Document Database
Neptune     → Graph Database
```

This section is part of my broader AWS learning repository:

**Compute → Storage → Networking → DevOps → AI/ML → Security →
Monitoring**

**Learn → Implement → Document → Revise → Build Projects 🚀**
