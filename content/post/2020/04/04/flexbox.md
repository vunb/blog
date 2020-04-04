---
title: CSS3 Flexbox
date: 2020-04-04T06:55:52+07:00
draft: false
share: true

# View.
#   1 = List
#   2 = Compact
#   3 = Card
view: 2
tags:
- CSS3
- Flexbox
categories:
- BasicWeb
---

Sử dụng CSS để dàn bố cục trang web là một việc không dễ dàng. Trong rất nhiều trường hợp muốn tạo bố cục trang web như mong muốn, chúng ta thường sử dụng thuộc tính float ở rất nhiều nơi và đặt *position: absolute* cho những thành phần con nằm trong những thành phần cha có *position: relative*, việc này khiến ta phải viết rất nhiều code CSS và kết quả thì thực sự là khó đoán trước?

CSS3 ra đời giống như phiên bản cải thiện những nhược điểm hiện có của nó, trong đó bao gồm luôn việc cải thiện kỹ thuật dàn trang linh hoạt hơn, đơn giản hơn và thuộc tính CSS3 chúng ta sử dụng để dàn trang là Flexbox. Flexbox cho phép chúng ta có thể giải quyết rất nhiều vấn đề về dàn trang trong CSS chỉ bằng một vài dòng code? Và thực sự khi sử dụng nó bạn thấy rất thoải mái, tiện ích và gọn nhẹ.

# Flexbox là gì?

Flexbox là một kiểu dàn trang (layout mode) mà nó sẽ tự cân đối kích thước của các phần tử bên trong để hiển thị trên mọi thiết bị. Nói theo cách khác, bạn không cần thiết lập kích thước của phần tử, không cần cho nó float, chỉ cần thiết lập nó hiển thị chiều ngang hay chiều dọc, lúc đó các phần tử bên trong có thể hiển thị theo ý muốn.

Theo lời khuyên từ Mozilla thì chúng ta sử dụng Flexbox để thiết lập bố cục trong phạm vi nhỏ (ví dụ như những khung trong website) và khi thiết lập bố cục ở phạm vi lớn hơn (như chia cột website) thì vẫn nên sử dụng kiểu thông thường là dàn trang theo dạng lưới (grid layout).

# Tham khảo

Một số bài viết về Flexbox rất công phu để các bạn có nhiều chiều về kỹ thuật này, cũng như hiểu hơn về nó.

* [Giới thiệu về CSS3 Flexbox](https://viblo.asia/p/gioi-thieu-ve-css3-flexbox-3P0lPM785ox)
* [DÀN TRANG VỚI CSS FLEXBOX TOÀN TẬP](https://thachpham.com/web-development/html-css/huong-dan-css3-flexbox-toan-tap.html)
* [Basic concepts of flexbox](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout/Basic_Concepts_of_Flexbox)
