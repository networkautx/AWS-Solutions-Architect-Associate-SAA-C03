# AWS Foundations: EC2 and VPC Overview

This report provides a topic-based Markdown overview and a concise gist of the two sources:

- **AWS EC2 Foundations**
- **AWS VPC Architecture**

---

# 1. AWS EC2 (Elastic Compute Cloud)

## Key Topics

### Basic Concept
Renting virtual computers (instances) in the cloud with customizable specifications such as:
- CPU
- RAM
- Operating System
- Storage

### The Hypervisor Foundation

#### AWS Xen
- Legacy virtualization platform.
- Uses a privileged virtual machine (**Dom0**).
- Incurs a **virtualization tax**, resulting in additional overhead.

#### AWS Nitro
- Modern hardware-accelerated architecture.
- Uses dedicated **Nitro Cards**.
- Provides near bare-metal performance.
- Enables faster networking and better security.

### Key Components

#### Amazon Machine Images (AMIs)
Templates containing:
- Operating System
- Pre-installed software
- Configuration required to launch an EC2 instance

#### Instance Types

| Category | Purpose |
|----------|---------|
| General Purpose (T/M Family) | Balanced CPU, memory, and networking |
| Compute Optimized (C Family) | High-performance computing |
| Memory Optimized (R/X Family) | Memory-intensive applications |
| Accelerated Computing (G/P/F Family) | GPU and FPGA workloads |
| Storage Optimized (I/D/H Family) | High-speed local storage |

#### Purchase Options

- **On-Demand** – Pay only for what you use.
- **Savings Plans / Reserved Instances** – Lower pricing with long-term commitments.
- **Spot Instances** – Use spare AWS capacity at significant discounts.
- **Dedicated Hosts** – Physical server isolation for compliance or licensing.

### EC2 Instance Lifecycle

An EC2 instance transitions through the following states:

1. Pending
2. Running
3. Stopping
4. Stopped
5. Hibernated
6. Shutting-Down
7. Terminated

### EC2 Storage Options

#### Elastic Block Store (EBS)
- Network-attached block storage.
- Persistent storage.
- Locked to a single Availability Zone.

#### Instance Store
- Local SSD storage.
- Extremely fast.
- Temporary (ephemeral) storage.

#### Elastic File System (EFS)
- Managed Network File System (NFS).
- Shared by multiple EC2 instances.
- Automatically scales as storage grows.

---

## Gist

AWS EC2 provides the **fundamental compute infrastructure** of AWS. It is much more than renting virtual servers. Performance depends on the underlying **hypervisor architecture (Nitro vs. Xen)** and the selected **instance family**. AWS also offers flexible **pricing models** and multiple **storage solutions** to balance performance, persistence, and cost.

---

# 2. AWS VPC (Virtual Private Cloud)

## Key Topics

### Basic Concept

A **Virtual Private Cloud (VPC)** is a logically isolated private network within AWS.

Think of it as your own secure private section inside the AWS cloud where you control networking, security, and connectivity.

---

### AWS Service Scope

#### Global Services
- IAM
- Route 53
- CloudFront

#### Regional Services
- VPC
- S3
- RDS

#### Availability Zone (AZ) Services
- EC2
- Subnets
- EBS

---

### Networking Building Blocks

#### CIDR Blocks
- Define the IPv4 address range of the VPC.
- Supported IPv4 ranges: **/16 to /28**
- Optional IPv6 support through dual-stack networking.

#### Subnets

A VPC is divided into smaller networks called subnets.

##### Public Subnet
- Has a route to an Internet Gateway (IGW).
- Can communicate directly with the internet.

##### Private Subnet
- No direct internet access.
- Used for databases and backend services.

#### Route Tables
A collection of routing rules that determine where network traffic is directed.

---

### Connectivity Gateways

#### Internet Gateway (IGW)
- Enables inbound and outbound internet communication.
- Required for public subnets.

#### NAT Gateway
- Allows private subnet instances to access the internet.
- Prevents unsolicited inbound internet traffic.
- Commonly used for downloading updates and packages.

---

### VPC Security

#### Security Groups

Characteristics:
- Instance-level firewall
- Stateful
- Supports only Allow rules

#### Network ACLs (NACLs)

Characteristics:
- Subnet-level firewall
- Stateless
- Supports both Allow and Deny rules

---

### Default VPC

AWS automatically creates a **Default VPC** in every region.

Features:
- Pre-configured networking
- Public subnets
- Internet Gateway attached
- Ready for launching EC2 instances immediately

---

## Gist

AWS VPC enables organizations to create **secure, isolated, and highly configurable cloud networks**. Traffic is controlled using **Route Tables**, **Internet Gateways**, and **NAT Gateways**, while security is enforced using **Security Groups** and **Network ACLs**, providing multiple layers of network protection.

---
