---
title: 🔊 Release Notes - v1.4.0
linktitle: v1.4.0 - 18/02/2021
toc: true
type: docs
date: "2021-02-18T12:05:52+07:00"
lastmod: "2021-02-18T12:05:52+07:00"
draft: false
menu:
  botscript-ai:
    parent: Release Notes
    weight: 1

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 1002
---

Vui mừng gửi thông báo phát hành phiên bản **1.4.0** tới các bạn với một số tính năng mới và cập nhật mới sau đây:

## New Features

* Add new directive system
  * Syntax: `/directive: text or command or [definition]`
* Add new built-in plugin: NLU
* Current supported two directive: **/include**, **/nlu**
* Support trigger pattern to test NLU extraction
  * Syntax: `+ intent: greeting`
* Add new api: **parseUrl(url: string)**

## Changes & Improvement

* Refactor util test method

## Summary Notes

Phiên bản **1.4.0** bổ sung thêm hệ thống Directive và thêm mới Plugin NLU.

Các Directives sẵn có trong phiên bản này bao gồm:

* /include: Chỉ dẫn để nhập dữ liệu kịch bản từ URL
* /nlu: Chỉ dẫn sử dụng custom NLU API Server.

Và bổ sung thêm một vài API cho phép thuận tiện lập trình và phát triển hệ thống Trợ lý AI với BotScript.

Ví dụ: Một kịch bản sử dụng Directive chỉ dẫn:

```bash
# khai báo download và nạp kịch bản từ Web/URL.
/include: https://raw.githubusercontent.com/yeuai/botscript/master/examples/hello.bot

# sử dụng hệ thống NLU Server riêng.
# directive tham chiếu đến tên của một command
/nlu: command_nlu
```

## References

* PR: [#38](https://github.com/vunb/botscript.ai/pull/38)
* Release Tags: [v1.4.0](https://github.com/vunb/botscript.ai/releases/tag/1.4.0)
