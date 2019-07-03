---
title: Biểu diễn văn bản trong Machine Learning sử dụng scikit-learn
date: 2017-09-29T00:00:00Z
draft: true
share: true
ref: https://machinelearningmastery.com/prepare-text-data-machine-learning-scikit-learn/

# View.
#   1 = List
#   2 = Compact
#   3 = Card
view: 2
tags:
- Text Representations
- Machine Learning
categories:
- NLP

# Optional header image (relative to `static/img/` folder).
header:
  caption: ""
  image: ""
---

Dữ liệu văn bản yêu cậu sự chuẩn bị đặc biết trước khi chúng ta đưa nó vào sử dụng trong các mô hình dự đoán.

Văn bản cần phải được phân tích để tách ra các từ có ý nghĩa, quá trình này được gọi là tokenization. Sau khi có được văn bản chuẩn hóa rồi, các từ được tách ra sẽ được mã hóa thành các con số, có thể là số nguyên, số nhị phân hoặc số thực để làm đầu vào input cho các thuật toán machine learning, ta gọi quá trình này là trích xuất đặc trưng (feature extraction hay vectorization)

Chúng ta sẽ tìm hiểu thư viện `scikit-learn` trong python để thực hiện các tác vụ tokenization và feature extraction với dữ liệu của bạn. Qua đó bạn sẽ biết cách chuẩn bị với dữ liệu riêng của bạn cho các mô hình dự đoán.

Cụ thể, chúng ta sẽ thực hiện các việc sau:

* Tính vector số lượng (word count) với class CountVectorizer.
* Tính vector tần suất (word frequency) với class TfidfVectorizer.
* Tính vector số duy nhất (unique integers) với class HashingVectorizer.

# Bag-of-Words Model

Do chúng ta không thể làm việc trực tiếp với văn bản trong các thuật toán machine learning. Vì thế, chúng ta cần phải chuyển đổi văn bản sang dạng số học mà các thuật toán có thể hiểu được.

Ví dụ, ta cần phân lớp một tập các tài liệu văn bản, thì mỗi văn bản là một đầu vào "input" và mỗi nhãn đầu ra là "output" cho thuật toán. Các thuận toán nhận đầu vào là các con số, do đó, chúng ta cần chuyển đổi các tài liệu đó sang các vector có số chiều cố định.

Một mô hình đơn giản và hiệu quả cho các văn bản tài liệu trong machine learning, đó là **Bag-of-Words**, viết tắt `BOW`.

