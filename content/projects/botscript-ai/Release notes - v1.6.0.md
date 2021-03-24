---
title: 🔊 Release Notes - v1.6.0
linktitle: v1.6.0 - 24/03/2021
toc: true
type: docs
date: "2021-03-24T12:05:52+07:00"
lastmod: "2021-03-24T12:05:52+07:00"
draft: false
menu:
  botscript-ai:
    parent: Release Notes
    weight: 1

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 1002
---

Vui mừng gửi thông báo phát hành phiên bản: `1.6.0` tới các bạn một số tính năng mới và cập nhật khác đáng chú ý:

## New Features

* Add new directive /plugin
* Support directive /plugin code is written in botscript document
* Support directive /plugin run in node and browser

## Bugfixes & Improvement

* Refactor struct directive paring
* Update readme

## Summary Notes

Trong lần nâng cấp này, tính năng nổi bật nhất là tài liệu BotScript cho phép soạn các đoạn mã ngay trực tiếp trong kịch bản, mà không cần quan tâm đến viết mã nguồn hay phải biên dịch lại hệ thống.

Ví dụ: Một kịch bản soạn bổ sung directive `/plugin: addToday`

~~~bash
# khai báo và định nghĩa plugin
/plugin: addToday
```js
# lấy thông tin ngày, thứ hiện tại
req.variables.today = new Date().getDate();
req.variables.day = new Date().getDay();

# lấy năm hiện tại
req.variables.year = new Date().getFullYear();
```

# plugin được chạy với mỗi yêu cầu
> addToday

+ howdy
- Today is $today
~~~

## References

* PR: [#51](https://github.com/vunb/botscript.ai/pull/51)
* Release Tags: [v1.6.0](https://github.com/vunb/botscript.ai/releases/tag/1.6.0)
