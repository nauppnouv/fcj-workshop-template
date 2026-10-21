---
title: "Week 5 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.5. </b> "
---

During the fifth week (October 12–16, 2026), I began preparing a workshop with the FCAJ Hackathon System team. I joined brainstorming, discussed the scope, outlined an initial approach, and received direction for my Backend 2 responsibilities ahead of Week 6. Alongside this work, I strengthened my understanding of security responsibilities, AWS Identity and Access Management (IAM), and cost management to support planning.

### Week 5 Objectives

- Clarify the problem, intended users, and workshop goals with the team.
- Define the proof-of-concept (PoC) scope and distinguish it from possible extensions.
- Relate EC2, VPC, and S3 concepts to the initial deployment approach and data flow.
- Strengthen my understanding of IAM policies and roles, and distinguish AWS permissions from application user roles.
- Receive direction for Backend 2 and identify the inputs needed for deployment, messaging, and cost estimation.
- Consolidate the plan and dependencies before starting Week 6 work.

### Completed Daily Worklog

| Day | Work Completed | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | Joined team brainstorming on the problem, intended users, and workshop goals. Discussed a minimal demo flow that others could reproduce; studied the Shared Responsibility Model to connect the team's responsibilities with its use of cloud services. | 10/12/2026 | 10/12/2026 | [Shared Responsibility Model](https://www.youtube.com/watch?v=tsobAlSg19g); [AWS Well-Architected](https://docs.aws.amazon.com/wellarchitected/latest/framework/the-pillars-of-the-framework.html) |
| 3 | Discussed the PoC scope, reusable parts of the existing system, and ideas to defer. Studied IAM, policies, and roles; distinguished AWS resource permissions from application user roles to prepare questions about security. | 10/13/2026 | 10/13/2026 | [IAM](https://www.youtube.com/watch?v=N_vlJGAqZxo), [Create IAM Policy](https://www.youtube.com/watch?v=XXjEpIRWJBk), [Create IAM Role](https://www.youtube.com/watch?v=pJWANviu8QM); [IAM best practices](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html) |
| 4 | Outlined an initial deployment approach and the data flow between the backend and the AI component. Reviewed EC2/S3 concepts and how workloads use IAM roles; identified dependencies to discuss further with the lead, backend contributors, and AI owner. | 10/14/2026 | 10/14/2026 | [Create IAM role — Lab48](https://www.youtube.com/watch?v=j8Gj2DJtZUE), [Using IAM role](https://www.youtube.com/watch?v=Z0liKVSjt_Q); [IAM best practices](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html); [project repository](https://github.com/nhatnhm1405/fcaj-hackathon-system) |
| 5 | Discussed work allocation and received direction for Backend 2, focusing on deployment, messaging, and cost inputs. Reviewed cost optimization; identified information to clarify, such as Region, operating schedule, and workload, before preparing an estimate. | 10/15/2026 | 10/15/2026 | [AWS Cost Optimization and Working with AWS Support](https://www.youtube.com/watch?v=IY61YlmXQe8); [AWS Budgets](https://docs.aws.amazon.com/cost-management/latest/userguide/budgets-managing-costs.html) |
| 6 | Consolidated the workshop plan, work areas, and dependency order; prepared the items to continue in Week 6. Reviewed my responsibilities, required outputs, and documentation outline to connect learning with the team's work. | 10/16/2026 | 10/16/2026 | [Project repository](https://github.com/nhatnhm1405/fcaj-hackathon-system); [AWS Well-Architected](https://docs.aws.amazon.com/wellarchitected/latest/framework/the-pillars-of-the-framework.html) |

### Week 5 Achievements

- Began workshop preparation with the team and clarified the problem focus and purpose of the initial demo flow.
- Distinguished PoC priorities from possible extensions to focus on an achievable scope.
- Outlined an initial approach and identified deployment, data, and AI coordination questions that needed further clarification.
- Strengthened my understanding of IAM policies, roles, and application permissions; related access requirements to the proposed components.
- Received direction for Backend 2 and identified the inputs needed for the technical proposal and cost estimate.
- Consolidated the initial plan, dependencies, and transition into Week 6 work.

### Lessons Learned

- I learned to agree on the problem and demo scope before selecting many AWS services. The approach should support the workshop goals and fit the team's available time.
- I learned that an architecture diagram should help the team explain data flow, component responsibilities, and decisions that still need confirmation.
- I distinguished AWS resource permissions from application user roles. When planning access, I need to identify which component performs each action and which permissions it requires.
- I understood the role of IAM roles for workloads and the principle of least privilege. Studying policies and roles helped me ask more specific questions about resource access.
- I learned that a cost estimate needs explicit assumptions about resources, Region, workload, and operating schedule. Credits also need confirmation before being included in the calculation.
- I learned that task allocation needs outputs, dependencies, and completion criteria so that the parts can be integrated. I prioritized learning that directly supports my responsibilities.

### Next Steps

- Start Backend 2 work in Week 6: examine the existing Dockerfile, Docker Compose configuration, and workflow; develop the deployment, pipeline, and rollback proposal.
- Clarify the job/result contract and SQS flow with the AI owner; prepare an estimate with assumptions, pricing sources, and questions for the lead.
- Follow [Issue #7](https://github.com/nhatnhm1405/fcaj-hackathon-system/issues/7), created on October 19, 2026, for the formal task scope and record review outcomes in Week 6.
- Add personal details: **[TO BE COMPLETED: the official workshop title, my specific idea or contribution, and links to notes or diagrams if available.]**
