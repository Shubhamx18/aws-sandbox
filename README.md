<div align="center">

# ☁️ AWS Sandbox — Learning Repository

![AWS](https://img.shields.io/badge/AWS-Cloud-FF9900?style=for-the-badge&logo=amazonaws&logoColor=white)
![Status](https://img.shields.io/badge/Status-Active-brightgreen?style=for-the-badge)
![Days](https://img.shields.io/badge/Days%20Covered-13+-blue?style=for-the-badge)

> A structured, day-by-day AWS learning journey covering core cloud services with hands-on notes, commands, and topic slides.

</div>

---

## 📌 About This Repository

This repository documents my personal hands-on practice with AWS. It is organized into two main sections — **topic slide references** and **daily learning notes** — covering everything from cloud fundamentals to advanced services like CloudFormation, Lambda, and VPC.

---

## 📁 Repository Structure

```
aws-sandbox/
│
├── 📂 All Topic Slides/              
│   ├── 01 - What is cloud computing.pdf
│   ├── 02 - What is AWS An Overview.pdf
│   ├── 03 - What is AWS IAM.pdf
│   ├── 04 - AWS EC2.pdf
│   ├── 05 - AWS EBS.pdf
│   ├── 06 - AWS AMI.pdf
│   ├── 07 - ELB & ASG.pdf
│   ├── 08 - AWS S3.pdf
│   ├── 09 - AWS RDS.pdf
│   ├── 10 - AWS DynamoDB.pdf
│   ├── 11 - AWS Lambda.pdf
│   ├── 12 - AWS CloudFormation.pdf
│   ├── 13 - AWS Route 53.pdf
│   ├── 14 - AWS CloudFront.pdf
│   ├── AWS Amplify.pdf
│   ├── AWS ECS.pdf
│   ├── AWS EKS.pdf
│   └── What is Virtualization.pdf
│
└── 📂 Learnings/                   
    ├── Day-1-Introduction/
    ├── Day-2-IAM/
    ├── Day-3-EC2/
    ├── Day-4-AMI/
    ├── Day-5-ELB AND ASG/
    ├── Day-6-S3/
    ├── Day-7-RDS/
    ├── Day-8-DynamoDB/
    ├── Day-9-Lambda/
    ├── Day-10-CloudFormation/
    ├── Day-11-Route53/
    ├── Day-12-CloudFront/
    └── Day-13-VPC/
```

---

## 🗓️ Day-by-Day Learning Progress

| Day | Topic | Key Concepts |
|-----|-------|-------------|
| Day 1 | ☁️ Introduction | Cloud computing basics, AWS overview, virtualization |
| Day 2 | 🔐 IAM | Users, groups, roles, policies, permissions |
| Day 3 | 🖥️ EC2 | Instances, key pairs, security groups, SSH |
| Day 4 | 🖼️ AMI | Amazon Machine Images, custom AMIs, launch templates |
| Day 5 | ⚖️ ELB & ASG | Load balancers, auto scaling groups, high availability |
| Day 6 | 🪣 S3 | Buckets, objects, policies, static hosting |
| Day 7 | 🗄️ RDS | Managed databases, snapshots, multi-AZ |
| Day 8 | 📦 DynamoDB | NoSQL, tables, keys, on-demand capacity |
| Day 9 | λ Lambda | Serverless functions, triggers, event-driven |
| Day 10 | 🏗️ CloudFormation | Infrastructure as Code, stacks, templates |
| Day 11 | 🌐 Route 53 | DNS, hosted zones, routing policies |
| Day 12 | 🚀 CloudFront | CDN, distributions, edge locations |
| Day 13 | 🔌 VPC | Virtual networks, subnets, IGW, security groups |

---

## 🛠️ AWS Services Covered

<details>
<summary><b>🔐 IAM — Identity and Access Management</b></summary>

- Creating users, groups, and roles
- Attaching managed and inline policies
- MFA setup and best practices
- Principle of least privilege

</details>

<details>
<summary><b>🖥️ EC2 — Elastic Compute Cloud</b></summary>

- Launching and connecting to instances via SSH
- Security groups and key pairs
- Instance types and pricing models
- Start, stop, and terminate via CLI

</details>

<details>
<summary><b>🖼️ AMI — Amazon Machine Images</b></summary>

- Creating custom AMIs from instances
- Launching instances from AMIs
- AMI sharing and copying across regions

</details>

<details>
<summary><b>⚖️ ELB & ASG — Load Balancer & Auto Scaling</b></summary>

- Application, Network, and Gateway Load Balancers
- Target groups and health checks
- Auto Scaling policies and launch configurations

</details>

<details>
<summary><b>🪣 S3 — Simple Storage Service</b></summary>

- Buckets, objects, prefixes
- Bucket policies, ACLs, versioning
- Static website hosting and lifecycle rules

</details>

<details>
<summary><b>🗄️ RDS — Relational Database Service</b></summary>

- Managed MySQL, PostgreSQL, and more
- Snapshots, backups, multi-AZ deployments
- Read replicas and scaling

</details>

<details>
<summary><b>📦 DynamoDB</b></summary>

- NoSQL tables, partition keys, sort keys
- On-demand vs provisioned capacity
- Global tables and streams

</details>

<details>
<summary><b>λ Lambda</b></summary>

- Serverless function creation and deployment
- Event-driven triggers (S3, API Gateway, etc.)
- Execution roles and environment variables

</details>

<details>
<summary><b>🏗️ CloudFormation</b></summary>

- Writing CloudFormation templates (YAML/JSON)
- Creating and managing stacks
- Parameters, outputs, and cross-stack references

</details>

<details>
<summary><b>🌐 Route 53</b></summary>

- Hosted zones and DNS records
- Routing policies (simple, weighted, latency, failover)
- Domain registration

</details>

<details>
<summary><b>🚀 CloudFront</b></summary>

- CDN distributions and origin setup
- Edge locations and caching behavior
- HTTPS with ACM certificates

</details>

<details>
<summary><b>🔌 VPC — Virtual Private Cloud</b></summary>

- Subnets (public & private), route tables
- Internet Gateway, NAT Gateway
- Security groups vs NACLs

</details>

---

## 🚀 Getting Started

### Prerequisites

- [ ] An active [AWS Account](https://aws.amazon.com/free/) (Free Tier works)
- [ ] [AWS CLI v2](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html) installed
- [ ] IAM user with programmatic access

### Clone the Repository

```bash
git clone https://github.com/Shubhamx18/aws-sandbox.git
cd aws-sandbox
```

### Configure AWS CLI

```bash
aws configure
# AWS Access Key ID:     YOUR_ACCESS_KEY
# AWS Secret Access Key: YOUR_SECRET_KEY
# Default region name:   us-east-1
# Default output format: json
```

> 💡 Verify setup: `aws sts get-caller-identity`

---

## 📚 Resources

| Resource | Link |
|----------|------|
| 📖 AWS Docs | [docs.aws.amazon.com](https://docs.aws.amazon.com/) |
| 💻 AWS CLI Reference | [CLI v2 Docs](https://awscli.amazonaws.com/v2/documentation/api/latest/index.html) |
| 🆓 AWS Free Tier | [aws.amazon.com/free](https://aws.amazon.com/free/) |
| 🎓 AWS Skill Builder | [skillbuilder.aws](https://skillbuilder.aws/) |

---

## 🔒 Security Reminder

> ⚠️ **Never commit AWS credentials, `.pem` files, or secret keys to this repository.**

```bash
# Add to .gitignore
echo ".env" >> .gitignore
echo "*.pem" >> .gitignore
echo "credentials" >> .gitignore
```

---

## 👤 Author

<div align="center">

**Shubham**
[![GitHub](https://img.shields.io/badge/GitHub-Shubhamx18-181717?style=for-the-badge&logo=github)](https://github.com/Shubhamx18)

*Learning AWS one day at a time ☁️*

⭐ **Star this repo if it helped you!** ⭐

</div>
