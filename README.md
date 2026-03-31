# AWS SAA Exam Notes

Study notes for core AWS Solutions Architect Associate topics, organized into numbered chapters. Each chapter folder includes a local `README.md` with direct links to the note file and its main sections.

## Reading Order

1. [IAM](./1-iam/README.md) - Identity, permissions, roles, and IAM review tools.
2. [EC2 Basics](./2-ec2-basics/README.md) - Compute fundamentals, sizing, security groups, access, and purchase options.
3. [EC2 Placement Groups and Networking](./3-ec2-placement-groups-networking/README.md) - Elastic IPs, placement strategies, ENIs, and hibernation.
4. [EC2 Storage](./4-ec2-storage/README.md) - EBS, snapshots, AMIs, EFS, and storage tradeoffs.
5. [Scalability and Availability](./5-scalability-availability/README.md) - High availability, load balancers, and Auto Scaling patterns.

## Documentation Map

### [1-iam](./1-iam/README.md)

- [IAM](./1-iam/IAM%203343839a13c2802a9b75f1cc42a5855c.md) - Covers IAM identities, permission models, service roles, and account review tools.
  - [IAM users, groups, and policies](./1-iam/IAM%203343839a13c2802a9b75f1cc42a5855c.md#iam-users-groups-and-policies)
  - [IAM Roles for services](./1-iam/IAM%203343839a13c2802a9b75f1cc42a5855c.md#iam-roles-for-services)
  - [IAM Credential Report](./1-iam/IAM%203343839a13c2802a9b75f1cc42a5855c.md#iam-credential-report)
  - [IAM Access Advisor](./1-iam/IAM%203343839a13c2802a9b75f1cc42a5855c.md#iam-access-advisor-service-last-accessed-data)

### [2-ec2-basics](./2-ec2-basics/README.md)

- [EC2 Basics](./2-ec2-basics/EC2%20Basics%203323839a13c2802fbddbfa38a1a57df3.md) - Introduces EC2 fundamentals, sizing, instance types, access methods, and purchase options.
  - [EC2 Sizing & Configuration Options](./2-ec2-basics/EC2%20Basics%203323839a13c2802fbddbfa38a1a57df3.md#ec2-sizing--configuration-options)
  - [EC2 Instance Types](./2-ec2-basics/EC2%20Basics%203323839a13c2802fbddbfa38a1a57df3.md#ec2-instance-types)
  - [Security Group](./2-ec2-basics/EC2%20Basics%203323839a13c2802fbddbfa38a1a57df3.md#security-group)
  - [EC2 SSH Connection](./2-ec2-basics/EC2%20Basics%203323839a13c2802fbddbfa38a1a57df3.md#ec2-ssh-connection)
  - [EC2 IAM Role](./2-ec2-basics/EC2%20Basics%203323839a13c2802fbddbfa38a1a57df3.md#ec2-iam-role)
  - [EC2 Purchase Options](./2-ec2-basics/EC2%20Basics%203323839a13c2802fbddbfa38a1a57df3.md#ec2-purchase-options)

### [3-ec2-placement-groups-networking](./3-ec2-placement-groups-networking/README.md)

- [EC2 Placement Groups & Networking](./3-ec2-placement-groups-networking/EC2%20Placement%20Groups%20%26%20Networking%203343839a13c280d08bc0d8937c13ee93.md) - Summarizes Elastic IPs, placement group strategies, ENIs, and EC2 hibernation.
  - [Elastic IP](./3-ec2-placement-groups-networking/EC2%20Placement%20Groups%20%26%20Networking%203343839a13c280d08bc0d8937c13ee93.md#elastic-ip)
  - [Placement Groups](./3-ec2-placement-groups-networking/EC2%20Placement%20Groups%20%26%20Networking%203343839a13c280d08bc0d8937c13ee93.md#placement-groups)
  - [Cluster Placement Group](./3-ec2-placement-groups-networking/EC2%20Placement%20Groups%20%26%20Networking%203343839a13c280d08bc0d8937c13ee93.md#cluster-placement-group)
  - [Spread Placement Group](./3-ec2-placement-groups-networking/EC2%20Placement%20Groups%20%26%20Networking%203343839a13c280d08bc0d8937c13ee93.md#spread-placement-group)
  - [Partition Placement Group](./3-ec2-placement-groups-networking/EC2%20Placement%20Groups%20%26%20Networking%203343839a13c280d08bc0d8937c13ee93.md#partition-placement-group)
  - [Elastic Network Interface (ENI)](./3-ec2-placement-groups-networking/EC2%20Placement%20Groups%20%26%20Networking%203343839a13c280d08bc0d8937c13ee93.md#elastic-network-interface-eni)
  - [EC2 Hibernate](./3-ec2-placement-groups-networking/EC2%20Placement%20Groups%20%26%20Networking%203343839a13c280d08bc0d8937c13ee93.md#ec2-hibernate)

### [4-ec2-storage](./4-ec2-storage/README.md)

- [EC2 Storage](./4-ec2-storage/EC2%20Storage%203343839a13c28058b2c2de7c478889cb.md) - Explains EBS volumes, snapshots, AMIs, EFS, lifecycle options, and storage selection tradeoffs.
  - [Elastic Storage Block (ESB)](./4-ec2-storage/EC2%20Storage%203343839a13c28058b2c2de7c478889cb.md#elastic-storage-block-esb)
  - [EBS Snapshot](./4-ec2-storage/EC2%20Storage%203343839a13c28058b2c2de7c478889cb.md#ebs-snapshot)
  - [EBS Snapshot Features](./4-ec2-storage/EC2%20Storage%203343839a13c28058b2c2de7c478889cb.md#ebs-snapshot-features)
  - [Amazon Machine Image (AMI)](./4-ec2-storage/EC2%20Storage%203343839a13c28058b2c2de7c478889cb.md#amazon-machine-image-ami)
  - [EBS Volume Types](./4-ec2-storage/EC2%20Storage%203343839a13c28058b2c2de7c478889cb.md#ebs-volume-types)
  - [EBS Multi-Attach](./4-ec2-storage/EC2%20Storage%203343839a13c28058b2c2de7c478889cb.md#ebs-multi-attach)
  - [Elastic File System (EFS)](./4-ec2-storage/EC2%20Storage%203343839a13c28058b2c2de7c478889cb.md#elastic-file-system-efs)
  - [EFS Use Cases and Access](./4-ec2-storage/EC2%20Storage%203343839a13c28058b2c2de7c478889cb.md#efs-use-cases-and-access)
  - [EFS Performance and Throughput Modes](./4-ec2-storage/EC2%20Storage%203343839a13c28058b2c2de7c478889cb.md#efs-performance-and-throughput-modes)
  - [EFS Storage Classes and Lifecycle Tiers](./4-ec2-storage/EC2%20Storage%203343839a13c28058b2c2de7c478889cb.md#efs-storage-classes-and-lifecycle-tiers)
  - [EBS vs EFS vs Instance Store](./4-ec2-storage/EC2%20Storage%203343839a13c28058b2c2de7c478889cb.md#ebs-vs-efs-vs-instance-store)

### [5-scalability-availability](./5-scalability-availability/README.md)

- [Scalability and Availability](./5-scalability-availability/Scalability%20and%20Availability%203323839a13c280be8b87e193a51d496e.md) - Reviews high availability, scalability patterns, load balancer choices, SSL handling, and Auto Scaling groups.
  - [High Availability](./5-scalability-availability/Scalability%20and%20Availability%203323839a13c280be8b87e193a51d496e.md#high-availability)
  - [Scalability](./5-scalability-availability/Scalability%20and%20Availability%203323839a13c280be8b87e193a51d496e.md#scalability)
  - [Elastic Load Balancer](./5-scalability-availability/Scalability%20and%20Availability%203323839a13c280be8b87e193a51d496e.md#elastic-load-balancer)
  - [Application Load Balancer (ALB)](./5-scalability-availability/Scalability%20and%20Availability%203323839a13c280be8b87e193a51d496e.md#application-load-balancer-alb)
  - [Network Load Balancer (NLB)](./5-scalability-availability/Scalability%20and%20Availability%203323839a13c280be8b87e193a51d496e.md#network-load-balancer-nlb)
  - [Gateway Load Balancer](./5-scalability-availability/Scalability%20and%20Availability%203323839a13c280be8b87e193a51d496e.md#gateway-load-balancer)
  - [Load Balancer - SSL Certificate](./5-scalability-availability/Scalability%20and%20Availability%203323839a13c280be8b87e193a51d496e.md#load-balancer---ssl-certificate)
  - [Connection Draining](./5-scalability-availability/Scalability%20and%20Availability%203323839a13c280be8b87e193a51d496e.md#connection-draining)
  - [Auto Scaling Group](./5-scalability-availability/Scalability%20and%20Availability%203323839a13c280be8b87e193a51d496e.md#auto-scaling-group)
