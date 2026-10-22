---
title: "Blog 1 - Amazon SQS"
date: 2026-10-22
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# Một message SQS, vì sao có thể gửi email nhiều lần?

- **Ngày đăng:** 22/10/2026.
- **Bài đăng gốc:** [Xem bài viết trên Facebook](https://www.facebook.com/share/p/1CJMAYWQBf/).
- **Ngôn ngữ bài đăng gốc:** Tiếng Việt.

Đưa tác vụ gửi email vào Amazon SQS là một cách giúp ứng dụng phản hồi nhanh hơn. Backend gửi message vào queue, còn một worker nhận message và xử lý phía sau.

Nhưng nếu một message bị xử lý nhiều lần, người nhận cũng có thể nhận email trùng. Một nguyên nhân cần kiểm tra là visibility timeout.

Khi worker nhận message từ SQS, message chưa bị xóa khỏi queue. Nó chỉ tạm thời không hiển thị với các worker khác trong khoảng thời gian gọi là visibility timeout. Giá trị mặc định của queue là 30 giây.

Xét một tình huống minh họa với SQS Standard và worker tự nhận, xử lý rồi xóa message:

- Giây 0: worker A nhận message và bắt đầu xử lý.
- Tác vụ cần 45 giây, nhưng visibility timeout chỉ có 30 giây.
- Khoảng giây 30: nếu chưa được xóa hoặc gia hạn, message có thể xuất hiện trở lại.
- Worker B có thể nhận cùng message trong khi worker A vẫn đang chạy.

Nếu cả hai worker đều gửi email mà không kiểm soát tác vụ trùng, khách hàng có thể nhận hai email từ cùng một yêu cầu ban đầu.

Visibility timeout vì vậy cần phù hợp với thời gian xử lý. Đặt quá ngắn làm tăng nguy cơ xử lý chồng lặp; đặt quá dài khiến message phải chờ lâu hơn để được thử lại khi worker gặp sự cố.

Với tác vụ có thời gian xử lý thay đổi, worker có thể định kỳ gọi ChangeMessageVisibility để gia hạn trong lúc vẫn đang làm việc.

Tuy nhiên, tăng timeout chưa giải quyết toàn bộ vấn đề. SQS Standard sử dụng cơ chế giao message ít nhất một lần — at-least-once delivery. Message vẫn có thể được giao lại, nên consumer cần thiết kế để xử lý việc này.

Một số điểm nên có:

- Dùng mã nghiệp vụ ổn định, chẳng hạn notificationId, để nhận diện cùng một yêu cầu gửi.
- Lưu trạng thái xử lý bền vững và kiểm soát việc nhiều worker cùng nhận một yêu cầu.
- Chỉ xóa message sau khi xử lý thành công.
- Cấu hình dead-letter queue để tách các message thất bại nhiều lần.

Riêng với email, chỉ kiểm tra “đã gửi chưa” rồi gửi vẫn có khoảng hở: worker có thể gửi thành công nhưng gặp sự cố trước khi lưu trạng thái. Nếu nhà cung cấp email hỗ trợ khóa idempotency, có thể tận dụng để giảm nguy cơ gửi trùng.

Điều cần nhớ: **visibility timeout giúp hạn chế xử lý đồng thời; thiết kế consumer mới quyết định tác vụ lặp ảnh hưởng thế nào đến người dùng.**

Nguồn tham khảo: [Amazon SQS — Visibility timeout](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-visibility-timeout.html)

![Sơ đồ dòng thời gian nhận, xử lý và xóa message trong khoảng visibility timeout của Amazon SQS.](/images/blogs/sqs-visibility-timeout.png)

Nguồn ảnh: [AWS Documentation](https://docs.aws.amazon.com/images/AWSSimpleQueueService/latest/SQSDeveloperGuide/images/sqs-visibility-timeout-diagram.png).

#AWS #AWSStudyGroup #FCAJ #AmazonSQS #MessageQueue
