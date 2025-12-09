---
title: "Week 10 Worklog"
date: ""
weight: 2
chapter: false
pre: " <b> 1.10. </b> "
---


#### Week 10 Objectives:

- **Solution Architecture:** Refine both High-Level (HLD) and Low-Level (LLD) diagrams aligned with the AWS Well-Architected Framework.  
- **Resource Planning & Cost Estimation:** Develop an understanding of Total Cost of Ownership (TCO) and evaluate service options for efficiency.  
- **Network Foundation:** Lay down the initial networking environment including VPCs, subnets, and basic security mechanisms.  

### Activities Undertaken This Week:

| Day     | Activity                                                                                                                                                                                                                                                   | Start Date | Completion Date | Reference |
| :------ | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------- | :-------------- | :-------- |
| **2-3** | **Architecture & Planning:**<br>- Reviewed business requirements and identified critical components.<br>- Drafted system architecture diagrams illustrating resource flows.<br>- Estimated costs using AWS Pricing Calculator and considered cost-saving measures.<br>- Checked alignment with the 5 pillars of the Well-Architected Framework. | 10/11/2025 | 11/11/2025      |           |
| **4-5** | **Infrastructure Initialization (IaC):**<br>- Developed Terraform/CloudFormation scripts to provision VPC, Public/Private Subnets, NAT Gateway, and Route Tables.<br>- Configured Security Groups for Bastion Hosts, Application Servers, and Databases following best practices. | 12/11/2025 | 13/11/2025      |           |

---

### Week 10 Reflection: Architecture and Network Foundations

#### 1. Architecture Design Insights

- **Diagrammatic Representation:** Successfully completed data flow and resource layout diagrams, following a **Single-AZ** setup for simplicity during the initial phase.  
- **Service Decisions:**  
  - **Relational Database:** Chose RDS MySQL with Multi-AZ for resilience.  
  - **Storage:** S3 for static files and backups.  
- **Cost Awareness:** Developed a preliminary monthly cost estimate and identified optimization strategies, such as leveraging Spot Instances in development and applying Savings Plans in production environments.

#### 2. Networking & Security Foundation

- **VPC Setup:** Established a well-structured VPC with clear separation between Public and Private subnets for applications and databases.  
- **Security Implementation:** Applied **least privilege principles** in Security Group configurations to protect bastion, web, and database layers.  

Overall, this week laid the groundwork for both architectural clarity and a secure, operational network environment, setting the stage for further deployments and service integrations.

