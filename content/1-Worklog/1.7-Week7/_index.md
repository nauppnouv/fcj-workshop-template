---
title: "Week 7 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.7. </b> "
---

During Week 7 (October 26–30, 2026), I reviewed the AWS proposal and architecture for the FCAJ Hackathon System, prepared for the handoff between Backend 1 and Backend 2, and examined the database and networking requirements for running the backend with Amazon RDS for MySQL 8.4.

### Week 7 Objectives

- Explain how user traffic, application releases, and AI jobs move through the proposed architecture.
- Identify schema compatibility risks before moving from MySQL 8.0 to MySQL 8.4.
- Prepare a handoff checklist covering the source revision, tests, migrations, runtime configuration, and permissions.
- Read the VPC and private RDS configuration in the AWS Console and identify the checks needed before testing connectivity.

### Completed Daily Worklog

| Day | Work Completed | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | Reviewed proposal v1 and the architecture plan with GPT/Codex. Clarified that EC2 was the proposed backend runtime and Lambda was a separate investigation. Traced user traffic, deployment, and the SQS job and result flow, including the purpose of the dead-letter queue (DLQ). Compared my working branch with `develop` to determine whether I needed to pull or merge, and related the proposed VPC, subnets, and routes to the diagram. | 10/26/2026 | 10/26/2026 | [Issue #7](https://github.com/nhatnhm1405/fcaj-hackathon-system/issues/7), [Subnets](https://www.youtube.com/watch?v=DHYgA94SefE), [Route table](https://www.youtube.com/watch?v=dHoYmQR7FYs) |
| 3 | Compared the MySQL 8.0 dump with Hibernate mappings and identified a table-name case mismatch to check before migrating to MySQL 8.4. Added `lower_case_table_names` and a test against a separate database to the handoff notes. Reviewed the runtime, AI review, and deployment diagrams with GPT/Codex and selected the runtime diagram as the main overview. Discussed reusing AI analysis for the same submission revision as a design option. | 10/27/2026 | 10/27/2026 | [Issue #13](https://github.com/nhatnhm1405/fcaj-hackathon-system/issues/13), [Issue #14](https://github.com/nhatnhm1405/fcaj-hackathon-system/issues/14), [RDS for MySQL](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/MySQL.KnownIssuesAndLimitations.html) |
| 4 | Prepared the Backend 1/2 handoff checklist: source commit, test results for that revision, Flyway V1–V3, Docker Compose and runtime settings, IAM permissions, and a mock worker test flow. Inspected the Backend 1 candidate in a separate Git worktree and identified what Backend 2 could prepare before integration. Created and installed a project handoff skill with GPT/Codex to make future handoff notes easier to prepare. | 10/28/2026 | 10/28/2026 | [Backend 1 candidate](https://github.com/nhatnhm1405/fcaj-hackathon-system/commit/bab44e5), [Issue #14](https://github.com/nhatnhm1405/fcaj-hackathon-system/issues/14), [IAM roles for EC2](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-roles-for-amazon-ec2.html) |
| 5 | Reviewed the Amazon RDS/MySQL section of Module 06-02 and the AWS documentation. Prepared a checklist for inspecting a private RDS instance: DB subnet group, security group, DNS endpoint, and the `lower_case_table_names` setting. | 10/29/2026 | 10/29/2026 | [Amazon RDS & Aurora](https://www.youtube.com/watch?v=qbrobQZrokY), [RDS in a VPC](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_VPC.WorkingWithRDSInstanceinaVPC.html), [RDS security groups](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Overview.RDSSecurityGroups.html), [RDS for MySQL](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/MySQL.KnownIssuesAndLimitations.html) |
| 6 | Used AWS Console screenshots and GPT/Codex to identify where to find VPC and subnet IDs and review the Availability Zone, DB subnet group, and security group. Recorded that the MySQL 8.4 instance was shown as private and identified what still needed checking before migration: the parameter group, DNS endpoint, and connectivity from EC2. Also prepared a draft of Blog 2 on Lambda concurrency and throttling. | 10/30/2026 | 10/30/2026 | [RDS in a VPC](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_VPC.WorkingWithRDSInstanceinaVPC.html), [RDS security groups](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Overview.RDSSecurityGroups.html) |

### Week 7 Achievements

- Selected a main architecture diagram and identified where the AI and deployment diagrams add detail.
- Identified the table-name case risk and added a separate database test to the migration checklist.
- Prepared handoff criteria covering the revision, tests, migrations, runtime configuration, and permissions.
- Prepared a private RDS checklist and used Console screenshots to review the visible configuration. EC2-to-RDS connectivity and migration still needed verification.

### Lessons Learned

- I learned to read each diagram for a specific question: how users reach the system, how the AI flow handles a job, or how a release reaches the host.
- Comparing the SQL dump with the application mappings helped me identify risks before migration. Compatibility still needs to be tested against the target MySQL version.
- I learned to check routing, security groups, and application permissions separately. Reading the Console configuration tells me what to test next; a connection test is needed to confirm the application can reach the database.

### Next Steps

- Inventory the PoC resources in Week 8, confirm the candidate revision and runtime requirements, and agree on the order for testing database connectivity, migrations, and the mock worker flow.
