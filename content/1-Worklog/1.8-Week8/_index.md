---
title: "Week 8 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.8. </b> "
---

During Week 8 (November 2–6, 2026), I worked with the FCAJ Hackathon System team on the proof-of-concept (PoC) architecture, took inventory of the AWS environment, and prepared the Backend 2 release. I then recorded which parts of the frontend, API, and worker flow had been tested.

### Week 8 Objectives

- Clarify how the static frontend, API, and application storage are separated.
- Compare the AWS resources in Singapore with the CloudFormation template and identify gaps before deployment.
- Prepare a release that can be traced to a specific source revision and Docker image.
- Check HTTPS, frontend delivery, and message transport using a mock worker.

### Completed Daily Worklog

| Day | Work Completed | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | Studied the proposed architecture with the team. Traced the frontend through CloudFront to a private S3 bucket and the API through Caddy to the Spring Boot backend on EC2 and then RDS. Reviewed how S3 Block Public Access and CloudFront Origin Access Control (OAC) work with the bucket policy. Distinguished frontend assets from application files and AI results. | 11/02/2026 | 11/02/2026 | [Issue #14](https://github.com/nhatnhm1405/fcaj-hackathon-system/issues/14), [Amazon S3](https://www.youtube.com/watch?v=_yunukwcAwc), [S3 Block Public Access](https://docs.aws.amazon.com/AmazonS3/latest/userguide/access-control-block-public-access.html), [CloudFront OAC](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/private-content-restricting-access-to-s3.html) |
| 3 | Checked access through the AWS tooling with GPT/Codex and took inventory of the Singapore PoC: the CloudFormation stack, S3, the SQS job and result queues and their dead-letter queues, ECR, logging, EC2/SSM, and RDS. Compared the resources with the template, noting gaps in runtime permissions, image availability, and logs, as well as a visibility timeout mismatch between the queues and the template. | 11/03/2026 | 11/03/2026 | [Issue #14](https://github.com/nhatnhm1405/fcaj-hackathon-system/issues/14), [SSM Run Command](https://docs.aws.amazon.com/systems-manager/latest/userguide/run-command.html), [SQS visibility timeout](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-visibility-timeout.html) |
| 4 | Studied the release design with the team. Traced the path from a tested source revision to a Docker image in ECR, then from an SSM command to EC2 pulling that exact digest. Identified checks for RDS before startup, frontend delivery through CloudFront, the API over HTTPS, anonymous access to S3, and SQS/S3 transport with a mock worker. | 11/04/2026 | 11/04/2026 | [Issue #14](https://github.com/nhatnhm1405/fcaj-hackathon-system/issues/14), [ECR pull by digest](https://docs.aws.amazon.com/AmazonECR/latest/userguide/docker-pull-ecr-image.html), [SSM Run Command](https://docs.aws.amazon.com/systems-manager/latest/userguide/run-command.html), [CloudFront checks](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/GettingStarted.SimpleDistribution.html), [SQS visibility timeout](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-visibility-timeout.html) |
| 5 | Prepared the PoC release steps for deploying a digest-pinned ECR image through SSM with an RDS check before backend startup. Compared the running candidate's revision and image against the deployment record. Prepared frontend delivery through private S3 and CloudFront and the Caddy HTTPS configuration for the API. | 11/05/2026 | 11/05/2026 | [Public PoC release report](https://github.com/nhatnhm1405/fcaj-hackathon-system/blob/9caeef3572a3c5eb92c5b3dc8d98c6f728621b85/docs/report/issue-14-execution-status-2026-11-05.md), [PR #24](https://github.com/nhatnhm1405/fcaj-hackathon-system/pull/24) |
| 6 | Recorded checks of HTTPS, static frontend files, and browser access without signing in. Checked that a Java mock worker could receive a job through SQS, read and write S3, and send a result. Updated the draft PR documentation and removed environment identifiers from the public report. This check covered SQS/S3 transport; signed-in workflows and the real AI worker remained unverified. | 11/06/2026 | 11/06/2026 | [Public validation report](https://github.com/nhatnhm1405/fcaj-hackathon-system/blob/9caeef3572a3c5eb92c5b3dc8d98c6f728621b85/docs/report/issue-14-execution-status-2026-11-05.md), [PR #24](https://github.com/nhatnhm1405/fcaj-hackathon-system/pull/24) |

**Weekend note (November 7):** Inspected Docker Desktop storage and removed one old Maven image after checking that no container referenced it. Kept the containers and volumes. [Docker disk usage](https://docs.docker.com/reference/cli/docker/system/df/)

### Week 8 Achievements

- Clarified the frontend and API paths with the team and identified checks for the release.
- Recorded the AWS PoC inventory and the configuration differences to address before running the backend.
- Prepared deployment by image digest and documented the candidate revision and RDS check.
- Recorded HTTPS and frontend checks and a Java mock round trip through SQS/S3 in draft PR #24.

### Lessons Learned

- A CloudFormation inventory tells me which resources exist. Application readiness also depends on the image, runtime permissions, and database access.
- I can trace what EC2 runs by recording the source revision and image digest. ECR stores the image; SSM sends the deployment command.
- A successful mock round trip confirms the messaging and storage path tested. Signing in, completing a business workflow, and processing a job with the real AI worker each need their own checks.

### Next Steps

- Review PR #24 with the team, clarify access and release prerequisites, and plan the remaining API and signed-in workflow checks in Week 9.
