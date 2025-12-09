---
title: "Week 1 Worklog"
date: ""
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---


### Week 1 Objectives:
* Get acquainted with the members of the **First Cloud Journey (FCJ)** program and familiarize yourself with the rules and regulations of the internship unit.
* Gain a solid understanding of core cloud computing concepts and the AWS service ecosystem, including Compute, Storage, Networking, Databases, and Security.
* Hands-on practice in creating and managing an AWS Free Tier account using best practices: setting up IAM Users, Groups, and Roles; limiting root account usage; and configuring Budgets for cost monitoring.
* Work with both the AWS Management Console and AWS CLI to manage resources, while building basic scripting skills for automation.
* Learn cost optimization strategies such as Spot Instances, the AWS Pricing Calculator, and AWS Budgets/Cost Explorer.
* Explore Serverless architecture through AWS Lambda and DynamoDB, and use Hugo to build and deploy static workshop websites.
* Study and practice essential AWS Networking components, including VPC, Subnets, Route Tables, Security Groups, NACLs, Internet Gateway, NAT Gateway, VPC Endpoints, VPC Flow Logs, VPN, Direct Connect, and Elastic Load Balancing.

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 2 | - Learn to draw cloud system workflows using AWS architecture icons <br> - Study Cloud Computing Module 01: AWS overview, policies, services and AWS Support <br> - Create AWS Free Tier account, Admin group and Admin User <br> - Install & configure AWS CLI  - Learn how to request AWS Support assistance | 08/11/2025 | 08/11/2025 | <https://000001.awsstudygroup.com/> <br> https://000009.awsstudygroup.com/ |
| 3   | - Learn Markdown writing and website creation with Hugo  <br>- Complete Module 1 labs for hands-on practice <br> - Study Spot Instances for cost optimization (~90% cheaper but interruptible) <br> - Understand serverless concepts (Lambda, DynamoDB) <br> - Use AWS Pricing Calculator to estimate and compare costs by Region <br> - Review key networking services: VPC, Subnets, Route Tables, Security Groups, NACLs, VPC Peering, Transit Gateway, VPN, Direct Connect, ELB | 08/12/2025 | 08/12/2025 | https://van-hoang-kha.github.io/ |
| 4   | <br> - Set up IAM User, Polices, Group, and Role instead of using the root account <br> - Configure Budget/Cost Budget to monitor monthly credits - Review VPC basics: public/private subnets, Route Tables, IGW, NAT Gateway <br> - Learn ENI (network interfaces) and Elastic IP usage <br> - Study VPC Endpoints (Gateway vs Interface) <br> - Compare Security Groups (stateful) and NACLs (stateless) <br> - Enable and review VPC Flow Logs (CloudWatch / S3) <br> - Understand VPC Peering and its common limitations <br> - Learn Transit Gateway and how Attachments connect networks <br> - Complete Module 02 — 01 | 10/09/2025 | 10/09/2025 | https://cloudjourney.awsstudygroup.com/ 
| 5 | - Learn AWS Direct Connect (Dedicated & Hosted) <br>&emsp; + Use cases and connectivity models <br> - Understand Site-to-Site VPN with Virtual Private Gateway & Customer Gateway <br> - Review Client VPN fundamentals <br> - Study Elastic Load Balancing (ALB, NLB, CLB, Global LB) <br>&emsp; + Health checks, sticky sessions, access logs <br>&emsp; + Routing rules and target types <br> - Complete Module 02 - 03 | 11/09/2025 | 11/09/2025 | https://cloudjourney.awsstudygroup.com/ |
| 6 | - Consolidate key topics: IAM, VPC, Subnets, Security, ELB, etc. <br> &emsp; + Review architecture flow and dependencies <br> - Practice advanced VPC networking labs <br>- Learn Route 53 Resolver for hybrid DNS setups <br> - Configure and test VPC Peering connections | 12/09/2025 | 14/09/2025 | [My Notes on AWS Services](https://www.notion.so/i-n-to-n-m-m-y-26a4c2b6beb680beb5eaf9d9f48b8b00?source=copy_link)|


### Week 1 – AWS Learning Summary

### 1. Core AWS Understanding
- Gained a clear overview of AWS and its primary service categories:
  - Compute, Storage, Networking, Databases, Security, etc.
- Learned the differences between:
  - **AWS Management Console** (web UI)
  - **AWS CLI** (command-line access)
  - **AWS SDK** (programmatic interaction)

### 2. Account Setup & Free Tier Work
- Created and configured an AWS Free Tier account.
- Installed and set up AWS CLI with:
  - Access Key
  - Secret Key
  - Default Region
- Practiced operating AWS resources using both **Console** and **CLI**.

### 3. CLI Hands-On Experience
- Verified account identity and CLI configuration.
- Listed active AWS Regions.
- Worked with EC2:
  - Viewed instances
  - Generated and managed key pairs
  - Checked running services
- Started writing simple automation scripts for repeated commands.

### 4. IAM (Identity & Access Management)
- Created and organized IAM Users, Groups, and Roles.
- Attached both managed and inline policies.
- Practiced signing in as IAM User and switching roles.
- Understood why daily root account usage is not recommended.

### 5. Cost Management & Optimization
- Learned how **Spot Instances** work (high savings, interruptible).
- Created Budgets and Free Tier usage monitoring.
- Used AWS Pricing Calculator to compare cost differences by region.

### 6. Serverless & Workshop Tools
- Learned the fundamentals of Serverless services: Lambda, DynamoDB, and more.
- Practiced using **Hugo** to build static workshop pages.

### 7. Networking Fundamentals
- Understood VPC (Virtual Private Cloud) structure.
- Differentiated public/private subnets and learned:
  - Route Tables
  - Internet Gateway (IGW)
  - NAT Gateway
  - Elastic IP
  - Elastic Network Interface (ENI)
- Learned about:
  - VPC Endpoints
  - VPC Flow Logs
  - Security Groups (stateful) vs NACLs (stateless)
  - VPC Peering & Transit Gateway
  - Intro to Site-to-Site VPN, Client VPN, Direct Connect
  - Load Balancers: ALB, NLB, CLB, Global LB


### Reflection – Progress, Challenges, and Next Steps

#### Strengths Developed
- Strong grasp of AWS fundamentals and how services are categorized.
- Confident in configuring accounts and applying IAM best practices.
- Improved understanding of AWS networking components.

#### Difficulties Encountered
- Initially confused between CLI and SDK usage.
- VPC components (CIDR, subnets, NACLs, SG) were challenging at first.
- “EC2:Running Hours” metric missing during Budget setup due to no activity data.
- Estimating pricing took time because of unfamiliar service options.
- Advanced networking labs (Peering, Hybrid DNS, Route 53 Resolver) required multiple attempts.

#### Improvement Plan
- Continue practicing CLI and networking labs.
- Perform more hands-on cost management tasks, including Spot Instances.
- Review official AWS documentation to reduce conceptual confusion.
- Build diagrams and summaries after complex labs to strengthen memory.
