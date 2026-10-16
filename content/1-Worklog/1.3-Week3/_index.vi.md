---
title: "Worklog Tuần 3"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.3. </b> "
---

Trong tuần thứ ba (28/09/2026–02/10/2026), tôi học cách kết nối nhiều VPC, tìm hiểu EC2 và các lựa chọn lưu trữ, sau đó thực hành quy trình backup và kiểm tra khôi phục bằng AWS Backup. Tôi ghi lại nội dung theo từng ngày, từ VPC Peering đến cleanup tài nguyên.

### Mục tiêu tuần 3

- Hiểu cách kết nối hai VPC qua VPC Peering, cấu hình route và phân giải DNS giữa các mạng.
- Tìm hiểu Transit Gateway, VPC attachments và cách phối hợp VPC route tables với TGW route tables.
- Nắm tiêu chí chọn EC2 instance types, AMI, key pair và snapshot theo workload.
- Phân biệt EBS với instance store, đồng thời tìm hiểu EFS và FSx cho nhu cầu lưu trữ tệp.
- Hiểu vai trò của User Data, instance metadata, EC2 Auto Scaling, Lightsail và AWS MGN.
- Thiết lập backup plan và kiểm tra restore; nhận diện trách nhiệm cleanup của từng tài nguyên.

### Các công việc đã hoàn thành trong tuần

| Thứ | Công việc đã hoàn thành | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | Đã thiết lập môi trường hai VPC cho Lab19, cấu hình Security Group và Network ACL, tạo VPC Peering, thêm route hai phía, bật Cross-Peer DNS; kiểm tra kết nối qua private IP và dọn tài nguyên lab. | 28/09/2026 | 28/09/2026 | [Playlist Module 02, Lab19 — 9 video](https://www.youtube.com/playlist?list=PLahN4TLWtox2a3vElknwzU_urND8hLn1i); [FCJ Lab19](https://000019.awsstudygroup.com/); [VPC peering](https://docs.aws.amazon.com/vpc/latest/peering/vpc-peering-basics.html), [peering DNS](https://docs.aws.amazon.com/vpc/latest/peering/vpc-peering-dns.html) |
| 3 | Đã thiết lập mô hình bốn VPC kết nối qua Transit Gateway; cấu hình attachments, association/propagation và route tables; kiểm tra luồng kết nối giữa EC2 bằng bài lab và phân tích đường đi theo cấu hình bằng Reachability Analyzer; dọn tài nguyên. | 29/09/2026 | 29/09/2026 | [Playlist Module 02, Lab20 — 7 video](https://www.youtube.com/playlist?list=PLahN4TLWtox2a3vElknwzU_urND8hLn1i); [FCJ Lab20](https://000020.awsstudygroup.com/); [How Transit Gateway works](https://docs.aws.amazon.com/vpc/latest/tgw/how-transit-gateways-work.html), [Reachability Analyzer](https://docs.aws.amazon.com/vpc/latest/reachability/how-reachability-analyzer-works.html) |
| 4 | Đã học khái niệm compute VM, tiêu chí chọn EC2 instance type, AMI, key pair và backup; so sánh Amazon EBS với instance store về cách gắn kết, vòng đời dữ liệu và tình huống sử dụng. | 30/09/2026 | 30/09/2026 | [Compute VM](https://www.youtube.com/watch?v=-t5h4N6vfBs), [AMI / Backup / Key Pair](https://www.youtube.com/watch?v=yAR6QRT3N1k), [EBS](https://www.youtube.com/watch?v=hKr_TfGP7NY), [Instance store](https://www.youtube.com/watch?v=6IHNDJ85aoQ); [EC2 instance types](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instance-types.html), [EBS](https://docs.aws.amazon.com/ebs/latest/userguide/what-is-ebs.html), [Instance store persistence](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instance-store-lifetime.html) |
| 5 | Đã tìm hiểu User Data và instance metadata, cơ chế EC2 Auto Scaling; so sánh vai trò của EFS, FSx, Lightsail và AWS Application Migration Service theo nhu cầu khởi tạo, co giãn, lưu trữ tệp và di chuyển ứng dụng. | 01/10/2026 | 01/10/2026 | [User Data](https://www.youtube.com/watch?v=_v_43Wi7zjo), [Metadata](https://www.youtube.com/watch?v=Ew3QRaKJQSA), [EC2 Auto Scaling](https://www.youtube.com/watch?v=bbLcPitXJSY), [Compute services overview](https://www.youtube.com/watch?v=hFVYG8WqfU0); [EC2 User Data](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/user-data.html), [EC2 instance types](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instance-types.html) |
| 6 | Đã chuẩn bị hạ tầng lab AWS Backup, tạo backup plan/vault và gán tài nguyên; kiểm tra backup job, quy trình restore có Lambda và thông báo, xem restore jobs/log, rồi cleanup các tài nguyên theo phạm vi quản lý. | 02/10/2026 | 02/10/2026 | [FCJ Lab13 — Introduction](https://000013.awsstudygroup.com/1-introduce/), [Deploy infrastructure](https://000013.awsstudygroup.com/2-prerequiste/2.2-deployinfras/), [Create Backup plan](https://000013.awsstudygroup.com/3-createbackupplan/), [Test Restore](https://000013.awsstudygroup.com/5-testrestore/), [Cleanup](https://000013.awsstudygroup.com/6-cleanup/); [S3/template preparation](https://000013.awsstudygroup.com/2-prerequiste/2.1-creates3bucket/), [notifications](https://000013.awsstudygroup.com/4-enablenoti/) |

### Kết quả đạt được tuần 3

- Hoàn thành gói học gồm 24 video YouTube và 6 trang tài liệu FCJ/AWS bổ sung, được tổng hợp thành năm nhóm hoạt động theo ngày.
- Cấu hình VPC Peering trong lab và hiểu các điều kiện cần cho kết nối giữa hai VPC, gồm CIDR không chồng lấn, route hai phía và quy tắc bảo mật phù hợp.
- Thiết lập mô hình nhiều VPC qua Transit Gateway; phân biệt route trong VPC với route trong TGW, cùng vai trò của attachment, association và propagation.
- Tổng hợp tiêu chí lựa chọn EC2 instance type và hiểu khác biệt về tính bền dữ liệu giữa EBS và instance store.
- Phân biệt User Data với metadata; nắm mục đích của Auto Scaling, EFS, FSx, Lightsail và MGN ở mức tổng quan.
- Tạo backup plan trong lab, theo dõi backup/restore jobs và log; hiểu vì sao cần kiểm tra khả năng khôi phục ứng dụng và cleanup cả tài nguyên ngoài stack.

### Bài học rút ra sau khi học

- Tôi rút ra rằng trạng thái VPC Peering active chưa đủ để đảm bảo ứng dụng kết nối được. Tôi cần xem CIDR, route hai phía, Security Group, Network ACL và cách phân giải tên miền theo đúng luồng.
- Tôi phân biệt được VPC route table với TGW route table. Association chọn bảng TGW xử lý traffic từ attachment, còn propagation đưa các route của attachment vào bảng được chọn.
- Reachability Analyzer giúp tôi phân tích tính khả thi theo cấu hình mạng; kết quả của công cụ không thay thế kiểm tra kết nối thực tế của ứng dụng.
- Tôi hiểu lựa chọn EBS hay instance store phụ thuộc vào hiệu năng và yêu cầu lưu dữ liệu. Instance store phù hợp dữ liệu tạm như cache; dữ liệu cần giữ lâu dài phải nằm trên storage bền vững phù hợp.
- Tôi rút ra AMI và User Data hỗ trợ khởi tạo các instance nhất quán, trong khi metadata cung cấp thông tin của instance cho quy trình vận hành. Đây là những khái niệm hữu ích khi tìm hiểu Auto Scaling.
- Tôi hiểu tạo backup thành công và khôi phục workload thành công là hai kết quả khác nhau. Cần xác định tiêu chí kiểm tra restore và quản lý vòng đời tài nguyên được tạo trong quá trình kiểm thử.

### Bước tiếp theo

Ở Tuần 4, tôi chuyển sang S3, CloudFront và các chủ đề lưu trữ tiếp theo trong lộ trình học AWS.
