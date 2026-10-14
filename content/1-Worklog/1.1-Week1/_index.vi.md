---
title: "Worklog Tuần 1"
date: 2026-10-07
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---

> **Trạng thái: Kế hoạch học tập.** Bảng dưới đây ghi phạm vi dự kiến của Tuần 1. Ngày học, kết quả thực tế và cảm nhận cá nhân sẽ được cập nhật sau khi có hoạt động tương ứng; nội dung hướng dẫn trong video/Lab không được xem là thao tác đã hoàn thành.

### Mục tiêu tuần 1

- Nắm các khái niệm nền tảng về điện toán đám mây, mô hình trả phí theo mức sử dụng và khả năng co giãn tài nguyên.
- Phân biệt Region, Availability Zone và Edge Location; nhận biết vai trò của Console, CLI và SDK.
- Tìm hiểu tài khoản AWS, IAM và MFA theo hướng quản lý danh tính, quyền truy cập và thông tin xác thực an toàn.
- Làm quen với AWS Budgets, các loại ngân sách và cách theo dõi chi phí.
- Tìm hiểu các kênh AWS Support và sáu trụ cột Well-Architected để chuẩn bị cho các tuần tiếp theo.

### Nội dung học tập theo kế hoạch

| Chủ đề | Phạm vi và đầu ra dự kiến | Nguồn học |
| --- | --- | --- |
| Cloud và cách học | Điện toán đám mây, giá trị của AWS và định hướng học tập; ghi lại các khái niệm cần liên hệ với project sau này. | [Module 01-01](https://www.youtube.com/watch?v=HxYZAK1coOI), [01-02](https://www.youtube.com/watch?v=IK59Zdd1poE), [01-03](https://www.youtube.com/watch?v=HSzrWGqo3ME); [First Cloud Journey](https://cloudjourney.awsstudygroup.com/) |
| Hạ tầng và công cụ | Region/AZ/Edge Location; phân biệt cách quản lý bằng Console, CLI và SDK; khảo sát tối ưu chi phí và Well-Architected. | [Module 01-04](https://www.youtube.com/watch?v=pjr5a-HYAjI), [01-05](https://www.youtube.com/watch?v=2PQYqH_HkXw), [01-06](https://www.youtube.com/watch?v=IY61YlmXQe8), [01-07](https://www.youtube.com/watch?v=Hku7exDBURo); [AWS global infrastructure](https://docs.aws.amazon.com/whitepapers/latest/aws-overview/global-infrastructure.html), [Well-Architected pillars](https://docs.aws.amazon.com/wellarchitected/latest/framework/the-pillars-of-the-framework.html) |
| Tài khoản, IAM và MFA | Tìm hiểu luồng đăng ký/xác thực, MFA, user/group/policy và hỗ trợ tài khoản; ghi lại nguyên tắc bảo vệ danh tính và quyền. | [Lab01-01](https://www.youtube.com/watch?v=waR5S_lljrk), [01-02](https://www.youtube.com/watch?v=1dG5xutGbr4), [01-03](https://www.youtube.com/watch?v=b9pK1oG534Q), [01-04](https://www.youtube.com/watch?v=69iKhwI7k2Y); [FCJ Lab01](https://000001.awsstudygroup.com/), [IAM best practices](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html) |
| Theo dõi chi phí | Tìm hiểu Cost/Usage Budgets, RI/Savings Plans budgets, số liệu actual/forecast và phạm vi cleanup trong Lab. | [Lab07-01](https://www.youtube.com/watch?v=_a09nLVw6Sg), [07-02](https://www.youtube.com/watch?v=sd_KCcZOou0), [07-03](https://www.youtube.com/watch?v=kkcdRBRnxl4), [07-04](https://www.youtube.com/watch?v=aPQynt3CfYc), [07-05](https://www.youtube.com/watch?v=NoF8eEIEA6M), [07-06](https://www.youtube.com/watch?v=KeZi7eOLpOA); [FCJ Lab07](https://000007.awsstudygroup.com/), [AWS Budgets](https://docs.aws.amazon.com/cost-management/latest/userguide/budgets-managing-costs.html) |
| Support và kiến trúc tốt | Nhận biết loại yêu cầu hỗ trợ, thông tin nên chuẩn bị khi mô tả sự cố và cách dùng sáu trụ cột làm khung đánh giá kiến trúc. | [Lab09-01](https://www.youtube.com/watch?v=4FDcK0_kbfY), [09-02](https://www.youtube.com/watch?v=BAEh-_RzmNg), [09-03](https://www.youtube.com/watch?v=haafDPugAnE), [09-04](https://www.youtube.com/watch?v=ThJBaQ3DEBs); [FCJ Lab09](https://000009.awsstudygroup.com/), [AWS Support plans](https://aws.amazon.com/premiumsupport/plans/) |

### Bài học sẽ ghi nhận sau khi học

- Khi chọn dịch vụ và Region, cần xét nhu cầu ứng dụng, độ trễ, yêu cầu dữ liệu, tính sẵn sàng và chi phí thay vì chọn theo tên dịch vụ.
- Console, CLI và SDK là các cách tương tác khác nhau với AWS; tự động hóa không làm mất yêu cầu kiểm soát danh tính và quyền.
- MFA, quyền IAM tối thiểu cần thiết và thông tin xác thực phù hợp là các phần riêng nhưng cùng đóng góp vào bảo mật tài khoản.
- Budget giúp theo dõi và cảnh báo chi phí; cần phân biệt cảnh báo với giới hạn chi tiêu. Xóa budget mẫu cũng không đồng nghĩa đã xóa mọi tài nguyên có thể phát sinh phí.
- Khi cần hỗ trợ, mô tả triệu chứng, phạm vi ảnh hưởng và thông tin liên quan giúp yêu cầu rõ ràng hơn. Thời gian phản hồi không đồng nghĩa với thời gian xử lý xong.

### Kết quả và ghi chú thực tế

Trang hiện ghi kế hoạch và nguồn học cho 7 video bài giảng, 14 video Lab cùng tài liệu First Cloud Journey/AWS. Chưa có ngày học, kết quả thao tác hoặc trải nghiệm cá nhân được xác nhận trong ghi chú đầu vào, nên các mục này sẽ được bổ sung sau khi có dữ liệu thực tế.

### Bước tiếp theo

Chuyển sang chủ đề VPC và networking ở Tuần 2; bổ sung các câu hỏi còn lại từ phần nền tảng AWS khi bắt đầu áp dụng vào project.
