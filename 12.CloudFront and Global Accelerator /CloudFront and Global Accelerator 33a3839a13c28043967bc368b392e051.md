# CloudFront and Global Accelerator

# CloudFront

**Amazon CloudFront** is AWS’s **CDN**—think of it like putting copies of your store’s flyers in many neighborhood kiosks around the world, so customers grab them nearby instead of traveling to your main office. It speeds up delivery of **static and dynamic content** by caching it at global **edge locations** and pulling from the **origin** only when needed.

**Key Use Case**

- Choose **CloudFront** when you need **low-latency global delivery** for websites, APIs, media, or files while reducing load on the origin.

**Exam Tip**

**If you see “global users + faster content delivery + caching at edge,” think *CloudFront*.** Also watch for **S3 + static website/content acceleration** clues.

**Visual Logic (Mermaid)**

![cloudfront.png](CloudFront%20and%20Global%20Accelerator/cloudfront.png)

**Common Similar-Service Difference**

**CloudFront vs Global Accelerator**: **CloudFront** improves delivery of **cacheable web content and HTTP(S)** through edge caching; **Global Accelerator** improves routing to application endpoints but **does not cache content**.

# **CloudFront Geo Restriction**

**CloudFront Geo Restriction** is like a nightclub bouncer who checks what **country** a visitor is coming from before letting them in. You can tell **CloudFront** to allow only certain countries or block certain countries from accessing your content, and blocked users get a **403 Forbidden** response.

**Key Use Case**

- Choose **Geo Restriction** when content must be **available only in specific countries** due to licensing, compliance, or business rules.

**Exam Tip**

**If you see “restrict website/content by country,” think *CloudFront Geo Restriction* with an allowlist or blocklist.**

**Visual Logic (Mermaid)**

![cloudfront-geo-location.png](CloudFront%20and%20Global%20Accelerator/cloudfront-geo-location.png)

**Main Difference**

**Geo Restriction vs AWS WAF geo match**: **CloudFront Geo Restriction** is a simple **country-level allow/block** for the whole distribution, while **AWS WAF** is better when you need **more flexible rules** and can work with other request conditions too. Also, for restricting only **some files** or using granularity finer than country level, AWS notes you may need a **third-party geolocation service**

# **CloudFront cache invalidation**

**CloudFront cache invalidation** is like telling every branch of a bookstore to throw away an old poster immediately so customers stop seeing outdated info. Instead of waiting for the cached file to expire naturally, **CloudFront** clears the old copy at edge locations so the next request pulls the fresh version from the **origin**.

**Key Use Case**

- Choose **cache invalidation** when you updated a file and need users to see the **new version right away** without waiting for the TTL to expire.

**Exam Tip**

**If you see “updated content must appear immediately,” think *CloudFront Invalidation*; if updates happen often, think *versioned file names* instead.** AWS specifically recommends **versioning** as the primary approach for frequent updates.

**Visual Logic (Mermaid)**

![cloudfront-cache-invalidation.png](CloudFront%20and%20Global%20Accelerator/cloudfront-cache-invalidation.png)

**Main Difference**

**Invalidation vs TTL/versioning**: **Invalidation** removes cached objects now, while **TTL** makes them expire later, and **versioned file names** are usually better for frequent changes because users and intermediary caches may still keep old copies of the old filename. Also, if you cache by **query strings**, you must invalidate the specific query-string variants or use a wildcard path.

# **AWS Global Accelerator**

**AWS Global Accelerator** is like giving your application a **global VIP front door** with fixed addresses, then letting AWS route each visitor over its private backbone to the **best healthy regional endpoint**. Unlike a CDN, it does **not cache content**; it improves **performance, availability, and failover** for internet-facing apps such as **ALBs, NLBs, EC2 instances, and Elastic IPs**.

**Key Use Case**

- Choose **Global Accelerator** when you need **static anycast IPs**, **fast global routing**, and **automatic failover across Regions** for an application.

**Exam Tip**

**If you see “global users + static IPs + fastest path to healthy regional app endpoint,” think *Global Accelerator*.**

**Visual Logic (Mermaid)**

![global-accelerator.png](CloudFront%20and%20Global%20Accelerator/global-accelerator.png)

**Main Difference**

**Global Accelerator vs CloudFront**: **Global Accelerator** routes users to the **optimal healthy application endpoint** using **static global IPs** and the AWS network, while **CloudFront** speeds up delivery of **web content** by **caching at edge locations**.

# CloudFront vs Global Accelerator

Think of **CloudFront** as a **global caching layer**—like storing copies of your content in local warehouses worldwide so users get it faster.

**AWS Global Accelerator** is a **smart traffic router**—like giving users a single VIP entrance that directs them to the **best-performing data center** using AWS’s private network.

**Key Use Case**

- Choose **CloudFront** for **content delivery & caching (websites, images, videos, APIs)**
- Choose **Global Accelerator** for **low-latency routing + failover to apps across Regions**

**Exam Tip**

**If you see “cache, CDN, static content,” → CloudFront**

**If you see “static IP, multi-region failover, TCP/UDP apps,” → Global Accelerator**

**Visual Logic (Mermaid)**

![cloudfront-vs-global-accelerator.png](CloudFront%20and%20Global%20Accelerator/cloudfront-vs-global-accelerator.png)

**Main Difference (High-Yield for Exam)**

- **CloudFront** → **Caches content at edge (HTTP/HTTPS only)** → best for **web performance + static/dynamic content delivery**
- **Global Accelerator** → **No caching, routes traffic via AWS backbone (TCP/UDP)** → best for **multi-region apps, failover, static IPs**