---
layout: post
title: Tìm hiểu trực quan về Word Embeddings - Từ Count Vectors đến Word2Vec
category: nlp
tags: text-representations word-embeddings deep-learning
ref: https://www.analyticsvidhya.com/blog/2017/06/word-embeddings-count-word2veec/
---

Trước khi bắt đầu, hãy xem xét các ví dụ dưới đây:

1. Bạn mở Google ra và tìm kiếm một bài báo về các giải vô địch đang diễn ra và bạn nhận được hàng trăm ngàn kết quả về thứ bạn tìm kiếm.
2. [Nate Silver](https://en.wikipedia.org/wiki/Nate_Silver) đã phân tích hàng triệu tweet và dự đoán chính xác kết quả 49/50 tiểu ban trong cuộc bầu cử Tổng thống Hoa Kỳ năm 2008.
3. Bạn nhập một câu vào Google Translate bằng tiếng Anh và bạn có được 1 phiên bản tương ứng bằng tiếng Trung Quốc.

![Giới thiệu](../img/collage.png)

> Source: https://s3-ap-south-1.amazonaws.com/av-blog-media/wp-content/uploads/2017/06/06052154/collage.png

Những ví dụ trên có đặc điểm gì chung ?

Có thể bạn có ngay đáp án - đó là **Xử lý văn bản**. Và mỗi một công việc đó phải xử lý với một lượng khổng lồ văn bản, thực hiện các tác vụ như: **Phân cụm** trong ví dụ tìm kiếm của Google, **Phân lớp** trong ví dụ thứ 2 và **Máy dịch** trong ví dụ thứ 3.

Con người có thể xử lý với các định dạng văn bản một cách trực quan nhưng nếu cung cấp cho chúng ta hàng triệu tài liệu được sinh ra trong một ngày, chúng ta không ai có thể thực hiện được ba nhiệm vụ trên. Hoặc nó không thể mở rộng hoặc không hiệu quả.

![Con người xử lý văn bản nhị phân](../img/joke-297x300.jpg)

> Source: https://s3-ap-south-1.amazonaws.com/av-blog-media/wp-content/uploads/2017/06/06064148/joke-297x300.jpg

Rõ ràng con người không thể làm được với 1 khối lượng công việc lớn như vậy được, chúng ta cần máy tính hỗ trợ, để thực hiện các nhiệm vụ tự động, phân cụm, phân lớp, ... trên tập các dữ liệu văn bản. Vậy làm thế nào máy tính có thể xử lý được văn bản, các chuỗi ký tự để cho được một kết quả kì vọng một cách hiệu quả ?


