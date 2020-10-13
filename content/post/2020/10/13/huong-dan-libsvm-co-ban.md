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

LibSVM là công cụ hỗ trợ giải bài toán phân lớp SVM và hồi quy, một số bài toán như: Phân lớp C-SVM, nu-SVM, hồi qui epsilon-SVM và hồi qui nu-SVM. Thư viện này, cung cấp một công cụ lựa chọn mô hình tự động đối với phân lớp C-SVM.

Một số chương trình có trong bộ thư viện này:

* svm-scale: Đây là một công cụ đối với việc xác định file dữ liệu vào.
* svm-toy: Đây là một giao diện đồ họa đơn giản thể hiện dữ liệu phân tách SVM trong mặt phẳng. Ta có thể kích vào cửa sổ để vẽ các điểm dữ liệu. Sử dụng nút “change” để chọn lớp 1 hoặc 2, nút “load” để đọc dữ liệu từ một file, nút “save” để lưu dữ liệu vào file, nút “run” để thu được một mô hình SVM và nút “clear” để xóa cửa sổ. Chú ý rằng, nút “load” và “save” chỉ áp dụng cho truờng hợp phân lớp, không áp dụng cho trường hợp hồi qui.
* svm-train: Chương trình được sử dụng để train dữ liệu trên tập dữ liệu quan sát được
* svm-predict: Chương trình được sử dụng để predict dữ liệu quan sát mới


Để sử dụng được thư viện LIBSVM, chúng ta phải đưa dữ liệu huấn luyện và kiểm tra theo cấu trúc tiêu chuẩn mà bộ thư viện quy định như sau:

```bash
# mỗi quan sát là một dòng dữ liệu
[label1] [index1]:[value1] [index2]:[value2] ...
...
...
```

Trong đó:

- Mỗi dòng là một dữ liệu quan sát
- **label1**: nhãn lớp quan sát được, là giá trị đích của tập huấn luyện, vì SVM chỉ hiểu được số liệu số nên mỗi nhãn phải "số hóa" nó bằng cách đặt cho các giá trị số khác nhau.
- **index1**, **index2**,... là các chỉ số đại diện của các đặc trưng có trong từ điển. Là một số nguyên bắt đầu từ 1.
- **value1**,**value2**,... là giá trị kiểu số thực ứng với các vị trí của các đặc trưng. Giá trị này thể hiện mức độ liên quan của đặc trưng đối với một phân loại nằm trong khoảng [-1, 1].

Ví dụ:

```bash
1 1:0 2:3
2 1:5 2:8
```

Chú ý: tại các quá sát có giá trị bằng 0 ta có thể bỏ đi luôn, ví dụ trên trở thành:

```bash
1 2:3
2 1:5 2:8
```

# svm-train

Đây là chương trình được sử dụng để train dữ liệu đầu vào với những quan sát thu thập được. Đầu ra của chương trình cho phép chúng ta thu được tệp mô hình (file .model)

Lệnh: 

```bash
svm-train.exe <data_file.txt>
# 1 file có tên giống tên file <train>.model được tạo ra sau khi train thành công
```

# svm-predict

Sử dụng mô hình và tập test để kiểm tra hiệu quả phân lớp.

Lệnh: 

```bash
svm-predict.exe <file test> <file model> <file output>
```

