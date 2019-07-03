---
title: Tìm hiểu mô hình CRF - Conditional Random Fields
date: 2017-10-11T00:00:00Z
draft: true
share: true
ref: http://blog.echen.me/2012/01/03/introduction-to-conditional-random-fields/

# View.
#   1 = List
#   2 = Compact
#   3 = Card
view: 2
tags:
- Machine Learning
categories:
- NLP

# Optional header image (relative to `static/img/` folder).
header:
  caption: ""
  image: ""
---

Hãy tưởng tượng bạn có một chuỗi các bức ảnh sinh hoạt hàng ngày của cô vợ mình tên là **Anna**, và bạn muốn dán nhãn *hoạt động* đại diện cho mỗi bức ảnh (ví dụ như: đang ăn, đang ngủ, đang lái xe, v.v.). Bạn sẽ làm như nào ?

Có một phương án là bỏ qua tính chất tuần tự của mỗi bức ảnh, và xây dựng một bộ phân lớp cho mỗi bức ảnh. Ví dụ: Với các bức ảnh đã được gán nhãn trong 1 tháng, bạn có thể **nhận biết** được các đặc trưng là với các bức ảnh tối

