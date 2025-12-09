---
title: "Week 11 Worklog"
date: ""
weight: 2
chapter: false
pre: " <b> 1.11. </b> "
---
### Week 11 Objectives:

- **Core Service Deployment:** Configure foundational compute and database resources to support the application.  
- **Automation & DevOps:** Establish a CI/CD pipeline to streamline build and deployment processes for cloud-based environments.  

### Activities Undertaken This Week:

| Day     | Activity                                                                                                                                                                                                                                                           | Start Date | Completion Date | Reference |
| :------ | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------- | :-------------- | :-------- |
| **2-3** | **Compute & Database Setup:**<br>- Provisioned RDS instance (initially Single-AZ, later expanded to Multi-AZ for resilience).<br>- Established connectivity between application servers and MySQL database.                                                         | 17/11/2025 | 18/11/2025      |           |
| **4-5** | **CI/CD Pipeline Implementation:**<br>- Configured source repository (CodeCommit/GitHub).<br>- Automated build processes via CodeBuild.<br>- Integrated CodeDeploy and CodePipeline for automated deployments to EC2 instances.<br>- Verified end-to-end deployment flow from local code to cloud environment. | 19/11/2025 | 20/11/2025      |           |

---

### Week 11 Reflection: Operational Environment & Automation

#### 1. Application Availability & Database Connectivity

- **RDS Stability:** Database now operates in Multi-AZ mode, improving fault tolerance and data durability.  
- **Application Integration:** Application servers successfully connected to the database, enabling data-driven functionalities.  

#### 2. DevOps & Continuous Deployment

- **Pipeline Realization:** Achieved a fully automated CI/CD workflow:  
  - **Source Control:** Commits pushed to GitHub or CodeCommit automatically trigger builds.  
  - **Build Process:** Dependencies are installed, artifacts packaged, and tested in an automated fashion.  
  - **Deployment:** New versions are rolled out to EC2 instances with minimal disruption, implementing zero-downtime deployment strategies such as rolling updates.  

This week established a robust operational foundation, combining resilient database setup with automated deployment practices, setting the stage for scalable and maintainable cloud application operations.
