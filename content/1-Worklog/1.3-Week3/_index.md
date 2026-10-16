---
title: "Week 3 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.3. </b> "
---

During the third week (September 28–October 2, 2026), I studied multi-VPC connectivity, EC2, and storage options, then worked through an AWS Backup lab covering backup and restore testing. The daily log moves from VPC Peering to resource cleanup.

### Week 3 objectives

- Understand how to connect two VPCs through VPC Peering, configure routes, and resolve DNS across the networks.
- Learn Transit Gateway, VPC attachments, and how VPC route tables work with TGW route tables.
- Understand how to choose EC2 instance types, AMIs, key pairs, and snapshots for a workload.
- Distinguish EBS from instance store and review EFS and FSx for shared file storage.
- Learn the roles of User Data, instance metadata, EC2 Auto Scaling, Lightsail, and AWS MGN.
- Create a backup plan and test a restore; identify cleanup responsibilities for each resource.

### Tasks completed this week

| Day | Completed work | Start date | Completion date | Learning sources |
| --- | --- | --- | --- | --- |
| Monday | Prepared a two-VPC environment for Lab19, configured Security Groups and Network ACLs, created VPC Peering, added routes on both sides, and enabled Cross-Peer DNS; tested connectivity through private IPs and cleaned up the lab resources. | 09/28/2026 | 09/28/2026 | [Module 02 playlist, Lab19 — 9 videos](https://www.youtube.com/playlist?list=PLahN4TLWtox2a3vElknwzU_urND8hLn1i); [FCJ Lab19](https://000019.awsstudygroup.com/); [VPC peering](https://docs.aws.amazon.com/vpc/latest/peering/vpc-peering-basics.html), [peering DNS](https://docs.aws.amazon.com/vpc/latest/peering/vpc-peering-dns.html) |
| Tuesday | Set up a four-VPC environment connected through Transit Gateway; configured attachments, association/propagation, and route tables; tested EC2 connectivity and used Reachability Analyzer to inspect the path based on the network configuration; cleaned up the resources. | 09/29/2026 | 09/29/2026 | [Module 02 playlist, Lab20 — 7 videos](https://www.youtube.com/playlist?list=PLahN4TLWtox2a3vElknwzU_urND8hLn1i); [FCJ Lab20](https://000020.awsstudygroup.com/); [How Transit Gateway works](https://docs.aws.amazon.com/vpc/latest/tgw/how-transit-gateways-work.html), [Reachability Analyzer](https://docs.aws.amazon.com/vpc/latest/reachability/how-reachability-analyzer-works.html) |
| Wednesday | Studied compute VMs, EC2 instance type selection, AMIs, key pairs, and backups; compared Amazon EBS with instance store based on attachment, data lifecycle, and use cases. | 09/30/2026 | 09/30/2026 | [Compute VM](https://www.youtube.com/watch?v=-t5h4N6vfBs), [AMI / Backup / Key Pair](https://www.youtube.com/watch?v=yAR6QRT3N1k), [EBS](https://www.youtube.com/watch?v=hKr_TfGP7NY), [Instance store](https://www.youtube.com/watch?v=6IHNDJ85aoQ); [EC2 instance types](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instance-types.html), [EBS](https://docs.aws.amazon.com/ebs/latest/userguide/what-is-ebs.html), [Instance store persistence](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instance-store-lifetime.html) |
| Thursday | Studied User Data and instance metadata, and the EC2 Auto Scaling mechanism; compared EFS, FSx, Lightsail, and AWS Application Migration Service by their roles in initialization, scaling, file storage, and application migration. | 10/01/2026 | 10/01/2026 | [User Data](https://www.youtube.com/watch?v=_v_43Wi7zjo), [Metadata](https://www.youtube.com/watch?v=Ew3QRaKJQSA), [EC2 Auto Scaling](https://www.youtube.com/watch?v=bbLcPitXJSY), [Compute services overview](https://www.youtube.com/watch?v=hFVYG8WqfU0); [EC2 User Data](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/user-data.html), [EC2 instance types](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instance-types.html) |
| Friday | Prepared the AWS Backup lab infrastructure, created a backup plan and vault, and assigned resources; checked backup jobs, the Lambda and notification restore flow, restore jobs and logs, then cleaned up resources according to their ownership. | 10/02/2026 | 10/02/2026 | [FCJ Lab13 — Introduction](https://000013.awsstudygroup.com/1-introduce/), [Deploy infrastructure](https://000013.awsstudygroup.com/2-prerequiste/2.2-deployinfras/), [Create Backup plan](https://000013.awsstudygroup.com/3-createbackupplan/), [Test Restore](https://000013.awsstudygroup.com/5-testrestore/), [Cleanup](https://000013.awsstudygroup.com/6-cleanup/); [S3/template preparation](https://000013.awsstudygroup.com/2-prerequiste/2.1-creates3bucket/), [notifications](https://000013.awsstudygroup.com/4-enablenoti/) |

### Week 3 achievements

- Completed the learning set of 24 YouTube videos and 6 supplemental FCJ/AWS documents, organized into five daily topic groups.
- Configured VPC Peering in the lab and learned the conditions for connectivity between two VPCs, including non-overlapping CIDRs, routes on both sides, and appropriate security rules.
- Set up a multi-VPC Transit Gateway lab and distinguished VPC routes from TGW routes, as well as the roles of attachments, association, and propagation.
- Consolidated EC2 instance selection criteria and understood the difference in data persistence between EBS and instance store.
- Distinguished User Data from instance metadata and learned the purpose of Auto Scaling, EFS, FSx, Lightsail, and MGN at a high level.
- Created a backup plan in the lab, followed backup/restore jobs and logs, and learned why application recovery checks and cleanup of resources outside the stack matter.

### Lessons learned

- I learned that an active VPC Peering connection alone does not ensure application connectivity. I need to check CIDRs, routes on both sides, Security Groups, Network ACLs, and name resolution along the traffic path.
- I distinguished VPC route tables from TGW route tables. Association selects the TGW route table used for traffic from an attachment, while propagation adds that attachment's routes to the selected table.
- Reachability Analyzer helps me reason about reachability based on network configuration; its result does not replace testing a running application connection.
- I learned that choosing EBS or instance store depends on performance and data-retention needs. Instance store suits temporary data such as caches, while data that must persist needs appropriate durable storage.
- I learned how AMIs and User Data support consistent instance initialization, while metadata provides information about an instance for operational processes. These concepts help me understand Auto Scaling designs.
- I understood that a successful backup job and a successful workload recovery are different outcomes. Restore checks need clear success criteria, and resources created during testing also need lifecycle management.

### Next step

In Week 4, I will move on to S3, CloudFront, and the next storage topics in the AWS learning path.
