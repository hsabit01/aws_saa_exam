# RDS, Aurora, and ElastiCache

# RDS Overview

**Amazon RDS** is like renting a **fully managed apartment** for your database instead of building and maintaining the whole house yourself. AWS handles routine work like **backups, patching, and scaling**, so you can focus more on the application than database operations.

**Key Use Case:**

- Choose **RDS** when you need a **managed relational database** and want AWS to reduce admin overhead like setup, operations, backups, and scaling.

**Exam Tip:**

If you see **"managed relational database," "automated backups," "patching,"** or **"reduce operational overhead,"** think **RDS**.

**Why AWS-managed over self-managed?**

- **RDS** = less admin work, faster setup, easier operations.
- **Self-managed on EC2** = more control, but you handle the heavy lifting yourself.

**Storage Auto Scaling:**

RDS **storage autoscaling** automatically increases storage when free space runs low. A common trigger is when free storage falls to **10% or less** for at least **5 minutes**, and you set a **maximum storage limit** so it does not grow forever.

![rds.png](RDS,%20Aurora,%20and%20ElastiCache/rds.png)

# RDS Multi Replica vs Multi AZ

Think of **RDS Multi-AZ** as a **backup driver** in another Availability Zone, ready to take over if the main one fails. Think of **RDS Read Replica** as making **extra read-only copies** so more people can read without slowing down the main database. **RDS Custom** is the middle ground when you want AWS to manage much of the database service but still need deeper **OS/database-level access** than standard RDS gives you.

**Key Use Cases:**

- **Multi-AZ:** choose for **high availability** and **automatic failover**.
- **Read Replica:** choose for **read scaling**, **reporting**, and **offloading read traffic**.
- **RDS Custom:** choose when you need **more control over the host and database environment** for legacy, packaged, or specialized workloads.

**Exam Tip:**

If you see **“automatic failover”**, think **Multi-AZ**. If you see **“read-heavy workload”**, think **Read Replica**. If you see **“need OS access / custom agent / legacy DB requirement”**, think **RDS Custom**.

**RDS Read Replica vs Multi-AZ — main difference:**

**Multi-AZ** is for **resilience** and uses a standby in another AZ; the standby for a Multi-AZ DB instance **does not serve read traffic**. **Read Replicas** are for **performance/read scaling** and are typically **asynchronous** copies that can serve read traffic.

**RDS Read Replica Network Cost:**

For the exam, remember the cost trigger is mainly **cross-Region replication**: AWS states that **cross-Region read replica replication incurs data transfer charges**. Same-Region questions are usually testing the **read-scaling pattern**, not cross-Region transfer pricing.

**RDS Disaster Recovery:**

Use **Multi-AZ** for **AZ failure within one Region**. For **regional disaster recovery**, use a **cross-Region read replica** and promote it if the primary Region fails; AWS notes promotion is part of the failover process for non-Aurora RDS.

**RDS Transition from Single-AZ to Multi-AZ:**

You can **modify an existing RDS DB instance** to enable **Multi-AZ**, and RDS creates the standby in another AZ for you.

**RDS Custom:**

Use **RDS Custom** when standard RDS is too restrictive but full self-managed EC2 is too much work. It is designed for cases where you need **privileged access**, custom software, or legacy/vendor requirements that need control of the **underlying OS and DB environment**.

![rds-read-replica-multi-az.png](RDS,%20Aurora,%20and%20ElastiCache/rds-read-replica-multi-az.png)

**Fast memory hook:**

**Multi-AZ = availability.**

**Read Replica = read scaling.**

**RDS Custom = more control.**

# Aurora

**Amazon Aurora** is a cloud-native relational database built for **MySQL** and **PostgreSQL** compatibility, but optimized by AWS for better availability and performance. Think of it like a **smarter RDS engine** where storage is shared across the cluster and compute nodes can be added for **writes and reads** separately.

**Key Use Case:**

- Choose **Aurora** when you need a **managed relational database** with **high availability**, **fast failover**, and **read scaling**.

**Exam Tip:**

If you see **“relational + high availability + read scaling + MySQL/PostgreSQL compatible,”** think **Aurora**.

**Aurora High Availability and Read Scaling:**

Aurora stores data **across multiple AZs** and can automatically fail over to a new primary if the writer fails. For read scaling, it uses **Aurora Replicas** plus a **reader endpoint** that load-balances read connections across replicas.

**Aurora DB Cluster:**

An **Aurora DB cluster** usually has **one writer** and **zero or more reader instances** sharing the same cluster storage. It comes with a **cluster (writer) endpoint** for writes and a **reader endpoint** for read-only traffic.

**Features of Aurora:**

- **MySQL/PostgreSQL compatibility**
- **Built-in high availability** across AZs
- **Reader endpoint** for read scaling
- **Automatic failover**
- **Aurora Auto Scaling** can add/remove **Aurora Replicas** based on demand

**Main difference vs standard RDS:**

**Aurora** is designed around a **cluster model with shared storage and replicas for scaling**, while standard **RDS** is usually more instance-centered.

![aurora.png](RDS,%20Aurora,%20and%20ElastiCache/aurora.png)

**Fast memory hook:**

**Aurora = RDS + better HA + easier read scaling.**

# Aurora Advance

These Aurora features are all about making the database more **elastic**, **global**, and **migration-friendly**. Think of them as add-ons to the **Aurora cluster** model: some help with **read scaling**, some help route traffic smarter, some reduce admin work, and some help you move from **SQL Server** or connect to **ML services**.

**Key Use Cases:**

- **Aurora Replicas + Auto Scaling:** handle **changing read traffic** by automatically adding/removing reader instances.
- **Custom Endpoints:** send different apps or workloads to **specific subsets of instances**.
- **Aurora Serverless v2:** best for **unpredictable or spiky workloads** with automatic capacity scaling.
- **Global Aurora:** best for **cross-Region disaster recovery** and **low-latency global reads**.
- **Aurora Machine Learning:** call AWS ML capabilities directly from Aurora workflows.
- **Babelfish for Aurora PostgreSQL:** migrate **SQL Server apps** to Aurora PostgreSQL with **fewer code and driver changes**.

**Exam Tip:**

If you see **“read scaling”**, think **Aurora Replicas**. If you see **“spiky workload”**, think **Aurora Serverless v2**. If you see **“global reads / cross-Region DR”**, think **Aurora Global Database**. If you see **“SQL Server app migration with minimal app changes”**, think **Babelfish**.

**Aurora Replicas – Auto Scaling:**

Aurora Auto Scaling automatically adds or removes **Aurora Replicas** based on workload and CloudWatch metrics. It helps only with **reader workload**, not the writer, and works best when apps use the **reader endpoint**.

**Aurora – Custom Endpoints:**

Custom endpoints let you create named endpoints for **selected DB instances**, such as bigger readers for analytics or a subset for specific apps. AWS says you can create up to **five custom endpoints** per provisioned Aurora cluster or **Aurora Serverless v2** cluster.

**Aurora Serverless:**

**Aurora Serverless v2** is an on-demand, autoscaling configuration for Aurora. You set a **minimum and maximum capacity range**, and Aurora scales compute automatically; AWS positions it for **variable or unpredictable workloads** and notes it supports features like **reader instances** and **global databases** that Serverless v1 did not.

**Global Aurora:**

An **Aurora global database** has **one primary Region** for writes and up to **10 read-only secondary Regions**. It is the Aurora choice for **global low-latency reads** and **cross-Region disaster recovery**.

**Aurora Machine Learning:**

Aurora ML lets your Aurora cluster integrate with AWS ML services directly from database-driven workflows. AWS currently documents integration with **Amazon Bedrock** for Aurora machine learning.

**Babelfish for Aurora PostgreSQL:**

Babelfish lets **SQL Server clients** talk to **Aurora PostgreSQL** using the **SQL Server wire protocol** and commonly used **T-SQL**, which reduces the amount of application change needed during migration. The easy exam contrast is: **standard Aurora PostgreSQL = PostgreSQL-native**, **Babelfish = SQL Server compatibility layer on Aurora PostgreSQL**.

**Visual Logic (Mermaid):**

![aurora-advanced.png](RDS,%20Aurora,%20and%20ElastiCache/aurora-advanced.png)

**Fast memory hook:**

**Replicas = read scale**

**Serverless v2 = spiky workload**

**Global = cross-Region**

**Babelfish = SQL Server migration**

# RDS and Aurora Backup and Monitoring

Think of **RDS backups** as AWS taking regular save points plus transaction logs for your database, so you can recover from mistakes or failure. **Aurora backup** is even more built-in: it continuously backs up the **cluster storage**, so you can restore to a point in time without managing lots of manual snapshots.

**Key Use Cases:**

- **RDS Backups:** use for **instance recovery** and **point-in-time restore** of standard RDS databases.
- **Aurora Backup:** use for **continuous cluster-level backup** and fast restore of Aurora clusters.
- **Aurora Database Cloning:** use when you need a **full copy fast** for **testing, dev, or analytics** without copying all storage up front.

**Exam Tip:**

If you see **“restore to a specific time,”** think **PITR**. If you see **“fast copy for testing”**, think **Aurora cloning**. If you see **“continuous and incremental cluster backups,”** think **Aurora**.

**RDS Backups:**

For standard **RDS**, AWS supports **automated backups** and **manual snapshots**. Automated backups enable **point-in-time recovery**, while snapshots are manual save points you keep until you delete them.

**Aurora Backup:**

Aurora backups are **continuous and incremental** during the retention period, and AWS notes you can restore a **new copy of the DB cluster** to any point in time in that window. Aurora also supports **DB cluster snapshots** and **retained automated backups** even after deletion if you choose to keep them.

**RDS & Aurora Restore options:**

Both **RDS** and **Aurora** support **point-in-time restore (PITR)**. **RDS** restores a **new DB instance** from automated backups, while **Aurora** restores a **new DB cluster** from continuous backup data or from a **DB cluster snapshot**. AWS Backup can also restore Aurora from either a **snapshot** or a **point in time**.

**Aurora Database Cloning:**

**Aurora cloning** creates a new cluster using **copy-on-write**, so the clone shares the same underlying storage pages at first and only stores changes separately as data diverges. The exam angle is: **clone = fast and space-efficient**, especially for **dev/test**.

**Main difference:**

**RDS backup** is usually more **instance-focused**, while **Aurora backup** is **cluster/storage-focused**. **Aurora cloning** is not just restore—it is a **rapid copy mechanism** for creating a usable duplicate cluster.

**Visual Logic (Mermaid):**

![rds-backup-monitoring.png](RDS,%20Aurora,%20and%20ElastiCache/rds-backup-monitoring.png)

**Fast memory hook:**

**RDS = backups for instance restore**

**Aurora = continuous cluster backup**

**Clone = instant-ish test copy**

# RDS and Aurora Security

Think of **RDS** and **Aurora** security like protecting a bank vault in layers: **lock the data when stored**, **protect it while traveling**, **control who can get in**, and **record what happened**. For the exam, the big idea is that AWS gives you multiple security layers: **encryption**, **network isolation**, **identity controls**, and **logging/auditing**.

**Key Use Case:**

- Choose **RDS/Aurora security features** when the question mentions **compliance, encryption, private access, IAM-based auth, or audit requirements**.

**Exam Tip:**

If you see **“encrypt at rest”**, think **KMS-backed DB encryption**. If you see **“encrypt in transit”**, think **SSL/TLS**. If you see **“control network access”**, think **Security Groups**. If you see **“track DB activity”**, think **audit/database logs**.

**At Rest Encryption:**

For **RDS**, encryption at rest protects the underlying storage, and for encrypted DB instances **logs, backups, and snapshots are also encrypted**. For **Aurora**, encryption is done at the storage layer, and AWS now states that **new Aurora DB clusters created on or after February 18, 2026 are encrypted at rest automatically using AES-256**.

**In-Flight Encryption:**

Both **RDS** and **Aurora** support **SSL/TLS** to encrypt connections between your application and the database. Aurora documentation explicitly notes you can use SSL/TLS and, for Aurora PostgreSQL, you can even **require** SSL/TLS connections.

**IAM Roles / IAM Authentication:**

This is the easy exam distinction: **IAM controls AWS-side access and permissions**, while **IAM database authentication** lets supported engines authenticate to the DB using an **IAM-generated auth token instead of a password**. Aurora supports IAM database authentication for **Aurora MySQL and Aurora PostgreSQL**, and RDS supports it for **MariaDB, MySQL, and PostgreSQL**.

**Security Groups:**

**VPC security groups** act like the firewall for your RDS DB instance or Aurora cluster. By default, **network access is off**, and you allow inbound access only from approved IP ranges, ports, or other security groups.

**Audit Logs:**

RDS engines generate logs you can **view, download, and monitor**, and RDS can export supported database logs to **Amazon CloudWatch Logs** for centralized analysis. For Aurora MySQL specifically, AWS documents **Advanced Auditing** to capture supported database activity.

**Main difference to remember:**

**Security Groups** control **who can reach the DB over the network**; **IAM/IAM DB auth** control **who can authenticate and how**; **encryption** protects the data; **audit logs** help you **prove and investigate activity**.

**Visual Logic (Mermaid):**

![rds-aurora-security.png](RDS,%20Aurora,%20and%20ElastiCache/rds-aurora-security.png)

**Fast memory hook:**

**At rest = KMS**

**In transit = TLS**

**Access = SG + IAM**

**Tracking = logs**

# RDS Proxy

**Amazon RDS Proxy** is like a **smart receptionist** that sits between your app and the database, reusing connections instead of making the database handle every new one directly. It helps apps scale better and stay more resilient during failovers, especially when there are **many short-lived connections**.

**Key Use Case:**

- Choose **RDS Proxy** when your app creates **lots of database connections**, such as **Lambda**, web apps, or microservices, and you want **connection pooling** plus better failover behavior.

**Exam Tip:**

If you see **“Lambda + relational database + too many connections”**, think **RDS Proxy**.

**What it does:**

**RDS Proxy** provides **connection pooling and sharing**, which reduces the load on the database and improves application scalability. AWS also states it can automatically reconnect to a standby DB instance while preserving application connections during failures.

**Security angle:**

RDS Proxy supports **IAM authentication** and integrates with **AWS Secrets Manager** for database credentials. AWS also documents **end-to-end IAM authentication** as an option for proxy-to-database connections.

**Main difference vs direct DB connection:**

A direct connection sends every app connection straight to the DB. **RDS Proxy** sits in front, **manages pooled connections**, and can smooth over failovers better than apps connecting directly.

**Visual Logic (Mermaid):**

![rds-proxy.png](RDS,%20Aurora,%20and%20ElastiCache/rds-proxy.png)

**Fast memory hook:**

**RDS Proxy = connection pooling for RDS/Aurora.**

# ElastiCache

**ElastiCache** is like putting a **super-fast memory shelf** in front of your database so your app can grab frequently used data without waiting on the slower database every time. It is an **in-memory cache** service, commonly used to speed up apps, reduce database load, and store short-lived user session data.

**Key Use Case:**

- Choose **ElastiCache** when the exam mentions **low latency**, **offloading repeated reads from a database**, or **storing temporary session data**.

**Exam Tip:**

If you see **“frequently accessed data,” “reduce DB load,”** or **“microsecond latency,”** think **ElastiCache**. If you see **“session store”** or **“leaderboard”**, think **Redis** more than **Memcached**.

**ElastiCache DB Cache Architecture:**

The classic exam pattern is: **App → ElastiCache → Database**. The app checks the cache first; on a **cache hit**, data comes back immediately, and on a **cache miss**, the app reads from the database and can place the result into the cache for next time.

**ElastiCache User Session Store Architecture:**

A common pattern is storing **user sessions** in ElastiCache so session data is fast to read and shared across multiple app servers. This works well because session data is usually **temporary**, **frequently accessed**, and benefits from fast in-memory retrieval.

**ElastiCache – Redis vs Memcached:**

**Redis** is the better fit when you need **replication, durability options, richer data structures, or session storage**. **Memcached** is simpler and often chosen for **basic distributed caching** when you just want a straightforward, multi-threaded in-memory cache. Main exam difference: **Redis = more features**, **Memcached = simpler cache only**. AWS also notes replication is available for **Valkey/Redis OSS**, **not Memcached**.

![elasticache.png](RDS,%20Aurora,%20and%20ElastiCache/elasticache.png)

**Fast memory hook:**

**DB cache = speed up reads.**

**Session store = shared login/session data.**

**Redis = advanced. Memcached = simple.**

# ElastiCache Security

**ElastiCache security** is about protecting cached data with several layers: **private network access**, **encryption**, and **authentication/authorization**. Think of it like a fast vault in memory: you still need strong doors, secure transport, and controlled keys even if the data is temporary.

**Key Use Case:**

- Choose **ElastiCache security features** when the question mentions **private cache access**, **TLS**, **encryption at rest**, **IAM auth**, or **least-privilege access to Redis/Valkey users**.

**Exam Tip:**

If you see **“cache in a VPC”**, think **Security Groups**. If you see **“encrypt data moving to/from cache”**, think **in-transit encryption/TLS**. If you see **“fine-grained Redis access”**, think **RBAC user groups**.

**Network Security:**

ElastiCache runs in a **VPC**, and access is typically controlled with **security groups**, so only approved application tiers can reach the cache. For the exam, this is the first control to think about for **network isolation**.

**At Rest Encryption:**

ElastiCache supports **at-rest encryption** for on-disk data such as **sync, backup, and swap** operations. It is **always enabled on serverless caches**, and for replication groups it must be chosen when the cache is **created**; you **can’t turn it on later** for an existing replication group.

**In-Flight Encryption:**

ElastiCache supports **in-transit encryption (TLS)** to protect data between the application and cache, and also between cache nodes. AWS notes that **all serverless caches have in-transit encryption enabled**.

**IAM / Authentication / Authorization:**

For **Valkey and Redis OSS**, ElastiCache supports **IAM authentication** and the **AUTH** command, with authorization through **RBAC** using **users and user groups**. The exam-friendly contrast is: **IAM = identity-based access**, **RBAC = fine-grained command/data access inside Redis/Valkey**.

**Main difference to remember:**

**Redis/Valkey** has richer security controls like **IAM auth** and **RBAC user groups**. **Memcached** is simpler and does not have the same feature set for replication/auth patterns.

**Visual Logic (Mermaid):**

![elasticache-security.png](RDS,%20Aurora,%20and%20ElastiCache/elasticache-security.png)

**Fast memory hook:**

**VPC + SG = network protection**

**TLS = in transit**

**At-rest encryption = create-time choice for replication groups**

**IAM/RBAC = Redis/Valkey access control**