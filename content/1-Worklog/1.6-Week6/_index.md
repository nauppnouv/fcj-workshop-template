---
title: "Week 6 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.6. </b> "
---

During Week 6 (October 19–23, 2026), I started my Backend 2 assignment for the FCAJ Hackathon System. I reviewed the existing deployment, submitted a proposal for running the backend on AWS, and shared what I learned about Amazon SQS in Blog 1.

### Week 6 Objectives

- Understand how the existing Docker Compose configuration and GitHub Actions workflow build and run the backend.
- Propose a deployment and rollback process that identifies the exact container image in use.
- Outline how the backend exchanges jobs and results with the local AI worker.
- Document the assumptions behind the AWS cost estimate and explain how SQS messages can be processed again.

### Completed Daily Worklog

| Day | Work Completed | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | Reviewed the Backend 2 requirements in Issue #7, the Dockerfile, Docker Compose configuration, and deployment workflow. Traced how GitHub Actions ran tests and then connected to EC2 over SSH so the host could fetch the source and build the containers. | 10/19/2026 | 10/19/2026 | [Issue #7](https://github.com/nhatnhm1405/fcaj-hackathon-system/issues/7), [Compute VM on AWS](https://www.youtube.com/watch?v=-t5h4N6vfBs), [Docker Compose](https://docs.docker.com/compose/) |
| 3 | Sent a technical draft proposing that GitHub Actions build the backend image, publish it to Amazon Elastic Container Registry (ECR), and verify the running revision after deployment. Proposed rolling back to a known image digest, subject to database and file compatibility. Outlined an SQS job queue for the local worker, Amazon S3 for output files, and a result queue back to the backend, with retry and duplicate handling and a dead-letter queue for repeated failures. | 10/20/2026 | 10/20/2026 | [Technical draft](https://github.com/nhatnhm1405/fcaj-hackathon-system/issues/7#issuecomment-6291981789), [ECR image lifecycle](https://docs.aws.amazon.com/AmazonECR/latest/userguide/getting-started-cli.html), [Pull by digest](https://docs.aws.amazon.com/AmazonECR/latest/userguide/docker-pull-ecr-image.html), [SQS visibility timeout](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-visibility-timeout.html) |
| 4 | Updated the proposal after the team lead's feedback: EC2 with Docker, ECR, GitHub Actions, and CloudFormation, with S3 and CloudFront for the frontend and a private RDS MySQL database. Reviewed assumptions for the Singapore Region, resource sizing, workload, and runtime. Compared 160 and 730 EC2 hours per month, with RDS assumed to run for 730 hours in both scenarios. AWS credits were still unverified. | 10/21/2026 | 10/21/2026 | [Team lead's feedback](https://github.com/nhatnhm1405/fcaj-hackathon-system/issues/7#issuecomment-6308395467), [AWS Cost Optimization](https://www.youtube.com/watch?v=IY61YlmXQe8), [AWS Pricing Calculator](https://calculator.aws/), [AWS Budgets](https://docs.aws.amazon.com/cost-management/latest/userguide/budgets-managing-costs.html) |
| 5 | Submitted proposal v1 as a Markdown attachment on Issue #7, covering deployment, messaging, the cost estimate, and five proposed follow-up tasks. Published Blog 1 in the Facebook group, using a duplicate email example to explain SQS visibility timeout and how to handle repeated processing. | 10/22/2026 | 10/22/2026 | [Proposal submission](https://github.com/nhatnhm1405/fcaj-hackathon-system/issues/7#issuecomment-6323090811), [Facebook post](https://www.facebook.com/share/p/1CJMAYWQBf/), [SQS visibility timeout](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-visibility-timeout.html) |
| 6 | Added the English and Vietnamese versions of Blog 1 to the workshop repository, preserving the original publication date of October 22 and linking to the Facebook post and AWS documentation. | 10/23/2026 | 10/23/2026 | [Bilingual Blog 1 update](https://github.com/nauppnouv/fcj-workshop-template/commit/18ababc4a69b852d4a74e0310612764ca58a56c2), [Facebook post](https://www.facebook.com/share/p/1CJMAYWQBf/) |

### Week 6 Achievements

- Submitted the Backend 2 proposal with deployment and rollback designs, the proposed job and result flow, and five follow-up tasks for team review.
- Prepared two cost scenarios with explicit assumptions about each resource's operating hours and identified AWS credits as an item to confirm.
- Published the SQS article in the Facebook group and added both language versions to the workshop repository.

### Lessons Learned

- I learned to trace a release from the source commit to the image that actually runs. A digest identifies the image, while rollback also depends on whether the earlier application version can use the current database schema and files.
- I learned that a cost comparison needs to show how each resource is used. Changing EC2 hours does not change the estimate for an RDS instance assumed to run continuously.
- I learned that a worker on SQS Standard must handle a message more than once without repeating side effects. Visibility timeout and a dead-letter queue help manage retries; the application still needs to prevent duplicate actions.

### Next Steps

- Clarify the handoff between Backend 1 and Backend 2: identify the source revision and test results, review database and network requirements, and agree on how to validate a small deployment.
