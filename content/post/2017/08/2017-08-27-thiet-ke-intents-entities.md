---
layout: post
title: Chatbots - Thiết kế các intents và entities cho các mô hình NLP
category: Chatbots
tags: chatbot-design
---

![chatbots and design intents](/img/chatbots-design-intents-entities.jpg)

Chìa khóa để cho một con bot có thể hiểu được con người là nó phải có khả năng hiểu các ý định của con người và trích xuất các thông tin liên quan từ ý định đó và tất nhiên có các hành động đáp ứng tương thích với thông tin đó.

Xử lý ngôn ngữ tự nhiên (NLP) là khoa học của việc trích xuất ý định và thông tin từ văn bản `text`. Lý do mà bạn thấy rất nhiều nền tảng phát triển bot ra đời như nấm cùng với NLP như một dịch vụ nền tảng. Việc kết nối các kênh mạng xã hội và phát triển bot không phải là một vấn đề, liên kết thiếu duy nhất đó là một nền tảng NLP mà `có thể mở rộng` và `dễ dàng làm việc`, bởi vì bạn sẽ không học NLP để tạo ra một con bot ngớ ngẩn!

Một vài nền tảng dịch vụ phổ biển:

1. Luis.ai - by Microsoft
2. Wit.ai - by Facebook
3. Api.ai - by Google
4. Watson - by IBM

Một nền tảng bot lý tưởng cung cấp:

1. **Một dịch vụ NLP** - bạn có thể tự huấn luyện
2. **SDK** để hỗ trợ và xử lý các hội thoại và `meta-data` của chúng.
3. Một nền tảng **lưu trữ các con bot**.
4. Một nền tảng cho phép **kết nối bot với nhiều kênh**, mạng xã hội, dịch vụ khác nhau.

Trong khi NLP như 1 dịch vụ (NLP-as-a-service) giúp cho người phát triển có phát triển NLP trong khoảng thời gian ít nhất có thể, đôi khi developer vẫn có khả năng tiếp tục huấn luyện dịch vụ NLP đạt chất lượng cao nhất có thể. Mỗi dịch vụ NLP có miền và tập ngôn ngữ riêng của nó và bạn phải chọn domain thích hợp nhất để triển khai một dịch vụ NLP. Trong bài note này sẽ chỉ ra một vài tình huống tốt nhất để huấn luyến một dịch vụ mô hình NLP.

# Intent

Intent đơn giản là ý định của người dùng cuối, những ý định này được chuyển tải bởi người dùng tới con bot của bạn. Bạn có thể chủ yếu đặt ý định vào 2 nhóm chính:

1. Các ý định ngẫu nhiên, casual intents
2. Các ý định nghiệp vụ, business intents.

**1. Casual Intents** - Đây là những ý định mở đầu hoặc kết thúc một cuộc hội thoại. Nhưng lời chào như: `hi`, `hello`, `hallo`, `ciao`, hay `bye` là những câu lệnh mở đầu hoặc kết thúc một cuộc hội thoại. Những ý định này nên hướng con bot của bạn phản hồi bằng một câu trả lời gợi ý như: "Xin chào, tôi có thể giúp được gì cho bạn?" hay "Tạm biệt, cảm ơn đã trò chuyện cùng với tôi".

Các ý định ngẫu nhiên cũng bao gồm các ý định **Khẳng định - Affirmative** và **Không nhận - Negative** cho các câu nói như: "Ok", "vâng", "Không, không phải cái này."

Bằng các ý định chung chung có thể giúp bạn xử lý tất cả các ý định của khách hàng thay vì đưa câu chuyện đã có vào cuộc trò chuyện với bot. Ví dụ, nếu con bot chỉ hỏi một câu hỏi cho người dùng cuối - bạn nên mong đợi hoặc là một ý định khẳng định Affirmative hoặc một ý định Negative và nếu có bất cứ thứ gì khác bot có thể hỏi cùng một câu hỏi. Các ý đồ Affirmative và Negative nên xử lý tất cả các câu nói như vậy.

**2. Business Intents** - Đây là các ý định được map trực tiếp với ý đồ ban đầu của các con bot khi được xây dựng, tức là bot cần phải hỗ trợ và xử lý được các ý định này của người dùng cuối khi họ truy cập vào website. Ví dụ, nếu ý định đó là thông tin của một bộ phim, khi có 1 câu nói **"Khi nào danh sách của Schindler được phát hành?"** là một ý định nghiệp vụ mà có ý định tìm ra năm phát hành của bộ phim và bạn nên gắn nhãn nó theo một cái tên có thể hiểu được, giống như: **"GetReleaseYearByTile"**. Lý tưởng là bạn nên nghĩ về các ý định nghiệp vụ bởi vì phần còn lại của câu chuyện như những câu chào hay sự lựa chọn thì được quản lý chung bởi các ý định ngẫu nhiên Casual Intents.

# Entities

Các ý định nghiệp vụ có `meta-data` về các intent được gọi là **"Entities"**. Lấy ví dụ về intent *"GetReleaseYearByTile"*, với input: "Khi nào Danh sách của Schindler được phát hành?". Ở đây "Danh sách của Schindler" là tên của bộ phim mà người dùng "có ý định" tìm ra năm phát hành. Quá trình tìm kiếm các thực thể entities có thể được hiểu giống với việc gán nhãn thẻ câu Part-of-Sentence tagging (POS). Tuy nhiên, một người sử dụng NLP as a service thì bạn không cần phải biết kỹ thuật của việc POS tagging được thực hiện như thế nào, nhưng nếu muốn có một bài báo hay nói về nó ở đây: http://nlp.stanford.edu/software/tagger.shtml

Khi người dùng nghĩ về việc thiết kế intent thì các entities cũng phải được xác định và gán nhãn theo đó. Một lần nữa, bạn cũng có các thực thể chung được gán nhãn để sử dụng trong các mục đích chung như các số liệu metrics (bao gồm: số lượng, số đếm, khối lượng, ...), ngày tháng và hầu hết các dịch vụ NLP cho phép bạn gán thẻ thực thể của các loại chung như vậy mà không gặp phải bất kỳ rắc rối lớn nào.

 Một vài thực thể có thể được gán như những thực thể phức hợp (composite entities), giống như việc có nhiều hơn một thực thể (có các thực thể thành phần bên trong nó). Là một khoa học, không quan trọng nếu bạn không có những tính năng này trong dịch vụ NLP của bạn, miễn là bạn có ghi nhãn thực thể đơn giản. Một nhãn phải được xác định các thực thể trước khi gán nhãn các thực thể phức hợp.

Ví dụ: Tìm cho tôi đôi giày thể thao Red Adidas cỡ 8.

Intent: ------------------- SearchProduct  
Entities: -----------------  
Composite Entity: --------- ProductDetail  
Component Entity: ---------  
Size: --------------------- 8  
Brand: -------------------- Adidas  
Color: -------------------- Red  
Category: ----------------- Sport Shoes  

### Huấn luyện các Intents và Entities

* Rule #1 của việc huấn luyện bất kỳ một mô hình học máy nào là --- Bạn không bao giờ có thể huấn luyện đủ, lấy thêm dữ liệu và tiếp tục train nó.  
* Rule #1 của việc huấn luyện bất kỳ một mô hình học máy nào là --- Bạn không bao giờ có thể huấn luyện đủ, lấy thêm dữ liệu và tiếp tục train nó.  
* Rule #1 của việc huấn luyện bất kỳ một mô hình học máy nào là --- Bạn không bao giờ có thể huấn luyện đủ, lấy thêm dữ liệu và tiếp tục train nó.  

Lý tưởng là bạn nên huấn luyện dịch vụ NLP với các tập ngữ liệu thực tế, nếu bạn có những đoạn chat với khách hàng qua Facebook, hoặc Skype hoặc bất kỳ mạng xã hội nào bạn làm việc với các tin nhắn có thể giúp cho việc huấn luyện intent, hoặc không thì bạn có thể nghĩ tới việc huấn luyện các intent với các bộ dữ liệu tự sản xuất (Manufactured utterances). Ví dụ -- Huấn luyện intent *"GetReleaseYearByTile"* với các bộ dữ liệu huấn luyện cho intent này như sau:

* what was the release year of movie Pulp fiction
* in which year Pulp fiction was released
* when did pulp fiction came
* When was Pulp fiction released

Huấn luyện với bộ dữ liệu giả lập **Manufactured utterances** giúp cho việc khởi động nhanh hệ thống nhưng sau một tgian hệ thống cần được huấn luyện lại khi có dữ liệu là các câu nói thực tế. Quá trình huấn luyện lại hệ thống luôn được tiếp tục cho đến khi tỉ lệ lỗi được giảm. Sự khác biệt là những câu nói bạn nhận được từ các cuộc trò chuyện thực sự càng tốt bạn có thể huấn luyện dịch vụ NLP của mình cho các ý định. Tối thiểu là 5 hoặc tối ưu là 10 câu nói cho mỗi ý định là đủ tốt để khởi động hệ thống chạy thực.

Các dịch vụ NLP đi qua một quá trình học **Supervised - Unsupervised - Supervised**. Mỗi giai đoạn học được giám sát đóng vai trò như một vòng phản hồi trở lại cho việc điều chỉnh lại mô hình NLP.

Người dùng huấn luyện hệ thống với các câu nói - đây là quá trình học giám sát, sau đó dịch vụ NLP tự học trên cơ sở học tập có giám sát và khoảng 10% những gì mà dịch vụ NLP đã học được trong quá trình học không giám sát sẽ được hỏi lại từ dịch vụ NLP cho người sử dụng, nếu những gì nó học được là chính xác hay không, người sử dụng một lần nữa đạo tạo lại hoặc bằng việc khẳng định / phủ nhận kết quả học tập không giám sát của dịch vụ NLP và huấn luyện lại mô hình. Quá trình này tiếp tục và cuối cùng người sử dụng sẽ tìm thấy câu hỏi ít hơn bởi dịch vụ NLP với mức độ tin cậy hơn đối với các caua hỏi của nó yêu cầu người dùng xác nhận.

Các bước thực hiện chính
========================

1. Xác định ý định trước -- phân biệt giữa ý định chung/ngẫu nhiên và những ý định nghiệp vụ
2. Xác định các thực thể -- phân biệt giữa các thực thể liên quan đến số liệu (metric) và danh từ (noun)
3. Nếu có thể hãy huấn luyện với tập văn bản hội thoại thực tế, không có thì tự tạo ra tập mẫu. Tối thiểu 5 câu nói cho việc xác định 1 ý định, hoặc tối ưu nên thiết kế được 10 câu / 1 ý định.
4. Huấn luyện, sử dụng, đạo tạo lại - Vòng lặp phản hồi liên tục đào tạo và cải tiến mô hình NLP.

Tham khảo liên kết
==================

* [Chat Bots — Designing Intents and Entities for your NLP Models][5]
* [How to Prevent a Plague of Dumb Chatbots][1]
* [Setting Intent - an Article by the NLP and Coaching Institute][2]
* [Natural Language Processing - Research at Google][3]
* [The Stanford Natural Language Processing Group][4]


[1]: https://www.technologyreview.com/s/601279/how-to-prevent-a-plague-of-dumb-chatbots/
[2]: http://www.nlpca.com/DCweb/settingintent.html
[3]: https://research.google.com/pubs/NaturalLanguageProcessing.html
[4]: http://nlp.stanford.edu/software/tagger.shtml
[5]: https://medium.com/@brijrajsingh/chat-bots-designing-intents-and-entities-for-your-nlp-models-35c385b7730d