---
title: "Week 4 Worklog"
date: ""
weight: 1
chapter: false
pre: " <b> 1.4. </b> "
---

### Week 4 Objectives:

* Strengthen hands-on knowledge of **AWS Identity & Security**:  
    - Explore **IAM**, **Cognito**, **AWS Identity Center (SSO)**, and **Organizations** for access control and governance.  
    - Practice **AWS KMS** to protect data at rest.  

* Work with **AWS Security Hub** to aggregate security information and evaluate compliance standards.  

* Understand advanced IAM mechanisms, including **Roles, Condition Keys, and Permission Boundaries**, to control and limit access.  

* Analyze compute options and optimize costs by comparing **EC2** and **Lambda** for different use cases.  

* Improve skills in reading, analyzing, and translating AWS technical documentation for internal knowledge sharing.

### Tasks for This Week:

| Day | Tasks                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                            |
| --- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | --------------- | ------------------------------------------- |
| 2   | - Explore AWS Identity & Security services: <br> &emsp; + Experiment with **Amazon Cognito**: User Pools (signup/sign-in) and Identity Pools (access to other AWS services). <br> &emsp; + Study **AWS Organizations**: manage multi-account setups, Organizational Units (OUs), Service Control Policies (SCPs), and consolidated billing. <br> &emsp; + Understand **AWS Identity Center (SSO)** for cross-account and external application access. <br> &emsp; + Practice **AWS KMS**: encrypt data at rest using CMKs and Data Keys. <br> - Hands-on labs: IAM Roles, Permission Boundaries, resource tagging, Security Hub, KMS workflows. | 29/09/2025 | 29/09/2025      | [AWS Study Group YouTube Playlist](https://www.youtube.com/watch?v=pZ2fgEFK3Vs&list=PLahN4TLWtox2a3vElknwzU_urND8hLn1i&index=152) |
| 3   | - Explore **AWS Security Hub**: enable the service, integrate with GuardDuty, Config, and Inspector, review compliance frameworks, analyze findings, and respond to alerts. <br> - Compare **EC2 vs Lambda** costs across usage patterns and determine the most cost-effective solution. <br> - Apply tag-based IAM policies to control EC2 access and validate effectiveness. | 30/09/2025 | 30/09/2025      | [AWS Security Hub Overview](https://www.notion.so/i-n-to-n-m-m-y-26a4c2b6beb680beb5eaf9d9f48b8b00?source=copy_link) <br> [EC2 vs Lambda Cost Optimization](https://www.notion.so/i-n-to-n-m-m-y-26a4c2b6beb680beb5eaf9d9f48b8b00?source=copy_link) |
| 4   | - Study **IAM Roles and Condition Keys**: attach roles to EC2/Lambda, differentiate **Trust Policies** vs **Permission Policies**, and practice conditional access based on IP, region, or tags. <br> - Practice **encrypting data at rest** using AWS KMS and compare with encryption in transit. | 01/10/2025 | 01/10/2025      | [IAM Role Documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles.html) <br> [AWS KMS Overview](https://docs.aws.amazon.com/kms/latest/developerguide/overview.html) |
| 5   | - Learn **Permission Boundaries**: define maximum permission limits for users or roles, compare with standard IAM policies. <br> - Lab: create a user with a permission boundary restricting EC2 creation to a specific region; verify effectiveness via CLI and Console. | 02/10/2025 | 02/10/2025      | [IAM Permission Boundaries](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles.html) |
| 6   | - Explore AWS monitoring and auditing services: <br> &emsp; + Review **AWS CloudTrail** to track API activity across AWS accounts. <br> &emsp; + Use **AWS Config** to observe resource compliance and configuration changes. <br> &emsp; + Use **Amazon CloudWatch** to monitor metrics, create dashboards, and set alarms for key resources. <br> - Practice creating alerts and analyzing logs to understand system activity and potential security issues. | 03/10/2025 | 03/10/2025      | [AWS CloudTrail Overview](https://docs.aws.amazon.com/cloudtrail/index.html) <br> [AWS Config Overview](https://docs.aws.amazon.com/config/index.html) <br> [Amazon CloudWatch Overview](https://docs.aws.amazon.com/cloudwatch/index.html) |

### Week 4 Achievements:

* Improved knowledge and hands-on skills with **AWS Identity & Security**:  
  - Configured **Cognito** for user authentication and authorization.  
  - Managed multi-account setups with **AWS Organizations**, using OUs, SCPs, and consolidated billing.  
  - Configured **AWS Identity Center (SSO)** for cross-account and external application access.  
  - Applied **AWS KMS** for encrypting data at rest.  
  - Monitored security posture with **AWS Security Hub** and responded to findings.  
  - Used **IAM Permission Boundaries** to limit maximum permissions for users and roles.

* Completed labs reinforcing key concepts: IAM Roles & Conditions, Permission Boundaries, Security Hub, tag-based EC2 access control, KMS encryption.  

* Applied advanced IAM concepts: **Trust Policies**, **Permission Policies**, and **Condition Keys** to implement fine-grained access control.  

* Analyzed cost-effectiveness of compute services, determining appropriate workloads for **EC2** vs **Lambda**.  

* Strengthened ability to read, synthesize, and present AWS technical information for internal knowledge sharing.
