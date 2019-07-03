---
title: Chatbot FAQ - Các câu hỏi thường gặp
date: 2017-06-26T00:00:00Z
draft: false
share: false

# View.
#   1 = List
#   2 = Compact
#   3 = Card
view: 2
tags:
- tensorflow
- chatbots
- word-embeddings
- seq2seq
categories:
- Chatbots

# Optional header image (relative to `static/img/` folder).
header:
  caption: "https://towardsdatascience.com/44d9b41cd42d"
  image: "seq2seq.png"
---

# [How to train tensorflow chat application on updated dataset everyday?][1]

**Q**: I have created chatbot on **Cornell** movie dataset and it's working fine. I have trained chatbot application up to global step 330000. I am using tensorflow library. I am also receiving output fine. Then I created this new dataset file by modifying original dataset and i wish to train chatbot application with updated files. Now should I delete previously saved checkpoints and saved data and start training from zero or should i train from 330000 onwards without worrying changes in dataset. I wish to modify database daily basis and train on modified database. Please kindly let me know if you have a suggestion for me as I am stuck on this issue. I will really appreciate if you help me with this issue.

**A**: The distribution of your data won't change too much over a smaller period of time, retraining from scratch seems like a waste. Just add the new data to your set and do one or more epochs on all your data, not just the new ones. It can readjust the weights a little bit for changes in the distribution which is exactly what you want. Make sure you are not overreliant on early stopping as regularization method against overfitting because you continuously train like this, use some other regularizer. I would suggest periodically to retrain from scratch but this doesn't have to happen very regularly, maybe once every two months.

Source: [https://datascience.stackexchange.com/a/18899][1]

# [Các bài toán NLP cơ bản khi phát triển một hệ thống chatbot là gì ?][2]

Các hệ thống chatbot được triển khai trong thực tế phần lớn tuân theo mô hình truy xuất thông tin và được áp dụng trong những miền ứng dụng cụ thể (miền đóng). Ba vấn đề cơ bản NLP mà một hệ thống Chatbot cần xác định và phát triển tích hợp:

## 1. Xác định, phân loại ý định của người dùng.

Thông thường người dùng truy cập hệ thống chatbot đều mong muốn một hành động trợ giúp về một vấn đề nào đó. Ví dụ, người dùng mong muốn chatbot hỗ trợ đặt vé máy bay, để đưa ra hỗ trợ được chính xác, chatbot cần xác định được ý điện (intent) đó của người dùng. Việc xác định ý định của người dùng sẽ quyết định hội thoại tiếp theo giữa người dùng và chatbot sẽ diễn ra như thê nào; Nếu xác định sai ý định người dùng, chatbot sẽ không đưa ra được những phản hồi đúng hợp ngữ cảnh. Khi đó, người dùng cảm thấy thất vọng và không quay lại sử dụng hệ thống. Đây được coi là bài toán quan trọng nhất trong hệ thống chatbot.

## 2. Trích xuất thông tin

Bên cạnh việc xác định intent trong câu hội thoại của người dùng, chúng ta cần trích xuất các thông tin cần thiết trong đó. Các thông tin cần trích xuất trong một câu hội thoại thường là các thực thể thuộc về một loại nào đó. Ví dụ, khi một khách hàng muốn đặt vé máy bay, hệ thống cần biết địa điểm xuất phát và địa điểm khách muốn đến, ngày giờ khách hàng muốn bay,…Thành phần NLU của các hệ thống chatbot thường hỗ trợ các loại thực thể sau:

* Vị trí (Location)
* Thời gian (Datetime)
* Số (Number)
* Địa chỉ liên lạc (Contact)
* Khoảng cách (Distance)
* Khoảng thời gian (Duration)

Trong bài toán trích xuất thông tin, tập nhãn cho các từ trong câu đầu vào thường được tạo ra theo mô hình BIO, với B là viết tắt của `Beginning`, I là viết tắt của `Inside`, và O là viết tắt của `Outside`.

## 3. Quản lý hội thoại

Trong các phiên trao đổi dài (long conversation) giữa người và chatbot, chatbot sẽ cần ghi nhớ những thông tin về ngữ cảnh (context) hay quản lý các trạng thái hội thoại (dialog state). Vấn đề quản lý hội thoại (dialoge management) khi đó là quan trọng để đảm bảo việc trao đổi giữa người và máy là thông suốt.

Source: [3 vấn đề NLP cơ bản khi phát triển một hệ thống chatbot và một số phương pháp giải quyết điển hình][2]

[1]: https://datascience.stackexchange.com/a/18899
[2]: https://tech.fpt.com.vn/3-van-de-nlp-co-ban-khi-phat-trien-mot-thong-chatbot-va-mot-phuong-phap-giai-quyet-dien-hinh/
