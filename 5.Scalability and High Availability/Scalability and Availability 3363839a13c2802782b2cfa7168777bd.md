# Scalability and Availability

Think of **scalability** like growing a restaurant. **Vertical scalability** means making the kitchen bigger with a stronger stove and more staff in the same building; **horizontal scalability** means opening more branches to serve more customers. **High availability** means if one branch has a problem, customers can still eat at another branch without noticing much disruption.

## **Key Use Case**

- Choose these designs when you need an application to **handle growth** and **stay online even if part of the system fails**.

## **Exam Tip**

**If you see “fault tolerant across data centers” or “minimal downtime,” think Multi-AZ / high availability; if you see “handle more traffic,” think scaling.**

## **Main Difference**

- **Vertical Scalability** = scale **up/down** by changing the size of **one server**
- **Horizontal Scalability** = scale **out/in** by adding or removing **multiple servers**
- **High Availability** = keep the system **running despite failures**, usually by spreading across **multiple AZs**

![scalability-availability.png](Scalability%20and%20Availability/scalability-availability.png)

# Elastic Load Balancers

**Elastic Load Balancer (ELB)** is like a smart traffic officer standing in front of your app, sending each user to a healthy server so no one line gets overloaded. It also checks which servers are unhealthy and stops sending traffic to them automatically.

## **Key Use Case**

- Choose **ELB** when you need to **distribute traffic across multiple targets/AZs** and improve **scalability + availability**.

## **Exam Tip**

**If you see “distribute incoming traffic,” “only send traffic to healthy instances,” or “multi-AZ app entry point,” think ELB.**

## **Health Check**

A **health check** is ELB’s way of asking, “Are you okay?” If a target fails the check, ELB **stops routing traffic** to it until it becomes healthy again.

## **Elastic Load Balancer Types**

- **ALB (Application Load Balancer)** → for **HTTP/HTTPS**, smart app-level routing
- **NLB (Network Load Balancer)** → for **TCP/UDP/TLS**, very high performance / low latency
- **GWLB (Gateway Load Balancer)** → for **third-party virtual appliances** like firewalls
- **CLB (Classic Load Balancer)** → older generation, mostly seen in legacy scenarios

## **Main Difference**

- **ALB vs NLB**: **ALB** understands **web/app traffic**; **NLB** is better for **network-level traffic and extreme performance**.

![elastic-load-balancer.png](Scalability%20and%20Availability/elastic-load-balancer.png)

# Application Load Balancer (ALB)

**Application Load Balancer (ALB)** is the smart front door for **HTTP/HTTPS** applications. It can look at the request itself—like the **URL path**, **hostname**, or **headers**—and send traffic to the right backend service, which makes it great for modern web apps and microservices.

## **Key Use Case**

- Choose **ALB** when you need **Layer 7 routing**, such as sending `/images` to one app and `/api` to another.

## **Exam Tip**

**If you see “HTTP/HTTPS,” “path-based routing,” “host-based routing,” or “microservices,” think ALB.**

## **Target Groups**

A **target group** is the bucket of backends that ALB sends requests to. ALB listener rules forward traffic to a target group, and that group can contain **EC2 instances**, **IP addresses**, or even a **Lambda function**; health checks are configured **per target group**.

## **Main Difference**

- **ALB** = decides **how to route web requests**
- **Target Group** = defines **where those requests go**

![application-load-balancer.png](Scalability%20and%20Availability/application-load-balancer.png)

# Network Load Balancer

**Network Load Balancer (NLB)** is like a super-fast highway traffic controller for **network connections**. It works at **Layer 4**, routing **TCP, UDP, and TLS** traffic to healthy targets with **very low latency**, which makes it ideal for sudden spikes and heavy traffic.

## **Key Use Case**

- Choose **NLB** when you need to handle **very high-performance network traffic** or **non-HTTP protocols** such as **TCP/UDP/TLS**.

## **Exam Tip**

**If you see “millions of requests per second,” “ultra-low latency,” “static IP,” or “TCP/UDP,” think NLB.**

## **Main Difference**

- **ALB** = smart routing for **HTTP/HTTPS**
- **NLB** = ultra-fast routing for **TCP/UDP/TLS** at the **network layer**

![network-load-balancer.png](Scalability%20and%20Availability/network-load-balancer.png)

# Server Name Indication

**Server Name Indication (SNI)** is like telling the receptionist which company you want before entering a shared office building. During the **TLS handshake**, the client sends the **hostname**, so one load balancer listener can present the **right certificate** for the right domain.

## **Key Use Case**

- Choose **SNI** when you need **multiple HTTPS/TLS websites or apps on one load balancer listener** with different certificates.

## **Exam Tip**

**If you see “multiple SSL/TLS certificates on the same listener” or “multiple secure domains behind one load balancer,” think SNI.**

## **Main Difference**

- **SNI** = many domains, **one listener/IP**, different certs
- **Dedicated IP** = separate IP-based approach, usually for older client compatibility contexts like CloudFront’s dedicated-IP option.

![server-name-indication.png](Scalability%20and%20Availability/server-name-indication.png)

# Gateway Load Balancer (GWLB)

**Gateway Load Balancer (GWLB)** is like a security checkpoint in front of your network. It sends traffic to **virtual appliances** such as firewalls or intrusion detection systems, while also scaling them and checking whether they are healthy.

## **Key Use Case**

- Choose **GWLB** when you need to deploy and scale **third-party network/security appliances** transparently across environments.

## **Exam Tip**

**If you see “firewall,” “security appliance,” “traffic inspection,” or “bump-in-the-wire,” think GWLB.**

## **Target Groups**

A **target group** in GWLB is the set of appliance targets that receive inspected traffic. GWLB target groups support configurable **flow stickiness** attributes such as `5_tuple` behavior by default, and optional stickiness modes like **source_ip_dest_ip** or **source_ip_dest_ip_proto**.

## **Sticky Sessions**

For **GWLB**, this is really **flow stickiness**, not the cookie-based stickiness you see with ALB. It keeps packets from the same flow going to the **same appliance**, which is important for stateful inspection like firewalls.

## **Cross-Zone Load Balancing**

With **GWLB**, **cross-zone load balancing is disabled by default**. By default, each GWLB node sends traffic only to targets in the **same Availability Zone**; if you enable cross-zone, it can distribute traffic to healthy targets in **all enabled AZs**.

## **Main Difference**

- **GWLB Target Group Stickiness** = keeps a **network flow** on the same appliance
- **ALB Sticky Sessions** = keeps a **user’s web session** on the same backend, often with cookies
    
    ![gateway-laod-balancer.png](Scalability%20and%20Availability/gateway-laod-balancer.png)
    

# Connection Draining

**Connection Draining** is like telling a store cashier to **finish serving the customers already in line**, but **stop accepting new ones**. In AWS, when a target is being removed, the load balancer stops sending it new traffic and gives existing requests/connections time to finish first.

## **Key Use Case**

- Choose this when you want **safer deployments, instance replacement, or scale-in events** without cutting off active users.

## **Exam Tip**

**If you see “remove instance without interrupting in-flight requests,” think Connection Draining, also called Deregistration Delay.**

## **Main Difference**

- **Classic Load Balancer (CLB)** uses the term **Connection Draining**
- **ALB / NLB / GWLB** usually use **Deregistration Delay**, but the idea is the same.
    
    ![connection-draining.png](Scalability%20and%20Availability/connection-draining.png)
    

# Auto Scaling Group

An **Auto Scaling Group (ASG)** is like having an automatic manager for your app servers. It keeps the **right number of EC2 instances** running, adds more when demand rises, and removes some when demand falls, while also replacing unhealthy instances automatically.

## **Key Use Case**

- Choose **ASG** when you need **automatic scaling + self-healing EC2 capacity** for changing workloads.

## **Exam Tip**

**If you see “maintain desired capacity,” “replace failed EC2 instances,” or “scale based on demand,” think ASG.**

## **Scaling Policies**

- **Target Tracking** → easiest option; keeps a metric near a target, like **CPU at 50%**
- **Step Scaling** → add/remove capacity in **steps** based on alarm size
- **Simple Scaling** → older, simpler alarm-based scaling; less flexible than step scaling

## **Scaling Cooldown**

A **cooldown** is a pause that helps the group stabilize after scaling. For **simple scaling policies**, Auto Scaling waits for the cooldown to finish before another simple scaling activity starts; AWS generally recommends using **default instance warmup** for newer scaling behavior, especially with **target tracking** and **step scaling**.

## **Main Difference**

- **Target Tracking** = “keep metric near target”
- **Step Scaling** = “scale by amount of alarm breach”
- **Simple Scaling** = “basic legacy alarm response”

![auto-scaling-group.png](Scalability%20and%20Availability/auto-scaling-group.png)