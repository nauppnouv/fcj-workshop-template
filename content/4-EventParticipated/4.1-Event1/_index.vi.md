---
title: "Buildrathon Kickoff: Code the Future with CMC Global"
date: 2026-09-26
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

### Thông tin sự kiện

- **Ngày tổ chức:** 26/09/2026
- **Giờ bắt đầu công bố:** 09:00 (giờ Việt Nam, UTC+7)
- **Địa điểm:** Bitexco Financial Tower, Thành phố Hồ Chí Minh
- **Vai trò:** Người tham dự
- **Trang sự kiện:** [Buildrathon Kickoff: Code the Future with CMC Global](https://luma.com/8fe9vvps)

### Mục tiêu của sự kiện

- Giới thiệu chương trình Buildrathon và những kỳ vọng dành cho người tham gia.
- Kết nối việc học Cloud và AI với các ví dụ do người làm chuyên môn chia sẻ.
- Tạo cơ hội để người tham dự đặt câu hỏi và trao đổi về nội dung trình bày.

### Diễn giả

| Thứ tự | Diễn giả | Chức danh | Phần chia sẻ tại sự kiện |
| --- | --- | --- | --- |
| 1 | [Nguyễn Gia Hưng](https://www.linkedin.com/in/jotaguy/) | Head of Solutions Architect, AWS Việt Nam và Campuchia | Mở đầu chương trình, giới thiệu Buildrathon, mục đích và định hướng của chương trình. |
| 2 | [Nhật Trường Bùi](https://www.linkedin.com/in/dominicbui0000/) | Tech Lead, CMC Global | Tiếp nối bằng phần chia sẻ kỹ thuật, trong đó có ví dụ kiến trúc Slack bot ứng dụng AI, và trả lời câu hỏi. |

Phần mở đầu đặt bối cảnh cho chương trình, sau đó phần chia sẻ kỹ thuật đưa người tham dự đến một kiến trúc phần mềm cụ thể. Trình tự này giúp kết nối nội dung giới thiệu Buildrathon với một ví dụ trong thực tế chuyên môn.

### Nội dung nổi bật

#### 1. Giới thiệu chương trình và định hướng Buildrathon

Anh Nguyễn Gia Hưng giới thiệu chương trình và thử thách Buildrathon. Phần khai mạc giúp người tham dự nắm bối cảnh của hành trình học tập và những kết quả cần hướng đến. [Nội dung sự kiện được công bố trên Luma](https://luma.com/8fe9vvps) cũng đề cập mục tiêu thử thách và tiêu chí đánh giá.

Tài liệu trình chiếu có phần tổng quan về sự hiện diện của AWS tại Việt Nam, với các hướng đầu tư vào nguồn nhân lực địa phương, hạ tầng và kỹ năng tương lai. Nội dung này bổ sung bối cảnh cho việc phát triển năng lực Cloud và AI.

#### 2. Ví dụ thực tế: kiến trúc Slack bot ứng dụng AI

Phần chia sẻ kỹ thuật trình bày sơ đồ có tên **Market Slack Bot**. Diễn giả giới thiệu kiến trúc qua các thành phần kết nối với nhau:

| Thành phần trên slide | Chi tiết được minh họa trong sơ đồ |
| --- | --- |
| Slack | Yêu cầu gắn với lượt nhắc tên, tin nhắn trực tiếp và các luồng hội thoại đang hoạt động. |
| Socket Mode / WebSocket | Kết nối giữa Slack và luồng xử lý của bot. |
| Response gate | Thành phần kiểm soát phản hồi được đặt trước Claude Code. |
| Claude Code | Thành phần xử lý, với đầu ra được ghi là `print · JSON`. |
| `SOUL.md` và Memory | Cấu hình giọng điệu, phạm vi hoạt động và ngữ cảnh của luồng hội thoại. |
| Bot schedule, internal API và cron + database | Lượt xử lý theo lịch, tác vụ thuộc ứng dụng, cùng nơi lưu thông tin liên quan đến bộ nhớ và tác vụ định kỳ. |

Sơ đồ làm rõ những phần cần quan tâm khi đọc một kiến trúc ứng dụng AI: kênh tiếp nhận yêu cầu, xử lý phản hồi, ngữ cảnh và tác vụ theo lịch. Đây là các chi tiết tôi ghi nhận để có thể xem lại ví dụ sau sự kiện.

#### 3. Đặt câu hỏi và trao đổi trực tiếp với diễn giả

Sau khi lắng nghe các phần trình bày, tôi đặt câu hỏi cho anh Nhật Trường Bui trong phiên trao đổi. Đây là hoạt động tôi trực tiếp tham gia, đồng thời là cơ hội trao đổi với một Tech Lead tại CMC Global.

### Bài học rút ra

- Phần giới thiệu giúp tôi nắm rõ mục đích của buổi khai mạc và bối cảnh chương trình Buildrathon.
- Ví dụ Slack bot giúp tôi hệ thống hóa kiến trúc theo các nhóm tiếp nhận yêu cầu, xử lý, ngữ cảnh và tác vụ theo lịch.
- Đặt câu hỏi là cách tham gia chủ động và làm rõ những điểm trong một phần trình bày kỹ thuật.

### Định hướng áp dụng

Từ nội dung trình bày, các hướng tìm hiểu tiếp theo gồm xem lại sơ đồ đã chụp, hệ thống hóa các thành phần thành một bản phác thảo kiến trúc, và tìm hiểu cách thể hiện ngữ cảnh hội thoại cùng tác vụ theo lịch trong một dự án học tập. Đây là định hướng học thêm, chưa phải kết quả triển khai tại sự kiện.

### Trải nghiệm tham dự

Tôi tham dự với vai trò người nghe, theo dõi phần giới thiệu chương trình và phần chia sẻ kỹ thuật, đặt câu hỏi cho anh Nhật Trường Bui, đồng thời nhận được quà tại sự kiện. Các ảnh bên dưới ghi lại buổi chia sẻ và phần trao quà.

Trang đăng ký có liệt kê hoạt động thực hành AI Agent Challenge, nhưng phần này không diễn ra trong sự kiện mà tôi tham dự. Hoạt động thực tế của tôi là lắng nghe và đặt câu hỏi; tôi không xây dựng hay kiểm thử AI Agent tại sự kiện.

### Hình ảnh sự kiện

![Người tham dự lắng nghe phần trình bày tại buổi khai mạc Buildrathon.](/images/4-EventParticipated/4.1-Event1/IMG_6071.jpg)

*Một phần trình bày tại sự kiện.*

![Slide tổng quan về đầu tư của AWS tại Việt Nam, gồm nguồn nhân lực địa phương, hạ tầng và kỹ năng tương lai.](/images/4-EventParticipated/4.1-Event1/IMG_6074.jpg)

*Slide bổ sung bối cảnh về AWS và phát triển kỹ năng tại Việt Nam.*

![Slide minh họa kiến trúc Slack bot gồm Slack, WebSocket, response gate, Claude Code, internal API và cơ sở dữ liệu.](/images/4-EventParticipated/4.1-Event1/IMG_6077.jpg)

*Ví dụ về kiến trúc Slack bot ứng dụng AI được trình bày tại sự kiện.*

![Người tham dự chụp ảnh cùng những món quà tại sự kiện CMC Global.](/images/4-EventParticipated/4.1-Event1/cmc.jpg)

*Ảnh chụp tập thể trong phần trao quà của sự kiện.*
