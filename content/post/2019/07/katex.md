---
title: Katex
date: 2019-07-10T00:00:00Z
draft: false
share: false
ad: true
katex: true
markup: "mmark"

tags:
- Katex
- Latex
- Hugo
- Today I Learned

categories:
- TIL # Today I Learned

---

Cấu hình Hugo sử dụng `katex` và `mmark`. Không khó lắm, mất khoảng 15 phút là làm được. Sau khi cài đặt xong thì giờ quan tâm tới cách sử dụng thôi :smile:

### Display Block
Type equation on a single line, with top and bottom spaces. Use double dollar signs as delimiter.

```md
The following

$$\int_{a}^{b} x^2 dx$$

Is an integral
```

The following

$$\int_{a}^{b} x^2 dx$$

Is an integral

### Display Inline
Type the equation as per usual, nothing extra needed. Use double dollar signs as delimiter.
```md
Integrate $$\int x^3 dx$$
```

Integrate $$\int x^3 dx$$

### Notice

Để đoạn mã trên hoạt động được, thêm cấu hình vào từng bài post cấu hình sau:

```js
---
katex: true
markup: "mmark"
---
```

# Liên kết tham khảo

Một vài hướng dẫn cấu hình

* https://eankeen.github.io/blog/render-latex-with-katex-in-hugo-blog/
* https://katex.org/docs/browser.html
* https://katex.org/docs/autorender.html
