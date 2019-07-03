---
title: Sử dụng mô hình được huấn luyện bằng Tensorflow trong C++
date: 2017-06-27T00:00:00Z
draft: false
share: false

# View.
#   1 = List
#   2 = Compact
#   3 = Card
view: 2
tags:
- tensorflow
- howto
categories:
- Tensorflow

# Optional header image (relative to `static/img/` folder).
header:
  caption: ""
  image: ""
---

Một trong những khả năng của Tensorflow đó là định nghĩa và huấn luyện model sử dụng **Python API** và chuyển model học được sang sử dụng trong **C++**.

Các bước thực hiện
==================

1. Định nghĩa input, output graph của model
2. Lưu lại các checkpoints. (Bước này rất quan trọng, bởi vì tất cả các biến được huấn luyện và lưu giữ ở bước này)
3. Lưu lại `graph` (raw definition, no variable). Đặt là `input_graph`
4. Sử dụng file `freeze_graph` để kết hợp cấu trúc (3) `input_graph` với các giá trị tại mỗi node (2) và sinh ra một graph model mới, đặt là: `output_graph`
5. Sử dụng `output_graph` trong file **C++** để suy diễn. #Optional: Có thể map ánh xạ output của mạng vào các nhãn label.
6. Tạo một file build trong thư mục `tensorflow/tensorflow/{our_project}`. Việc này mất một khoảng thời gian để bundle tất cả các file thư viện của tensorflow vào một file có thể chạy.
7. File thực thi đã sẵn sàng để chạy!

**Chi tiết các bước:** [Exporting trained TensorFlow models to C++ the RIGHT way!](https://medium.com/@hamedmp/exporting-trained-tensorflow-models-to-c-the-right-way-cf24b609d183)

Liên kết tham khảo
==================

* [Training a TensorFlow graph in C++ API](https://tebesu.github.io/posts/Training-a-TensorFlow-graph-in-C++-API)
* [Exporting trained TensorFlow models to C++ the RIGHT way!](https://medium.com/@hamedmp/exporting-trained-tensorflow-models-to-c-the-right-way-cf24b609d183)
