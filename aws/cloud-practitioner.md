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