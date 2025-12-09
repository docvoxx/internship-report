---
title: "Week 7 Worklog"
date: ""
weight: 1
chapter: false
pre: " <b> 1.7. </b> "
---

### Week 7 Goals:

- Organize and consolidate knowledge acquired in the first half of the internship.  
- Deepen understanding of **Security** and **Resiliency** in AWS.  
- Build a strong foundation for the Midterm Exam.

### Tasks for This Week:

| Day   | Task                                                                                                                                                                                                                                                                                                                                 | Start Date | Completion Date | Reference                                                                     |
| :---- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------- | :-------------- | :---------------------------------------------------------------------------- |
| **2** | **Midterm Review:**<br><br>**Part 1: Security Fundamentals**<br>- IAM (Identity & Access Management)<br>- KMS (Key Management Service)<br>- Security Groups & NACLs<br>- Secrets Manager<br>- GuardDuty (Threat Detection)<br>- Shield & WAF (DDoS and Web Application Protection)<br><br>**Part 2: Resilient Architecture**<br>- Core metrics: RTO/RPO<br>- Multi-AZ RDS<br>- Disaster Recovery Strategies<br>- Auto Scaling & Load Balancing<br>- Route 53 & DNS<br>- AWS Backup | 20/10/2025 | 20/10/2025      | [Review Link](https://ruskicoder.github.io/fcj-midterm-2025/)                 |
| **3** | Self-study: Systematize security services knowledge and practice simulation labs                                                                                                                                                                                                                                                   | 21/10/2025 | 21/10/2025      |                                                                               |
| **4** | Self-study: Redraw High Availability (HA) and Disaster Recovery (DR) architecture diagrams to reinforce concepts                                                                                                                                                                                                                  | 22/10/2025 | 22/10/2025      |                                                                               |
| **5** | Take practice tests to review knowledge and identify weak areas                                                                                                                                                                                                                                                                   | 23/10/2025 | 23/10/2025      | [Practice Exams](https://ezse.net/aws/certified-cloud-practitioner/examtopics.html) |
| **6** | Compile questions and summarize key notes for final review                                                                                                                                                                                                                                                                        | 24/10/2025 | 24/10/2025      | [Additional Resources](https://ruskicoder.github.io/fcj-midterm-2025/6-additional-resources/) |

---

### Week 7 Achievements: Strengthening Security Awareness and Resilient Architecture

- **Defense in Depth Mindset:**  
  - Clearly distinguished between **Security Groups** (stateful, instance-level) and **NACLs** (stateless, subnet-level).  
  - Understood protection at multiple layers: **WAF** for application layer (L7), **Shield** for infrastructure (L3/L4), and **GuardDuty** for intelligent threat detection.  
  - Mastered the role of **KMS** and **Secrets Manager** in safeguarding sensitive data at rest and in transit.

- **Resiliency & Recovery:**  
  - Learned and internalized **RTO (Recovery Time Objective)** and **RPO (Recovery Point Objective)** for selecting appropriate DR strategies (Backup & Restore, Pilot Light, Warm Standby, Multi-site Active/Active).  
  - Gained a clear understanding of **Multi-AZ RDS** for High Availability versus Read Replicas for scaling read operations.  
  - Understood how **Route 53, ELB, and Auto Scaling** work together to build flexible, self-healing, and scalable architectures.
