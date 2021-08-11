---
# Course title, summary, and position.
linktitle: Kites.js
summary: Framework xây dựng các ứng dụng đa nhiệm trên nền tảng Node.js
weight: 1

# Page metadata.
title: Kites.js
date: "2020-04-07T22:27:52+07:00"
lastmod: "2020-04-07T22:27:52+07:00"
draft: false # Is this a draft? true/false
toc: true # Show table of contents? true/false
type: docs # Do not modify.

# Add menu entry to sidebar.
# - name: Declare this menu item as a parent with ID `name`.
# - weight: Position of link in menu.
menu:
  kites.js:
    name: Giới thiệu
    weight: 1

# Meta for og:image
header:
  caption: "Kites.js"
  image: "kites-js/kites.gif"
---

Kites là một dự án mã nguồn mở với mục tiêu là tạo ra các ứng dụng Web dựa trên các bản mẫu một cách nhanh chóng và dễ dàng.

# Mục tiêu của dự án

- Là 1 framework tạo ra các ứng dụng web đầy tham vọng
- Là 1 công cụ dòng lệnh, hỗ trợ khởi tạo nhanh dự án
- Kết nối với nhiều loại cơ sở dữ liệu: MongoDB, Cassandra, MySQL, Postgres, Redis, ...
- Mô-đun hóa các thành phần, tiện ích tái sử dụng thành các phần mở rộng (extensions)
- Phân tách tầng ứng dụng: device access layer, database access layer, cron jobs, ...
- Đóng gói các dự án cơ sở thành khuôn mẫu (templates)
- Mỗi một khuôn mẫu đều có Dockerfile và docker-compose
- Tích hợp với các dự án, module khác mà không gây ra xung đột
