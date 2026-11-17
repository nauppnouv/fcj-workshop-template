---
title: "Worklog Tuần 6"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.6. </b> "
---

Trong Tuần 6 (19–23/10/2026), tôi bắt đầu phần việc Backend 2 của dự án FCAJ Hackathon System. Tôi rà cách triển khai hiện có, gửi đề xuất chạy backend trên AWS và chia sẻ bài học về Amazon SQS qua Blog 1.

### Mục tiêu tuần 6

- Hiểu cách cấu hình Docker Compose và workflow GitHub Actions hiện tại build và chạy backend.
- Đề xuất quy trình triển khai và quay về phiên bản trước, xác định được chính xác image đang chạy.
- Phác thảo cách backend trao đổi công việc và kết quả với AI worker chạy cục bộ.
- Ghi rõ các giả định trong dự toán AWS và giải thích vì sao message SQS có thể được xử lý lại.

### Các công việc đã hoàn thành trong tuần

| Thứ | Công việc đã hoàn thành | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | Rà yêu cầu Backend 2 trong Issue #7, Dockerfile, cấu hình Docker Compose và workflow triển khai. Xác định luồng hiện có: GitHub Actions chạy kiểm thử rồi kết nối tới EC2 qua SSH để máy chủ lấy mã nguồn và build các container. | 19/10/2026 | 19/10/2026 | [Issue #7](https://github.com/nhatnhm1405/fcaj-hackathon-system/issues/7), [Compute VM on AWS](https://www.youtube.com/watch?v=-t5h4N6vfBs), [Docker Compose](https://docs.docker.com/compose/) |
| 3 | Gửi bản nháp kỹ thuật đề xuất GitHub Actions build image backend, đẩy lên Amazon Elastic Container Registry (ECR) và đối chiếu revision đang chạy sau triển khai. Đề xuất quay về image theo digest đã biết sau khi kiểm tra tương thích với cơ sở dữ liệu và tệp. Phác thảo luồng từ hàng đợi SQS tới worker cục bộ, lưu tệp đầu ra trên Amazon S3 và trả kết quả về backend qua hàng đợi, kèm cơ chế thử lại, xử lý trùng và hàng đợi lỗi (DLQ) cho thông điệp thất bại nhiều lần. | 20/10/2026 | 20/10/2026 | [Bản nháp kỹ thuật](https://github.com/nhatnhm1405/fcaj-hackathon-system/issues/7#issuecomment-6291981789), [Vòng đời image ECR](https://docs.aws.amazon.com/AmazonECR/latest/userguide/getting-started-cli.html), [Kéo image theo digest](https://docs.aws.amazon.com/AmazonECR/latest/userguide/docker-pull-ecr-image.html), [SQS visibility timeout](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-visibility-timeout.html) |
| 4 | Cập nhật đề xuất theo phản hồi trưởng nhóm: EC2 chạy Docker, ECR, GitHub Actions và CloudFormation; frontend dùng S3 và CloudFront, cơ sở dữ liệu dự kiến là RDS MySQL private. Rà giả định về Region Singapore, cấu hình, tải và thời gian chạy. So sánh hai kịch bản EC2 chạy 160 và 730 giờ/tháng, giả định RDS chạy 730 giờ ở cả hai. Credit AWS chưa được xác minh. | 21/10/2026 | 21/10/2026 | [Phản hồi trưởng nhóm](https://github.com/nhatnhm1405/fcaj-hackathon-system/issues/7#issuecomment-6308395467), [AWS Cost Optimization](https://www.youtube.com/watch?v=IY61YlmXQe8), [AWS Pricing Calculator](https://calculator.aws/), [AWS Budgets](https://docs.aws.amazon.com/cost-management/latest/userguide/budgets-managing-costs.html) |
| 5 | Gửi proposal v1 dạng Markdown đính kèm trên Issue #7, gồm phương án triển khai, luồng thông điệp, dự toán và năm đầu việc đề xuất cho giai đoạn tiếp theo. Đăng Blog 1 lên nhóm Facebook, dùng ví dụ gửi email trùng để giải thích SQS visibility timeout và cách xử lý khi nhận lại message. | 22/10/2026 | 22/10/2026 | [Comment gửi proposal](https://github.com/nhatnhm1405/fcaj-hackathon-system/issues/7#issuecomment-6323090811), [Bài đăng Facebook](https://www.facebook.com/share/p/1CJMAYWQBf/), [SQS visibility timeout](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-visibility-timeout.html) |
| 6 | Đưa Blog 1 bản tiếng Anh và tiếng Việt lên repo workshop, giữ ngày đăng gốc 22/10 và dẫn lại bài Facebook cùng tài liệu AWS. | 23/10/2026 | 23/10/2026 | [Bản cập nhật Blog 1 song ngữ](https://github.com/nauppnouv/fcj-workshop-template/commit/18ababc4a69b852d4a74e0310612764ca58a56c2), [Bài đăng Facebook](https://www.facebook.com/share/p/1CJMAYWQBf/) |

### Kết quả đạt được tuần 6

- Gửi đề xuất Backend 2 để nhóm rà soát, gồm cách triển khai và quay về bản trước, luồng xử lý công việc và trả kết quả, cùng năm đầu việc tiếp theo.
- Lập hai kịch bản chi phí với giả định rõ về thời gian chạy của từng tài nguyên và ghi lại phần credit AWS cần xác minh.
- Đăng bài SQS lên nhóm Facebook và đưa hai bản EN/VI lên repo workshop.

### Bài học rút ra sau khi học

- Tôi rút ra cần truy được một bản phát hành từ commit đến đúng image đang chạy. Digest định danh image; khả năng quay về bản trước còn phụ thuộc vào việc ứng dụng cũ có dùng được schema và tệp hiện tại hay không.
- Tôi hiểu khi so sánh chi phí, cần nêu cách sử dụng từng tài nguyên. Thay đổi giờ chạy EC2 không làm thay đổi chi phí RDS nếu vẫn giả định RDS chạy liên tục.
- Tôi hiểu worker dùng SQS Standard phải xử lý được message nhận lại mà không lặp tác dụng phụ. Visibility timeout và DLQ hỗ trợ quản lý việc thử lại; ứng dụng vẫn phải ngăn hành động trùng.

### Bước tiếp theo

- Làm rõ bàn giao giữa Backend 1 và Backend 2: xác định revision và kết quả kiểm thử, rà điều kiện cơ sở dữ liệu và mạng, rồi thống nhất cách kiểm chứng một lượt triển khai nhỏ.


