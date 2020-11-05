---
title: Chuẩn bị dữ liệu cho bài toán phân loại văn bản SVM
date: 2020-10-13T17:36:52+07:00
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

# 1. Hiểu cách dữ liệu được biểu diễn như thế nào?

Đối với bài toán phân loại văn bản, dữ liệu mà chúng ta thường có là tập dữ liệu văn bản ngôn ngữ tự nhiên, hoặc là Tiếng Việt hoặc một ngôn ngữ khác như tiếng Anh chẳng hạn. Và chúng ta cần phải phân loại chúng vào các nhóm giả định trước. Ví dụ, bạn có một tập các câu Trích dẫn và muốn tìm những câu trích dẫn về tình yêu, hay bạn có những emails và muốn lọc ra nhưng email rác và bỏ chúng vào thùng rác.

SVM là một thuật toán học có giám sát. Nó có nghĩa là bạn cần phải gắn nhãn cho dữ liệu một cách thủ công với những gì bạn đánh giá đó là lựa chọn chính xác. Sau đó, SVM sẽ được sử dụng để huấn luyện mô hình với tập dữ liệu đã được gắn nhãn. Cuối cùng là bạn có thể sử dụng mô hình SVM thu được để dự đoán dữ liệu chưa được gắn nhãn.

Theo thứ tự, để huấn luyện một mô hình SVM, bạn cần phải chuẩn bị dữ liệu theo các bước sau:

1. Gán nhãn dữ liệu
2. Sinh tập từ điển chứa các từ vừng trong miền dữ liệu
3. Tạo một ma trận tần suất (toán học) [document-term](http://en.wikipedia.org/wiki/Document-term_matrix)

Nếu bạn chưa có tập dữ liệu nào, hãy tải xuống một vài [bộ dữ liệu mẫu tại đây](http://www.csie.ntu.edu.tw/~cjlin/libsvmtools/datasets/), được công bố miễn phí cho cộng đồng.

Tuy nhiên, nó trông như thế này và khá khó hiểu bởi cái nhìn đầu tiên.

![svm datasets](/img/svm/libsvm_dataset.png "Tập dữ liệu không dễ để đọc")

Cái chúng ta cần là phân loại văn bản, nhưng dữ liệu để huấn luyện trong file này chỉ chứa những con số.

# 2. Biến đổi dữ liệu theo cách của bạn

Như vậy chúng ta cần phải chuyển đổi dữ liệu văn bản, sang tập dữ liệu mà thuật toán học máy có thể hiểu được, ở đây, cụ thể là SVM. Hãy xem xét một ví dụ đơn giản về dữ liệu thời tiết sau đây.

Mục tiêu của chúng ta là dự đoán được theo dữ kiện văn bản đó đang nói về nắng (sunny) hay mưa (rainy).
Để đơn giản hơn thì mỗi cấu sẽ được viết bởi 2 từ: sunny ở rainy.

![SVM_Tutorial_unlabeled_data](/img/svm/SVM_Tutorial_unlabeled_data.png "Tập dữ liệu chưa được gắn nhãn")

Đối với mỗi dòng, chúng ta ghi như sau:

* +1 nếu chúng ta nghĩ rằng nó nên được phân loại vào lớp "sunny"
* -1 nếu chúng ta nghĩ rằng nó nên được phân loại vào lớp "rainy"

![SVM_Tutorial_initial_dataset](/img/svm/SVM_Tutorial_initial_dataset.png "Tập dữ liệu khởi tạo được gắn nhãn")

Sau đó, chúng ta sẽ xem xét từng từ trong tập dữ liệu đó, và tạo ra một từ vựng và đưa vào tập từ điển của miền dữ liệu thời tiết.

Như vậy, từ điển mà chúng ta sẽ có 2 từ vựng và được sắp xếp theo thứ tự Alphabet (an pha bê) như sau:

![SVM_Tutorial_vocabulary.png](/img/svm/SVM_Tutorial_vocabulary.png "Tập từ điển từ vựng")

Tới đây, cuối cùng là chúng ta tạo ra một ma trận tần suất document-term.

* Dòng dữ liệu được ghi bắt đầu bởi lớp đại diện (+1 hoặc -1)
* Tiếp theo sau là chỉ số index của từ vựng đó trong tập từ điển. Đối với từ sunny, có chỉ số là 2.
* Theo sau từ vựng đó là số lần nó xuất hiện trong câu, và được phân tách bởi dấu hai chấm (:).

![SVM_Tutorial_Document_Term_Matrix.png](/img/svm/SVM_Tutorial_Document_Term_Matrix.png "Ma trận tần suất document-term")

Như bạn có thể thấy, bây giờ chúng ta đã có một tập dữ liệu trông giống như tập dữ liệu mẫu đã tải xuống ở mục 1. Theo phương thức như trên, bạn đã có thể tự tạo cho mình tập dữ liệu riêng theo mục đích và bài toán cụ thể của mình rồi đấy.

