---
title: "Worklog Tuần 7"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.7. </b> "
---

Trong Tuần 7 (26–30/10/2026), tôi rà proposal và sơ đồ AWS cho dự án FCAJ Hackathon System, chuẩn bị bàn giao giữa Backend 1 và Backend 2, đồng thời tìm hiểu các điều kiện về cơ sở dữ liệu và mạng để chạy backend với Amazon RDS for MySQL 8.4.

### Mục tiêu tuần 7

- Giải thích đường truy cập của người dùng, luồng phát hành ứng dụng và luồng xử lý AI trong kiến trúc đề xuất.
- Nhận diện rủi ro tương thích schema trước khi chuyển từ MySQL 8.0 sang MySQL 8.4.
- Chuẩn bị checklist bàn giao gồm revision mã nguồn, kiểm thử, migration, cấu hình runtime và quyền truy cập.
- Đọc cấu hình VPC và RDS private trên AWS Console để xác định những mục cần rà trước khi thử kết nối.

### Các công việc đã hoàn thành trong tuần

| Thứ | Công việc đã hoàn thành | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | Rà proposal v1 và kế hoạch vẽ kiến trúc cùng GPT/Codex. Làm rõ EC2 là hướng chạy backend trong đề xuất, còn Lambda là hướng khảo sát riêng. Lần theo đường truy cập, luồng triển khai và luồng gửi job/trả kết quả qua SQS, gồm vai trò của hàng đợi lỗi (DLQ). So sánh nhánh đang làm với `develop` để xác định có cần pull hoặc merge; liên hệ VPC, subnet và hướng định tuyến với sơ đồ đề xuất. | 26/10/2026 | 26/10/2026 | [Issue #7](https://github.com/nhatnhm1405/fcaj-hackathon-system/issues/7), [Subnets](https://www.youtube.com/watch?v=DHYgA94SefE), [Route table](https://www.youtube.com/watch?v=dHoYmQR7FYs) |
| 3 | Đối chiếu bản dump MySQL 8.0 với mapping Hibernate và phát hiện khác biệt chữ hoa/thường của tên bảng cần kiểm tra trước khi chuyển sang MySQL 8.4. Bổ sung `lower_case_table_names` và bước thử trên cơ sở dữ liệu riêng vào ghi chú bàn giao. Rà ba sơ đồ tổng quan, luồng AI và triển khai cùng GPT/Codex, chọn sơ đồ tổng quan làm hình chính. Trao đổi phương án dùng lại kết quả phân tích AI cho cùng revision của bài nộp. | 27/10/2026 | 27/10/2026 | [Issue #13](https://github.com/nhatnhm1405/fcaj-hackathon-system/issues/13), [Issue #14](https://github.com/nhatnhm1405/fcaj-hackathon-system/issues/14), [RDS for MySQL](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/MySQL.KnownIssuesAndLimitations.html) |
| 4 | Chuẩn bị checklist bàn giao Backend 1/2: commit mã nguồn, kết quả test theo revision, Flyway V1–V3, cấu hình Docker Compose/runtime, quyền IAM và luồng kiểm tra bằng mock worker. Rà nhánh ứng viên của Backend 1 trong Git worktree riêng, xác định phần việc Backend 2 có thể chuẩn bị trước khi tích hợp. Dùng GPT/Codex tạo và cài skill bàn giao để chuẩn bị ghi chú dự án thuận tiện hơn. | 28/10/2026 | 28/10/2026 | [Nhánh ứng viên Backend 1](https://github.com/nhatnhm1405/fcaj-hackathon-system/commit/bab44e5), [Issue #14](https://github.com/nhatnhm1405/fcaj-hackathon-system/issues/14), [IAM role cho EC2](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-roles-for-amazon-ec2.html) |
| 5 | Ôn phần Amazon RDS/MySQL trong Module 06-02 và đối chiếu tài liệu AWS. Chuẩn bị checklist đọc cấu hình RDS private: DB subnet group, security group, DNS endpoint và tham số `lower_case_table_names`. | 29/10/2026 | 29/10/2026 | [Amazon RDS & Aurora](https://www.youtube.com/watch?v=qbrobQZrokY), [RDS trong VPC](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_VPC.WorkingWithRDSInstanceinaVPC.html), [RDS security groups](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Overview.RDSSecurityGroups.html), [RDS for MySQL](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/MySQL.KnownIssuesAndLimitations.html) |
| 6 | Dùng ảnh AWS Console và GPT/Codex để xác định nơi lấy VPC/subnet ID và đối chiếu Availability Zone, DB subnet group và security group. Ghi nhận instance MySQL 8.4 hiển thị ở chế độ private và xác định những mục cần kiểm trước migration: parameter group, DNS endpoint và kết nối từ EC2. Tôi cũng chuẩn bị bản nháp Blog 2 về Lambda concurrency và throttling. | 30/10/2026 | 30/10/2026 | [RDS trong VPC](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_VPC.WorkingWithRDSInstanceinaVPC.html), [RDS security groups](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Overview.RDSSecurityGroups.html) |

### Kết quả đạt được tuần 7

- Chọn sơ đồ kiến trúc chính và xác định phần thông tin nên trình bày ở sơ đồ luồng AI và sơ đồ triển khai.
- Nhận diện rủi ro chữ hoa/thường của tên bảng và bổ sung bước kiểm thử trên cơ sở dữ liệu riêng vào checklist migration.
- Chuẩn bị các đầu vào bàn giao về revision, kiểm thử, migration, cấu hình runtime và quyền.
- Chuẩn bị checklist RDS private và dùng ảnh Console để rà cấu hình hiển thị. Kết nối EC2 tới RDS và migration vẫn cần kiểm chứng.

### Bài học rút ra sau khi học

- Tôi rút ra mỗi sơ đồ nên trả lời một câu hỏi cụ thể: người dùng vào hệ thống bằng đường nào, một job AI được xử lý ra sao hoặc bản phát hành tới máy chủ bằng cách nào.
- Đối chiếu bản dump với mapping ứng dụng giúp tôi phát hiện rủi ro trước migration. Vẫn cần kiểm thử với phiên bản MySQL đích để xác nhận tương thích.
- Tôi hiểu cần kiểm tra định tuyến, security group và quyền của ứng dụng riêng. Cấu hình hiển thị trên Console giúp xác định bước kiểm tiếp theo; cần thử kết nối mới xác nhận được ứng dụng truy cập cơ sở dữ liệu.

### Bước tiếp theo

- Kiểm kê tài nguyên PoC ở Tuần 8, xác định revision ứng viên và yêu cầu runtime, rồi thống nhất thứ tự kiểm kết nối database, migration và luồng mock worker.


