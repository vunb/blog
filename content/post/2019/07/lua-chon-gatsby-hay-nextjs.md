---
title: Lựa chọn Gatsby hay Nextjs
date: 2019-07-18T00:00:00Z
draft: false
share: true
#ad: true
#katex: true
#markup: "mmark"

tags:
- Gatsby
- Nextjs
- GraphQL
- Redux
- React
- Today I Learned

categories:
- React

# header:
#   caption: "Nên chọn framework React nào?"
#   image: "dev/gatsbyvsnext.png"
---

![Gatsby hay Nextjs](/img/dev/gatsbyvsnext.png)

# Gatsby vs Next

Gatsby và Nexjs gần đây khá hot và được cộng đồng quan tâm. Nhìn qua, thì cả hai có vẻ rất giống nhau, và có một số điểm chung như:

* Khởi tạo dự án web rất nhanh
* Mặc định khởi tạo web SPA
* Mặc định hỗ trợ SEO
* Có đội ngũ kinh nghiệm

Những điều trên khiến bạn có thể thấy khó lựa chọn thằng nào để sử dụng???

Mặc dù chúng có nhiều điểm tương đồng, xong có một vài điểm khác biệt sau đây để bạn có thể lựa chọn một cách dễ dàng hơn:

# Static site generator vs. server side rendered pages

Static site generator có nghĩa là ứng dụng được sinh ra ngay trong quá trình **build time** và nó không sử dụng server. Trái lại, server-side rendering là các trang HTML được sinh ra *dynamically* mỗi lần có một request mới đến. Và nó sử dụng server cho việc này.

Gatsby:

* Gatsby là một static site generator tool
* Gatsby tạo ra các tài liệu HTML/CSS/JS, điều này có nghĩa là bạn có thể host nó ở `S3`, `Netlify`, `Github`, hoặc các dịch vụ hosting khác.
* Do tính chất tĩnh, nên cực kỳ có thể mở rộng đối với hệ thống có traffic cao.
* Gatsby không cần server

Nextjs:

* Next render các tài liệu HTML với mỗi request đến trong thời gian chạy
* Next cũng là một server để kết xuất ra các trạng HTML từ server
* Next cũng hỗ trợ **[export ra web tĩnh](https://nextjs.org/docs/#static-html-export)** để chạy trên hosting giống Gatsby.
* Next cần server để chạy

Tất nhiên cả hai đều có thể gọi **API** từ phía client.

# Xử lý dữ liệu của Gatsby

Một điểm khác biệt lớn khác nữa đó là cách xử lý dữ mà 2 nền tảng này cung cấp.

* Tất cả dữ liệu trong ứng dụng Gatsby đưa vào GraphQL. Nếu bạn lấy dữ liệu từ API server, ngay sau đó bạn phải thông báo cho Gatsby để import dữ liệu vào trong db GraphQL.
* React component sẽ lấy dữ liệu từ GraphQL.
* Gatsby có nhiều plugins cho việc này để dễ dàng tích hợp với dữ liệu từ nhiều nguồn khác nhau như: [Contentful](https://www.gatsbyjs.org/packages/gatsby-source-contentful/?=contentfu#gatsby-source-contentful), [Wordpress](https://www.gatsbyjs.org/packages/gatsby-source-contentful/?=contentfu#gatsby-source-contentful), [MongoDB](https://www.gatsbyjs.org/packages/gatsby-source-contentful/?=contentfu#gatsby-source-contentful), và [GraphQL](https://www.gatsbyjs.org/packages/gatsby-source-contentful/?=contentfu#gatsby-source-contentful).
* Khi build production thì GraphQL không được sử dụng, nhưng dữ liệu thì được lưu trong tệp JSON.

Gatsby chỉ cho bạn cách xử lý dữ liệu trong ứng dụng. Next thì không và việc đó hoàn toàn phụ thuộc vào quyết định của bạn. Bạn phải tự dựng kiến trúc cách xử lý dữ liệu, hoặc GraphQL, hoặc Redux, ...

# Tôi nên chọn Gatsby hay Next?

Việc lựa chọn vẫn phụ thuộc vào tình huống sử dụng của bạn:

## Trường hợp không nên sử dụng Gatsby

Nếu hệ thống của bạn muốn xây dựng có rất nhiều content, đặc biệt là sự tăng trưởng của content theo thời gian, khi đó hệ thống sinh web tĩnh như Gatsby không phải là giải pháp tốt cho bạn. Lý do là nó sẽ mất rất nhiều thời gian để build site nếu có có nhiều content.

Khi tạo một hệ thống rất lớn với hàng nghìn **Pages** thì nó thực sự trở thành vấn đề, hệ thống build rất chậm. Bạn có thể phải chờ 20 phút để sẵn sàng publish và trạng thái go live của hệ thống không phải là giải pháp tốt!

Vì vậy, nếu bạn có một trang web có nội dung mà bạn sẽ mong đợi tăng trưởng và phát triển theo thời gian, thì Gatsby có thể không mở rộng được cho bạn. Và bạn không chỉ nghĩ về việc bạn có bao nhiêu nội dung bây giờ, mà còn bạn mong đợi bao nhiêu trong tương lai. Bạn sẽ có bao nhiêu **Pages** trong 1 năm? 5 năm?

## Trường hợp nên sử dụng Gatsby

Ví dụ hệ thống của bạn là một site về thương mại điện tử bán điện thoại? Cửa hàng có < 200 sản phẩm. Bạn có thể chỉ mất vài phút để dựng được một hệ thống lên và không kỳ vọng danh mục sản phẩm nhiều lên trong tương lai. Gatsby hoàn toàn tuyệt vời trong trường hợp này.

Bạn không bao giờ phải lo lắng hay suy nghĩ về quy mô. Bạn thừa biết rằng hệ thống có thể xử lý được bất kỳ lưu lượng nào vì nó chỉ là dữ liệu tĩnh!!! :smile:

Một tình huống khác nữa đó là lưu được toàn bộ lịch sử của dữ liệu. Ví dụ, định kỳ hàng ngày bạn phải build và deploy hệ thống mỗi khi có dữ liệu thay đổi và dữ liệu cũ được lưu lại trong **S3**. Điều này có nghĩa là bạn luôn có thể deploy lại hệ thống (cũ) trước đó. Nếu dữ liệu

# Liên kết tham khảo

Bài viết tham khảo và tổng hợp lại từ một số nguồn để đưa ra đánh giá riêng cá nhân. Có nghĩa là bạn cần có tư duy độc lập để đưa ra quyết định lựa chọn của bạn! Ngoài ra bạn có thể tham khảo các liên kết ngoài trogn danh sách dưới đây.

* [Why we decided to move to Next.js](https://dev.to/giogiordano93/why-we-decided-to-move-tonextjs-28gp)
* [Nextjs for everyone — with some basic knowledge of React](https://www.freecodecamp.org/news/an-introduction-to-next-js-for-everyone-507d2d90ab54/)
* [Why you should use GatsbyJS to build static sites](https://www.freecodecamp.org/news/why-you-should-use-gatsbyjs-to-build-static-sites-4f90eb6d1a7b/)
* [Why choose gatsby.js when developing your new website](https://ori.solutions/blog/why-choose-gatsby-js-when-developing-your-new-website/)
* [3 reasons why you should consider Gatsby.js for your next project](https://www.storyblok.com/tp/3-reasons-why-you-should-consider-gatsby-js-for-your-next-project)
* [Gatsby vs Next](https://blog.jakoblind.no/gatsby-vs-next/)
