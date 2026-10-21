---
title: "Worklog Tuần 5"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.5. </b> "
---

Trong tuần thứ năm (12–16/10/2026), tôi học về VM Import/Export, ôn lại quy trình S3 File Gateway và tìm hiểu cách vận hành Amazon FSx for Windows File Server. Nội dung tập trung vào điều kiện và quyền truy cập khi di chuyển máy ảo, lưu trữ tệp lai, file share Windows, giám sát hiệu năng và bảo vệ dữ liệu.

### Mục tiêu tuần 5

- Giải thích quy trình VM Import/Export và phân biệt Amazon Machine Image (AMI) với EC2 instance đang chạy.
- Nhận biết các quyền IAM và yêu cầu S3 khi nhập hoặc xuất máy ảo.
- Ôn cách S3 File Gateway cung cấp giao diện file SMB/NFS với dữ liệu lưu trữ phía sau trên Amazon S3.
- So sánh các lựa chọn lưu trữ và triển khai FSx for Windows File Server cho workload Windows.
- Hiểu vai trò của monitoring, quotas, data deduplication, shadow copies và thay đổi dung lượng trong vận hành file server.
- Nắm các tài nguyên và số liệu cần kiểm tra khi đánh giá quy trình migration hoặc storage lab.

### Các công việc đã hoàn thành trong tuần

| Thứ | Công việc đã hoàn thành | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | Tìm hiểu cách chuẩn bị máy ảo, xuất đĩa ảo và đưa lên S3 để sử dụng với VM Import/Export. Phân biệt quyền IAM của người gọi, `iam:PassRole` và service role `vmimport`, gồm trust policy và permissions policy của role. | 12/10/2026 | 12/10/2026 | FCJ Lab14: [Chuẩn bị VM](https://000014.awsstudygroup.com/1-deploy-application-server/), [xuất từ môi trường ảo hóa](https://000014.awsstudygroup.com/2-import-vm-to-aws/1-export-vm-from-virtual-env/), [tải VM lên AWS](https://000014.awsstudygroup.com/2-import-vm-to-aws/2-upload-vm-to-aws/), [nhập VM](https://000014.awsstudygroup.com/2-import-vm-to-aws/3-import-vm-to-ami/); [quyền VM Import/Export của AWS](https://docs.aws.amazon.com/vm-import/latest/userguide/required-permissions.html), [boot mode được hỗ trợ](https://docs.aws.amazon.com/vm-import/latest/userguide/prerequisites.html) |
| 3 | Tìm hiểu luồng import đĩa ảo thành AMI rồi khởi chạy EC2, cùng quy trình export instance đủ điều kiện về S3. Ôn cách theo dõi trạng thái task, các yêu cầu của bucket đích và những tài nguyên cần rà soát khi cleanup như AMI, snapshot, volume và object S3. | 13/10/2026 | 13/10/2026 | FCJ Lab14: [Triển khai instance từ AMI](https://000014.awsstudygroup.com/2-import-vm-to-aws/4-deploy-imported-vm/), [cấu hình S3 cho export](https://000014.awsstudygroup.com/3-export-vm-from-aws/1-config-s3-for-exporting/), [export instance](https://000014.awsstudygroup.com/3-export-vm-from-aws/2-export-from-instance/), [dọn tài nguyên](https://000014.awsstudygroup.com/4-clean-up/); [điều kiện export của AWS](https://docs.aws.amazon.com/vm-import/latest/userguide/vmexport-prerequisites.html) |
| 4 | Ôn lại quy trình S3 File Gateway đã học trong Week 4: gateway appliance, cache, SMB file share và đường đi của dữ liệu từ Windows client lên S3. So sánh giao diện file này với FSx for Windows File Server và tìm hiểu vì sao thay đổi trực tiếp trên S3 có thể cần refresh cache inventory. | 14/10/2026 | 14/10/2026 | FCJ Lab24: [chuẩn bị S3](https://000024.awsstudygroup.com/1-prepare/1.1-creates3/), [chuẩn bị gateway instance](https://000024.awsstudygroup.com/1-prepare/1.2-createstoragegwinstance/), [tạo gateway](https://000024.awsstudygroup.com/2-useawsstoragegw/2.1-createstoragegw/), [tạo file share](https://000024.awsstudygroup.com/2-useawsstoragegw/2.2-createfileshare/), [mount share](https://000024.awsstudygroup.com/2-useawsstoragegw/2.3-mountfileshare/), [cleanup](https://000024.awsstudygroup.com/3-cleanup/); [refresh cache theo tài liệu AWS](https://docs.aws.amazon.com/filegateway/latest/files3/refresh-cache.html) |
| 5 | Tìm hiểu FSx for Windows File Server, tích hợp Active Directory, triển khai Multi-AZ và lựa chọn ổ SSD/HDD. Đọc quy trình lab về môi trường và SMB share; tìm hiểu cách dùng số đo DiskSpd/fio như throughput, IOPS và latency để đánh giá workload mà không xem số liệu mẫu là kết quả cá nhân. | 15/10/2026 | 15/10/2026 | [Tổng quan FSx của AWS](https://docs.aws.amazon.com/fsx/latest/WindowsGuide/what-is.html); FCJ Lab25: [chuẩn bị môi trường](https://000025.awsstudygroup.com/2-prerequiste/2.1-cloudformation/), [tạo SSD Multi-AZ](https://000025.awsstudygroup.com/2-prerequiste/2.2-create-maz-ssd-file-system/), [tạo HDD Multi-AZ](https://000025.awsstudygroup.com/2-prerequiste/2.3-create-maz-hdd-file-system/), [tạo file share](https://000025.awsstudygroup.com/3-create-new-file-shares/), [kiểm tra hiệu năng](https://000025.awsstudygroup.com/4-test-performance/) |
| 6 | Tìm hiểu các nội dung vận hành FSx: giám sát bằng CloudWatch, data deduplication, shadow copies, sessions và open files, user quotas, thay đổi throughput/storage capacity và cleanup. So sánh mục đích của từng cơ chế và rà soát tài nguyên, kết quả mà người vận hành cần kiểm tra. | 16/10/2026 | 16/10/2026 | FCJ Lab25: [giám sát hiệu năng](https://000025.awsstudygroup.com/5-monitor-performance/), [data deduplication](https://000025.awsstudygroup.com/6-enable-data-dedup/), [shadow copies](https://000025.awsstudygroup.com/7-enable-shadow-copies/), [sessions và open files](https://000025.awsstudygroup.com/8-manage-user-sessions-open-files/), [quotas](https://000025.awsstudygroup.com/9-enable-quotas/), [tăng throughput](https://000025.awsstudygroup.com/11-scale-throughput-capacity/), [tăng storage](https://000025.awsstudygroup.com/12-scale-storage-capacity/), [cleanup](https://000025.awsstudygroup.com/13-delete-environment/); [hướng dẫn deduplication của AWS](https://docs.aws.amazon.com/fsx/latest/WindowsGuide/managing-data-dedup.html), [storage capacity](https://docs.aws.amazon.com/fsx/latest/WindowsGuide/managing-storage-configuration.html), [throughput capacity](https://docs.aws.amazon.com/fsx/latest/WindowsGuide/managing-throughput-capacity.html) |

### Kết quả đạt được tuần 5

- Trình bày được các bước chính của VM Import/Export và vai trò của đĩa ảo, AMI, EC2 instance, S3 và service role.
- Phân biệt quyền của người thực hiện với quyền cấp cho VM Import/Export; hiểu vai trò của `iam:PassRole` và trust relationship.
- Ôn lại kiến thức S3 File Gateway từ Week 4 và so sánh mô hình truy cập tệp với FSx for Windows File Server.
- So sánh các lựa chọn triển khai và lưu trữ FSx, gồm tích hợp Active Directory, Multi-AZ, SSD và HDD.
- Tổng hợp cách đọc số đo hiệu năng và dùng monitoring để tìm hiểu workload file; không ghi số benchmark mẫu thành số đo cá nhân.
- Phân biệt mục đích vận hành của data deduplication, shadow copies, quotas và capacity scaling.

### Bài học rút ra sau khi học

- Tôi rút ra cần kiểm tra hệ điều hành và boot mode trước khi đánh giá việc import máy ảo. VM Import/Export hỗ trợ cả UEFI và Legacy BIOS, tùy yêu cầu của hệ điều hành và ảnh đĩa nguồn.
- Tôi phân biệt quyền của user hoặc role gửi yêu cầu import/export với service role mà VM Import/Export đảm nhận. Cấu hình service role đúng chưa đủ nếu bên gọi không có quyền truyền role.
- Tôi hiểu cần theo dõi task import/export đến tài nguyên đầu ra rồi đánh giá ảnh hoặc instance có đáp ứng mục đích sử dụng hay không; trạng thái task tự nó chưa chứng minh ứng dụng đã sẵn sàng.
- Tôi phân biệt truy cập SMB/NFS qua S3 File Gateway với object trên S3 dùng làm backend. Khi dữ liệu thay đổi trực tiếp trên S3, cần xét inventory cache của gateway.
- Tôi hiểu lựa chọn storage và throughput của FSx cần phù hợp với workload. Kết quả benchmark ngắn phản ánh điều kiện kiểm thử cụ thể, không bảo đảm hiệu năng ứng dụng duy trì.
- Tôi phân biệt shadow copies, dùng để truy cập phiên bản tệp cũ khi có bản phù hợp, với backup của file system. Quotas và deduplication giải quyết các yêu cầu quản lý dung lượng khác nhau.
- Tôi hiểu storage capacity và throughput là hai thiết lập riêng. Storage capacity chỉ tăng, vì vậy cần cân nhắc thay đổi cấu hình cùng chi phí và các tài nguyên còn lại.

### Bước tiếp theo

- Tiếp tục nội dung học của Week 6 và áp dụng kiến thức lưu trữ, kiểm soát truy cập phù hợp khi có phạm vi project.
- Công việc project trong Week 5: **[CẦN BỔ SUNG: mô tả project, việc đã thực hiện, ngày làm, kết quả hoặc artifact thực tế.]**
