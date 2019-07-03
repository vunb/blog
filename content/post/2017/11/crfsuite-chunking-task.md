---
title: CRFSuite - Tìm hiểu và ứng dụng với task Chunking
date: 2017-11-05T00:00:00Z
draft: false
share: true
ref: http://www.chokkan.org/software/crfsuite/tutorial.html

# View.
#   1 = List
#   2 = Compact
#   3 = Card
view: 2
tags:
- CRFsuite
- Text Chunking
- POS Tagging
categories:
- Neural Networks
- Deep Learning

# Optional header image (relative to `static/img/` folder).
header:
  caption: ""
  image: ""
---

Giới thiệu
==========

Text-chunking là bài toán chia một văn bản thành các cụm thành phần có liên quan tới cú pháp. Ví dụ, trong câu: **"He reckons the current account deficit will narrow to only # 1.8 billion in September."** có thể được phân tích thành như sau:

> [NP He ] [VP reckons ] [NP the current account deficit ] [VP will narrow ] [PP to ] [NP only # 1.8 billion ] [PP in ] [NP September ] .

Trong ví dụ này, NP đại diện cho một cụm danh từ, VP là một cụm động từ, và PP là cụm giới từ. Text-chunking là một task, có nhiệm vụ là dán các nhãn cho một nhóm các phần tử (token) trong một câu văn bản, kết quả là ta thu được một chuỗi các nhãn tương ứng. Chúng ta sẽ sử dụng ký pháp `IOB` để gán nhãn cho các token trong câu.

Như vậy, một chunk là NP (một đoạn liên tục các token) thì có chú thích như sau:

* **B-NP** bắt đầu một chunk
* **I-NP** bên trong một chunk
* **O** nếu token đó không thuộc chunk nào cả

Ta có một kết quả đầy đủ cho ví dụ trên như sau:

```bash
B-NP He
B-VP reckons
B-NP the
I-NP current
I-NP account
I-NP deficit
B-VP will
I-VP narrow
B-PP to
B-NP only
I-NP #
I-NP 1.8
I-NP billion
B-PP in
B-NP September
O    .
```

Mục tiêu của bài hướng dẫn này, là xây dựng một model có thể dự đoán, tách được các chunk và gán nhãn tương ứng cho nó. Tôi sẽ sử dụng công cụ [crfsuite](https://npmjs.com/package/crfsuite) với ngôn ngữ **node/javascript**.

Dữ liệu huấn luyện
==================

Bài hướng dẫn này sử dụng dữ liệu được cung cấp bởi task [CONLL-2000 shared task: Chunking](https://dl.acm.org/citation.cfm?id=1117631)

Bạn có thể tìm thấy mã nguồn và dữ liệu của bài hướng dẫn này, tại đây: https://github.com/vntk/vntk-chunking

```bash
Confidence NN B-NP
in IN B-PP
the DT B-NP
pound NN I-NP
is VBZ B-VP
widely RB I-VP
expected VBN I-VP
to TO I-VP
take VB I-VP
another DT B-NP
sharp JJ I-NP
dive NN I-NP
if IN B-SBAR
trade NN B-NP
figures NNS I-NP
for IN B-PP
September NNP B-NP
, , O
due JJ B-ADJP
for IN B-PP
release NN B-NP
tomorrow NN B-NP
, , O
fail VB B-VP
to TO I-VP
show VB I-VP
a DT B-NP
substantial JJ I-NP
improvement NN I-NP
-- More  --
```

Dữ liệu bao gồm một tập các câu (sequences), mỗi câu chứa một chuỗi các từ ('Confidence', 'in', ...), các nhãn POS ('NN', 'IN', ...), các nhãn chunk ('B-NP', 'B-PP') ngăn cách nhau bởi khoảng trắng. Trong bài này, chúng ta sẽ khởi tạo một model CRF để gán các nhãn cú pháp chunking, với điều kiện là biết trước nhãn từ loại (POS - Part of Speech) của chúng.

Trích chọn đặc trưng (Feature selection)
========================================

Bước tiếp theo là tiền xử lý dữ liệu training và testing để trích xuất ra được đặc trưng của words trong tập dữ liệu. CRFsuite có khả năng tạo ra các đặc trưng từ các thuộc tính (attribute - còn gọi là tính chất) của tập dữ liệu. Tổng quan, thì đây là một quá trình quan trọng nhất của tiếp cận machine-learning, bởi vì một đặc trưng ảnh hưởng rất lớn đến độ chính xác của nhãn được dự báo. Ví dụ sau đây, chúng ta sẽ lấy 19 loại attributes của một từ tại vị trí `t` (vị trí thứ t trong chuỗi câu).

```js
w[t-2], w[t-1], w[t], w[t+1], w[t+2],
w[t-1]|w[t], w[t]|w[t+1],
pos[t-2], pos[t-1], pos[t], pos[t+1], pos[t+2],
pos[t-2]|pos[t-1], pos[t-1]|pos[t], pos[t]|pos[t+1], pos[t+1]|pos[t+2],
pos[t-2]|pos[t-1]|pos[t], pos[t-1]|pos[t]|pos[t+1], pos[t]|pos[t+1]|pos[t+2]
```

Trong danh sách này, thì w[t] và pos[t] đại diện cho từ vựng (words) và từ loại (part-of-speech) tương ứng tại vị trí `t` trong câu. Các đặc trưng này thể hiện tính chất của từ vựng tại vị trí `t` bằng việc sử dụng các thông tin xung quanh từ đó, ví dụ: w[t-1] và pos[t+1]. Ví dụ, xem xét tính chất của token `the` sau đây:

```js
        He PRP B-NP
        reckons VBZ B-VP
t -->   the DT B-NP
        current JJ I-NP
        account NN I-NP
```

từ vựng `the` tại ví trí `t` có những thuộc tính sau đây (t được lược bỏ cho đơn giản và dễ nhìn):

```js
w[-2]=He, w[-1]=reckons, w[0]=the, w[1]=current, w[2]=account
w[-1]|w[0]=reckons|the, w[0]|w[1]=the|current
pos[-2]=PRP, pos[-1]=VBZ, pos[0]=DT, pos[1]=JJ, pos[2]=NN
pos[-2]|pos[-1]=PRP|VBZ, pos[-1]|pos[0]=VBZ|DT, pos[0]|pos[1]=DT|JJ, pos[1]|pos[2]=JJ|NN
pos[-2]|pos[-1]|pos[0]=PRP|VBZ|DT, pos[-1]|pos[0]|pos[1]=VBZ|DT|JJ, pos[0]|pos[1]|pos[2]=DT|JJ|NN
```

Trong ví dụ này, thuộc tính `w[0]=the` biểu diễn cho sự kiện mà mã từ vựng hiện tại là `the`, và thuộc tính `pos[0]|pos[1]|pos[2]=DT|JJ|NN` biểu diễn cho sự kiện từ loại tại ví trí hiện tại, từ tiếp theo, từ sau nữa là `DT`, `JJ`, `NN` tương ứng. Bạn có thể hình dung ta dịch chuyển 1 cửa sổ có window_size=2 tại ví trí `t`. CRFsuite sẽ học sự liên kết giữa các thuộc tính này và nhãn tương ứng của từ đang xem xét `the`, đó là `B-NP` để dự đoán nhãn khi cho 1 đầu vào (từ vựng) cụ thể khi biết các tính chất xung quanh nó. 



