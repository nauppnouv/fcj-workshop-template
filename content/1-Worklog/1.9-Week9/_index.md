---
title: "Week 9 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.9. </b> "
---

During Week 9 (November 9–13, 2026), I continued work on the FCAJ Hackathon System proof of concept (PoC). I reviewed Backend 2 changes, set up team access in AWS, and checked the API after moving HTTPS traffic to an Application Load Balancer.

### Week 9 Objectives

- Review the Backend 2 pull request and record the scope of its tests.
- Grant AWS access according to each team member's responsibilities.
- Verify HTTPS routing and API responses through the Application Load Balancer.
- Validate the Docker build in GitHub Actions and identify the remaining release and acceptance checks.

### Completed Daily Worklog

| Day | Work Completed | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | Reviewed the Backend 2 scope in Issue #17 against the SQS/S3 contract and rechecked CI, deployment, and database tests for PR #24. Moved the PR from Draft to Ready for review. The maintainer merged it into `develop`. The Java mock had covered SQS/S3 transport, and the Python AI worker still needed an end-to-end test. | 11/09/2026 | 11/09/2026 | [Issue #17][issue17], [PR #24][pr24] |
| 3 | Reviewed the GitHub environment, OpenID Connect (OIDC), release permissions, and checks to run on EC2. Set up individual AWS Identity and Access Management (IAM) access for four team members according to their responsibilities and sent access instructions privately. | 11/10/2026 | 11/10/2026 | [PR #24 review comment][lead], [IAM best practices][iam], [GitHub Actions OIDC][oidc] |
| 4 | Granted the team scoped read access to AWS services and logs. Set up an Application Load Balancer (ALB) in the existing VPC, validated the AWS Certificate Manager (ACM) certificate via DNS, and pointed the API hostname to the ALB. Checked HTTPS, target health, API responses, CORS, and CSRF. Finalized PR #28 to build and transfer the Docker image as a workflow artifact. All four CI jobs passed at revision `ff36d57`. The maintainer merged the PR. | 11/11/2026 | 11/11/2026 | [PR #28][pr28], [CI run][ci28], [Load Balancer video][v-lb], [Security Group video][v-sg], [ALB security groups][alb-sg], [ACM DNS validation][acm] |
| 5 | Studied the post-merge release process with the team. Reviewed how to check the source revision and image ID after loading the archive and how to select the image EC2 pulls using its digest in Amazon Elastic Container Registry (ECR). Recorded the allowed branch, GitHub environment, OIDC, and AWS Systems Manager (SSM) permissions in the release checklist. | 11/12/2026 | 11/12/2026 | [PR #28][pr28], [GitHub workflow artifacts][artifact], [GitHub Actions OIDC][oidc], [ECR pull by digest][ecr], [SSM Run Command][ssm] |
| 6 | Reviewed the acceptance checklist with the team and marked the checks already covered for HTTPS, target health, and API responses. Identified remaining test scenarios for browser sign-in with OAuth and the AI worker flow, from receiving an SQS job through reading input from S3 to returning a result. | 11/13/2026 | 11/13/2026 | [PR #24][pr24], [Issue #17][issue17], [PR #28][pr28] |

### Week 9 Achievements

- Prepared PR #24 for review and recorded the checks that supported the Backend 2 merge.
- Set up access for four team members and limited shared permissions to viewing services and logs.
- Verified HTTPS routing through the ALB to the EC2 target and checked API responses.
- Validated the Docker image build in CI and recorded the remaining AWS release and end-to-end acceptance checks.

### Lessons Learned

- Team members, GitHub Actions, and the EC2 workload need different permissions. I learned to match the OIDC trust policy to the workflow environment and check which branches can deploy to it. [IAM best practices][iam], [GitHub Actions OIDC][oidc]
- I learned that security groups govern the ALB-to-target connection. The ACM validation CNAME proves control of the domain, and the API DNS record directs clients to the ALB. [ALB security groups][alb-sg], [ACM DNS validation][acm]
- I learned how to trace an image from a source revision to an image ID in the build archive and a digest in ECR. SSM sends the deployment command, and EC2 pulls the image by digest. [GitHub workflow artifacts][artifact], [ECR pull by digest][ecr], [SSM Run Command][ssm]
- A healthy target and successful API responses cover specific parts of the system. I identified separate tests for signing in and for the Python AI worker to process a job and return the expected result. [PR #24][pr24], [Issue #17][issue17]

### Next Steps

- Confirm release permissions and environment settings before running the post-merge workflow. Run the browser sign-in and AI worker scenarios and record the results.

[issue17]: https://github.com/nhatnhm1405/fcaj-hackathon-system/issues/17
[pr24]: https://github.com/nhatnhm1405/fcaj-hackathon-system/pull/24
[lead]: https://github.com/nhatnhm1405/fcaj-hackathon-system/pull/24#issuecomment-6730727583
[pr28]: https://github.com/nhatnhm1405/fcaj-hackathon-system/pull/28
[ci28]: https://github.com/nhatnhm1405/fcaj-hackathon-system/actions/runs/42985780436
[v-lb]: https://www.youtube.com/watch?v=CXU8D3kyxIc
[v-sg]: https://www.youtube.com/watch?v=B1qxOQLmavQ
[iam]: https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html
[oidc]: https://docs.github.com/en/actions/how-tos/secure-your-work/security-harden-deployments/oidc-in-aws
[alb-sg]: https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-update-security-groups.html
[acm]: https://docs.aws.amazon.com/acm/latest/userguide/dns-validation.html
[artifact]: https://docs.github.com/en/actions/concepts/workflows-and-actions/workflow-artifacts
[ecr]: https://docs.aws.amazon.com/AmazonECR/latest/userguide/docker-pull-ecr-image.html
[ssm]: https://docs.aws.amazon.com/systems-manager/latest/userguide/run-command.html
