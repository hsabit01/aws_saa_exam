# EC2 Basics

# EC2 Basics

Think of **EC2** like renting a computer in AWS’s data center instead of buying your own server. You choose the **size**, **operating system**, and how long you want to run it, then scale up or down when traffic changes. An **EC2 instance** is basically a virtual server you control.

**Key Use Case:**

- Choose **EC2** when you need **full control over the server**, such as custom software, specific OS settings, or long-running applications.

**Exam Tip:**

If you see **“virtual server,” “custom OS,”** or **“full control of compute,”** think **EC2**.

**Main Difference:**

**EC2 vs Lambda** → **EC2** = you manage the server; **Lambda** = AWS runs the code for you without server management. This fits EC2’s role as configurable cloud compute capacity.

![EC2.png](EC2%20Basics/EC2.png)

# EC2 Sizing & Configuration Options

Think of **EC2 sizing** like choosing a rental car: a **small sedan** for basic trips, an **SUV** for more space, or a **sports truck** for heavy work. In AWS, you pick the **instance family** for the job type and the **instance size** for how much **CPU, memory, storage, and network** you need.

**Key Use Case:**

- Choose the **right EC2 family + size** when you need to match workload needs like **balanced app servers, compute-heavy processing, memory-heavy databases, fast local storage, or GPU workloads**.

**Exam Tip:**

If you see **“choose based on CPU vs memory vs storage vs GPU needs”**, think **EC2 instance family first, then size**.

**Main Difference:**

**Family vs Size** → **Family** = what the instance is optimized for; **Size** = how much of it you get. Example: **M** = balanced, **C** = compute-heavy, **R** = memory-heavy; then **large / xlarge / 2xlarge** scales capacity up.

**What to remember fast:**

- **General purpose (M, T)** = balanced workloads, web apps.
- **Compute optimized (C)** = CPU-heavy apps.
- **Memory optimized (R, X, z, high-memory)** = in-memory DB/cache/analytics.
- **Storage optimized (I, D, H)** = very high local storage / IOPS.
- **Accelerated computing (G, P, Inf, Trn, F)** = GPU / ML / specialized acceleration.
- **T instances** = burstable; good for low/variable usage.
- You can **resize** an EC2 instance by changing its instance type if needed.

**Extra exam trigger:**

If the question is really about **cost**, the configuration choice may be **On-Demand vs Spot vs Savings Plans**, not just size:

- **On-Demand** = flexible, no commitment.
- **Spot** = cheapest, interruptible.
- **Savings Plans** = lower cost for steady usage commitments.

![sizing-configuration.png](EC2%20Basics/sizing-configuration.png)

# EC2 Instance Types

Think of **EC2 instance types** like choosing the right vehicle for a job: a **regular car** for everyday trips, a **truck** for heavy lifting, or a **race car** for speed. AWS groups EC2 into **families** based on what they’re best at—**balanced**, **CPU-heavy**, **memory-heavy**, **storage-heavy**, or **special acceleration**—and then gives each family different sizes.

**Key Use Case:**

- Choose the **instance type family** that matches the workload: **M/T** for balanced apps, **C** for compute-heavy, **R/X/U** for memory-heavy, **I/D/H** for storage-heavy, and **G/P/Inf/Trn/F** for accelerated workloads.

**Exam Tip:**

If you see **“high CPU,” “large in-memory database,” “GPU/ML,” or “very high IOPS local storage,”** think **EC2 instance family selection** first.

**Main Difference:**

**Instance family vs instance size** → **Family** tells you **what it is optimized for**; **size** tells you **how much capacity** you get. Instance names are based on **family, generation, processor/capabilities, and size**.

![ec2-instance-type.png](EC2%20Basics/ec2-instance-type.png)

# Security Group

Think of a **Security Group** like a **bouncer at the door** of your EC2 instance. It decides what traffic is allowed **in** and **out**, and it only lets in traffic you explicitly allow—plus it automatically allows the response back because it is **stateful**.

**Key Use Case:**

- Choose **Security Groups** when you need **instance-level firewall control** for resources in a **VPC**, such as allowing **HTTP/HTTPS** to a web server or **SSH** only from your office IP.

**Exam Tip:**

If you see **“instance firewall,” “allow rules only,”** or **“stateful,”** think **Security Group**.

**Main Difference:**

**Security Group vs NACL** → **Security Group** is **stateful** and works at the **instance/ENI level**; **NACL** is **stateless** and works at the **subnet level**.

![security-group.png](EC2%20Basics/security-group.png)

# EC2 SSH Connection

Think of **SSH** as a **secure remote key** that lets you unlock and control your EC2 Linux server from your laptop. To get in, you usually need **the instance’s public address**, **the correct username**, **your private key**, and a **Security Group rule allowing port 22**.

**Key Use Case:**

- Choose **SSH** when you need **secure command-line access** to manage a **Linux EC2 instance** directly.

**Exam Tip:**

If you see **“connect to Linux EC2,” “.pem key,”** or **“port 22,”** think **SSH + Security Group inbound rule for TCP 22**.

**Main Difference:**

**SSH vs EC2 Instance Connect** → **SSH** usually uses **your key pair** from your machine; **EC2 Instance Connect** can connect from the **AWS console/CLI** and still requires the right prerequisites, including **SSH access on port 22**.

**Visual Logic (Mermaid):**

![ec2-ssh-connection.png](EC2%20Basics/ec2-ssh-connection.png)

**Mini exam cues to memorize:**

- **Linux EC2** → use **SSH**.
- **Windows EC2** → usually **RDP (3389)**, not SSH.
- **Connection fails** → check **Security Group**, **correct key pair**, **correct username**, and **public reachability** first.

# EC2 IAM Role

Think of an **IAM role for EC2** like giving a delivery driver a **temporary company badge** instead of your personal keys. The EC2 instance uses the role to get **temporary AWS permissions** so apps on the server can call services like **S3** or **DynamoDB** without storing access keys on the machine.

**Key Use Case:**

- Choose an **IAM role for EC2** when an application on the instance needs secure access to other AWS services, such as reading from **S3** or publishing to **SQS**, without hardcoded credentials.

**Exam Tip:**

If you see **“EC2 needs access to AWS services securely”** or **“avoid storing access keys on the instance,”** think **IAM role attached through an instance profile**.

**Main Difference:**

**IAM user vs IAM role for EC2** → **IAM user** has long-term credentials; **IAM role for EC2** provides **temporary credentials** to the instance. Also, the role is attached to EC2 through an **instance profile**.

**Visual Logic (Mermaid):**

![ec2-iam-role.png](EC2%20Basics/ec2-iam-role.png)

**Fast memory hook:**

**EC2 permissions = Role**, **human/admin permissions = User or federated identity**.

Next good one: **NACL**, **EBS**, or **AMI**.

# EC2 Purchase Options

Think of **EC2 purchase options** like renting transportation: **pay as you go**, **commit for discounts**, or **grab unused seats cheaply if you can be flexible**. You are still using **EC2**, but the purchase option changes the **cost, commitment, interruption risk, and capacity guarantee**.

**Key Use Case:**

- Choose based on the workload: **On-Demand** for flexibility, **Spot** for interruptible workloads, **Savings Plans / Reserved Instances** for steady usage, and **Capacity Reservations** when guaranteed capacity in a specific AZ matters.

**Exam Tip:**

If you see **“steady state”**, think **Savings Plans or Reserved Instances**; if you see **“interruptible and cheapest”**, think **Spot**; if you see **“must guarantee capacity”**, think **Capacity Reservation**.

**Main Difference:**

**Savings Plans vs Reserved Instances** → both reduce cost for committed usage, but **Savings Plans** are more flexible around instance configuration, while **Reserved Instances** are tied more closely to a specific instance configuration and Region.

**Fast memory list:**

- **On-Demand** = no commitment, pay by the second.
- **Spot** = big discount, but AWS can interrupt it.
- **Savings Plans** = commit to usage spend for **1 or 3 years**.
- **Reserved Instances** = billing discount for matching usage, typically **1 or 3 years**.
- **Dedicated Hosts / Dedicated Instances** = single-tenant hardware needs. **Dedicated Hosts** are the main choice when **BYOL** and host-level visibility matter.
- **Capacity Reservations** = reserve EC2 capacity in a **specific Availability Zone**.

![ec2-purchase-options.png](EC2%20Basics/ec2-purchase-options.png)