---
title: Hoàn thiện đặc tả ngôn ngữ trí tuệ nhân tạo BotScript v1.3.0
date: 2020-09-12T23:28:52+07:00
draft: false
share: true

# View.
#   1 = List
#   2 = Compact
#   3 = Card
view: 2
tags:
- BotScript
- Specification
categories:
- BotScript
---

Hai tháng vừa rồi mình quá bận với công việc công ty, do các dự án lớn cần tập trung toàn bộ quân chủ lực để hoàn thiện gấp rút dự án, đến nay cơ bản dự án đã và đang triển khai bước đầu!

Nay cũng vừa để giải trí, vừa làm đỡ căng thẳng nên lại chăm chăm vào ngôn ngữ trí tuệ nhân tạo BotScript do chính bản thân mình phát minh ra :smile:

Đến thời điểm hiện tại, phiên bản BotScript `v1.3.0` đã chính thức bộ engine được cài đặt đầy đủ dựa trên bản đặc tả VERSION 1. Trong phiên bản này có các tính năng sau:

* Definition - Định nghĩa 1 biến hoặc danh sách
* Comment - Ghi chú cho hộp thoại hoặc các lưu ý
* Continuation - Cho phép xuống dòng đối với đoạn hội thoại dài
* Dialogue - Định nghĩa hộp thoại người-máy tương tác với nhau
* Trigger - Kích hoạt hộp thoại phù hợp nhất
* Reply - Mẫu nội dung cho bot trả lời
* Flows - Luồng nhiệm vụ mà bot cần theo đuổi nhiệm vụ mục tiêu
* Prompts - Các thông tin bổ sung hoặc gợi nhắc cho người
* Conditions - Các điều kiện kích hoạt hộp thoại hoặc điều kiện để chọn nội dung trả lời phù hợp nhất
* Commands - Thực thi lệnh nâng cao, như gọi tìm kiếm DB hoặc tìm kiếm thông tin mạng
* Variables - Các thông tin và tri thức có được trong quá trình tương tác hộp thoại
* Patterns - Các mẫu nâng cao để khớp ý định và bóc tách thông tin, vật thể, ...
* Plugins - Mở rộng tùy biến nâng cao sử dụng mã lập trình

# Tham khảo

Liên kết đến mã nguồn dự án và hệ thống thử nghiệm:

* https://github.com/yeuai/botscript
* https://github.com/yeuai/botscript/blob/master/examples
* https://botscript.ai/#/
