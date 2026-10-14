---
title: "Week 1 Worklog"
date: 2026-10-07
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---

> **Status: Learning plan.** This page records the planned scope for Week 1. Study dates, actual outcomes, and personal reflections will be added after the corresponding activities take place. Instructions shown in videos or labs are not reported as completed actions.

### Week 1 objectives

- Learn the foundations of cloud computing, pay-as-you-go pricing, and elastic resources.
- Distinguish AWS Regions, Availability Zones, and Edge Locations; identify the roles of the Console, CLI, and SDK.
- Review AWS accounts, IAM, and MFA with a focus on identity, access permissions, and credential security.
- Become familiar with AWS Budgets and basic cost monitoring.
- Review AWS Support channels and the six Well-Architected pillars as preparation for later weeks.

### Planned learning topics

| Topic | Planned scope and output | Learning sources |
| --- | --- | --- |
| Cloud foundations and learning approach | Cloud computing, AWS value, and a learning approach; note concepts to connect to the future project. | [Module 01-01](https://www.youtube.com/watch?v=HxYZAK1coOI), [01-02](https://www.youtube.com/watch?v=IK59Zdd1poE), [01-03](https://www.youtube.com/watch?v=HSzrWGqo3ME); [First Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| Global infrastructure and tools | Regions/AZs/Edge Locations; Console, CLI, and SDK; introductory cost optimization and Well-Architected concepts. | [Module 01-04](https://www.youtube.com/watch?v=pjr5a-HYAjI), [01-05](https://www.youtube.com/watch?v=2PQYqH_HkXw), [01-06](https://www.youtube.com/watch?v=IY61YlmXQe8), [01-07](https://www.youtube.com/watch?v=Hku7exDBURo); [AWS global infrastructure](https://docs.aws.amazon.com/whitepapers/latest/aws-overview/global-infrastructure.html), [Well-Architected pillars](https://docs.aws.amazon.com/wellarchitected/latest/framework/the-pillars-of-the-framework.html) |
| Accounts, IAM, and MFA | Review account setup/authentication, MFA, users/groups/policies, and account support; capture identity and access security principles. | [Lab01-01](https://www.youtube.com/watch?v=waR5S_lljrk), [01-02](https://www.youtube.com/watch?v=1dG5xutGbr4), [01-03](https://www.youtube.com/watch?v=b9pK1oG534Q), [01-04](https://www.youtube.com/watch?v=69iKhwI7k2Y); [FCJ Lab01](https://000001.awsstudygroup.com/), [IAM best practices](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html) |
| Cost monitoring | Review Cost/Usage Budgets, RI/Savings Plans budgets, actual versus forecast figures, and the cleanup scope shown in the lab. | [Lab07-01](https://www.youtube.com/watch?v=_a09nLVw6Sg), [07-02](https://www.youtube.com/watch?v=sd_KCcZOou0), [07-03](https://www.youtube.com/watch?v=kkcdRBRnxl4), [07-04](https://www.youtube.com/watch?v=aPQynt3CfYc), [07-05](https://www.youtube.com/watch?v=NoF8eEIEA6M), [07-06](https://www.youtube.com/watch?v=KeZi7eOLpOA); [FCJ Lab07](https://000007.awsstudygroup.com/), [AWS Budgets](https://docs.aws.amazon.com/cost-management/latest/userguide/budgets-managing-costs.html) |
| Support and architecture | Identify support request types, information to prepare when describing an issue, and how the six pillars can frame architecture reviews. | [Lab09-01](https://www.youtube.com/watch?v=4FDcK0_kbfY), [09-02](https://www.youtube.com/watch?v=BAEh-_RzmNg), [09-03](https://www.youtube.com/watch?v=haafDPugAnE), [09-04](https://www.youtube.com/watch?v=ThJBaQ3DEBs); [FCJ Lab09](https://000009.awsstudygroup.com/), [AWS Support plans](https://aws.amazon.com/premiumsupport/plans/) |

### Lessons to record after studying

- Service and Region choices should account for workload needs, latency, data requirements, availability, and cost rather than service names alone.
- The Console, CLI, and SDK are different ways to interact with AWS. Automation still requires deliberate identity and access controls.
- MFA, least-privilege IAM permissions, and suitable credentials are distinct practices that contribute to account security.
- Budgets support cost monitoring and alerts; an alert is not a spending limit. Deleting a sample budget also does not mean all potentially billable resources have been removed.
- Clear support requests describe symptoms, impact, and relevant context. Initial response time is not the same as resolution time.

### Actual results and notes

This page currently records the planned scope and sources for 7 lecture videos, 14 lab videos, and First Cloud Journey/AWS documentation. The supplied notes do not confirm study dates, hands-on results, or personal reflections, so those will be added when actual details are available.

### Next step

Move on to VPC and networking in Week 2, and revisit any foundational AWS questions when applying these concepts to the project.
