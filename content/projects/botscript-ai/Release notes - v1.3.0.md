---
title: 🔊 Release Notes - v1.3.0
linktitle: v1.3.0 - 20/03/2020
toc: true
type: docs
date: "2020-03-20T12:05:52+07:00"
lastmod: "2020-03-20T12:05:52+07:00"
draft: false
menu:
  botscript-ai:
    parent: Release Notes
    weight: 1

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 1001
---

Tôi rất vui mừng gửi thông báo phát hành phiên bản **1.3.0** tới các bạn với một số tính năng mới và cập nhật mới sau đây:

## New Features

* Extend pattern capability to capture user intent, entity information, ...
* Upgrade NLP Core, refactor data types
* Add bot plugin pipeline: nlp

## Changes & Improvement

* add ui button to delete bot scripts
* refactor features engineering data types
* add iob entity definition
* fix plugin nlp extractor
* fix nlp pattern to detect intent
* remove intent from variables

## Summary Notes

Phiên bản **1.3.0** bổ sung plugin mới hỗ trợ việc phân tích ý định, bóc tách thông tin có trong câu nói của khách hàng.

* Tích hợp mới plugin: `nlp`
* Bổ sung thêm cú pháp để bắt ý định người dùng, từ đó, cho phép người dùng thiết kế kịch bản phù hợp với ý định đó.
* Cho phép bot trả lời chính xác mong muốn của người dùng, hoặc yêu cầu bot theo dõi và xử lý nhiệm vụ phục vụ khách hàng.

Để dùng được cú pháp mới hỗ trợ NLP, thì người dùng phải khai báo sử dụng plugin `> nlp` trong tài liệu kịch bản BSD của chatbot. Sau đó soạn một hộp thoại với trigger bắt đầu với từ khóa `+ intent: buy some thing` 

Ví dụ: Một kịch bản bsd được soạn như sau:

```bash
# khai báo sử dụng plugin
> nlp

# kịch bản hỏi khách hàng mua sản phẩm gì?
+ intent: mua_dien_thoai
~ ask $product_name
~ ask $product_amount
* true => @ get_price
- Đơn hàng của bạn đã được ghi nhận, bạn đã chọn: $product_name, $product_amount với giá $product_price

~ ask $product_name
- Bạn muốn lấy điện thoại hãng nào?
+ ner: product_name

~ ask $product_amount
- Bạn muốn lấy mấy chiếc?
+ ner: product_amount
```

Như vậy, khi người dùng nhập: *Tôi muốn mua điện thoại* hoặc *bạn có bán điện thoại không?* thì bot sẽ dẫn nhập và hỏi thêm khách hàng muốn lấy sản phẩm tên là gì, số lượng bao nhiêu, ... kiểm tra đơn giá của giỏ hàng và sau đó phản hồi thông tin về đơn hàng mới cho khách hàng.

Từ đây, đặt ra một vấn đề là khi khách hàng sửa lại thông tin kiểu như: *à, tôi muốn lấy 2 chiếc chứ không phải 1.* Nghe cũng có vẻ khoai phết nhỉ? Có lẽ, nên viết thêm một plugin cho phép bot tra khảo và cập nhật lại các thông tin đã nhận từ bước trước?

## References

* PR: [#19](https://github.com/vunb/botscript.ai/pull/19)
* Release Tags: [v1.3.0](https://github.com/vunb/botscript.ai/releases/tag/1.3.0)
