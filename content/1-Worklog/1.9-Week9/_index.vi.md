---
title: "Worklog Tuần 9"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.9. </b> "
---

Trong Tuần 9 (09–13/11/2026), tôi tiếp tục công việc trên bản chứng minh ý tưởng (PoC) của FCAJ Hackathon System. Tôi rà thay đổi của Backend 2, thiết lập quyền truy cập AWS cho team và kiểm tra API sau khi chuyển luồng HTTPS sang Application Load Balancer.

### Mục tiêu tuần 9

- Rà pull request của Backend 2 và ghi lại phạm vi kiểm thử.
- Cấp quyền truy cập AWS theo nhiệm vụ của từng thành viên.
- Xác minh luồng HTTPS qua Application Load Balancer và phản hồi API.
- Xác minh bước build Docker image trong GitHub Actions và xác định các mục còn cần kiểm khi phát hành và nghiệm thu.

### Các công việc đã hoàn thành trong tuần

| Thứ | Công việc đã hoàn thành | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | Đối chiếu phạm vi Backend 2 trong Issue #17 với quy ước trao đổi dữ liệu qua SQS/S3 và kiểm lại CI, kiểm thử triển khai và cơ sở dữ liệu của PR #24. Chuyển PR từ Draft sang Ready for review. Maintainer đã merge PR vào `develop`. Worker Java giả lập đã kiểm đường truyền qua SQS/S3, còn worker AI bằng Python vẫn cần kiểm thử đầu cuối. | 09/11/2026 | 09/11/2026 | [Issue #17][issue17], [PR #24][pr24] |
| 3 | Rà GitHub environment, OpenID Connect (OIDC), quyền phát hành và các mục cần kiểm trên EC2. Thiết lập quyền truy cập riêng qua AWS Identity and Access Management (IAM) cho bốn thành viên theo nhiệm vụ và gửi hướng dẫn riêng cho từng người. | 10/11/2026 | 10/11/2026 | [Phản hồi review PR #24][lead], [Thực hành tốt về IAM][iam], [GitHub Actions OIDC][oidc] |
| 4 | Cấp quyền xem dịch vụ AWS và log theo phạm vi cho team. Thiết lập Application Load Balancer (ALB) trong VPC hiện có, xác minh chứng chỉ AWS Certificate Manager (ACM) qua DNS và trỏ tên miền API về ALB. Kiểm tra HTTPS, trạng thái target, phản hồi API, CORS và CSRF. Hoàn thiện PR #28 để build và chuyển Docker image dưới dạng artifact giữa các job. Bốn job CI đều đạt tại revision `ff36d57`. Maintainer đã merge PR. | 11/11/2026 | 11/11/2026 | [PR #28][pr28], [Kết quả CI][ci28], [Video về Load Balancer][v-lb], [Video về Security Group][v-sg], [Security group của ALB][alb-sg], [Xác minh ACM qua DNS][acm] |
| 5 | Cùng team nghiên cứu quy trình phát hành sau merge. Rà cách đối chiếu revision mã nguồn và image ID sau khi nạp lại archive, rồi dùng digest trong Amazon Elastic Container Registry (ECR) để chỉ định image EC2 sẽ kéo. Ghi lại nhánh được phép phát hành, GitHub environment, OIDC và quyền AWS Systems Manager (SSM) trong checklist phát hành. | 12/11/2026 | 12/11/2026 | [PR #28][pr28], [Artifact trong GitHub Actions][artifact], [GitHub Actions OIDC][oidc], [Kéo image ECR theo digest][ecr], [SSM Run Command][ssm] |
| 6 | Cùng team rà checklist nghiệm thu và đánh dấu các mục đã kiểm cho HTTPS, trạng thái target và phản hồi API. Xác định các kịch bản còn cần kiểm cho đăng nhập OAuth trên trình duyệt và luồng AI worker, từ nhận job qua SQS, đọc dữ liệu đầu vào từ S3 đến trả kết quả. | 13/11/2026 | 13/11/2026 | [PR #24][pr24], [Issue #17][issue17], [PR #28][pr28] |

### Kết quả đạt được tuần 9

- Chuẩn bị PR #24 để review và ghi lại các lượt kiểm làm căn cứ cho việc merge phần Backend 2.
- Thiết lập quyền truy cập cho bốn thành viên và giới hạn quyền chung ở phạm vi xem dịch vụ và log.
- Xác minh luồng HTTPS qua ALB tới target EC2 và kiểm tra phản hồi API.
- Xác minh bước build Docker image trong CI và ghi lại các mục còn cần kiểm khi phát hành lên AWS và nghiệm thu đầu cuối.

### Bài học rút ra sau khi học

- Thành viên, GitHub Actions và workload trên EC2 cần các quyền khác nhau. Tôi rút ra rằng cần đối chiếu chính sách tin cậy OIDC với environment của workflow và kiểm tra nhánh nào được phép triển khai vào đó. [Thực hành tốt về IAM][iam], [GitHub Actions OIDC][oidc]
- Tôi hiểu security group kiểm soát kết nối từ ALB đến target. CNAME xác minh ACM chứng minh quyền kiểm soát tên miền, còn bản ghi DNS của API đưa lưu lượng đến ALB. [Security group của ALB][alb-sg], [Xác minh ACM qua DNS][acm]
- Tôi học được cách truy vết image từ revision mã nguồn đến image ID trong archive và digest trong ECR. SSM gửi lệnh triển khai, sau đó EC2 kéo image theo digest. [Artifact trong GitHub Actions][artifact], [Kéo image ECR theo digest][ecr], [SSM Run Command][ssm]
- Target healthy và API phản hồi thành công xác nhận các phần cụ thể của hệ thống. Tôi xác định các lượt kiểm riêng cho đăng nhập và cho worker AI bằng Python xử lý job rồi trả kết quả mong đợi. [PR #24][pr24], [Issue #17][issue17]

### Bước tiếp theo

- Xác nhận quyền phát hành và thiết lập environment trước khi chạy workflow sau merge. Thực hiện các kịch bản đăng nhập trên trình duyệt và xử lý job bằng AI worker, rồi ghi lại kết quả.

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
