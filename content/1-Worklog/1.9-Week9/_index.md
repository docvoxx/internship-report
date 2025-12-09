---
title: "Week 9 Worklog"
date: ""
weight: 1
chapter: false
pre: " <b> 1.9. </b> "
---



### Week 9 Goals:

- Progress the development of a personalized recommendation system.  
- Continuously refine data inputs and address issues emerging during the training cycle.  

### Focus Areas This Week:

| Day   | Focus                                                                                                                                                        | Start Date | Completion Date | Reference            |
| :---- | :----------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------- | :-------------- | :------------------- |
| **2** | **Initial Model Setup:**<br>- Configure the algorithm framework<br>- Load initial datasets for processing<br>- Start preliminary training routines | 10/11/2025 | 11/11/2025      | AWS Personalize Docs https://docs.aws.amazon.com/personalize/|
| **3** | Review early outputs and investigate anomalies or unexpected behaviors                                                                                      | 12/11/2025 | 12/11/2025      |                      |
| **4** | **Data Refinement:**<br>- Introduce additional data fields<br>- Clean and reconcile dataset inconsistencies<br>- Repeat training cycle with revised data | 12/11/2025 | 13/11/2025      |                      |
| **5** | Assess updated model performance and examine metric shifts                                                                                                   | 14/11/2025 | 14/11/2025      |                      |
| **6** | Iterative observations and planning next refinement steps                                                                                                     |            |                 |                      |

---

### Week 9 Reflection: Navigating Data and Training Challenges

This week highlighted the practical challenges of building a recommendation system and working with constrained data environments:

- **Limited Interaction Signals:**  
  The dataset mainly tracks completed actions ("Bookings"), lacking intermediary signals like "Views" or "Clicks". This scarcity constrains the system’s ability to infer deeper user preferences, reflected in modest evaluation scores.

- **Validation Constraints:**  
  Without a fully functional front-end interface, real-world validation remains largely theoretical. Current assessment relies on quantitative metrics rather than intuitive, visual confirmation.

- **Pipeline Sensitivity to Schema Changes:**  
  Introducing new data attributes requires revisiting the preprocessing pipeline. Each adjustment involves re-cleaning, re-mapping, and retraining, highlighting the delicacy of the end-to-end workflow.

- **Key Takeaways:**  
  While specific cloud tools support dataset handling and model training, the main insights are procedural: ensuring dataset completeness, maintaining flexible pipelines, and carefully managing iterative training cycles.
