# AWS SAA Exam Notes

Study notes for AWS Solutions Architect Associate topics, organized into chapter folders. Each chapter has a local `README.md` with direct links to the note file and its main review sections.

## Start Here

1. [IAM](./1.IAM/README.md) - Identity, policies, service roles, and account access review tools.
2. [EC2 Basics](./2.EC2%20Basics/README.md) - Core compute concepts, instance sizing, security groups, access, and purchase options.
3. [EC2 Placement Groups and Networking](./3.EC2%20Placement%20Groups%20and%20Networking/README.md) - Elastic IPs, placement strategies, ENIs, and hibernation behavior.
4. [EC2 Storage](./4.EC2%20Storage/README.md) - EBS, snapshots, AMIs, EFS, and storage tradeoffs.
5. [Scalability and High Availability](./5.Scalability%20and%20High%20Availability/README.md) - Load balancing, traffic distribution, and Auto Scaling patterns.
6. [RDS, Aurora, and ElastiCache](./6.RDS,Aurora,ElasticCache/README.md) - Managed relational databases, Aurora features, database protection, and caching patterns.
7. [Route 53](./7.Route%2053/README.md) - DNS records, hosted zones, health checks, and routing policies for global traffic control.
8. [Golden AMI and Elastic Beanstalk](./8.Golden%20AMI%20and%20Elastic%20Beanstalk/README.md) - Standardized EC2 images and managed application deployments for faster platform setup.
9. [Amazon S3](./9.Amazon%20S3/README.md) - Object storage fundamentals, lifecycle automation, storage classes, access controls, replication patterns, and static website hosting.
10. [Amazon S3 - Advance](./10.Amazon%20S3%20-%20Advance/README.md) - Advanced S3 features for shared-data billing, event-driven workflows, and Storage Lens analytics.
11. [Amazon S3 - Security](./11.Amazon%20S3%20-%20Security/README.md) - S3 encryption models, transport security, retention controls, access auditing, and specialized access patterns.
12. [CloudFront and Global Accelerator](./12.CloudFront%20and%20Global%20Accelerator%20/README.md) - Edge caching, geo restrictions, cache invalidation, and global application traffic acceleration.
13. [AWS Storage Extra](./13.AWS%20Storage%20Extra/README.md) - Offline migration, hybrid gateways, managed file storage, and network transfer services for large-scale data movement.

## Documentation Map

### [IAM](./1.IAM/README.md)

- [IAM](./1.IAM/IAM%203343839a13c2802a9b75f1cc42a5855c.md) - Identity management basics, service roles, credential audits, and permission usage review.
  - [IAM users, groups, and policies](./1.IAM/IAM%203343839a13c2802a9b75f1cc42a5855c.md#iam-users-groups-and-policies)
  - [IAM Roles for services](./1.IAM/IAM%203343839a13c2802a9b75f1cc42a5855c.md#iam-roles-for-services)
  - [IAM Credential Report](./1.IAM/IAM%203343839a13c2802a9b75f1cc42a5855c.md#iam-credential-report)
  - [IAM Access Advisor (Service Last Accessed data)](./1.IAM/IAM%203343839a13c2802a9b75f1cc42a5855c.md#iam-access-advisor-service-last-accessed-data)

### [EC2 Basics](./2.EC2%20Basics/README.md)

- [EC2 Basics](./2.EC2%20Basics/EC2%20Basics%203323839a13c2802fbddbfa38a1a57df3.md) - Compute fundamentals, sizing choices, access patterns, and purchasing models.
  - [EC2 Sizing & Configuration Options](./2.EC2%20Basics/EC2%20Basics%203323839a13c2802fbddbfa38a1a57df3.md#ec2-sizing--configuration-options)
  - [EC2 Instance Types](./2.EC2%20Basics/EC2%20Basics%203323839a13c2802fbddbfa38a1a57df3.md#ec2-instance-types)
  - [Security Group](./2.EC2%20Basics/EC2%20Basics%203323839a13c2802fbddbfa38a1a57df3.md#security-group)
  - [EC2 SSH Connection](./2.EC2%20Basics/EC2%20Basics%203323839a13c2802fbddbfa38a1a57df3.md#ec2-ssh-connection)
  - [EC2 IAM Role](./2.EC2%20Basics/EC2%20Basics%203323839a13c2802fbddbfa38a1a57df3.md#ec2-iam-role)
  - [EC2 Purchase Options](./2.EC2%20Basics/EC2%20Basics%203323839a13c2802fbddbfa38a1a57df3.md#ec2-purchase-options)

### [EC2 Placement Groups and Networking](./3.EC2%20Placement%20Groups%20and%20Networking/README.md)

- [EC2 Placement Groups & Networking](./3.EC2%20Placement%20Groups%20and%20Networking/EC2%20Placement%20Groups%20%26%20Networking%203343839a13c280d08bc0d8937c13ee93.md) - Elastic IPs, placement group strategies, ENIs, and EC2 hibernation.
  - [Elastic IP](./3.EC2%20Placement%20Groups%20and%20Networking/EC2%20Placement%20Groups%20%26%20Networking%203343839a13c280d08bc0d8937c13ee93.md#elastic-ip)
  - [Placement Groups](./3.EC2%20Placement%20Groups%20and%20Networking/EC2%20Placement%20Groups%20%26%20Networking%203343839a13c280d08bc0d8937c13ee93.md#placement-groups)
  - [Cluster Placement Group](./3.EC2%20Placement%20Groups%20and%20Networking/EC2%20Placement%20Groups%20%26%20Networking%203343839a13c280d08bc0d8937c13ee93.md#cluster-placement-group)
  - [Spread Placement Group](./3.EC2%20Placement%20Groups%20and%20Networking/EC2%20Placement%20Groups%20%26%20Networking%203343839a13c280d08bc0d8937c13ee93.md#spread-placement-group)
  - [Partition Placement Group](./3.EC2%20Placement%20Groups%20and%20Networking/EC2%20Placement%20Groups%20%26%20Networking%203343839a13c280d08bc0d8937c13ee93.md#partition-placement-group)
  - [Elastic Network Interface (ENI)](./3.EC2%20Placement%20Groups%20and%20Networking/EC2%20Placement%20Groups%20%26%20Networking%203343839a13c280d08bc0d8937c13ee93.md#elastic-network-interface-eni)
  - [EC2 Hibernate](./3.EC2%20Placement%20Groups%20and%20Networking/EC2%20Placement%20Groups%20%26%20Networking%203343839a13c280d08bc0d8937c13ee93.md#ec2-hibernate)

### [EC2 Storage](./4.EC2%20Storage/README.md)

- [EC2 Storage](./4.EC2%20Storage/EC2%20Storage%203343839a13c28058b2c2de7c478889cb.md) - EBS volumes, snapshots, AMIs, EFS, lifecycle options, and storage comparisons.
  - [Elastic Storage Block (ESB)](./4.EC2%20Storage/EC2%20Storage%203343839a13c28058b2c2de7c478889cb.md#elastic-storage-block-esb)
  - [EBS Snapshot](./4.EC2%20Storage/EC2%20Storage%203343839a13c28058b2c2de7c478889cb.md#ebs-snapshot)
  - [EBS Snapshot Features](./4.EC2%20Storage/EC2%20Storage%203343839a13c28058b2c2de7c478889cb.md#ebs-snapshot-features)
  - [Amazon Machine Image (AMI)](./4.EC2%20Storage/EC2%20Storage%203343839a13c28058b2c2de7c478889cb.md#amazon-machine-image-ami)
  - [EBS Volume Types](./4.EC2%20Storage/EC2%20Storage%203343839a13c28058b2c2de7c478889cb.md#ebs-volume-types)
  - [EBS Multi-Attach](./4.EC2%20Storage/EC2%20Storage%203343839a13c28058b2c2de7c478889cb.md#ebs-multi-attach)
  - [Elastic File System (EFS)](./4.EC2%20Storage/EC2%20Storage%203343839a13c28058b2c2de7c478889cb.md#elastic-file-system-efs)
  - [EFS Use Cases and Access](./4.EC2%20Storage/EC2%20Storage%203343839a13c28058b2c2de7c478889cb.md#efs-use-cases-and-access)
  - [EFS Performance and Throughput Modes](./4.EC2%20Storage/EC2%20Storage%203343839a13c28058b2c2de7c478889cb.md#efs-performance-and-throughput-modes)
  - [EFS Storage Classes and Lifecycle Tiers](./4.EC2%20Storage/EC2%20Storage%203343839a13c28058b2c2de7c478889cb.md#efs-storage-classes-and-lifecycle-tiers)
  - [EBS vs EFS vs Instance Store](./4.EC2%20Storage/EC2%20Storage%203343839a13c28058b2c2de7c478889cb.md#ebs-vs-efs-vs-instance-store)

### [Scalability and High Availability](./5.Scalability%20and%20High%20Availability/README.md)

- [Scalability and Availability](./5.Scalability%20and%20High%20Availability/Scalability%20and%20Availability%203363839a13c2802782b2cfa7168777bd.md) - Scaling models, load balancer choices, TLS routing, connection draining, and Auto Scaling behavior.
  - [Elastic Load Balancers](./5.Scalability%20and%20High%20Availability/Scalability%20and%20Availability%203363839a13c2802782b2cfa7168777bd.md#elastic-load-balancers)
  - [Application Load Balancer (ALB)](./5.Scalability%20and%20High%20Availability/Scalability%20and%20Availability%203363839a13c2802782b2cfa7168777bd.md#application-load-balancer-alb)
  - [Network Load Balancer](./5.Scalability%20and%20High%20Availability/Scalability%20and%20Availability%203363839a13c2802782b2cfa7168777bd.md#network-load-balancer)
  - [Server Name Indication](./5.Scalability%20and%20High%20Availability/Scalability%20and%20Availability%203363839a13c2802782b2cfa7168777bd.md#server-name-indication)
  - [Gateway Load Balancer (GWLB)](./5.Scalability%20and%20High%20Availability/Scalability%20and%20Availability%203363839a13c2802782b2cfa7168777bd.md#gateway-load-balancer-gwlb)
  - [Connection Draining](./5.Scalability%20and%20High%20Availability/Scalability%20and%20Availability%203363839a13c2802782b2cfa7168777bd.md#connection-draining)
  - [Auto Scaling Group](./5.Scalability%20and%20High%20Availability/Scalability%20and%20Availability%203363839a13c2802782b2cfa7168777bd.md#auto-scaling-group)

### [RDS, Aurora, and ElastiCache](./6.RDS,Aurora,ElasticCache/README.md)

- [RDS, Aurora, and ElastiCache](./6.RDS,Aurora,ElasticCache/RDS,%20Aurora,%20and%20ElastiCache%203353839a13c28014af7ed6183405490b.md) - Managed databases, Aurora cluster features, backup and security controls, and caching patterns.
  - [RDS Overview](./6.RDS,Aurora,ElasticCache/RDS,%20Aurora,%20and%20ElastiCache%203353839a13c28014af7ed6183405490b.md#rds-overview)
  - [RDS Multi Replica vs Multi AZ](./6.RDS,Aurora,ElasticCache/RDS,%20Aurora,%20and%20ElastiCache%203353839a13c28014af7ed6183405490b.md#rds-multi-replica-vs-multi-az)
  - [Aurora](./6.RDS,Aurora,ElasticCache/RDS,%20Aurora,%20and%20ElastiCache%203353839a13c28014af7ed6183405490b.md#aurora)
  - [Aurora Advance](./6.RDS,Aurora,ElasticCache/RDS,%20Aurora,%20and%20ElastiCache%203353839a13c28014af7ed6183405490b.md#aurora-advance)
  - [RDS and Aurora Backup and Monitoring](./6.RDS,Aurora,ElasticCache/RDS,%20Aurora,%20and%20ElastiCache%203353839a13c28014af7ed6183405490b.md#rds-and-aurora-backup-and-monitoring)
  - [RDS and Aurora Security](./6.RDS,Aurora,ElasticCache/RDS,%20Aurora,%20and%20ElastiCache%203353839a13c28014af7ed6183405490b.md#rds-and-aurora-security)
  - [RDS Proxy](./6.RDS,Aurora,ElasticCache/RDS,%20Aurora,%20and%20ElastiCache%203353839a13c28014af7ed6183405490b.md#rds-proxy)
  - [ElastiCache](./6.RDS,Aurora,ElasticCache/RDS,%20Aurora,%20and%20ElastiCache%203353839a13c28014af7ed6183405490b.md#elasticache)
  - [ElastiCache Security](./6.RDS,Aurora,ElasticCache/RDS,%20Aurora,%20and%20ElastiCache%203353839a13c28014af7ed6183405490b.md#elasticache-security)

### [Route 53](./7.Route%2053/README.md)

- [Route 53](./7.Route%2053/Route%2053%203363839a13c28005aa13c7ba79ce339d.md) - DNS fundamentals, hosted zones, alias behavior, health checks, and routing policy comparisons.
  - [Record Types](./7.Route%2053/Route%2053%203363839a13c28005aa13c7ba79ce339d.md#record-types)
  - [Hosted Zones](./7.Route%2053/Route%2053%203363839a13c28005aa13c7ba79ce339d.md#hosted-zones)
  - [Record TTL](./7.Route%2053/Route%2053%203363839a13c28005aa13c7ba79ce339d.md#record-ttl)
  - [CNAME vs Alias](./7.Route%2053/Route%2053%203363839a13c28005aa13c7ba79ce339d.md#cname-vs-alias)
  - [Alias and Alias Targets Records](./7.Route%2053/Route%2053%203363839a13c28005aa13c7ba79ce339d.md#alias-and-alias-targets-records)
  - [Routing Policies](./7.Route%2053/Route%2053%203363839a13c28005aa13c7ba79ce339d.md#routing-policies)
  - [Simple](./7.Route%2053/Route%2053%203363839a13c28005aa13c7ba79ce339d.md#simple)
  - [Weighted Based Routing](./7.Route%2053/Route%2053%203363839a13c28005aa13c7ba79ce339d.md#weighted-based-routing)
  - [Latency Based Routing](./7.Route%2053/Route%2053%203363839a13c28005aa13c7ba79ce339d.md#latency-based-routing)
  - [Health Check](./7.Route%2053/Route%2053%203363839a13c28005aa13c7ba79ce339d.md#health-check)
  - [Geolocation Routing](./7.Route%2053/Route%2053%203363839a13c28005aa13c7ba79ce339d.md#geolocation-routing)
  - [Geoproximity Routing](./7.Route%2053/Route%2053%203363839a13c28005aa13c7ba79ce339d.md#geoproximity-routing)
  - [Geolocation vs Geoproximity](./7.Route%2053/Route%2053%203363839a13c28005aa13c7ba79ce339d.md#geolocation-vs-geoproximity)
  - [IP-based Routing](./7.Route%2053/Route%2053%203363839a13c28005aa13c7ba79ce339d.md#ip-based-routing)
  - [Multi-Value Answer Routing](./7.Route%2053/Route%2053%203363839a13c28005aa13c7ba79ce339d.md#multi-value-answer-routing)
  - [Failover Routing](./7.Route%2053/Route%2053%203363839a13c28005aa13c7ba79ce339d.md#failover-routing)

### [Golden AMI and Elastic Beanstalk](./8.Golden%20AMI%20and%20Elastic%20Beanstalk/README.md)

- [Golden AMI and Elastic Beanstalk](./8.Golden%20AMI%20and%20Elastic%20Beanstalk/Golden%20AMI%20and%20Elastic%20Beanstalk%203383839a13c2809e8cd0eb1200c8feb2.md) - Standardized AMI patterns for repeatable EC2 launches and Elastic Beanstalk for managed web application deployment.
  - [Golden AMI](./8.Golden%20AMI%20and%20Elastic%20Beanstalk/Golden%20AMI%20and%20Elastic%20Beanstalk%203383839a13c2809e8cd0eb1200c8feb2.md#golden-ami)
  - [Elastic Beanstalk](./8.Golden%20AMI%20and%20Elastic%20Beanstalk/Golden%20AMI%20and%20Elastic%20Beanstalk%203383839a13c2809e8cd0eb1200c8feb2.md#elastic-beanstalk)

### [Amazon S3](./9.Amazon%20S3/README.md)

- [Amazon S3](./9.Amazon%20S3/Amazon%20S3%203393839a13c28076955dfb269211a6fd.md) - Object storage concepts, lifecycle rules, storage class selection, access controls, replication models, static websites, and version protection.
  - [Overview](./9.Amazon%20S3/Amazon%20S3%203393839a13c28076955dfb269211a6fd.md#overview)
  - [S3 Lifecycle](./9.Amazon%20S3/Amazon%20S3%203393839a13c28076955dfb269211a6fd.md#s3-lifecycle)
  - [S3 Object Lock](./9.Amazon%20S3/Amazon%20S3%203393839a13c28076955dfb269211a6fd.md#s3-object-lock)
  - [S3 Object Replication](./9.Amazon%20S3/Amazon%20S3%203393839a13c28076955dfb269211a6fd.md#s3-object-replication)
  - [S3 Object Batch Operations](./9.Amazon%20S3/Amazon%20S3%203393839a13c28076955dfb269211a6fd.md#s3-object-batch-operations)
  - [S3 Block Public Access](./9.Amazon%20S3/Amazon%20S3%203393839a13c28076955dfb269211a6fd.md#s3-block-public-access)
  - [S3 IAM Access](./9.Amazon%20S3/Amazon%20S3%203393839a13c28076955dfb269211a6fd.md#s3-iam-access)
  - [S3 Bucket Policies](./9.Amazon%20S3/Amazon%20S3%203393839a13c28076955dfb269211a6fd.md#s3-bucket-policies)
  - [S3 Static Website](./9.Amazon%20S3/Amazon%20S3%203393839a13c28076955dfb269211a6fd.md#s3-static-website)
  - [S3 Versioning](./9.Amazon%20S3/Amazon%20S3%203393839a13c28076955dfb269211a6fd.md#s3-versioning)
  - [Live Replication](./9.Amazon%20S3/Amazon%20S3%203393839a13c28076955dfb269211a6fd.md#live-replication)
  - [On-Demand Replication](./9.Amazon%20S3/Amazon%20S3%203393839a13c28076955dfb269211a6fd.md#on-demand-replication)
  - [Cross-Region Replication (CRR)](./9.Amazon%20S3/Amazon%20S3%203393839a13c28076955dfb269211a6fd.md#cross-region-replication-crr)
  - [Same-Region Replication (SRR)](./9.Amazon%20S3/Amazon%20S3%203393839a13c28076955dfb269211a6fd.md#same-region-replication-srr)
  - [Frequently Accessed Storage Classes (S3 Standard)](./9.Amazon%20S3/Amazon%20S3%203393839a13c28076955dfb269211a6fd.md#frequently-accessed-storage-classes-s3-standard)
  - [Auto-Optimizing (S3 Intelligent-Tiering)](./9.Amazon%20S3/Amazon%20S3%203393839a13c28076955dfb269211a6fd.md#auto-optimizing-s3-intelligent-tiering)
  - [Infrequently Accessed (S3 Standard-IA & One Zone-IA)](./9.Amazon%20S3/Amazon%20S3%203393839a13c28076955dfb269211a6fd.md#infrequently-accessed-s3-standard-ia--one-zone-ia)
  - [Rarely Accessed (Glacier Classes)](./9.Amazon%20S3/Amazon%20S3%203393839a13c28076955dfb269211a6fd.md#rarely-accessed-glacier-classes)

### [Amazon S3 - Advance](./10.Amazon%20S3%20-%20Advance/README.md)

- [Amazon S3 - Advance](./10.Amazon%20S3%20-%20Advance/Amazon%20S3%20-%20Advance%203393839a13c2800fb947fd0df78a58d8.md) - Advanced S3 features for requester-paid access, event-driven integrations, and account-wide storage analytics.
  - [Requester Pay](./10.Amazon%20S3%20-%20Advance/Amazon%20S3%20-%20Advance%203393839a13c2800fb947fd0df78a58d8.md#requester-pay)
  - [Event Notification](./10.Amazon%20S3%20-%20Advance/Amazon%20S3%20-%20Advance%203393839a13c2800fb947fd0df78a58d8.md#event-notification)
  - [S3 Storage Lens](./10.Amazon%20S3%20-%20Advance/Amazon%20S3%20-%20Advance%203393839a13c2800fb947fd0df78a58d8.md#s3-storage-lens)
  - [Storage Lens Metrics](./10.Amazon%20S3%20-%20Advance/Amazon%20S3%20-%20Advance%203393839a13c2800fb947fd0df78a58d8.md#storage-lens-metrics)
  - [Storage Lens Metrics Categories](./10.Amazon%20S3%20-%20Advance/Amazon%20S3%20-%20Advance%203393839a13c2800fb947fd0df78a58d8.md#storage-lens-metrics-categories)
  - [Storage Lens Default Dashboard](./10.Amazon%20S3%20-%20Advance/Amazon%20S3%20-%20Advance%203393839a13c2800fb947fd0df78a58d8.md#storage-lens-default-dashboard)

### [Amazon S3 - Security](./11.Amazon%20S3%20-%20Security/README.md)

- [Amazon S3 - Security](./11.Amazon%20S3%20-%20Security/Amazon%20S3%20-%20Security%203393839a13c2801ab07fea5523976ec0.md) - S3 encryption options, browser and network access controls, deletion safeguards, auditing features, and access point patterns.
  - [S3 Server-Side Encryption (SSE)](./11.Amazon%20S3%20-%20Security/Amazon%20S3%20-%20Security%203393839a13c2801ab07fea5523976ec0.md#s3-server-side-encryption-sse)
  - [S3 Encryption with Amazon-Managed Key (SSE-S3)](./11.Amazon%20S3%20-%20Security/Amazon%20S3%20-%20Security%203393839a13c2801ab07fea5523976ec0.md#s3-encryption-with-amazon-managed-key-sse-s3)
  - [S3 Encryption with AWS KMS (SSE-KMS)](./11.Amazon%20S3%20-%20Security/Amazon%20S3%20-%20Security%203393839a13c2801ab07fea5523976ec0.md#s3-encryption-with-aws-kms-sse-kms)
  - [S3 Encryption with Customer-Provided Key (SSE-C)](./11.Amazon%20S3%20-%20Security/Amazon%20S3%20-%20Security%203393839a13c2801ab07fea5523976ec0.md#s3-encryption-with-customer-provided-key-sse-c)
  - [S3 Client-Side Encryption](./11.Amazon%20S3%20-%20Security/Amazon%20S3%20-%20Security%203393839a13c2801ab07fea5523976ec0.md#s3-client-side-encryption)
  - [S3 In-Transit Encryption](./11.Amazon%20S3%20-%20Security/Amazon%20S3%20-%20Security%203393839a13c2801ab07fea5523976ec0.md#s3-in-transit-encryption)
  - [S3 CORS](./11.Amazon%20S3%20-%20Security/Amazon%20S3%20-%20Security%203393839a13c2801ab07fea5523976ec0.md#s3-cors)
  - [S3 MFA Delete](./11.Amazon%20S3%20-%20Security/Amazon%20S3%20-%20Security%203393839a13c2801ab07fea5523976ec0.md#s3-mfa-delete)
  - [S3 Access Logs](./11.Amazon%20S3%20-%20Security/Amazon%20S3%20-%20Security%203393839a13c2801ab07fea5523976ec0.md#s3-access-logs)
  - [S3 Pre-signed URLs](./11.Amazon%20S3%20-%20Security/Amazon%20S3%20-%20Security%203393839a13c2801ab07fea5523976ec0.md#s3-pre-signed-urls)
  - [Glacier Vault Lock](./11.Amazon%20S3%20-%20Security/Amazon%20S3%20-%20Security%203393839a13c2801ab07fea5523976ec0.md#glacier-vault-lock)
  - [S3 Object Lock](./11.Amazon%20S3%20-%20Security/Amazon%20S3%20-%20Security%203393839a13c2801ab07fea5523976ec0.md#s3-object-lock)
  - [S3 Access Points](./11.Amazon%20S3%20-%20Security/Amazon%20S3%20-%20Security%203393839a13c2801ab07fea5523976ec0.md#s3-access-points)
  - [S3 Access Points - VPC Origin](./11.Amazon%20S3%20-%20Security/Amazon%20S3%20-%20Security%203393839a13c2801ab07fea5523976ec0.md#s3-access-points--vpc-origin)
  - [S3 Access Points - Lambda Functions (S3 Object Lambda)](./11.Amazon%20S3%20-%20Security/Amazon%20S3%20-%20Security%203393839a13c2801ab07fea5523976ec0.md#s3-access-points--lambda-functions-s3-object-lambda)

### [CloudFront and Global Accelerator](./12.CloudFront%20and%20Global%20Accelerator%20/README.md)

- [CloudFront and Global Accelerator](./12.CloudFront%20and%20Global%20Accelerator%20/CloudFront%20and%20Global%20Accelerator%2033a3839a13c28043967bc368b392e051.md) - CloudFront edge caching, geo restriction, cache invalidation, and Global Accelerator routing for low-latency multi-region applications.
  - [CloudFront](./12.CloudFront%20and%20Global%20Accelerator%20/CloudFront%20and%20Global%20Accelerator%2033a3839a13c28043967bc368b392e051.md#cloudfront)
  - [CloudFront Geo Restriction](./12.CloudFront%20and%20Global%20Accelerator%20/CloudFront%20and%20Global%20Accelerator%2033a3839a13c28043967bc368b392e051.md#cloudfront-geo-restriction)
  - [CloudFront cache invalidation](./12.CloudFront%20and%20Global%20Accelerator%20/CloudFront%20and%20Global%20Accelerator%2033a3839a13c28043967bc368b392e051.md#cloudfront-cache-invalidation)
  - [AWS Global Accelerator](./12.CloudFront%20and%20Global%20Accelerator%20/CloudFront%20and%20Global%20Accelerator%2033a3839a13c28043967bc368b392e051.md#aws-global-accelerator)
  - [CloudFront vs Global Accelerator](./12.CloudFront%20and%20Global%20Accelerator%20/CloudFront%20and%20Global%20Accelerator%2033a3839a13c28043967bc368b392e051.md#cloudfront-vs-global-accelerator)

### [AWS Storage Extra](./13.AWS%20Storage%20Extra/README.md)

- [AWS Storage Extras](./13.AWS%20Storage%20Extra/AWS%20Storage%20Extras%2033b3839a13c280f0a877ff4f783f5236.md) - Offline migration, edge locality, hybrid gateways, managed file systems, and transfer services for moving data into AWS.
  - [AWS Snowball](./13.AWS%20Storage%20Extra/AWS%20Storage%20Extras%2033b3839a13c280f0a877ff4f783f5236.md#aws-snowball)
  - [AWS Edge Computing](./13.AWS%20Storage%20Extra/AWS%20Storage%20Extras%2033b3839a13c280f0a877ff4f783f5236.md#aws-edge-computing)
  - [Snowball into Glacier](./13.AWS%20Storage%20Extra/AWS%20Storage%20Extras%2033b3839a13c280f0a877ff4f783f5236.md#snowball-into-glacier)
  - [Amazon FSx](./13.AWS%20Storage%20Extra/AWS%20Storage%20Extras%2033b3839a13c280f0a877ff4f783f5236.md#amazon-fsx)
  - [AWS Storage Gateway](./13.AWS%20Storage%20Extra/AWS%20Storage%20Extras%2033b3839a13c280f0a877ff4f783f5236.md#aws-storage-gateway)
  - [AWS File Gateway](./13.AWS%20Storage%20Extra/AWS%20Storage%20Extras%2033b3839a13c280f0a877ff4f783f5236.md#aws-file-gateway)
  - [AWS Volume Gateway](./13.AWS%20Storage%20Extra/AWS%20Storage%20Extras%2033b3839a13c280f0a877ff4f783f5236.md#aws-volume-gateway)
  - [AWS Tape Gateway](./13.AWS%20Storage%20Extra/AWS%20Storage%20Extras%2033b3839a13c280f0a877ff4f783f5236.md#aws-tape-gateway)
  - [AWS Transfer Family](./13.AWS%20Storage%20Extra/AWS%20Storage%20Extras%2033b3839a13c280f0a877ff4f783f5236.md#aws-transfer-family)
  - [AWS DataSync](./13.AWS%20Storage%20Extra/AWS%20Storage%20Extras%2033b3839a13c280f0a877ff4f783f5236.md#aws-datasync)
