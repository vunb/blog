---
title: 🔊 Release Notes - v1.2.0
linktitle: v1.2.0 - 16/03/2020
toc: true
type: docs
date: "2020-03-16T12:05:52+07:00"
lastmod: "2020-03-16T12:05:52+07:00"
draft: false
menu:
  botscript-ai:
    parent: Release Notes
    weight: 1

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 1000
---

Tôi rất vui mừng gửi thông báo phát hành phiên bản **1.2.0** tới các bạn với một số tính năng mới và cập nhật mới như sau đây:

## New Features

* Add Bot NLU System for NER labeling and Intent detection
* add nlp, nlu services
* add user configuration
* add custom menu system
* add multiple language site for english and vietnamese
* add upload drop zone
* add basic ui to train bot NLU
* add message chat to nlp samples
* config mocha & webpack support typescript relative paths

## Improvement

* refactor nlp core features
* refactor text selection comp
* update nlp samples editor

## Summary Notes

Về lần phát hành này các thay đổi tập trung chủ yếu phía Backend, với cơ sở là xây dựng được bộ NLU để tổng hợp dữ liệu phục vụ cho việc đào tạo training cho Bot.

Sự huấn luyện sự thông minh cho bot ở việc từ một câu nói đầu vào (bằng văn bản), hệ thống sẽ định danh và chuyển giao tới Bot tiếp nhận, bóc tách thông tin như: Ý định của người nói và các thông tin có đề cập trong câu nói đó.

Bằng hệ thống NLU xây dựng được, bot sẽ từng bước tách và trích xuất các thông tin phục vụ cho việc quyết định nội dung nào sẽ được trả lời (reply).

Như vậy, phiên bản **1.2.0** là cơ sở quyết định để các phiên bản sau hoàn thiện hơn, tích hợp hoàn thiện một dòng chảy hội thoại: **Input** -> NLU -> Dialogue Engine -> Commands Unit -> NLG -> **Response**.

## References

Ref: [#16](https://github.com/vunb/botscript.ai/pull/16)
