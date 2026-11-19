# EASY-PEASY-AWS

## Table of Contents

1. [Introduction to the Course](#1-introduction-to-the-course)
2. [What You Will Learn](#2-what-you-will-learn)
3. [Overview of Topics](#3-overview-of-topics)
4. [What Is Virtualization?](#4-what-is-virtualization)
5. [What Is Cloud Computing?](#5-what-is-cloud-computing)
6. [What Is AWS?](#6-what-is-aws)
7. [AWS Account Setup](#7-aws-account-setup)
8. [AWS IAM Service](#8-aws-iam-service)
9. [AWS CLI Configuration](#9-aws-cli-configuration)
10. [AWS EC2 Service](#10-aws-ec2-service)
11. [AWS EBS Service](#11-aws-ebs-service)
12. [AWS AMI](#12-aws-ami)
13. [AWS ELB and Auto Scaling Group](#13-aws-elb-and-auto-scaling-group)
14. [AWS S3 Service](#14-aws-s3-service)
15. [AWS RDS Service](#15-aws-rds-service)
16. [AWS DynamoDB Service](#16-aws-dynamodb-service)
17. [AWS Lambda Function](#17-aws-lambda-function)
18. [AWS CloudFormation — Infrastructure as Code](#18-aws-cloudformation--infrastructure-as-code)
19. [AWS Route 53 Service](#19-aws-route-53-service)
20. [AWS CloudFront — CDN](#20-aws-cloudfront--cdn)
21. [AWS VPC](#21-aws-vpc)
22. [Creating a VPC](#22-creating-a-vpc)
23. [AWS Billing and Organizations](#23-aws-billing-and-organizations)
24. [AWS Amplify — Full-Stack Web Demo](#24-aws-amplify--full-stack-web-demo)
25. [AWS ECS](#25-aws-ecs)
26. [AWS EKS](#26-aws-eks)
27. [What Is Terraform?](#27-what-is-terraform)
28. [DNS Working — Practical Understanding](#28-dns-working--practical-understanding)
29. [SSL/TLS Certificates and Encryption](#29-ssltls-certificates-and-encryption)

---

## 1. Introduction to the Course

This course starts from the basics and gradually explains how applications work in the real world after development. Building a website is only one part of the process. A real application must also be hosted, made accessible through a domain, scaled for traffic, and delivered quickly to users.

The course combines cloud fundamentals with practical AWS services. It is intended to help a beginner understand the journey from a locally created website to an application that users can access over the internet.

**Key idea:** Development does not end when the code is written. Deployment, networking, scaling, storage, security, and cost management are also important.

[Back to contents](#table-of-contents) · [Next: What You Will Learn →](#2-what-you-will-learn)

## 2. What You Will Learn

Imagine that you have created a website. You now need to make it available to users.

The real-world journey includes:

1. **Hosting:** Put the website or application on infrastructure that can run it.
2. **Domain:** Give users a memorable name instead of making them remember an IP address.
3. **DNS:** Translate the domain name into the destination needed to reach the application.
4. **Scaling:** Handle increases in the number of users.
5. **Load balancing:** Distribute incoming requests across multiple servers.
6. **Global delivery:** Reduce loading delays for users in different parts of the world.
7. **Storage and databases:** Store files and application data.
8. **Security:** Control access and protect communication.
9. **Cost management:** Understand and monitor the resources being used.

Two common scaling approaches are:

- **Vertical scaling:** Increase the capacity of one machine, such as adding more CPU or memory.
- **Horizontal scaling:** Add more machines or instances and distribute work between them.

**Key idea:** A production application needs more than a server. It needs a complete infrastructure around it.

[← Previous](#1-introduction-to-the-course) · [Back to contents](#table-of-contents) · [Next →](#3-overview-of-topics)

## 3. Overview of Topics

The course follows a practical progression:

- First, understand virtualization and cloud computing.
- Next, learn AWS and set up an account.
- Learn identity and access management before creating resources.
- Use the command line and core compute services.
- Understand disks, machine images, load balancing, and automatic scaling.
- Learn object storage and managed databases.
- Explore serverless computing and infrastructure automation.
- Understand domains, content delivery, and virtual networking.
- Finish with deployment platforms, containers, infrastructure tools, DNS, and encryption.

This order is useful because later services build on earlier concepts. For example, understanding EC2 makes it easier to understand load balancing and Auto Scaling.

[← Previous](#2-what-you-will-learn) · [Back to contents](#table-of-contents) · [Next →](#4-what-is-virtualization)

## 4. What Is Virtualization?

**Virtualization** is the technique of creating virtual versions of computing resources, such as servers, operating systems, storage, or networks.

Instead of dedicating one physical computer to one workload, virtualization allows a physical machine to run multiple isolated virtual machines (VMs).

### Why is it useful?

- Better utilization of physical hardware.
- Multiple environments can run on one physical machine.
- Workloads can be isolated from one another.
- It is easier to create, manage, and remove virtual machines.

### Hypervisor

A **hypervisor** is the software layer that creates and manages virtual machines.

- **Type 1 (bare-metal):** Runs directly on the physical hardware.
- **Type 2 (hosted):** Runs as an application on top of a host operating system.

A VM generally has virtual CPU, memory, storage, and an operating system of its own.

**Simple example:** One powerful physical server can host several VMs, each running a different application or operating system.

[← Previous](#3-overview-of-topics) · [Back to contents](#table-of-contents) · [Next →](#5-what-is-cloud-computing)

## 5. What Is Cloud Computing?

**Cloud computing** means using computing resources over a network, usually the internet, instead of purchasing and maintaining all the physical infrastructure yourself.

You can provision resources such as virtual machines, storage, databases, and networking when required. You generally pay according to the resources and usage involved.

### Common cloud service models

| Model | What the provider supplies | What you generally manage |
|---|---|---|
| IaaS — Infrastructure as a Service | Virtual infrastructure such as compute, storage, and networking | Operating system, applications, and configuration |
| PaaS — Platform as a Service | A managed platform for building and running applications | Application code and application data |
| SaaS — Software as a Service | A complete software product | Mostly usage and configuration |

### Cloud deployment models

- **Public cloud:** Infrastructure is provided by a cloud provider and shared across customers with logical isolation.
- **Private cloud:** Cloud infrastructure dedicated to one organization.
- **Hybrid cloud:** A combination of private infrastructure and public cloud services.

### Why use cloud computing?

- Provision resources without buying physical servers.
- Scale resources as demand changes.
- Access services from different locations.
- Use managed services instead of maintaining every component yourself.

**Key idea:** Cloud computing changes infrastructure from something you must own and maintain into services you can provision and manage.

[← Previous](#4-what-is-virtualization) · [Back to contents](#table-of-contents) · [Next →](#6-what-is-aws)

## 6. What Is AWS?

**Amazon Web Services (AWS)** is Amazon's cloud platform. It provides services for compute, storage, databases, networking, security, application deployment, analytics, and more.

Examples used throughout these notes:

| Requirement | AWS service |
|---|---|
| Virtual server | EC2 |
| Block storage for a server | EBS |
| Object/file storage | S3 |
| Managed relational database | RDS |
| NoSQL database | DynamoDB |
| Run code without managing a server | Lambda |
| Manage users and permissions | IAM |
| Load balancing and traffic distribution | Elastic Load Balancing |
| DNS and domain routing | Route 53 |
| Content delivery network | CloudFront |
| Private cloud network | VPC |

### Regions and Availability Zones

- **Region:** A geographic area in which AWS operates infrastructure.
- **Availability Zone (AZ):** An isolated location within a Region, designed to provide independent infrastructure.
- **Local Zone:** An AWS infrastructure deployment that brings selected services closer to users in a particular metropolitan area.

Choosing a suitable Region can affect latency, service availability, compliance requirements, and cost. Using multiple Availability Zones can improve resilience.

### Cost awareness

AWS services can have different pricing models. Before creating resources, understand what is billed, check the pricing information, and use the AWS Pricing Calculator when estimating a design. Do not assume that every resource is free simply because an account is new.

[← Previous](#5-what-is-cloud-computing) · [Back to contents](#table-of-contents) · [Next →](#7-aws-account-setup)

## 7. AWS Account Setup

An AWS account gives you access to the AWS Management Console and AWS services.

A beginner should become familiar with:

- The **AWS Management Console**, which is the browser-based interface.
- The **Region selector**, which determines the Region in which regional resources are viewed or created.
- The **service search**, which helps locate AWS services.
- **Billing and cost information**, which helps track usage.

### Important account-safety practices

1. Protect the root user credentials.
2. Enable multi-factor authentication (MFA) for privileged access.
3. Avoid using the root user for everyday work.
4. Create IAM identities with only the permissions needed.
5. Set up billing alerts or budgets where appropriate.
6. Delete practice resources when they are no longer needed.

**Remember:** Stopping a resource does not always stop every related charge. Storage, snapshots, public IPs, and other associated resources may still incur costs.

[← Previous](#6-what-is-aws) · [Back to contents](#table-of-contents) · [Next →](#8-aws-iam-service)

## 8. AWS IAM Service

**IAM (Identity and Access Management)** controls who can access AWS and what actions they can perform.

IAM helps you apply the principle of **least privilege**: give an identity only the permissions required to do its job.

### Main IAM concepts

- **User:** An identity that represents a person or application requiring AWS access.
- **Group:** A collection of IAM users. Permissions can be assigned to the group.
- **Policy:** A JSON document that defines allowed or denied actions on resources.
- **Role:** An identity with permissions that can be assumed by a trusted user, service, or application.

### Policy basics

A policy commonly contains:

- `Effect`: `Allow` or `Deny`.
- `Action`: The operation, such as reading an object.
- `Resource`: The resource on which the action applies.
- Optional conditions that further restrict access.

A policy should be as narrow as practical. Avoid granting broad administrator permissions for routine tasks.

### User vs. role

A user is an identity with credentials. A role is assumed when a trusted identity or service needs temporary permissions. For example, an EC2 instance can use an IAM role to access an S3 bucket without storing long-lived access keys on the instance.

[← Previous](#7-aws-account-setup) · [Back to contents](#table-of-contents) · [Next →](#9-aws-cli-configuration)

## 9. AWS CLI Configuration

The **AWS Command Line Interface (AWS CLI)** lets you interact with AWS services from a terminal.

Instead of opening the console for every task, you can use commands and scripts to manage resources.

### Basic setup flow

1. Install the AWS CLI.
2. Create or obtain credentials for an appropriately permissioned identity.
3. Configure the CLI with the required credentials and default settings.
4. Select a default Region and output format.
5. Test the configuration with a simple read-only command.

A common configuration command is:

```bash
aws configure
```

The CLI may ask for an access key ID, secret access key, default Region, and output format. Treat credentials as secrets: never commit them to GitHub or paste them into public logs.

### Why use the CLI?

- Repeat tasks with commands.
- Automate workflows with scripts.
- Integrate AWS operations into development and deployment pipelines.
- Work efficiently when managing multiple resources.

For production workloads, prefer temporary credentials and IAM roles where possible instead of long-lived access keys.

[← Previous](#8-aws-iam-service) · [Back to contents](#table-of-contents) · [Next →](#10-aws-ec2-service)

## 10. AWS EC2 Service

**Amazon EC2 (Elastic Compute Cloud)** provides virtual servers called **instances**.

An EC2 instance can run an application, backend API, web server, or other workload. You choose its configuration based on the needs of your application.

### Important EC2 concepts

- **AMI:** The image/template used to launch an instance.
- **Instance type:** Defines the compute capacity, including CPU and memory characteristics.
- **Key pair:** Used for secure login to supported instance operating systems.
- **Security group:** Acts as a virtual firewall controlling inbound and outbound traffic.
- **Storage:** An instance can use attached EBS volumes and, depending on the instance, instance-store storage.
- **User data:** A way to pass startup scripts to an instance.
- **Elastic IP:** A static public IPv4 address that can be associated with a resource.

### Basic launch flow

1. Choose an AMI.
2. Select an instance type.
3. Configure network and subnet settings.
4. Configure storage.
5. Attach or create a security group.
6. Review and launch the instance.
7. Connect using the appropriate method and deploy the application.

### Vertical and horizontal scaling

- **Vertical:** Move to a larger instance type with more capacity.
- **Horizontal:** Run multiple instances and distribute requests between them.

**Security reminder:** Do not expose management ports to the entire internet unless there is a specific, controlled reason. Restrict access to trusted sources.

[← Previous](#9-aws-cli-configuration) · [Back to contents](#table-of-contents) · [Next →](#11-aws-ebs-service)

## 11. AWS EBS Service

**Amazon EBS (Elastic Block Store)** provides block storage volumes for use with EC2 instances.

Think of EBS as a virtual hard disk that you attach to an EC2 instance.

### Key concepts

- An EBS volume stores data independently of the instance's temporary lifecycle, subject to its configuration and deletion settings.
- Volumes are created in a particular Availability Zone.
- You can choose volume types based on performance and workload requirements.
- **Snapshots** are point-in-time backups of EBS volumes, stored by AWS.

### EBS vs. instance store

- **EBS:** Persistent block storage designed to remain available independently of the attached instance.
- **Instance store:** Storage physically attached to the host; its persistence depends on the instance type and lifecycle.

### When is EBS useful?

- Operating-system disks.
- Application data that needs block-level storage.
- Database storage on an EC2-hosted database.
- Volumes that need snapshots and recovery workflows.

**Remember:** A snapshot is a backup mechanism, not a replacement for a complete backup and disaster-recovery plan.

[← Previous](#10-aws-ec2-service) · [Back to contents](#table-of-contents) · [Next →](#12-aws-ami)

## 12. AWS AMI

An **Amazon Machine Image (AMI)** is a template used to launch EC2 instances.

An AMI contains the information required to create an instance, such as an operating system and configured software. Depending on how it is created, it can also include configuration and storage mappings.

### Why create a custom AMI?

Suppose you have configured an EC2 instance with:

- An operating system.
- Required packages.
- Runtime environments.
- Application dependencies.
- Common configuration.

You can create an AMI from that setup and use it to launch additional instances with a consistent starting configuration.

### AMI vs. EBS snapshot

| AMI | EBS snapshot |
|---|---|
| Used as an instance-launch template | A point-in-time backup of an EBS volume |
| Can include references to snapshots for its block devices | Represents volume data |
| Helps reproduce a configured server | Helps back up and restore storage |

[← Previous](#11-aws-ebs-service) · [Back to contents](#table-of-contents) · [Next →](#13-aws-elb-and-auto-scaling-group)

## 13. AWS ELB and Auto Scaling Group

A website may receive more requests than one EC2 instance can handle. Two important AWS concepts help with this problem: load balancing and automatic scaling.

### Elastic Load Balancing (ELB)

A **load balancer** receives incoming traffic and distributes it across registered targets, such as EC2 instances.

Benefits:

- Distributes traffic across multiple servers.
- Helps avoid sending all requests to one instance.
- Can perform health checks and route traffic to healthy targets.
- Supports highly available application architectures.

Common load balancer types include Application Load Balancer (ALB), Network Load Balancer (NLB), and Gateway Load Balancer (GWLB). Their capabilities differ, so choose based on the traffic and protocol requirements.

### Auto Scaling Group (ASG)

An **Auto Scaling Group** manages a group of EC2 instances and can adjust the number of instances according to configured policies and conditions.

Important settings include:

- **Minimum capacity:** Lowest number of instances to maintain.
- **Desired capacity:** Target number of instances.
- **Maximum capacity:** Upper limit for scaling.
- **Scaling policies:** Rules that determine when capacity should change.
- **Health checks:** Help identify unhealthy instances for replacement.

### How ELB and ASG work together

1. Users send requests to the load balancer.
2. The load balancer routes requests to healthy instances.
3. The Auto Scaling Group monitors capacity and scaling conditions.
4. When demand increases, the group can launch more instances.
5. When demand decreases, it can reduce capacity within the configured limits.

[← Previous](#12-aws-ami) · [Back to contents](#table-of-contents) · [Next →](#14-aws-s3-service)

## 14. AWS S3 Service

**Amazon S3 (Simple Storage Service)** is an object storage service. It is commonly used to store files such as images, videos, documents, backups, logs, and static website assets.

### Bucket and object

- **Bucket:** A container in which objects are stored. Bucket names must be globally unique within an AWS partition.
- **Object:** The data being stored, along with metadata and a key that identifies it inside the bucket.

Unlike a traditional file system, S3 is object storage. Folder-like views are generally created using key prefixes.

### Important S3 concepts

- **Bucket policies:** Resource-based policies that control access to a bucket and its objects.
- **Versioning:** Keeps multiple versions of an object, helping recover from accidental changes or deletions.
- **Storage classes:** Different classes are designed for different access patterns and cost/performance needs.
- **Lifecycle rules:** Automatically transition or expire objects according to configured rules.
- **Encryption:** Supports encryption at rest; secure access should also use HTTPS.
- **Static website hosting:** Can serve static website content from an S3 bucket when configured appropriately.

### Common storage-class idea

Frequently accessed data and rarely accessed archival data do not necessarily need the same storage class. Choose a class based on access frequency, retrieval needs, and cost.

### S3 use cases

- Store user-uploaded files.
- Keep application backups.
- Store static website assets.
- Store logs and exported data.
- Provide an origin for content delivery through CloudFront.

**Security reminder:** Do not make a bucket public just to make an application work. Prefer private buckets with controlled access, and use suitable policies or signed access mechanisms.

[← Previous](#13-aws-elb-and-auto-scaling-group) · [Back to contents](#table-of-contents) · [Next →](#15-aws-rds-service)

## 15. AWS RDS Service

**Amazon RDS (Relational Database Service)** is a managed service for relational databases.

A relational database stores structured data in tables, which contain rows and columns. Tables can be related to one another using keys.

RDS supports multiple database engines. The exact engine and features available depend on the AWS offering and configuration.

### Why use RDS?

When you run a database yourself on an EC2 instance, you are responsible for tasks such as installation, patching, backups, and much of the operational maintenance. RDS manages many routine database administration tasks, although you remain responsible for database design, access control, application queries, and configuration choices.

### Important concepts

- **DB instance:** The managed database environment.
- **DB engine:** The database software, such as MySQL or PostgreSQL.
- **Instance class:** The compute and memory capacity for the database.
- **Storage:** The allocated database storage and its performance characteristics.
- **Automated backups:** Backups managed according to the configured retention period.
- **Snapshots:** User-initiated backups that can be retained.
- **Multi-AZ deployment:** Uses another Availability Zone to improve availability and support failover.
- **Read replica:** A replicated database that can help scale read workloads; it is not the same thing as a Multi-AZ standby.

### RDS vs. database on EC2

| RDS | Database on EC2 |
|---|---|
| Managed database service | You manage the database software and much of its operations |
| Built-in options for backups and availability | You design and operate those mechanisms |
| Less infrastructure administration | More control over the environment |

[← Previous](#14-aws-s3-service) · [Back to contents](#table-of-contents) · [Next →](#16-aws-dynamodb-service)

## 16. AWS DynamoDB Service

**Amazon DynamoDB** is a fully managed NoSQL database service.

It is designed for applications that need predictable, low-latency access at scale. Unlike a relational database, DynamoDB does not require you to model all data as related tables with joins.

### Core concepts

- **Table:** A collection of items.
- **Item:** A single record in a table.
- **Attribute:** A field within an item.
- **Partition key:** The primary key attribute used to determine an item's partition.
- **Sort key:** An optional second key that allows related items to be organized and queried within a partition-key value.

### Primary key types

- **Simple primary key:** Partition key only.
- **Composite primary key:** Partition key plus sort key.

### When might you use DynamoDB?

- Applications that need fast key-value or document-style access.
- High-scale workloads with known access patterns.
- Serverless applications that need a managed database.
- Workloads where flexible item attributes are useful.

### RDS vs. DynamoDB

| RDS | DynamoDB |
|---|---|
| Relational database | NoSQL database |
| Tables with relational structure | Tables containing items and attributes |
| SQL queries and relational operations | Key-based access patterns and supported query operations |
| Useful for relational data and complex relationships | Useful for high-scale key-value/document access patterns |

**Design tip:** DynamoDB table design should begin with the application's access patterns. Do not assume that a relational schema can be copied directly into DynamoDB.

[← Previous](#15-aws-rds-service) · [Back to contents](#table-of-contents) · [Next →](#17-aws-lambda-function)

## 17. AWS Lambda Function

**AWS Lambda** is a serverless compute service. You provide code, and Lambda runs it in response to configured events without requiring you to manage the underlying servers.

“Serverless” does not mean that servers do not exist. It means the cloud provider manages the server infrastructure for you.

### How Lambda works

1. Write a function.
2. Configure its runtime and execution permissions.
3. Set up a trigger or invoke it through an integration.
4. Lambda runs the function when the event occurs.
5. Logs and monitoring help you understand its execution.

### Common triggers and integrations

A Lambda function can be invoked by events from services such as API Gateway, S3, EventBridge, and other AWS services.

### Important concepts

- **Function:** The code and configuration that Lambda executes.
- **Runtime:** The language environment used to run the function.
- **Handler:** The entry point invoked by the runtime.
- **Trigger:** An event source that causes the function to run.
- **Execution role:** IAM role that grants the function permission to access other AWS resources.
- **Timeout and memory:** Configuration that affects execution limits and available resources.
- **Concurrency:** The number of function invocations running at the same time.

### When is Lambda useful?

- Event-driven processing.
- Lightweight APIs and backend operations.
- Processing files after they are uploaded to S3.
- Scheduled jobs and automation.

[← Previous](#16-aws-dynamodb-service) · [Back to contents](#table-of-contents) · [Next →](#18-aws-cloudformation--infrastructure-as-code)

## 18. AWS CloudFormation — Infrastructure as Code

**Infrastructure as Code (IaC)** means defining infrastructure using files or code instead of creating every resource manually through a console.

**AWS CloudFormation** lets you describe AWS resources in a template. CloudFormation uses that template to create and manage a collection of resources called a **stack**.

### Why use CloudFormation?

- Re-create infrastructure consistently.
- Keep infrastructure definitions in version control.
- Reduce repetitive manual configuration.
- Review infrastructure changes before applying them.
- Manage related resources together.

### Basic workflow

1. Write a CloudFormation template.
2. Define the resources and their configuration.
3. Create a stack from the template.
4. CloudFormation provisions the resources.
5. Update the template and stack when the infrastructure needs to change.

### Important terms

- **Template:** The file describing the infrastructure.
- **Resource:** An AWS component defined in the template.
- **Stack:** A group of resources managed together.
- **Parameters:** Values supplied when creating or updating a stack.
- **Outputs:** Values returned after stack creation, such as a resource identifier or endpoint.

**Key idea:** Instead of documenting a sequence of manual clicks, describe the desired infrastructure so it can be created repeatedly.

[← Previous](#17-aws-lambda-function) · [Back to contents](#table-of-contents) · [Next →](#19-aws-route-53-service)

## 19. AWS Route 53 Service

**Amazon Route 53** is AWS's scalable DNS and domain-name service. It can register domains, host DNS records, and route user requests according to configured routing policies.

### DNS basics

People use domain names such as `example.com`, while network communication uses IP addresses. DNS helps translate a domain name into the records needed to locate a service.

### Hosted zones and records

- **Hosted zone:** A container for DNS records for a domain.
- **Record:** A DNS entry that describes how a name should resolve.
- **A record:** Maps a name to an IPv4 address.
- **AAAA record:** Maps a name to an IPv6 address.
- **CNAME record:** Maps one DNS name to another DNS name.
- **Alias record:** A Route 53 feature that can point a name to selected AWS resources.

### Routing policies

Route 53 supports different routing approaches, including simple, weighted, latency-based, failover, and geolocation/geoproximity-related routing options. The right policy depends on the application's availability and traffic requirements.

### Common use

A domain can be configured so that a user visiting `www.example.com` is directed to the appropriate application endpoint, such as a load balancer or a CloudFront distribution.

[← Previous](#18-aws-cloudformation--infrastructure-as-code) · [Back to contents](#table-of-contents) · [Next →](#20-aws-cloudfront--cdn)

## 20. AWS CloudFront — CDN

**Amazon CloudFront** is a Content Delivery Network (CDN). It delivers content to users through a global network of edge locations.

### Why use a CDN?

If every user had to download content from one distant origin server, users far away could experience higher latency. A CDN can cache eligible content closer to users and reduce repeated requests to the origin.

### Important terms

- **Distribution:** The CloudFront configuration that delivers content.
- **Origin:** The source from which CloudFront fetches content, such as an S3 bucket or an application server.
- **Edge location:** A location in the CloudFront network that serves content to users.
- **Cache behavior:** Rules that determine how requests are handled and cached.
- **TTL:** How long an object can remain cached, subject to cache policies and headers.
- **Invalidation:** A request to remove selected cached objects before their normal expiry.

### Typical request flow

1. A user requests a website asset.
2. DNS directs the user to the CloudFront distribution.
3. CloudFront checks whether the content is available in its cache.
4. If a valid cached copy exists, it can be served from the edge.
5. Otherwise, CloudFront fetches the content from the origin and may cache it.

### CloudFront and S3

A common architecture stores static files in a private S3 bucket and uses CloudFront to deliver them. Access can be restricted so users retrieve content through CloudFront rather than accessing the bucket directly.

[← Previous](#19-aws-route-53-service) · [Back to contents](#table-of-contents) · [Next →](#21-aws-vpc)

## 21. AWS VPC

**Amazon VPC (Virtual Private Cloud)** provides a logically isolated network in which you can launch AWS resources.

A VPC lets you define network addressing, subnets, routing, and traffic controls for your AWS resources.

### Main VPC components

- **CIDR block:** Defines the IP address range for the VPC.
- **Subnet:** A smaller IP range inside the VPC, associated with one Availability Zone.
- **Route table:** Contains rules that determine where network traffic is directed.
- **Internet Gateway (IGW):** Enables communication between a VPC and the internet when routing and security configuration allow it.
- **NAT Gateway:** Allows resources in a private subnet to initiate outbound internet connectivity without directly accepting unsolicited inbound internet connections.
- **Security Group:** A stateful virtual firewall associated with resources such as EC2 instances.
- **Network ACL (NACL):** A stateless network-level access control applied at the subnet boundary.

### Public vs. private subnet

A subnet is commonly described as **public** when its route table has a route to an Internet Gateway. A **private** subnet does not have a direct route to an Internet Gateway for general internet access.

A resource being in a public subnet does not automatically make it reachable from the internet. It also needs suitable addressing and security rules.

### Security group vs. Network ACL

| Security Group | Network ACL |
|---|---|
| Applied to supported network interfaces/resources | Applied at subnet level |
| Stateful | Stateless |
| Uses allow rules | Supports allow and deny rules |
| Return traffic is automatically considered | Return traffic must be allowed by rules |

[← Previous](#20-aws-cloudfront--cdn) · [Back to contents](#table-of-contents) · [Next →](#22-creating-a-vpc)

## 22. Creating a VPC

This section moves from VPC concepts to creating and connecting network components.

### Typical creation sequence

1. **Create a VPC:** Choose an IPv4 CIDR range that does not conflict with connected networks.
2. **Create subnets:** Divide the VPC address range into smaller ranges. Place subnets in the required Availability Zones.
3. **Create and attach an Internet Gateway:** This provides a path to and from the internet when routing permits.
4. **Create route tables:** Add routes that match the intended network design.
5. **Associate route tables with subnets:** Ensure each subnet uses the correct routes.
6. **Configure security groups and NACLs:** Allow only the traffic that is required.
7. **Add a NAT Gateway if needed:** A private subnet can use it for outbound internet access. A NAT Gateway has costs and should be planned carefully.
8. **Launch and test resources:** Confirm that resources can communicate only as intended.

### Example architecture

- A public subnet can contain an internet-facing load balancer.
- Private application subnets can contain application instances.
- Private database subnets can contain database resources.
- Route tables and security rules control communication between these layers.

**Important:** A secure network is not created merely by naming a subnet “private.” The route table, public IP assignment, gateways, and security rules determine actual connectivity.

[← Previous](#21-aws-vpc) · [Back to contents](#table-of-contents) · [Next →](#23-aws-billing-and-organizations)

## 23. AWS Billing and Organizations

Cloud resources can generate charges, so cost awareness is part of using AWS responsibly.

### Billing and cost concepts

- **Billing dashboard:** Shows account billing information.
- **Cost Explorer:** Helps analyze historical and current cost trends.
- **Budgets:** Lets you define cost or usage thresholds and receive alerts.
- **Free Tier / free offers:** Eligibility and limits depend on the account, service, and current AWS offer terms. Always check the current details.
- **Pricing Calculator:** Helps estimate the cost of a proposed architecture.

### AWS Organizations

**AWS Organizations** helps manage multiple AWS accounts centrally.

It can be used to:

- Group accounts into organizational units.
- Apply service control policies (SCPs) as permission guardrails.
- Consolidate billing.
- Separate environments or teams into different accounts.

### Practical cost checklist

- Check the Region before creating a resource.
- Choose an appropriate instance or database size.
- Stop or delete unused practice resources.
- Review EBS volumes, snapshots, public IPs, load balancers, and NAT Gateways.
- Set budget alerts.
- Review the bill rather than assuming a resource is free.

[← Previous](#22-creating-a-vpc) · [Back to contents](#table-of-contents) · [Next →](#24-aws-amplify--full-stack-web-demo)

## 24. AWS Amplify — Full-Stack Web Demo

**AWS Amplify** provides tools and managed services that help developers build and deploy web and mobile applications.

The course demonstrates deploying a website from a Git repository and connecting a custom domain.

### Typical deployment flow

1. Keep the website source code in a supported Git provider such as GitHub.
2. Connect the repository to Amplify.
3. Authorize the required repository access.
4. Select the repository and branch.
5. Configure build settings when needed.
6. Start the deployment.
7. Amplify builds and hosts the application.
8. Add a custom domain and configure the required DNS records.

### Why is this useful?

Without a managed deployment workflow, you may need to provision servers, configure a web server, upload build files, and manage deployment steps yourself. Amplify can simplify much of the build-and-host workflow for supported application types.

### Custom domain

A custom domain makes the deployed application accessible through a domain name you own. Domain setup involves DNS records and certificate configuration. DNS changes may take time to propagate.

**Remember:** The repository contains your source code; the hosting service builds and serves the deployed application.

[← Previous](#23-aws-billing-and-organizations) · [Back to contents](#table-of-contents) · [Next →](#25-aws-ecs)

## 25. AWS ECS

**Amazon ECS (Elastic Container Service)** is a managed container orchestration service. It helps run and manage containerized applications.

A container packages an application and its dependencies so it can run consistently across environments.

### Container basics

- **Image:** A packaged template used to create containers.
- **Container:** A running instance of an image.
- **Docker:** A widely used platform and toolset for building and running containers.
- **Registry:** A place to store and retrieve container images. Amazon ECR is AWS's container registry service.

### ECS concepts

- **Cluster:** A logical grouping where tasks and services run.
- **Task definition:** A blueprint describing one or more containers, their images, resources, ports, and configuration.
- **Task:** A running instantiation of a task definition.
- **Service:** Maintains the desired number of tasks and can integrate with load balancing.
- **Launch type / capacity provider:** Determines the infrastructure capacity used to run tasks.

### Common compute options

- **AWS Fargate:** Serverless compute for containers. AWS manages the underlying server infrastructure.
- **EC2 launch type:** Containers run on EC2 instances that you manage as part of the capacity.

### Typical workflow

1. Build a Docker image.
2. Push the image to a registry such as ECR.
3. Create an ECS task definition.
4. Run a task or create an ECS service.
5. Configure networking, IAM permissions, logging, and load balancing as required.

[← Previous](#24-aws-amplify--full-stack-web-demo) · [Back to contents](#table-of-contents) · [Next →](#26-aws-eks)

## 26. AWS EKS

**Amazon EKS (Elastic Kubernetes Service)** is AWS's managed Kubernetes service.

Kubernetes is a platform for orchestrating containers. It helps deploy, scale, and manage containerized applications across a cluster.

### Kubernetes concepts

- **Cluster:** The Kubernetes environment.
- **Control plane:** Coordinates and manages the cluster.
- **Node:** A machine that runs application workloads.
- **Pod:** The smallest deployable Kubernetes unit; it contains one or more containers.
- **Deployment:** Describes the desired state for a set of application Pods.
- **Service:** Provides a stable way to reach a set of Pods.
- **Namespace:** Helps logically separate resources within a cluster.

### EKS responsibility model

AWS manages the EKS control plane, while the compute capacity and workloads depend on the selected setup. Worker capacity can be provided through managed node groups, self-managed nodes, or supported serverless options such as Fargate.

### ECS vs. EKS

| ECS | EKS |
|---|---|
| AWS container orchestration service | Managed Kubernetes service |
| Uses ECS concepts such as tasks and services | Uses Kubernetes concepts such as Pods and Deployments |
| AWS-specific orchestration model | Kubernetes ecosystem and APIs |
| Often simpler when you want an AWS-native container platform | Useful when Kubernetes compatibility or its ecosystem is required |

[← Previous](#25-aws-ecs) · [Back to contents](#table-of-contents) · [Next →](#27-what-is-terraform)

## 27. What Is Terraform?

**Terraform** is an open-source Infrastructure as Code tool. It lets you define infrastructure using configuration files and manage it through a repeatable workflow.

Terraform can work with AWS and other infrastructure providers through provider plugins.

### Important Terraform concepts

- **Provider:** A plugin that allows Terraform to interact with a platform such as AWS.
- **Resource:** An infrastructure object Terraform manages.
- **Configuration:** The files describing the desired infrastructure.
- **State:** A record Terraform uses to map configuration to real infrastructure.
- **Plan:** A preview of the changes Terraform intends to make.
- **Apply:** Executes the planned changes.
- **Module:** A reusable collection of Terraform configuration.

### Basic workflow

```bash
terraform init
terraform plan
terraform apply
```

- `init` prepares the working directory and downloads required providers/modules.
- `plan` previews proposed changes.
- `apply` performs the changes after confirmation, depending on the command options.

### CloudFormation vs. Terraform

| CloudFormation | Terraform |
|---|---|
| AWS-native IaC service | Multi-provider IaC tool |
| Uses CloudFormation templates | Uses Terraform configuration language (HCL) |
| Manages AWS stacks | Uses Terraform state to track managed resources |

**Important:** Terraform state can contain sensitive information. Protect it, restrict access, and use a suitable remote state and locking setup for team workflows.

[← Previous](#26-aws-eks) · [Back to contents](#table-of-contents) · [Next →](#28-dns-working--practical-understanding)

## 28. DNS Working — Practical Understanding

**DNS (Domain Name System)** is the system that helps translate human-readable domain names into information that computers use to locate services.

For example, a user enters `www.example.com` into a browser. DNS resolution helps the browser discover where that name should direct the request.

### Simplified DNS lookup

1. The browser or operating system checks its local DNS cache.
2. If there is no usable cached answer, the request goes to a DNS resolver.
3. The resolver may contact DNS hierarchy servers to find the answer.
4. The authoritative DNS server provides the relevant record.
5. The resolver returns the answer and may cache it for the record's TTL.
6. The browser uses the result to connect to the destination.

### DNS hierarchy

- **Root DNS servers:** Direct resolvers toward the appropriate top-level domain servers.
- **TLD servers:** Handle domains such as `.com`, `.org`, or country-code domains.
- **Authoritative name servers:** Hold the DNS records for a domain.
- **Recursive resolver:** Performs the lookup process on behalf of the client and caches results.

### Common DNS record types

| Record | Purpose |
|---|---|
| A | Name to IPv4 address |
| AAAA | Name to IPv6 address |
| CNAME | Alias from one name to another name |
| MX | Mail exchange servers for a domain |
| NS | Name servers for a domain |
| TXT | Text data, often used for verification and email security |
| PTR | Reverse lookup from an IP address to a name |

### TTL

**Time to Live (TTL)** tells DNS resolvers how long a record can be cached. A change to a DNS record may not be visible everywhere immediately because resolvers can still have cached answers.

[← Previous](#27-what-is-terraform) · [Back to contents](#table-of-contents) · [Next →](#29-ssltls-certificates-and-encryption)

## 29. SSL/TLS Certificates and Encryption

When a browser communicates with a website over HTTPS, **TLS (Transport Layer Security)** helps protect the connection.

People often say “SSL certificate,” but modern HTTPS uses TLS. SSL is an older protocol and should not be used for new secure connections.

### What does TLS provide?

- **Encryption:** Helps prevent outsiders from reading the communication.
- **Integrity:** Helps detect whether data has been modified in transit.
- **Authentication:** Helps the browser verify that it is communicating with a server presenting a certificate valid for the requested domain.

### What is a digital certificate?

A TLS certificate binds a domain identity to a public key. It is issued by a Certificate Authority (CA) or can be issued through an appropriate certificate-management process.

A certificate includes information such as:

- The domain names it is valid for.
- The public key.
- The issuer.
- The validity period.
- The issuer's digital signature.

### Simplified HTTPS connection

1. The browser connects to the website using HTTPS.
2. The server presents its TLS certificate.
3. The browser checks whether the certificate is trusted, valid, and appropriate for the domain.
4. The browser and server negotiate cryptographic settings and establish shared session keys.
5. Application data is then exchanged over the encrypted connection.

### Public-key and symmetric encryption

- **Public-key cryptography:** Uses a public/private key pair and supports tasks such as authentication and key establishment.
- **Symmetric encryption:** Uses a shared secret key to encrypt and decrypt data efficiently.

TLS uses a combination of cryptographic techniques. It does not simply encrypt all website traffic using the certificate's public key.

### HTTPS

HTTPS is HTTP communication protected by TLS. It helps secure data exchanged between a browser and a website, but it does not by itself guarantee that the website is trustworthy or that the server/application is free from vulnerabilities.

[← Previous](#28-dns-working--practical-understanding) · [Back to contents](#table-of-contents) · [End of notes](#aws-zero-to-hero--beginner-friendly-notes)

---

## Quick Revision

| Topic | Remember this |
|---|---|
| Virtualization | Run multiple virtual machines on physical hardware |
| Cloud computing | Provision computing resources as services |
| IAM | Control identities and permissions |
| EC2 | Virtual compute instances |
| EBS | Persistent block storage for EC2 |
| AMI | Template for launching EC2 instances |
| ELB | Distributes incoming traffic |
| Auto Scaling | Adjusts the number of instances |
| S3 | Object storage |
| RDS | Managed relational database |
| DynamoDB | Managed NoSQL database |
| Lambda | Event-driven serverless compute |
| CloudFormation | AWS-native Infrastructure as Code |
| Route 53 | DNS and domain routing |
| CloudFront | Content delivery network |
| VPC | Isolated virtual network in AWS |
| Amplify | Build and deploy web/mobile applications |
| ECS | AWS container orchestration |
| EKS | Managed Kubernetes |
| Terraform | Multi-provider Infrastructure as Code |
| DNS | Resolves domain names |
| TLS | Protects data in transit |

## Suggested Learning Order

1. Understand Chapters 1–6 before creating cloud resources.
2. Learn IAM (Chapter 8) before using the CLI or launching services.
3. Practice EC2, EBS, and AMIs (Chapters 10–12).
4. Understand load balancing and scaling (Chapter 13).
5. Compare S3, RDS, DynamoDB, and Lambda (Chapters 14–17).
6. Learn VPC networking (Chapters 21–22) before designing a production deployment.
7. Explore containers and IaC (Chapters 25–27).
8. Finish by understanding DNS and TLS (Chapters 28–29).

## Official Documentation

- [AWS Documentation](https://docs.aws.amazon.com/)
- [AWS Getting Started](https://aws.amazon.com/getting-started/)
- [AWS Pricing Calculator](https://calculator.aws/)
- [AWS Well-Architected Framework](https://aws.amazon.com/architecture/well-architected/)

---

*Prepared as beginner-friendly English study notes following the chapter order and practical learning flow of the linked course. This is an independent learning summary, not official AWS documentation.*
