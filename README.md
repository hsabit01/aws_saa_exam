# AWS SAA Exam Notes

Study notes for AWS Solutions Architect Associate topics, organized into chapter folders. Each chapter has a local `README.md` with direct links to the note file and its main review sections.

## Start Here

1. [IAM](./1.IAM/README.md) - Identity, policies, service roles, and account access review tools.
2. [EC2 Basics](./2.EC2%20Basics/README.md) - Core compute concepts, instance sizing, security groups, access, and purchase options.
3. [EC2 Placement Groups and Networking](./3.EC2%20Placement%20Groups%20and%20Networking/README.md) - Elastic IPs, placement strategies, ENIs, and hibernation behavior.
4. [EC2 Storage](./4.EC2%20Storage/README.md) - EBS, snapshots, AMIs, EFS, and storage tradeoffs.
5. [Scalability and High Availability](./5.Scalability%20and%20High%20Availability/README.md) - Load balancing, traffic distribution, and Auto Scaling patterns.
6. [RDS, Aurora, and ElastiCache](./6.RDS,Aurora,ElasticCache/README.md) - Managed relational databases, Aurora features, database protection, and caching patterns.

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
