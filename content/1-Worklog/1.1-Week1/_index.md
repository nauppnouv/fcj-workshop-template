---
title: "Week 1 Worklog"
date: 2026-10-07
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---

During the first week (September 14–18, 2026), I completed the AWS foundations covered in Module 01 and consolidated lessons from the videos, First Cloud Journey, and AWS documentation.

### Week 1 objectives

- Learn the foundations of cloud computing, pay-as-you-go pricing, and elastic resources.
- Distinguish AWS Regions, Availability Zones, and Edge Locations; identify the roles of the Console, CLI, and SDK.
- Review AWS accounts, IAM, and MFA with a focus on identity, access permissions, and credential security.
- Become familiar with AWS Budgets and basic cost monitoring.
- Review AWS Support channels and the six Well-Architected pillars as preparation for later weeks.

### Tasks completed this week

The learning activities are recorded by day, from Monday through Friday.

| Day | Completed work | Start date | Completion date | Learning sources |
| --- | --- | --- | --- | --- |
| Monday | Studied cloud computing, AWS value, and how to approach the learning path; noted concepts to connect to the future project. | 09/14/2026 | 09/14/2026 | [Module 01-01](https://www.youtube.com/watch?v=HxYZAK1coOI), [01-02](https://www.youtube.com/watch?v=IK59Zdd1poE), [01-03](https://www.youtube.com/watch?v=HSzrWGqo3ME); [First Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| Tuesday | Studied Regions, Availability Zones, and Edge Locations; distinguished the Console, CLI, and SDK; reviewed introductory cost optimization and Well-Architected concepts. | 09/15/2026 | 09/15/2026 | [Module 01-04](https://www.youtube.com/watch?v=pjr5a-HYAjI), [01-05](https://www.youtube.com/watch?v=2PQYqH_HkXw), [01-06](https://www.youtube.com/watch?v=IY61YlmXQe8), [01-07](https://www.youtube.com/watch?v=Hku7exDBURo); [AWS global infrastructure](https://docs.aws.amazon.com/whitepapers/latest/aws-overview/global-infrastructure.html), [Well-Architected pillars](https://docs.aws.amazon.com/wellarchitected/latest/framework/the-pillars-of-the-framework.html) |
| Wednesday | Reviewed account setup and authentication, MFA, IAM users/groups/policies, and account support; noted identity and access security principles. | 09/16/2026 | 09/16/2026 | [Lab01-01](https://www.youtube.com/watch?v=waR5S_lljrk), [01-02](https://www.youtube.com/watch?v=1dG5xutGbr4), [01-03](https://www.youtube.com/watch?v=b9pK1oG534Q), [01-04](https://www.youtube.com/watch?v=69iKhwI7k2Y); [FCJ Lab01](https://000001.awsstudygroup.com/), [IAM best practices](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html) |
| Thursday | Reviewed Cost/Usage Budgets, RI/Savings Plans budgets, actual/forecast figures, and the lab cleanup scope; distinguished an alert from a spending limit. | 09/17/2026 | 09/17/2026 | [Lab07-01](https://www.youtube.com/watch?v=_a09nLVw6Sg), [07-02](https://www.youtube.com/watch?v=sd_KCcZOou0), [07-03](https://www.youtube.com/watch?v=kkcdRBRnxl4), [07-04](https://www.youtube.com/watch?v=aPQynt3CfYc), [07-05](https://www.youtube.com/watch?v=NoF8eEIEA6M), [07-06](https://www.youtube.com/watch?v=KeZi7eOLpOA); [FCJ Lab07](https://000007.awsstudygroup.com/), [AWS Budgets](https://docs.aws.amazon.com/cost-management/latest/userguide/budgets-managing-costs.html) |
| Friday | Reviewed AWS Support request types, information to include when describing an issue, and how the six Well-Architected pillars can frame architecture reviews. | 09/18/2026 | 09/18/2026 | [Lab09-01](https://www.youtube.com/watch?v=4FDcK0_kbfY), [09-02](https://www.youtube.com/watch?v=BAEh-_RzmNg), [09-03](https://www.youtube.com/watch?v=haafDPugAnE), [09-04](https://www.youtube.com/watch?v=ThJBaQ3DEBs); [FCJ Lab09](https://000009.awsstudygroup.com/), [AWS Support plans](https://aws.amazon.com/premiumsupport/plans/) |

### Week 1 achievements

- Completed the Module 01 learning content, covering 7 lectures and 14 lab videos, and consolidated notes into the five topic groups in the worklog table.
- Distinguished AWS infrastructure components and the roles of the Console, CLI, and SDK; understood how architecture choices relate to workload needs and cost.
- Learned identity and access management principles, cost monitoring with AWS Budgets, AWS Support request types, and the six Well-Architected pillars.

### Lessons learned

- From the cloud and AWS infrastructure material, I learned that service and Region choices should account for workload needs, latency, data requirements, availability, and cost. This gave me a basis for evaluating architecture options for the future project.
- I learned to distinguish the roles of the Console, CLI, and SDK. The CLI and SDK support automation, while access permissions and credentials still require careful management.
- I understood how MFA, least-privilege IAM permissions, and suitable credentials complement each other. I concluded that identity security should be considered when preparing an AWS environment.
- The AWS Budgets material helped me distinguish cost monitoring and alerts from a spending limit. I also learned that deleting a sample budget does not mean other AWS resources have been cleaned up.
- From the AWS Support material, I learned that describing symptoms, impact, and relevant context makes a support request clearer. I distinguished initial response time from the time required to resolve an issue.

### Next step

Move on to VPC and networking in Week 2, and revisit any foundational AWS questions when applying these concepts to the project.
