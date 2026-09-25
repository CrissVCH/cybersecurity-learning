# AWS Cloud Practitioner Essentials

## Module 1 - Cloud Computing Fundamentals

### Key Concepts

- Cloud computing provides computing resources and services over the internet.
- AWS Global Infrastructure is organized into **Regions** and **Availability Zones**.
- A **Region** is a geographic area where AWS operates infrastructure.
- An **Availability Zone (AZ)** is an isolated physical location inside a Region.
- Using multiple Availability Zones improves **high availability** and **fault tolerance**.
- **Hybrid Cloud** combines infrastructure controlled by an organization with public cloud services such as AWS.

### Shared Responsibility Model

- **AWS:** Security **of** the cloud.
- **Customer:** Security **in** the cloud.

### Quick Review

**What is Hybrid Cloud?**  
Using private/on-premises infrastructure together with public cloud services.

**What benefit reduces physical infrastructure costs?**  
Stop spending money running and maintaining data centers.

**What does "Stop guessing capacity" mean?**  
Instead of predicting future hardware needs, cloud resources can scale according to demand.

**What are two benefits of AWS Global Infrastructure?**  
High availability and fault tolerance.

### Topics to Review

- Cloud computing basics
- Regions
- Availability Zones
- Hybrid Cloud
- Shared Responsibility Model

## Module 2 - Compute

### Amazon EC2

Amazon Elastic Compute Cloud (EC2) provides resizable virtual servers in AWS.

EC2 allows users to choose the amount of compute capacity needed and adjust resources according to workload requirements.

---

### EC2 Instance Types

EC2 instances are grouped into categories based on the type of workload they are optimized for.

#### General Purpose

Provide a balanced combination of:

- Compute
- Memory
- Networking

They are suitable for workloads that do not require specialization in one specific resource.

#### Compute Optimized

Designed for workloads that require high CPU performance.

They are appropriate when processing power is the primary requirement.

#### Memory Optimized

Designed for workloads that require large amounts of RAM.

They are useful when applications need to process or maintain large amounts of data in memory.

#### Storage Optimized

Designed for workloads that require high storage performance and high read/write throughput.

They are optimized for workloads where storage speed and I/O performance are important.

#### Accelerated Computing

Use specialized hardware accelerators such as GPUs.

They are designed for workloads that benefit from hardware acceleration rather than relying only on traditional CPU processing.

---

### EC2 Pricing Options

AWS provides different EC2 pricing models depending on workload characteristics, flexibility, and cost requirements.

#### On-Demand

Provides compute capacity without a long-term commitment.

Main characteristics:

- High flexibility
- Pay for usage
- No long-term commitment
- Suitable for unpredictable workloads

#### Reserved Instances

Provide discounted pricing in exchange for a longer-term commitment.

They are most useful when workloads are predictable and expected to run consistently for an extended period.

#### Savings Plans

Provide discounted compute pricing in exchange for committing to a consistent amount of compute usage for a period of time.

They are useful for predictable and steady-state workloads.

#### Spot Instances

Use unused AWS compute capacity at a significantly reduced price.

The main limitation is that AWS can interrupt Spot Instances when the capacity is needed elsewhere.

They are best suited for workloads that can tolerate interruptions.

---

### Steady-State Workloads

A steady-state workload has relatively consistent and predictable resource usage over time.

Because the required capacity is predictable, these workloads can benefit from long-term pricing options such as Savings Plans or Reserved Instances.

---

### EC2 Multi-Tenancy

AWS normally uses a multi-tenant infrastructure model.

Multiple customers may share the same underlying physical infrastructure while their workloads remain logically isolated from each other.

Isolation between customers is an important part of the AWS cloud architecture.

---

### Dedicated Hosts

Dedicated Hosts provide physical EC2 servers dedicated to a single customer.

They can be useful when organizations have specific requirements related to:

- Compliance
- Licensing
- Physical server isolation

They are different from the standard multi-tenant EC2 model.

---

### AWS Management Tools

AWS provides several ways to interact with services.

#### AWS Management Console

A web-based graphical user interface (GUI) used to manage AWS services.

#### AWS Command Line Interface (AWS CLI)

Allows users to manage AWS services through command-line commands.

#### AWS Software Development Kits (SDKs)

Allow applications and developers to interact with AWS services programmatically using supported programming languages.

---

### Amazon EC2 Auto Scaling

Amazon EC2 Auto Scaling automatically adjusts the number of EC2 instances according to application demand and configured metrics.

It can:

- Add instances when demand increases
- Remove instances when demand decreases
- Improve availability
- Improve performance
- Reduce unnecessary costs

Auto Scaling focuses on adjusting compute capacity.

---

### Elastic Load Balancing

Elastic Load Balancing (ELB) automatically distributes incoming application traffic across multiple resources.

Its main purposes are:

- Distribute traffic
- Improve availability
- Reduce overload on individual instances
- Support fault tolerance

---

### Auto Scaling and Elastic Load Balancing

Amazon EC2 Auto Scaling and Elastic Load Balancing complement each other.

- **Auto Scaling** controls the number of EC2 instances.
- **Elastic Load Balancing** distributes traffic across those instances.

Together, they help applications remain scalable and highly available.

---

### Loosely Coupled Architecture

A loosely coupled architecture reduces dependencies between system components.

Each component can operate more independently, which reduces the impact of failures.

Benefits include:

- Greater resilience
- Better fault tolerance
- Easier scalability
- Reduced dependency between components

If one component fails, other components may continue operating.

---

### Amazon Simple Notification Service (SNS)

Amazon SNS is a publish/subscribe messaging service.

It distributes messages from a publisher to one or more subscribers.

SNS is primarily used for:

- Notifications
- Message distribution
- Event-based communication

Its purpose is to deliver messages to interested subscribers when an event occurs.

---

### Amazon Simple Queue Service (SQS)

Amazon SQS is a message queuing service.

It stores messages until they are retrieved and processed by another application or service.

SQS helps decouple application components because producers and consumers do not need to communicate directly or operate at the same time.

Its main benefits include:

- Reliable message storage
- Decoupling components
- Improved resilience
- Asynchronous processing

---

### SNS vs SQS

Although both services are used for messaging, they serve different purposes.

#### SNS

- Publish/subscribe model
- Distributes messages
- Sends messages to multiple subscribers
- Focuses on notification and event delivery

#### SQS

- Message queue model
- Stores messages
- Messages remain available until processed
- Focuses on reliable asynchronous processing

SNS and SQS can also be used together in architectures that require both message distribution and message queuing.

---

### Key Takeaways

- Amazon EC2 provides scalable virtual compute capacity.
- EC2 instance types are optimized for different resource requirements.
- Compute Optimized focuses on CPU performance.
- Memory Optimized focuses on RAM.
- Storage Optimized focuses on storage performance and I/O.
- Accelerated Computing uses specialized hardware such as GPUs.
- On-Demand provides flexibility without long-term commitments.
- Reserved Instances and Savings Plans are suited for predictable workloads.
- Spot Instances offer lower costs but can be interrupted.
- AWS normally uses a multi-tenant infrastructure model.
- Dedicated Hosts provide physical servers dedicated to one customer.
- The AWS Management Console provides a graphical interface.
- AWS CLI provides command-line access.
- AWS SDKs provide programmatic access.
- EC2 Auto Scaling adjusts the number of instances according to demand.
- Elastic Load Balancing distributes traffic across resources.
- Loosely coupled architectures reduce dependencies between components.
- SNS distributes messages and notifications.
- SQS stores messages until they are processed.

# Module 4 - AWS Global Infrastructure

## Overview

This module focused on how AWS Global Infrastructure is organized and how businesses can use it to improve:

- High availability
- Fault tolerance
- Agility
- Elasticity
- Global performance

The main topics were:

- AWS Regions
- Availability Zones
- Edge locations
- Choosing a Region
- Infrastructure as Code
- AWS CloudFormation
- Ways to interact with AWS resources

---

## Choosing an AWS Region

Choosing the correct AWS Region depends on several factors.

### Compliance

Different countries and regions have different laws and regulations.

Organizations may need to choose specific AWS Regions to comply with requirements such as:

- Data protection laws
- Data residency requirements
- Industry regulations

Example:

The GDPR applies to personal data belonging to individuals in the European Union.

---

### Proximity

Regions closer to users can reduce latency.

Lower latency means:

- Faster response times
- Better application performance
- Better user experience

Choosing a Region far away from users can increase delay.

---

### Feature Availability

Not every AWS service or feature is available in every Region.

Before selecting a Region, it is important to verify whether the required AWS services are supported there.

Example:

AWS GovCloud Regions are designed for specific US government security and compliance requirements.

---

### Pricing

AWS pricing can vary between Regions.

Factors that may affect cost include:

- Regional operating costs
- Taxes
- Regulations
- Data sovereignty requirements

---

# AWS Global Infrastructure

## Regions

AWS Regions are geographical areas around the world.

Each Region:

- Contains multiple Availability Zones
- Provides redundant infrastructure
- Is separated from other Regions

AWS Regions help businesses deploy applications closer to users and improve resilience.

---

## Availability Zones

Availability Zones (AZs) are isolated locations inside an AWS Region.

Each AZ has its own:

- Power
- Networking
- Connectivity

Each Availability Zone consists of one or more data centers.

AWS Regions contain multiple Availability Zones.

Using multiple AZs can improve:

- High availability
- Fault tolerance
- Application reliability

---

## Multi-Region and Multi-AZ Architectures

AWS resources can be distributed across:

- Multiple Availability Zones
- Multiple Regions
- Or both

This creates redundancy.

If one location becomes unavailable, another location can continue serving users.

---

# High Availability, Agility and Elasticity

## High Availability

High availability means a system can continue operating even when individual components fail.

Example:

Deploying an application across multiple Availability Zones can reduce downtime if one AZ fails.

---

## Agility

Agility is the ability to quickly adapt to changing requirements.

AWS makes it possible to:

- Deploy resources quickly
- Modify infrastructure
- Introduce new services faster

---

## Elasticity

Elasticity is the ability to scale resources up or down based on demand.

Example:

```text
More users
    ↓
More AWS resources

Less demand
    ↓
Reduce resources
```

This allows infrastructure to adapt to workload changes.

---

# Edge Locations

AWS also operates edge locations around the world.

Edge locations are smaller AWS facilities designed to bring content and services closer to users.

They can cache content such as:

- Images
- Videos
- Web content
- Application resources

The goal is to reduce latency and improve transfer speed.

---

## Amazon CloudFront

Amazon CloudFront is an AWS Content Delivery Network (CDN).

CloudFront uses edge locations to deliver cached content closer to users.

Conceptually:

```text
Origin Server
     ↓
Edge Location
     ↓
User
```

Instead of retrieving content from a distant Region every time, users can receive cached content from a nearby edge location.

---

# Region vs Availability Zone vs Edge Location

## Region

A geographical area containing multiple Availability Zones.

## Availability Zone

An isolated location inside a Region containing one or more data centers.

## Edge Location

A location closer to end users used for services such as content delivery and caching.

Quick comparison:

```text
Region
 ├── Availability Zone
 ├── Availability Zone
 └── Availability Zone

Edge Locations
 └── Distributed closer to users globally
```

---

# Infrastructure as Code (IaC)

Infrastructure as Code means defining and managing infrastructure using code or configuration files instead of manually creating resources.

Benefits include:

- Automation
- Consistency
- Repeatability
- Faster deployment
- Easier scaling

---

# AWS CloudFormation

AWS CloudFormation is an Infrastructure as Code service.

CloudFormation allows infrastructure to be defined using templates.

A template describes the AWS resources that should be created.

Example resources include:

- EC2 instances
- Networking resources
- Storage resources
- Other AWS services

CloudFormation then provisions and configures those resources automatically.

Conceptually:

```text
CloudFormation Template
        ↓
AWS CloudFormation
        ↓
AWS Resources
```

This helps create infrastructure in a consistent and repeatable way.

---

# Ways to Interact with AWS

AWS resources are ultimately managed through AWS APIs.

AWS provides several ways to interact with these APIs.

---

## AWS Management Console

The AWS Management Console is a graphical web interface.

It is useful for:

- Beginners
- Manual configuration
- Billing dashboards
- Cost visualization
- Services with graphical interfaces

---

## AWS CLI

The AWS Command Line Interface allows AWS services to be managed from the terminal.

It can be useful for:

- Automation
- Scripts
- Repetitive tasks

Example use case:

Automating backups.

---

## AWS SDKs

AWS SDKs allow applications to interact with AWS services using programming languages.

They can be used to call AWS APIs directly from applications.

Example:

An application could use an AWS SDK to store user data in Amazon S3.

---

## Infrastructure as Code

Tools such as CloudFormation automate infrastructure creation and management.

Useful for:

- DevOps
- CI/CD pipelines
- Repeatable deployments
- Multi-Region environments
- Scaling infrastructure consistently

---

# Quick Comparison

| Method | Best Use |
|---|---|
| AWS Management Console | Manual management and beginners |
| AWS CLI | Command-line automation and scripting |
| AWS SDK | Integrating AWS services into applications |
| CloudFormation | Automated and repeatable infrastructure deployment |

---

# Important Concepts to Remember

### Choosing a Region

Consider:

```text
Compliance
Proximity
Feature availability
Pricing
```

### AWS Global Infrastructure

```text
Region
   ↓
Availability Zones
   ↓
Data Centers
```

Edge locations exist separately to bring services and content closer to users.

### Infrastructure Benefits

```text
High Availability
Agility
Elasticity
Fault Tolerance
```

### Infrastructure as Code

```text
Infrastructure defined as code
        ↓
Automated deployment
        ↓
Consistent environments
```

---

# Module 4 Summary

In this module, I learned:

- How AWS Regions are selected
- The difference between Regions, Availability Zones, and edge locations
- How multiple Regions and AZs improve availability and fault tolerance
- The difference between high availability, agility, and elasticity
- How edge locations reduce latency
- How CloudFront uses edge locations for content delivery
- What Infrastructure as Code means
- How AWS CloudFormation automates infrastructure deployment
- The difference between the AWS Console, CLI, SDKs, and CloudFormation