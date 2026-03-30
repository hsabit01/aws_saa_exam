# Scalability and Availability

# High Availability

**High Availability (HA)** means designing AWS systems so they stay up even if **one part fails**. Think of it like having **multiple power generators** in different buildings: if one building loses power, the others keep everything running. In AWS, this usually means spreading resources across **multiple Availability Zones (AZs)** and avoiding a **single point of failure**.

**Key Use Case:**

- Choose **High Availability** when the app must **continue running during instance, AZ, or service component failures**.

**Exam Tip:**

**If you see “minimize downtime” or “survive failure,” think “Multi-AZ + Load Balancer + Auto Scaling.”**

**Visual Logic (Mermaid):**

![high-availability.png](Scalability%20and%20Availability/high-availability.png)

**Main difference to remember:**

**High Availability** = system stays **up during failure**.

**Scalability** = system handles **more traffic**.

A design can have **both**, but they are not the same.

# Scalability

**Scalability** means a system can handle **more work** as demand grows. Think of it like a restaurant adding **more tables or more staff** during busy hours so customers are still served quickly. In AWS, this usually means using services like **Auto Scaling**, **Elastic Load Balancing**, and sometimes serverless options like **Lambda**.

**Key Use Case:**

- Choose **Scalability** when traffic or workload can **grow, spike, or change over time**.

**Exam Tip:**

**If you see “variable traffic,” “traffic spikes,” or “unpredictable workload,” think “Auto Scaling + ELB” or “Lambda.”**

**Visual Logic (Mermaid):**

![scalability.png](Scalability%20and%20Availability/scalability.png)

**Main difference to remember:**

**Scalability** = handles **more demand**.

**High Availability** = survives **failures with minimal downtime**.

# Elastic Load Balancer

**Load Balancing** spreads incoming traffic across **multiple targets** so no single server gets overwhelmed. Think of it like a receptionist sending customers to the **shortest available line** so service stays fast and reliable. In AWS, this is usually done with **Elastic Load Balancing (ELB)**, especially **Application Load Balancer (ALB)** and **Network Load Balancer (NLB)**.

**Key Use Case:**

- Choose **Load Balancing** when you need to **distribute traffic**, improve **availability**, and support **scaling across multiple instances**.

**Exam Tip:**

**If you see “distribute traffic across multiple EC2 instances,” think “ELB.” If it mentions Layer 7/path-based routing, think “ALB.”**

**Visual Logic (Mermaid):**

![load-balancing.png](Scalability%20and%20Availability/load-balancing.png)

**Main difference to remember:**

**ALB** = **Layer 7**, smart routing based on **path/host/http headers**.

**NLB** = **Layer 4**, ultra-high performance for **TCP/UDP/TLS** traffic.

# Application Load Balancer (ALB)

An **Application Load Balancer (ALB)** is like a smart front-desk receptionist that looks at each request and sends it to the **right backend service**. A **Target Group** is the specific team or room that receives that traffic, such as a set of **EC2 instances**, **containers**, or **Lambda functions**. Together, they let one entry point route traffic based on rules like **URL path** or **host name**.

**Key Use Case:**

- Choose **ALB + Target Groups** when you need **Layer 7 routing** like **path-based** (`/api`, `/images`) or **host-based** (`app.example.com`, `api.example.com`) traffic distribution.

**Exam Tip:**

**If you see “path-based routing,” “host-based routing,” or “multiple apps behind one load balancer,” think “ALB + Target Groups.”**

**Visual Logic (Mermaid):**

![application-load-balancer.png](Scalability%20and%20Availability/application-load-balancer.png)

**Main difference to remember:**

**ALB** decides **how to route requests**.

**Target Group** defines **where those requests go**.

# Network Load Balancer (NLB)

A **Network Load Balancer (NLB)** is a very fast traffic director that works at the **network level**. Think of it like a highway traffic officer who quickly sends cars to open roads without inspecting what’s inside the car. It is built for **extreme performance**, **low latency**, and can handle **millions of requests per second**.

**Key Use Case:**

- Choose **NLB** when you need **ultra-high performance**, **static IPs**, or support for **TCP/UDP/TLS** traffic.

**Exam Tip:**

**If you see “very high performance,” “low latency,” “static IP,” or “TCP/UDP,” think “NLB.”**

**Visual Logic (Mermaid):**

![network-load-balancer.png](Scalability%20and%20Availability/network-load-balancer.png)

**Main difference to remember:**

**ALB** = smart **Layer 7** routing for **HTTP/HTTPS**.

**NLB** = fast **Layer 4** routing for **TCP/UDP/TLS**.

# Gateway Load Balancer

A **Gateway Load Balancer (GWLB)** is a special load balancer used to insert **network security appliances** into traffic flow, like **firewalls** or **intrusion detection systems**. Think of it like a **security checkpoint on a highway**: every car passes through inspection before reaching its destination. It helps you **scale, simplify, and centralize** third-party virtual appliances.

**Key Use Case:**

- Choose **GWLB** when you need to **deploy and scale firewalls, packet inspection, or security appliances transparently** across many workloads/VPCs.

**Exam Tip:**

**If you see “third-party firewall,” “traffic inspection,” or “centralized network security appliance,” think “Gateway Load Balancer.”**

**Visual Logic (Mermaid):**

![gateway-load-balancer.png](Scalability%20and%20Availability/gateway-load-balancer.png)

**Main difference to remember:**

**ALB** = routes **web requests**.

**NLB** = routes **network traffic fast**.

**GWLB** = sends traffic through **security appliances**.

# Load Balancer - SSL Certificate

For an AWS Load Balancer, the **SSL/TLS certificate** is what lets it handle **HTTPS** securely, so data between the user and the load balancer is encrypted. Think of it like a **security guard checking IDs at the front door**—users trust they are talking to the real site, and the conversation stays private. In AWS, the certificate is usually managed through **AWS Certificate Manager (ACM)** and attached to the load balancer **listener**.

**Key Use Case:**

- Choose **ACM + Load Balancer SSL termination** when you want **HTTPS encryption** without managing certificates on every EC2 instance.

**Exam Tip:**

**If you see “HTTPS,” “SSL certificate on load balancer,” or “offload encryption from EC2,” think “ACM certificate attached to an ALB/NLB listener.”**

**Visual Logic (Mermaid):**

![ssl-load-balancer.png](Scalability%20and%20Availability/ssl-load-balancer.png)

**Main difference to remember:**

**ACM** = provides/manages the **certificate**.

**Load Balancer listener** = **uses** that certificate to handle **HTTPS** traffic.

# Connection Draining

**Connection Draining** means a load balancer stops sending **new requests** to a server that is being removed, but lets it **finish the requests it is already handling**. Think of it like closing a checkout lane in a store: no new customers join, but the people already in line can finish. In AWS, this helps avoid **dropped user sessions** during scaling events or deployments.

**Key Use Case:**

- Choose **Connection Draining** when instances are being **terminated/deregistered** but you want **in-flight requests to complete gracefully**.

**Exam Tip:**

**If you see “avoid interrupting active users during scale-in or deployment,” think “Connection Draining / Deregistration Delay.”**

**Visual Logic (Mermaid):**

![connection-draining.png](Scalability%20and%20Availability/connection-draining.png)

**Main difference to remember:**

**Health check failure** = instance is considered **unhealthy**.

**Connection Draining** = instance is being **removed gracefully**, without cutting off active requests.

# Auto Scaling Group

An **Auto Scaling Group (ASG)** automatically adds or removes **EC2 instances** based on demand or health. Think of it like a store manager who calls in more staff when the shop gets busy and sends some home when it gets quiet. It also replaces unhealthy instances to help keep the application running.

**Key Use Case:**

- Choose **Auto Scaling Group** when you need **automatic scaling** and **self-healing EC2 fleets**.

**Exam Tip:**

**If you see “scale based on demand” or “replace failed EC2 instances automatically,” think “ASG.”**

**Visual Logic (Mermaid):**

![auto-scaling-group.png](Scalability%20and%20Availability/auto-scaling-group.png)

**Main difference to remember:**

**Load Balancer** = spreads traffic across instances.

**Auto Scaling Group** = decides **how many instances** should exist.