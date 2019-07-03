---
layout: post
title: Kiến thức toán học cơ bản để làm việc với Deep learning
category: deep-learning
tags: neural-networks machine-learning deep-learning
---

Trước khi bắt đầu vào việc học mạng nơ-ron và deep learning, chúng ta cũng cần chuẩn bị một số kiến thức nền tảng của toán học cần thiết. Một vài chủ đề toán học quan trọng để chúng ta có thể hiểu được các chủ đề trong phương pháp học nhiều tầng **Deep learning**.

# 1. ĐẠI SỐ TUYẾN TÍNH

Đại số tuyến tính bao gồm các dạng liên tục chứ không hoàn toàn là Toán học rời rạc, nhiều người làm khoa học máy tính có rất ít kinh nghiệm với nó. Hiểu biết về đại số tuyến tính là một kỹ năng cần thiết để có thể hiểu được và làm việc được với các thuật toán **Machine learning**, đặc biệt là với **Deep learning**.

Nghiên cứu về Đại số tuyến tính liên quan tới các đối tượng toán học sau:

1. **Đại lượng vô hướng (Scalar)**: Đại lượng (số) vô hướng là đại lượng được mô tả hoàn toàn chỉ bằng độ lớn. Mô tả bằng một con số mà thôi, không hơn không kém. Ví dụ như tốc độ, thể tích, khối lượng, nhiệt độ, công suất, thời gian, ... Chúng ta viết các đại lượng vô hướng bằng chữ cái không in đậm, có thể viết hoa, ví dụ: $$ (x_1, N, y, k) $$
2. **Vector**: Vector là một mảng (1-D) chứa các phần tử của nó là dãy các số vô hướng. Các số này được sắp xếp theo một trật tự và chúng ta có thể xác định các số này bằng chỉ số thứ tự của nó. Thường được ký hiệu bằng chữ cái không viết hoa in đậm, ví dụ: $$ (\mathbf{y}, \mathbf{x}_1) $$
3. **Ma trận**: Ma trận là một mảng 2 chiều (2-D), mỗi phần tử của nó được xác định bởi 2 chỉ số. Thường được ký hiệu bởi chữ cái viết hoa và in đậm, ví dụ: $$ (\mathbf{A, X, Y, W}) $$
4. **Tensor**: Ten-xơ là đối tượng hình học miêu ta quan hệ tuyến tính giữa các đại lượng `Vector`, `Vô hướng`, và các `ten-xơ` với nhau. Theo định nghĩa thì `Vector` và `Vô hướng` cũng là ten-xơ. Bậc (hay *hạng*) của một ten-xơ bằng số chiều của mảng cần để biểu diễn nó, hay tương đương với chỉ số cần để đánh dấu các thành phần của mảng. Đại lượng `vô hướng` là ten-xơ hạng **0**, ...

Một phép toán quan trọng trên ma trận đó là phép **Chuyển vị**. Chuyển vị của một ma trận là một ma trận mà ở đó các hàng được thay thế bằng các cột và ngược lại. Hay cách hình dùng khác thì ma trận chuyển vị là ảnh của ma trận qua **đường chéo chính**, chạy từ trên xuống theo hướng bên phải, bắt đầu từ góc trái nhất trên cùng (nghe mô tả mà cũng hoảng). Ký hiệu chuyển vị của ma trận $$\mathbf{A}$$ là $$\mathbf{A}^T$$, và được định nghĩa bằng công thức $$ \mathbf{A}^T(i, j) = \mathbf{A}(j, i) $$.

Trong ngữ cảnh của **deep learning**, chúng ta cũng sử dụng các ký hiệu thông thường ít hơn. Ví dụ, khi ta cộng ma trận với một vector, sinh ra một ma trận: $$ \mathbf{C} = \mathbf{A} + \mathbf{b} $$, trong đó $$ \mathbf{C}(i, j) = \mathbf{A}(i, j) + \mathbf{b}(j) $$. Nói cách khác, vector $$\mathbf{b}$$ được cộng vào mỗi hàng của ma trận. Với cách viết tắt này loại bỏ việc xác định thêm 1 ma trận với mỗi hàng có giá trị là $$ \mathbf{b} $$ trước khi thực hiện phép cộng hai ma trận. Việc sao chép $$ \mathbf{b} $$ như vậy được gọi là **broadcasting**.

Chuyển vị của một tích ma trận có dạng đơn giản là: $$ (\mathbf{AB})^T = \mathbf{B}^T\mathbf{A}^T $$. Ma trận nghịch đảo của $$ \mathbf{A} $$ được ký hiệu là $$ \mathbf{A}^{-1} $$, và tích của chúng đúng bằng ma trận đơn vị: $$ \mathbf{A}^{-1}\mathbf{A} = \mathbf{I} $$. Tuy nhiên, $$ \mathbf{A}^{-1} $$ chủ yếu có ích như một công cụ lý thuyết, và nó không nên được sử dụng ngoài thực tế trong hầu hết các ứng dụng phần mềm. Bởi vì $$ \mathbf{A}^{-1} $$ được biểu diễn với độ chính xác hạn chế trên máy tính, các thuật toán sử dụng giá trị của $$ \mathbf{b} $$ thường đạt được đó chính xác hơn ước lượng của $$ \mathbf{x} $$.

Chúng ta cần một vài chủ đề khác để hiểu hơn về kỹ thuật ứng dụng.

# 2. NORM (Chuẩn)

Trong machine learning, chúng ta thường đo độ lớn của một vector (điểm dữ liệu) hoặc khoảng cách giữa 2 vector, bằng việc sử dụng 1 hàm, được gọi là chuẩn. Việc đo độ lớn và khoảng cách giữa các vector với nhau, chúng ta có thể đánh giá được điểm nào là điểm gần nhất với một điểm dữ liệu cho trước; chúng ta cũng cần đánh giá độ chính xác của việc ước lượng là như thế nào.

Giả sử có các vector cột: $$ \mathbf{x} = [x_1; x_2; \cdots; x_n], \mathbf{y} = [y_1; y_2; \cdots; y_n] $$.

Với *p* **là một số không nhỏ hơn 1** bất kỳ, tổng quát $$ \mathbf{x} $$ có chuẩn norm *p* được tính bởi công thức:

$$ \Vert\mathbf{x}\Vert_p = (\vert x_1 \vert^p + \vert x_2 \vert^p + \cdots + \vert x_n \vert^p)^{\frac{1}{p}} ~~ (1) $$

* Khi $$ p = 2 $$, ta có chuẩn Euclid **norm 2**: $$ \Vert\mathbf{x}\Vert_2 = \sqrt{x_1^2 + x_2^2 + \cdots + x_n^2} ~~~ (2) $$
* Khi $$ p = 1 $$, ta có **norm 1**: $$ \Vert\mathbf{x}\Vert_1 = \vert x_1 \vert + \vert x_2 \vert + \cdots + \vert x_n \vert ~~~ (3) ~~~ $$ là tổng các trị tuyệt đối từng phần tử của $$ \mathbf{x} $$.
* Khi $$ p \rightarrow \infty $$, ta có norm $$ p $$ chính là trị tuyệt đối của phần tử lớn nhất của vector đó: $$ \Vert\mathbf{x}\Vert_{\infty} = \max_{i = 1, 2, \cdots, n} \vert x_i \vert ~~~ (4) $$

Chặt chẽ hơn, một chuẩn là một hàm số $$ f() $$ ánh xạ một điểm $$ \mathbf{x} $$ từ không gian $$ n $$ chiều sang tập số thực một chiều $$ \mathbf{R} $$ được gọi là norm nếu thỏa mãn các tính chất sau đây:

1. $$ f(\mathbf{x}) = 0 \geq 0 $$. Dấu bằng xảy ra $$ \Leftrightarrow \mathbf{x = 0} $$.  
2. $$ f(\alpha \mathbf{x}) = \vert\alpha\vert f(\mathbf{x}), ~~~ \forall \alpha \in \mathbb{R} $$.  
3. $$ f(\mathbf{x}_1) + f(\mathbf{x}_2) \geq f(\mathbf{x}_1 + \mathbf{x}_2), ~~\forall \mathbf{x}_1, \mathbf{x}_2 \in \mathbf{R}^n $$. Đây chính là bất đẳng thức tam giác, nếu coi $$ \mathbf{x_1 = w - y, x_2 = z - w} $$ với $$\mathbf{w}$$ là một điểm bất kỳ trong không gian.

Tham khảo thêm [định nghĩa][1] về **NORM** [tại đây][1]

# 3. TRỊ RIÊNG

To be continue ...

Liên kết tham khảo
==================

* [Basic Mathematics for Deep Learning][3]
* [Một số kiến thức về Đại Số Tuyến Tính, Xác Suất Thống Kê, Toán Tối Ưu cần thiết cho Machine Learning][2]

[1]: http://machinelearningcoban.com/math/#-norms-chuan
[2]: http://machinelearningcoban.com/math
[3]: https://medium.com/towards-data-science/deep-learning-basic-mathematics-for-deep-learning-a82981e95e3b