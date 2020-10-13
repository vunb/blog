---
title: Hướng dẫn sử dụng LibSVM cơ bản
date: 2020-10-13T16:36:52+07:00
draft: false
share: true

# View.
#   1 = List
#   2 = Compact
#   3 = Card
view: 2
tags:
- classification
- regression
categories:
- LibSVM
---

LibSVM là công cụ hỗ trợ giải bài toán phân lớp theo phương pháp SVM.

Để sử dụng được thư viện LIBSVM, chúng ta phải đưa dữ liệu huấn luyện và kiểm tra theo cấu trúc tiêu chuẩn mà bộ thư viện quy định như sau:

> 	[Indexlabel] [index1]:[value1] [index2]:[value2] ...
> 	[Indexlabel] [index1]:[value1] [index2]:[value2] ...

Trong đó:

- Mỗi dòng là một dữ liệu quan sát
- **Indexlabel**: nhãn lớp câu hỏi, là giá trị đích của tập huấn luyện, vì SVM chỉ hiểu được số liệu số nên mỗi nhãn phải "số hóa" nó bằng cách đặt cho các giá trị số khác nhau.
- **index1**, **index2**,... là các chỉ số đại diện của các đặc trưng có trong từ điển. Là một số nguyên bắt đầu từ 1.
- **value1**,**value2**,... là giá trị kiểu số thực ứng với các vị trí của các đặc trưng. Giá trị này thể hiện mức độ liên quan của đặc trưng đối với một phân loại nằm trong khoảng [-1,1]. Do các đặc trưng trong phân loại câu hỏi đều là đặc trưng nhị phân nên lúc huấn luyện giá trị này sẽ là 1.
