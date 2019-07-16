---
# Course title, summary, and position.
linktitle: '[01- Sentiment Analysis] Phân tích cảm xúc đối tượng'
summary: 'Khóa học về phân tích cảm xúc, từ nghiên cứu lý thuyết cơ bản cho đến thực hành: Xây dựng một công cụ lắng nghe mạng xã hội trực tuyến.'
weight: 1

# Page metadata.
title: Khóa học phân tích cảm xúc đối tượng
date: "2019-07-16T00:00:00Z"
lastmod: "2019-07-16T00:00:00Z"
draft: true  # Is this a draft? true/false
toc: true  # Show table of contents? true/false
type: docs  # Do not modify.

# Add menu entry to sidebar.
# - name: Declare this menu item as a parent with ID `name`.
# - weight: Position of link in menu.
menu:
  1-sentiment-analysis:
    name: Overview
    weight: 1
---

## Giới thiệu

Đây là chủ đề hấp dẫn để nghiên cứu và phân tích về cảm xúc của người dùng thông qua các phương tiện mạng xã hội. Việc phân tích sentiment, giúp chủ doanh nghiệp biết lắng nghe và thấu hiểu những gì đang được nói về thương hiệu và sản phẩm của mình trên các phương tiện thông tin đại chúng. Chủ đề nào được đề cập tới, nói như thế nào, tốt hay xấu, tốt về mặt nào và xấu về mặt nào?

Như vậy việc đo lường **cảm xúc** của người dùng thực sự quan trọng trong việc quản lý các chiến dịch truyền thông hoặc bảo vệ thương hiệu. Một số lợi ích chúng ta có thể thấy như:

* **Giúp brand nắm được tình hình thị trường:** Biết được điểm mạnh, điểm yếu của sản phẩm hoặc thương hiệu, biết được những mặt đang được đánh giá cao, mặt nào đang là tâm điểm của thảo luận tiêu cực
* **Giúp Agency quản lý thương hiệu phản hồi:** Nắm được những khía cạnh được đánh giá cao của thương hiệu/sản phẩm và có được thông tin nhanh chóng về các thảo luận tiêu cực (ở đâu, mang nội dung gì) cho phép agency có thể đến tận nơi thảo luận được viết để phản hồi kịp thời. Việc này không những giúp nâng cao hiệu quả hoạt động của agency mà còn giúp agency và brand chủ động hơn trong việc ngăn ngừa và xử lý khủng hoảng.

![Social listening tool](/img/aiml/sociallisteningtool.jpg)

Việc theo dõi sự thay đổi của Sentiment trong một thời gian dài sẽ nói sức khỏe của thương hiệu giúp các `brand manager` và các `marketer` phần nào đánh giá lại hiệu quả hoạt động của các chiến dịch marketing và đưa ra định hướng cho các chiến dịch trong tương lai.

![Amazon customer reviews](/img/aiml/amazon-customer-reviews.png)

**Sentiment analysis** là một chủ đề thách thức trong Machine Learning. Người nói thể hiện cảm nhận của mình thông qua ngôn ngữ tự nhiên có bản chất `nhập nhằng`, `mơ hồ` đã gây không ít khó khăn để làm cho máy tính có thể hiểu được. Chưa kể, họ sử dụng các cách chơi chữ, ẩn ý hay các kí hiệu thể hiện cảm xúc như: **`:), :(, =)))`**

## Mục tiêu khóa học

* Nghiên cứu một vấn đề xuyên suốt nội dung khóa học
* Tổng quan về lý thuyết và các kỹ thuật thực hiện
* Sử dụng các kỹ thuật cơ bản nhất, nêu được những lợi ích và hạn chế khi sử dụng, định hướng phát triển
* Thiết kế dạng top-down để người học có thể hình dung ngay về mục tiêu và triển khai chiến lược

## Đối tượng khóa học

* Là tutorial cơ bản dành cho người mới bắt đầu nghiên cứu về phân tích cảm xúc
* Người đã có nền tảng hệ thống lại kiến thức, có thể lắp giáp triển khai một dịch vụ

## Nội dung kiến thức

* Sử dụng tập dữ liệu: [Web data: Amazon Fine Foods reviews](http://snap.stanford.edu/data/web-FineFoods.html)
* Áp dụng kỹ thuật Sentiment Analysis, như:
  * 

## Các thuật ngữ

* **Brand:** Ở nghĩa rộng, là một dấu hiệu (hữu hình hoặc vô hình) đặc biệt để nhận biết một sản phẩm hàng hoá hay một dịch vụ nào đó được sản xuất hay được cung cấp bởi một cá nhân hay một tổ chức
* **Agency**: là các công ty dịch vụ hay một đơn vị truyền thông quảng cáo cung cấp dịch vụ tiếp thị quảng cáo cho các công ty khác

## Tham khảo

* [Vén màn bí mật công nghệ phân tích cảm xúc của các Social Listening Tool](https://www.brandsvietnam.com/congdong/topic/1412-Ven-man-bi-mat-cong-nghe-phan-tich-sentiment-cam-xuc-cua-cac-Social-Listening-Tool)
* [Sentiment Analysis cơ bản](https://ongxuanhong.wordpress.com/2016/12/03/sentiment-analysis-co-ban/)
* [[VNLP Core] [3] Bài toán phân loại văn bản - Phân tích cảm xúc của bình luận](https://forum.machinelearningcoban.com/t/vnlp-core-3-bai-toan-phan-loai-van-ban-phan-tich-cam-xuc-cua-binh-luan-text-classification/2371)
* [Phân loại văn bản Tiếng Việt tự động - Phần 1](https://viblo.asia/p/phan-loai-van-ban-tieng-viet-tu-dong-phan-1-yMnKM3bal7P)
* [Sentiment Analysis sử dụng Tf-Idf áp dụng cho ngôn ngữ tiếng việt](https://techblog.vn/moi-cac-ban-gop-y-project-sentiment-analysis-su-dung-tf-idf-ap-dung-cho-ngon-ngu-tieng-viet)
* [Thảo luận trên form Machine Learning](https://forum.machinelearningcoban.com/search?q=sentiment)
