---
title: "Week 5 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.5. </b> "
---

During the fifth week (October 12–16, 2026), I studied VM Import/Export, reviewed the S3 File Gateway workflow, and learned how to operate Amazon FSx for Windows File Server. I focused on migration prerequisites and permissions, hybrid file access, Windows file shares, performance monitoring, and data protection.

### Week 5 Objectives

- Explain the VM Import/Export workflow and distinguish an imported Amazon Machine Image (AMI) from a running EC2 instance.
- Identify the IAM permissions and S3 requirements involved in importing or exporting a virtual machine.
- Review how S3 File Gateway presents SMB/NFS file access backed by Amazon S3.
- Compare FSx for Windows File Server storage and deployment choices for Windows workloads.
- Understand how monitoring, quotas, data deduplication, shadow copies, and capacity changes support file server operations.
- Recognize the resources and measurements to check when validating a migration or storage lab.

### Completed Daily Worklog

| Day | Work Completed | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | Studied how to prepare a virtual machine, export its virtual disk, and stage it in S3 for VM Import/Export. Reviewed the distinction between the caller's IAM permissions, `iam:PassRole`, and the `vmimport` service role, including the role's trust and permissions policies. | 10/12/2026 | 10/12/2026 | FCJ Lab14: [Prepare a VM](https://000014.awsstudygroup.com/1-deploy-application-server/), [export from a virtual environment](https://000014.awsstudygroup.com/2-import-vm-to-aws/1-export-vm-from-virtual-env/), [upload a VM to AWS](https://000014.awsstudygroup.com/2-import-vm-to-aws/2-upload-vm-to-aws/), [import a VM](https://000014.awsstudygroup.com/2-import-vm-to-aws/3-import-vm-to-ami/); [AWS VM Import/Export permissions](https://docs.aws.amazon.com/vm-import/latest/userguide/required-permissions.html), [supported boot modes](https://docs.aws.amazon.com/vm-import/latest/userguide/prerequisites.html) |
| 3 | Studied the import task flow from a virtual disk to an AMI and then an EC2 instance, as well as exporting an eligible instance to S3. Reviewed how to track task status, the destination bucket's export requirements, and the AMI, snapshots, volumes, and S3 objects to consider during cleanup. | 10/13/2026 | 10/13/2026 | FCJ Lab14: [Deploy an instance from an AMI](https://000014.awsstudygroup.com/2-import-vm-to-aws/4-deploy-imported-vm/), [configure S3 for export](https://000014.awsstudygroup.com/3-export-vm-from-aws/1-config-s3-for-exporting/), [export an instance](https://000014.awsstudygroup.com/3-export-vm-from-aws/2-export-from-instance/), [clean up resources](https://000014.awsstudygroup.com/4-clean-up/); [AWS export prerequisites](https://docs.aws.amazon.com/vm-import/latest/userguide/vmexport-prerequisites.html) |
| 4 | Reviewed the S3 File Gateway workflow previously covered in Week 4: gateway appliance, cache, SMB file share, and the path from a Windows client to S3. Compared this file interface with FSx for Windows File Server and examined why changes made directly in S3 may require a cache inventory refresh. | 10/14/2026 | 10/14/2026 | FCJ Lab24: [prepare S3](https://000024.awsstudygroup.com/1-prepare/1.1-creates3/), [prepare the gateway instance](https://000024.awsstudygroup.com/1-prepare/1.2-createstoragegwinstance/), [create a gateway](https://000024.awsstudygroup.com/2-useawsstoragegw/2.1-createstoragegw/), [create a file share](https://000024.awsstudygroup.com/2-useawsstoragegw/2.2-createfileshare/), [mount the share](https://000024.awsstudygroup.com/2-useawsstoragegw/2.3-mountfileshare/), [clean up](https://000024.awsstudygroup.com/3-cleanup/); [AWS cache refresh](https://docs.aws.amazon.com/filegateway/latest/files3/refresh-cache.html) |
| 5 | Studied FSx for Windows File Server, Active Directory integration, Multi-AZ deployment, and SSD/HDD storage choices. Reviewed the lab's environment and SMB share workflow, and learned how DiskSpd/fio measurements such as throughput, IOPS, and latency help assess a workload without treating sample measurements as personal results. | 10/15/2026 | 10/15/2026 | [AWS FSx overview](https://docs.aws.amazon.com/fsx/latest/WindowsGuide/what-is.html); FCJ Lab25: [prepare the environment](https://000025.awsstudygroup.com/2-prerequiste/2.1-cloudformation/), [create SSD Multi-AZ](https://000025.awsstudygroup.com/2-prerequiste/2.2-create-maz-ssd-file-system/), [create HDD Multi-AZ](https://000025.awsstudygroup.com/2-prerequiste/2.3-create-maz-hdd-file-system/), [create file shares](https://000025.awsstudygroup.com/3-create-new-file-shares/), [test performance](https://000025.awsstudygroup.com/4-test-performance/) |
| 6 | Studied FSx operational topics: CloudWatch monitoring, data deduplication, shadow copies, sessions and open files, user quotas, throughput and storage capacity changes, and cleanup. Compared the purpose of these controls and reviewed which resources and outputs a lab operator should check. | 10/16/2026 | 10/16/2026 | FCJ Lab25: [monitor performance](https://000025.awsstudygroup.com/5-monitor-performance/), [data deduplication](https://000025.awsstudygroup.com/6-enable-data-dedup/), [shadow copies](https://000025.awsstudygroup.com/7-enable-shadow-copies/), [sessions and open files](https://000025.awsstudygroup.com/8-manage-user-sessions-open-files/), [quotas](https://000025.awsstudygroup.com/9-enable-quotas/), [scale throughput](https://000025.awsstudygroup.com/11-scale-throughput-capacity/), [scale storage](https://000025.awsstudygroup.com/12-scale-storage-capacity/), [clean up](https://000025.awsstudygroup.com/13-delete-environment/); [AWS deduplication guidance](https://docs.aws.amazon.com/fsx/latest/WindowsGuide/managing-data-dedup.html), [storage capacity](https://docs.aws.amazon.com/fsx/latest/WindowsGuide/managing-storage-configuration.html), [throughput capacity](https://docs.aws.amazon.com/fsx/latest/WindowsGuide/managing-throughput-capacity.html) |

### Week 5 Achievements

- Explained the main steps in VM Import/Export and the roles of a virtual disk, an AMI, an EC2 instance, S3, and the service role.
- Distinguished the permissions used by the caller from the permissions granted to VM Import/Export, and identified why `iam:PassRole` and the role trust relationship matter.
- Refreshed the S3 File Gateway concepts from Week 4 and compared its file access model with FSx for Windows File Server.
- Compared FSx deployment and storage options, including Active Directory integration, Multi-AZ, SSD, and HDD.
- Summarized how to interpret performance measurements and use monitoring to investigate a file workload; no sample benchmark values were recorded as personal measurements.
- Distinguished data deduplication, shadow copies, quotas, and capacity scaling by the operational problem each addresses.

### Lessons Learned

- I learned to check operating system and boot-mode compatibility before assessing a VM import. AWS VM Import/Export supports both UEFI and Legacy BIOS, subject to the source image and operating system requirements.
- I distinguished the permissions of the user or role making an import/export request from the service role assumed by VM Import/Export. A correct service role alone does not grant the caller permission to pass that role.
- I learned to follow an import or export task through its output and then assess whether the resulting image or instance meets the intended use; a task status by itself does not establish application readiness.
- I distinguished SMB/NFS access through S3 File Gateway from the S3 objects used as its backing storage. Changes made directly in S3 may require the gateway's cached object inventory to be refreshed.
- I learned to select FSx storage and throughput settings according to workload needs. A short benchmark is a measurement under its test conditions, not a guarantee of sustained application performance.
- I distinguished shadow copies, which provide access to earlier file versions when available, from file system backups. Quotas and deduplication address different storage-management needs.
- I learned that file system storage capacity and throughput are separate settings. Storage capacity increases are not reversible, so changes and remaining resources should be reviewed with cost and cleanup requirements in mind.

### Next Steps

- Continue with the Week 6 learning topics and apply the relevant storage and access-control concepts when the project scope is available.
- Project work for Week 5: **[TO BE COMPLETED: add the project scope, work performed, dates, and actual outcome or artifact.]**
