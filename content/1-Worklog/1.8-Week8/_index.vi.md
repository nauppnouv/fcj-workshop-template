---
title: "Worklog Tuần 8"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.8. </b> "
---

Trong Tuần 8 (02–06/11/2026), tôi cùng team rà kiến trúc bản chứng minh ý tưởng (PoC) của FCAJ Hackathon System, kiểm kê môi trường AWS và chuẩn bị phát hành Backend 2. Sau đó, tôi ghi lại phạm vi đã kiểm tra của frontend, API và luồng worker.

### Mục tiêu tuần 8

- Làm rõ cách tách frontend tĩnh, API và vùng lưu dữ liệu ứng dụng.
- Đối chiếu tài nguyên AWS tại Singapore với mẫu CloudFormation và xác định những điểm còn thiếu trước khi triển khai.
- Chuẩn bị quy trình phát hành có thể truy về đúng revision mã nguồn và Docker image.
- Kiểm tra HTTPS, việc phân phối frontend và đường truyền thông điệp bằng worker giả lập.

### Các công việc đã hoàn thành trong tuần

| Thứ | Công việc đã hoàn thành | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | Nghiên cứu kiến trúc đề xuất cùng team. Lần theo luồng frontend qua CloudFront đến bucket S3 private và luồng API qua Caddy đến backend Spring Boot trên EC2 rồi tới RDS. Rà cách S3 Block Public Access và CloudFront Origin Access Control (OAC) phối hợp với bucket policy. Phân biệt tệp frontend với tệp ứng dụng và kết quả AI. | 02/11/2026 | 02/11/2026 | [Issue #14](https://github.com/nhatnhm1405/fcaj-hackathon-system/issues/14), [Amazon S3](https://www.youtube.com/watch?v=_yunukwcAwc), [S3 Block Public Access](https://docs.aws.amazon.com/AmazonS3/latest/userguide/access-control-block-public-access.html), [CloudFront OAC](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/private-content-restricting-access-to-s3.html) |
| 3 | Kiểm tra kết nối công cụ AWS cùng GPT/Codex và kiểm kê môi trường PoC tại Singapore: stack CloudFormation, S3, hàng đợi công việc và kết quả SQS cùng các hàng đợi lỗi, ECR, nhóm log, EC2/SSM và RDS. Đối chiếu tài nguyên với mẫu triển khai, ghi lại các điểm còn thiếu về quyền runtime, image và log, đồng thời phát hiện chênh lệch visibility timeout giữa hàng đợi và mẫu. | 03/11/2026 | 03/11/2026 | [Issue #14](https://github.com/nhatnhm1405/fcaj-hackathon-system/issues/14), [SSM Run Command](https://docs.aws.amazon.com/systems-manager/latest/userguide/run-command.html), [SQS visibility timeout](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-visibility-timeout.html) |
| 4 | Nghiên cứu luồng phát hành cùng team, từ revision đã kiểm thử đến Docker image trong ECR, rồi từ lệnh SSM đến việc EC2 kéo đúng image theo digest. Xác định các điểm cần kiểm: RDS trước khi khởi động, frontend qua CloudFront, API qua HTTPS, truy cập S3 ẩn danh và đường truyền SQS/S3 bằng worker giả lập. | 04/11/2026 | 04/11/2026 | [Issue #14](https://github.com/nhatnhm1405/fcaj-hackathon-system/issues/14), [ECR pull theo digest](https://docs.aws.amazon.com/AmazonECR/latest/userguide/docker-pull-ecr-image.html), [SSM Run Command](https://docs.aws.amazon.com/systems-manager/latest/userguide/run-command.html), [Kiểm tra CloudFront](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/GettingStarted.SimpleDistribution.html), [SQS visibility timeout](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-visibility-timeout.html) |
| 5 | Chuẩn bị quy trình phát hành PoC bằng image ECR ghim theo digest, triển khai qua SSM và kiểm RDS trước khi khởi động backend. Đối chiếu revision và image của bản ứng viên đang chạy với hồ sơ triển khai. Chuẩn bị phân phối frontend qua S3 private và CloudFront, cùng cấu hình HTTPS cho API qua Caddy. | 05/11/2026 | 05/11/2026 | [Báo cáo release PoC công khai](https://github.com/nhatnhm1405/fcaj-hackathon-system/blob/9caeef3572a3c5eb92c5b3dc8d98c6f728621b85/docs/report/issue-14-execution-status-2026-11-05.md), [PR #24](https://github.com/nhatnhm1405/fcaj-hackathon-system/pull/24) |
| 6 | Ghi nhận kết quả kiểm tra HTTPS, tệp frontend tĩnh và truy cập từ trình duyệt khi chưa đăng nhập. Kiểm tra worker Java giả lập nhận job qua SQS, đọc/ghi S3 và gửi kết quả. Cập nhật tài liệu trong PR nháp và lược định danh môi trường khỏi báo cáo công khai. Lượt này kiểm đường truyền SQS/S3; luồng đăng nhập và worker AI thật vẫn cần xác minh. | 06/11/2026 | 06/11/2026 | [Báo cáo kiểm tra công khai](https://github.com/nhatnhm1405/fcaj-hackathon-system/blob/9caeef3572a3c5eb92c5b3dc8d98c6f728621b85/docs/report/issue-14-execution-status-2026-11-05.md), [PR #24](https://github.com/nhatnhm1405/fcaj-hackathon-system/pull/24) |

**Ghi chú cuối tuần (07/11):** Kiểm tra dung lượng Docker Desktop và xóa một image Maven cũ sau khi xác nhận không có container nào tham chiếu. Giữ nguyên container và volume. [Dung lượng Docker](https://docs.docker.com/reference/cli/docker/system/df/)

### Kết quả đạt được tuần 8

- Cùng team làm rõ luồng frontend và API, đồng thời xác định các mục cần kiểm khi phát hành.
- Ghi lại hiện trạng AWS PoC và các khác biệt cấu hình cần xử lý trước khi chạy backend.
- Chuẩn bị triển khai theo image digest và ghi lại revision ứng viên cùng bước kiểm RDS.
- Ghi nhận kết quả kiểm HTTPS, frontend và một lượt Java mock qua SQS/S3 trong PR nháp #24.

### Bài học rút ra sau khi học

- Tôi hiểu kiểm kê CloudFormation cho biết tài nguyên nào đang tồn tại. Để biết ứng dụng đã sẵn sàng, còn phải kiểm image, quyền runtime và khả năng truy cập cơ sở dữ liệu.
- Tôi rút ra cần ghi revision mã nguồn và image digest để truy được bản chạy trên EC2. ECR lưu image; SSM gửi lệnh triển khai.
- Một lượt mock thành công xác nhận phần đường truyền thông điệp và lưu trữ đã kiểm. Đăng nhập, luồng nghiệp vụ và xử lý bằng worker AI thật cần các lượt kiểm riêng.

### Bước tiếp theo

- Cùng team rà PR #24, làm rõ quyền truy cập và điều kiện phát hành, rồi lập kế hoạch kiểm tiếp API và luồng sau đăng nhập trong Tuần 9.
