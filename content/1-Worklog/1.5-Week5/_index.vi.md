---
title: "Worklog Tuần 5"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.5. </b> "
---

Trong tuần thứ năm (12–16/10/2026), tôi bắt đầu chuẩn bị workshop cùng team cho dự án FCAJ Hackathon System. Tôi tham gia brainstorming, thảo luận phạm vi, phác thảo phương án và nhận hướng công việc Backend 2 để chuẩn bị cho Week 6. Song song, tôi củng cố kiến thức về trách nhiệm bảo mật, AWS Identity and Access Management (IAM) và quản lý chi phí để phục vụ việc lập kế hoạch.

### Mục tiêu tuần 5

- Làm rõ bài toán, đối tượng sử dụng và mục tiêu của workshop cùng team.
- Xác định phạm vi bản chứng minh ý tưởng (PoC) và phân biệt với các ý tưởng mở rộng.
- Liên hệ kiến thức EC2, VPC và S3 với phương án triển khai và luồng dữ liệu ban đầu.
- Củng cố IAM policy, role và cách phân biệt quyền AWS với vai trò người dùng trong ứng dụng.
- Nhận hướng công việc Backend 2 và xác định các đầu vào cần có cho deployment, messaging và dự toán.
- Tổng hợp kế hoạch và các phụ thuộc để bắt đầu công việc Week 6.

### Các công việc đã hoàn thành trong tuần

| Thứ | Công việc đã hoàn thành | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | Tham gia brainstorming với team về bài toán, đối tượng sử dụng và mục tiêu workshop. Trao đổi về một luồng demo tối thiểu có thể hướng dẫn người khác thực hiện lại; tìm hiểu Shared Responsibility Model để liên hệ trách nhiệm của nhóm khi dùng dịch vụ cloud. | 12/10/2026 | 12/10/2026 | [Shared Responsibility Model](https://www.youtube.com/watch?v=tsobAlSg19g); [AWS Well-Architected](https://docs.aws.amazon.com/wellarchitected/latest/framework/the-pillars-of-the-framework.html) |
| 3 | Thảo luận phạm vi PoC, phần có thể tận dụng từ hệ thống hiện có và các ý tưởng cần để sau. Tìm hiểu IAM, policy và role; phân biệt quyền truy cập tài nguyên AWS với vai trò của người dùng trong ứng dụng để chuẩn bị các câu hỏi về bảo mật. | 13/10/2026 | 13/10/2026 | [IAM](https://www.youtube.com/watch?v=N_vlJGAqZxo), [Create IAM Policy](https://www.youtube.com/watch?v=XXjEpIRWJBk), [Create IAM Role](https://www.youtube.com/watch?v=pJWANviu8QM); [IAM best practices](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html) |
| 4 | Phác thảo phương án deployment và đường đi dữ liệu giữa backend với thành phần AI ở mức ban đầu. Ôn kiến thức EC2/S3 và cách workload sử dụng IAM role; xác định các phụ thuộc cần trao đổi thêm với lead, backend và người phụ trách AI. | 14/10/2026 | 14/10/2026 | [Create IAM role — Lab48](https://www.youtube.com/watch?v=j8Gj2DJtZUE), [Using IAM role](https://www.youtube.com/watch?v=Z0liKVSjt_Q); [IAM best practices](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html); [repo dự án](https://github.com/nhatnhm1405/fcaj-hackathon-system) |
| 5 | Thảo luận cách chia nhóm việc và nhận hướng phụ trách Backend 2, tập trung vào phương án deployment, messaging và đầu vào chi phí. Ôn cost optimization; xác định những thông tin cần làm rõ như Region, lịch chạy và tải trước khi lập dự toán. | 15/10/2026 | 15/10/2026 | [AWS Cost Optimization and Working with AWS Support](https://www.youtube.com/watch?v=IY61YlmXQe8); [AWS Budgets](https://docs.aws.amazon.com/cost-management/latest/userguide/budgets-managing-costs.html) |
| 6 | Tổng hợp kế hoạch workshop, các nhóm việc và thứ tự phụ thuộc; chuẩn bị nội dung cần tiếp tục làm trong Week 6. Rà lại phần phụ trách cá nhân, đầu ra cần có và đề cương tài liệu để liên kết việc học với công việc của team. | 16/10/2026 | 16/10/2026 | [Repo dự án](https://github.com/nhatnhm1405/fcaj-hackathon-system); [AWS Well-Architected](https://docs.aws.amazon.com/wellarchitected/latest/framework/the-pillars-of-the-framework.html) |

### Kết quả đạt được tuần 5

- Bắt đầu làm workshop cùng team, làm rõ trọng tâm bài toán và mục đích của luồng demo ban đầu.
- Phân biệt phần cần ưu tiên trong PoC với các ý tưởng mở rộng để tập trung vào phạm vi có thể hoàn thành.
- Phác thảo phương án và nhận diện những câu hỏi về deployment, dữ liệu và phối hợp với thành phần AI cần tiếp tục làm rõ.
- Củng cố cách phân biệt IAM policy, role và quyền trong ứng dụng; liên hệ quyền truy cập với từng thành phần dự kiến.
- Nhận hướng công việc Backend 2 và xác định các đầu vào cần chuẩn bị cho phương án kỹ thuật và dự toán.
- Tổng hợp kế hoạch ban đầu, các phụ thuộc và bước chuyển sang công việc Week 6.

### Bài học rút ra sau khi học

- Tôi nhận ra cần thống nhất bài toán và phạm vi demo trước khi lựa chọn nhiều dịch vụ AWS. Một phương án cần phục vụ mục tiêu workshop và phù hợp với thời gian của team.
- Tôi hiểu sơ đồ kiến trúc cần giúp cả nhóm giải thích được đường đi dữ liệu, trách nhiệm của từng thành phần và những điểm còn cần xác nhận.
- Tôi phân biệt quyền truy cập tài nguyên AWS với vai trò người dùng trong ứng dụng. Khi xây dựng phương án, tôi cần xác định thành phần nào thực hiện hành động nào và cần quyền gì.
- Tôi hiểu vai trò của IAM role đối với workload và nguyên tắc cấp quyền tối thiểu. Việc học policy/role giúp tôi đặt câu hỏi cụ thể hơn khi chuẩn bị phương án truy cập tài nguyên.
- Tôi rút ra dự toán chỉ có ý nghĩa khi đi kèm giả định về tài nguyên, Region, tải và lịch chạy. Credit cũng cần được xác nhận trước khi tính vào chi phí.
- Tôi hiểu việc chia task cần có đầu ra, phụ thuộc và tiêu chí hoàn thành để các phần có thể tích hợp. Tôi ưu tiên học những nội dung phục vụ trực tiếp phần việc của mình.

### Bước tiếp theo

- Bắt đầu công việc Backend 2 trong Week 6: tìm hiểu hiện trạng Dockerfile, Docker Compose và workflow; hoàn thiện phương án deployment, pipeline và rollback.
- Làm rõ hợp đồng job/result và luồng SQS với người phụ trách AI; chuẩn bị dự toán có giả định, nguồn giá và các điểm cần lead xác nhận.
- Theo dõi [Issue #7](https://github.com/nhatnhm1405/fcaj-hackathon-system/issues/7), được tạo ngày 19/10/2026, để thực hiện đầu việc chính thức và cập nhật kết quả review trong Week 6.
- Bổ sung thông tin cá nhân hóa: **[CẦN BỔ SUNG: tên workshop chính thức, ý tưởng đóng góp cụ thể của tôi và liên kết ghi chú/sơ đồ nếu có.]**
