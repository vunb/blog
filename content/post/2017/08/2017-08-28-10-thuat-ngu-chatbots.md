---
layout: post
title: Chatbots - 10 thuật ngữ cần biết
category: Chatbots
tags: chatbot-design
---

![10 thuật ngữ chatbots cần biết](/img/chatbots-intent-entity-utterances.png)

Có thể khi tìm hiểu về chatbots và xử lý ngôn ngữ tự nhiên, sẽ có nhiều từ vựng hay các thuật ngữ làm cho bạn cảm thấy khó hình dung, hoặc cảm thấy dễ bị lẫn lộn với nhau. Sau đây là 10 thuật ngữ mà chúng ta cần biết và phân biệt chúng khi nghiên cứu và tìm hiểu về chatbots.

3 thuật ngữ quan trọng: Utterances, intents và entities
=======================================================

Đây là ba thuật ngữ quan trọng nhất trong chatbots:

**Utterances**: Đây là những gì mà người dùng nói ra. Ví dụ, một người dùng gõ: "Show me yesterday's financial news", thì toàn bộ câu này là một lời nói hay utterance.

**Intent**: Là ý định của người dùng trong câu nói. Với ví dụ trên, "show me yesterday's financial news", thì ý định của người dùng ở đây là mong muốn nhận một danh sách các tiêu đề về tài chính. Ý định đều có thể đặt tên, thường là một động từ kết hợp với một danh từ, chẳng hạn: *"showNews"*.

**Entity**: Là các thực thể bổ nghĩa cho một ý định. Vẫn ví dụ trên, "show me yesterday's financial news", thì các thực thể bổ nghĩa là "yesterday" và "financial". Các thực thể cũng đều có thể được đặt tên, ví dụ: "dateTime", và "newsType". Các thực thể này đôi khi được gọi là các "Slot", có thể hình dung đó là các khe thông tin.

7 thuật ngữ hữu ích khác
========================

**Broadcast**: Đây là một dạng thông điệp được gửi một cách chủ động tới người dùng. Đây không phải là một tin nhắn hồi đáp cho người dùng mà gần như là một thông báo đẩy (trong app mobile)

**Channel**: Các kênh là phương tiện cho các cuộc trò chuyện bằng chatbot. Ví dụ về các kênh như mạng xã hội Facebook, Skype, Slack và SMS. Email và cửa sổ chát trên web cũng là các phương tiện.

**Conversational UI**: Là giao diện giao tiếp với con người, hoặc là viết tay, hoặc là thông qua lời nói (khôn sử dụng buttons, links, hoặc graphical elements). Thường có nhiều chatbots kết hợp conversational UI với graphical UI.

**Natural Language Processing (NLP)**: NLP là công cụ phân tích một lời nói Utterance và trích xuất các ý định và thực thể trong lời nói. Một số dịch vụ Amazon Lex, Facebook Wit.ai, Google API.ai, Microsoft LUIS đều có sử dụng NLP.

**Pilot**: Giai đoạn phát triển chatbot được triển khai cho một nhóm nhỏ người dùng để thử nghiệm. Các pilots đặc biệt quan trọng với chatbot, bởi vì không giống như các ứng dụng Web, phạm vi đầu vào của người dùng là không giới hạn. Nên cần pilot chatbot theo từng giai đoạn.

**Proof-of-concept (POC)**: Đây là giai đoạn mà các tính năng của Chatbot hoạt động đúng cách, miễn là đầu vào thử nghiệm được kiểm soát đúng cách. Do đó, POC thể hiện tiềm năng của chatbot.

**Response**: Bất cứ điều gì mà bot nói ra đáp ứng với input đầu vào của người dùng.

Tham khảo liên kết
==================

* [Chatbot Vocabulary: 10 Chatbot Terms You Need to Know][1]
* [How I built a fully functional Deep Learning Neural Network chatbot platform (NLU Engine) in under a week....][2]
* [How I built a fully functional Deep Learning Neural Network chatbot platform (NLU Engine) in under a week....][3]

[1]: https://chatbotsmagazine.com/chatbot-vocabulary-10-chatbot-terms-you-need-to-know-3911b1ef31b4
[2]: https://www.techbubble.info/blog/artificial-intelligence/chatbots/entry/deep-learning-neural-network-nlu-engine
[3]: https://chatbotsmagazine.com/how-i-built-a-fully-functional-deep-learning-neural-network-chatbot-platform-nlu-engine-in-under-1765180d16db