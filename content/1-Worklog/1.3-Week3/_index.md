---
title: "Week 3 Worklog"
date: ""
weight: 1
chapter: false
pre: " <b> 1.3. </b> "
---

### Week 3 Objectives:

* Get practical experience with AWS storage services, including:  
    - Amazon S3, Storage Gateway, AWS Backup, Amazon FSx.  
* Strengthen knowledge of AWS security and access management concepts through IAM (Users, Groups, Roles, Policies).  
* Gain hands-on experience operating services via both Console and CLI.  
* Record observations and structure notes to support upcoming exercises.  

### Tasks for This Week:

| Day | Tasks                                                                                                                                                                   | Start date  | Completion date | Reference Material                                                                                          |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------- | --------------- | ---------------------------------------------------------------------------------------------------------- |
| 2   | - Investigate AWS storage options: S3, Snow Family devices, Storage Gateway, and AWS Backup; explore their roles in data protection and recovery                         | 22/09/2025  | 22/09/2025      | [FCJ YT](https://www.youtube.com/watch?v=AQlsd0nWdZk&list=PLahN4TLWtox2a3vElknwzU_urND8hLn1i), [Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| 3   | - Create and configure Amazon S3 buckets; set up AWS Backup plans and test backup/restore workflows                                                                      | 23/09/2025  | 23/09/2025      | [My Notes on AWS Services](https://www.notion.so/i-n-to-n-m-m-y-26a4c2b6beb680beb5eaf9d9f48b8b00?source=copy_link) |
| 4   | - Deploy a File Storage Gateway to enable hybrid access to cloud storage from on-premises systems                                                                       | 24/09/2025  | 24/09/2025      | [My Notes on AWS Services](https://www.notion.so/i-n-to-n-m-m-y-26a4c2b6beb680beb5eaf9d9f48b8b00?source=copy_link) |
| 5   | - Launch Amazon FSx for Windows File Server and verify file-sharing functionality and AD integration                                                                   | 25/09/2025  | 25/09/2025      | [My Notes on AWS Services](https://www.notion.so/i-n-to-n-m-m-y-26a4c2b6beb680beb5eaf9d9f48b8b00?source=copy_link)|
| 6   | - Study AWS IAM and security mechanisms; document users, roles, policies, and recommended best practices                                                                | 26/09/2025  | 26/09/2025      | [Video Security](https://www.youtube.com/watch?v=N_vlJGAqZxo&list=PLahN4TLWtox2a3vElknwzU_urND8hLn1i&index=151) |

### Week 3 Achievements:

### Amazon S3
- Object storage that scales virtually without limits; supports individual objects up to 5 TB.  
- Supports multipart uploads, notifications, and automated lifecycle management.  
- Guarantees 99.999999999% durability and 99.99% availability.  
- Offers multiple storage classes: Standard, Standard-IA, One Zone-IA, Intelligent-Tiering, Glacier, Deep Archive.  
- Lifecycle rules can move data automatically between tiers.  
- Can host static websites and supports CORS for cross-origin requests.  
- Access controlled via ACLs, bucket policies, and IAM policies; private access possible with VPC endpoints.  
- Versioning enables recovery from accidental deletion or overwrites.  
- Glacier provides cost-effective long-term storage with three retrieval speeds: Expedited, Standard, Bulk.  

### Snow Family & Storage Gateway
- **Snowball:** ~80 TB appliance for transferring on-premises data to AWS.  
- **Snowball Edge:** ~100 TB storage plus compute capabilities at the edge for pre-processing data.  
- **Snowmobile:** truck-scale device (~100 PB) for extremely large datasets.  
- **Storage Gateway:** bridges on-premises systems with AWS storage:  
    - **File Gateway (NFS/SMB):** presents S3 as file shares.  
    - **Volume Gateway (iSCSI):** block-level storage with snapshots to EBS/S3.  
    - **Tape Gateway (VTL):** virtual tape library storing to S3/Glacier, replacing physical tapes.  

### Backup & Disaster Recovery
- **RTO (Recovery Time Objective):** maximum allowable downtime.  
- **RPO (Recovery Point Objective):** maximum acceptable data loss period.  
- Common recovery strategies: Backup & Restore, Pilot Light, Low-capacity Active-Active, Full Active-Active.  
- **AWS Backup:** centralized service to manage and monitor backups for EBS, EC2, RDS, DynamoDB, EFS, and Storage Gateway.  

### FSx
- Configured Amazon FSx for Windows File Server.  
- Provides managed Windows-native file storage accessible through SMB.  
- Ideal for workloads requiring Active Directory integration or Windows-based applications.  

### Security & IAM
- **Shared Responsibility Model:** AWS secures infrastructure; customers secure their data and configurations.  
- **Root Account:** full permissions — best practice is to minimize use, create IAM admins, and secure credentials.  
- **IAM User:** identity with no default permissions, can be grouped for easier management.  
- **IAM Policy:** JSON-based permission rules; types include identity-based and resource-based; deny takes priority over allow.  
- **IAM Role:** temporary credentials via STS, combining permissions and a trust policy.  
    - Useful for least-privilege access, cross-account access, and service-level permissions.  
