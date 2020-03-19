---
title: Tích hợp hoàn thiện NLU, ngày 18/03/2020
linktitle: Hoàn thiện NLU
toc: true
type: docs
date: "2020-03-18T12:05:52+07:00"
lastmod: "2020-03-18T12:05:52+07:00"
draft: false
menu:
  botscript-ai:
    parent: Ghi chép
    weight: 1

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 2
---

## Kết quả đạt được

Việc tích hợp thành công thành phần NLU vào trong BotScript Platform là một phần rất quan trọng. NLU giúp cho bot hiểu được văn bản đầu vào, qua đó cho phép bot quyết định chính xác thông tin cần trả lời cho khách hàng.

Về cốt lõi thì NLU là thành phần trong đó có nhiều kỹ thuật xử lý ngôn ngữ tự nhiên (NLP) được áp dụng.

1. Xác định, phân loại ý định của người dùng.
2. Trích xuất thông tin
3. Quản lý hội thoại

![NLU Integration Testing](/img/botscript-ai/nlu-integration.jpg)

BotScript bản thân nó đã là một chương trình quản lý hội thoại, việc cần thiết mà tôi vừa làm là đã tích hợp xong thêm 2 đơn vị nhỏ còn lại trong bộ phận NLU này, qua kinh nghiệm xây dựng mã nguồn mở [Rivebot CE](https://github.com/yeuai/rivebot-ce) thì việc triển khai cho BotScript dễ dàng hơn rất nhiều.

Một điểm thách thức là cả BotScript Platform (**BSP**) và ngôn ngữ đặc tả BotScript Document (**BSD**) đều rất mới, đang ở trong giai đoạn sơ khai nên việc thay đổi và cập nhật khả năng cho nó là rất nhiều. Ví dụ như để làm sao Bot hiểu được lệnh đang đưa vào là một câu nói ở một hình thái khác, tức là bot chỉ có thể hiểu được qua ý định của câu nói mà thôi? BotScript sẽ không thể bắt chính xác được từng chữ cái của người dùng, điều đó sẽ khiến người thiết kế bot phải quan tâm đến rất nhiều tình huống.

Tuy nhiên, tính mới, tính non trẻ đó cũng là một lợi thế để BotScript có thể điều chỉnh thay đổi phù hợp với các kịch bản từ thực tiễn. Nhưng phải đảm bảo được tính tổng quát chức năng của ngôn ngữ đặc tả **BSD**, hay các api của BotScript Engine (**BSE**).

## Cú pháp mới

Ngay từ thiết kế ban đầu của **BSD** cho phép các hệ thống riêng có thể mở rộng và hỗ trợ các cú pháp mới để phù hợp với năng lực cũng như nhu cầu mới, hay đơn giản sở thích của nhà thiết kế tạo ra cú pháp thân thiệt nhất với người dùng.

Để dùng được cú pháp mới hỗ trợ NLP, thì người dùng phải khai báo sử dụng plugin `> nlp` trong tài liệu kịch bản BSD của chatbot. Sau đó soạn một hộp thoại với trigger bắt đầu với từ khóa `+ intent: buy some thing` 

Ví dụ: Một kịch bản bsd được soạn như sau:

<pre>
> nlp

+ intent: mua_dien_thoai
- Bạn muốn lấy điện thoại hãng nào?
</pre>

Như vậy, khi người dùng nhập: *Tôi muốn mua điện thoại* hoặc *bạn có bán điện thoại không?* thì bot sẽ trả lời là: *Bạn muốn lấy điện thoại hãng nào?*

Kết hợp với **Flows** người dùng có thể thiết kế kịch bản bot nâng cao hơn, bằng việc hỏi chi tiết thêm các nội dung đơn hàng mà khách hàng họ đang có mục tiêu **mua một chiếc điện thoại**.

Ví dụ:

<pre>
> nlp

+ intent: mua_dien_thoai
~ ask product_name
~ ask product_color
~ ask product_amount
- Đơn hàng của bạn đã xử lý, bạn đã chọn: $product_name, $product_color, $product_amount với giá $product_price
</pre>

## Thuật ngữ

Các thuật ngữ về người sử dụng và vai trò của họ khi tương tác với BotScript Platform:

* Nhà thiết kế: Người xây dựng tao ra nền tảng cung cấp dịch vụ chatbot
* Người dùng: Người sử dụng tạo ra dịch vụ chatbot
* Khách hàng: Người sử dụng dịch vụ chatbot

Các thuật ngữ trong hệ sinh thái trợ lý ảo riêng BotScript AI:

* BSP: **BotScript Platform** - nền tảng cung cấp dịch vụ, sân chơi cho người thiết kế bot
* BSD: **BotScript Document** - tài liệu đặc tả BotScript, tiêu chuẩn để cho người dùng xây dựng kịch bản, tạo ra dịch vụ chatbot
* BSE: **BotScript Engine** - chương trình lõi quản lý hội thoại của một chatbot.

