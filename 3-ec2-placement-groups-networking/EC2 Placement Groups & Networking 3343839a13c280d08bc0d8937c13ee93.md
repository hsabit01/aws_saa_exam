# EC2 Placement Groups & Networking

# Elastic IP

Think of **Elastic IP** like reserving a **permanent street address** for your house, even if you move your furniture to a different building. It gives you a **static public IPv4 address** that stays with your AWS account until you release it, and you can quickly remap it to another resource if needed.

**Key Use Case:**

- Choose **Elastic IP** when you need a **fixed public IPv4 address** for an internet-facing resource, such as an **EC2 instance**, **NAT Gateway**, or **Network Load Balancer**.

**Exam Tip:**

**If you see “static public IP” or “must keep same public IP after instance replacement,” think *Elastic IP*.** Also remember: **EIPs are regional and AWS charges for public IPv4 addresses, including EIPs.**

**Main Difference:**

**Elastic IP vs Auto-assigned Public IP** → **Elastic IP** is **persistent and reusable**; an **auto-assigned public IP** is temporary and released when disassociated or when the instance is stopped/terminated, depending on the setup.

![elastic-ip.png](EC2%20Placement%20Groups%20&%20Networking/elastic-ip.png)

# Placement Groups

Think of **Placement Groups** like choosing where your team sits in an office building. You can put servers **very close together** for speed, **far apart** to reduce shared failure risk, or **grouped into isolated sections** so one hardware issue does not affect everyone.

**Key Use Case:**

- Choose **Placement Groups** when you need to control **EC2 instance placement** for either **low latency/high throughput** or **fault isolation**.

**Exam Tip:**

**If you see “HPC” or “ultra-low latency between EC2 instances,” think *Cluster Placement Group*. If you see “reduce correlated hardware failure,” think *Spread* or *Partition*.**

**Main Difference:**

**Cluster vs Spread vs Partition** → **Cluster** = pack instances close together in **one AZ** for performance; **Spread** = keep a **small number** of critical instances on **distinct hardware**; **Partition** = place large distributed workloads across **separate partitions/racks** for fault isolation. **Partition** can span **multiple AZs in the same Region** and supports up to **7 partitions per AZ**

![placement-groups.png](EC2%20Placement%20Groups%20&%20Networking/placement-groups.png)

# Cluster Placement Group

Think of **Cluster Placement Group** like seating your entire team in the **same small room** so they can talk as fast as possible. AWS places EC2 instances **physically close together in a single Availability Zone** to give **very low network latency** and **high throughput** between them.

**Key Use Case:**

- Choose **Cluster Placement Group** for **high-performance computing (HPC)**, tightly coupled apps, or workloads needing **fast instance-to-instance communication**.

**Exam Tip:**

**If you see “low latency,” “high throughput,” “HPC,” or “nodes must communicate very fast,” think *Cluster Placement Group*.** It works **within one AZ only** and can hit **insufficient capacity** more easily if you mix instance types or add instances later.

**Main Difference:**

**Cluster vs Spread/Partition** → **Cluster** is for **performance**; **Spread** and **Partition** are for **fault isolation**.

![cluster-placement-group.png](EC2%20Placement%20Groups%20&%20Networking/cluster-placement-group.png)

# Spread Placement Group

Think of **Spread Placement Group** like seating a few important team members in **different rooms** so one power problem does not affect all of them at once. AWS places each EC2 instance on **distinct underlying hardware** to reduce the chance of **correlated failure**.

**Key Use Case:**

- Choose **Spread Placement Group** for a **small number of critical EC2 instances** that must be kept separate for **high availability**.

**Exam Tip:**

**If you see “small number of critical instances” or “reduce correlated hardware failure,” think *Spread Placement Group*.** In a Region, a rack-level spread placement group supports up to **7 running instances per AZ per group**.

**Main Difference:**

**Spread vs Cluster** → **Spread** is for **availability/fault isolation**; **Cluster** is for **performance/low latency**. **Spread vs Partition** → **Spread** is best for a **small set** of critical instances, while **Partition** is for **larger distributed workloads** like Hadoop, Cassandra, or Kafka

![spread-placement-group.png](EC2%20Placement%20Groups%20&%20Networking/spread-placement-group.png)

# Partition Placement Group

Think of **Partition Placement Group** like splitting a large team across **separate office sections**, so if one section loses power, the others keep working. AWS spreads EC2 instances across **logical partitions** where instances in different partitions do **not share the same underlying hardware**, helping contain failures.

**Key Use Case:**

- Choose **Partition Placement Group** for **large distributed, replicated workloads** like **Hadoop, HBase, Cassandra, or Kafka** that need **fault isolation at scale**.

**Exam Tip:**

**If you see “large distributed system,” “replication across nodes,” or “rack-aware fault isolation,” think *Partition Placement Group*.** It can span **multiple AZs in one Region** and supports up to **7 partitions per AZ**.

**Main Difference:**

**Partition vs Spread** → **Partition** is for **many instances / distributed systems**; **Spread** is for a **small number of critical instances**. **Partition vs Cluster** → **Partition** is for **fault isolation**, while **Cluster** is for **low latency and high throughput**.

![partition-pacement-group.png](EC2%20Placement%20Groups%20&%20Networking/partition-pacement-group.png)

# Elastic Network Interface (ENI)

Think of an **ENI** as a **removable network card** for an EC2 instance. It holds networking settings like **private IP addresses**, **security groups**, and even an **Elastic IP**, and you can move a **secondary ENI** to another instance in the **same AZ** if needed.

**Key Use Case:**

- Choose **ENI** when you need to **preserve network settings** or build **multi-network / network appliance** setups for EC2.

**Exam Tip:**

**If you see “move private IP / security groups / network identity from one EC2 to another,” think *ENI*.** Also remember: the **primary ENI can’t be detached**, but a **secondary ENI can** be moved to another instance in the **same Availability Zone**.

**Main Difference:**

**ENI vs EIP** → **ENI** is the **virtual network interface** itself; **EIP** is just a **static public IPv4 address** that can be associated with that interface.

![elastic-network-interface.png](EC2%20Placement%20Groups%20&%20Networking/elastic-network-interface.png)

# EC2 Hibernate

Think of **EC2 Hibernate** like closing your laptop lid instead of shutting it down. AWS saves the instance’s **RAM contents to the EBS root volume**, so when you start it again, your apps resume much faster from where they left off.

**Key Use Case:**

- Choose **EC2 Hibernate** for instances that take a **long time to boot or warm up**, such as pre-warmed app servers, desktops, or memory-heavy workloads.

**Exam Tip:**

**If you see “preserve in-memory state” or “resume faster without full reboot,” think *EC2 Hibernate*.** You must **enable it at launch**, and it requires a **supported HVM AMI**, **supported instance type**, and an **encrypted EBS root volume** large enough to hold RAM contents.

**Main Difference:**

**Hibernate vs Stop** → **Stop** keeps disk data only; **Hibernate** keeps **disk + RAM state**. Also, after restart, the instance keeps its **private IP** and **Elastic IP**, but a non-EIP **public IPv4** is released and a new one is assigned.

![ec2-hibernate.png](EC2%20Placement%20Groups%20&%20Networking/ec2-hibernate.png)