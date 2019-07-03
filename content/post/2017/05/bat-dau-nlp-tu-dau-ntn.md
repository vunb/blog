---
title: Bắt đầu NLP từ đâu và như thế nào ?
date: "2017-05-31T00:00:00Z"

# View.
#   1 = List
#   2 = Compact
#   3 = Card
view: 1

# Optional header image (relative to `static/img/` folder).
header:
  caption: "Source: [**Towards Data Science**](https://towardsdatascience.com/6a62aa4eaeff)"
  image: "this-is-what-i-needed.png"
---


Có thể bạn đã nghe rất nhiều về `Trí tuệ nhân tạo (AI)`, `Học máy (Machine Learning)`, hay `Xử lý ngôn ngữ tự nhiên (NLP)`. Và rất muốn được tiếp cận nhưng chưa biết phải bắt đầu từ đâu và cách tiếp cận như thế nào ? Bài viết này cũng là bài đầu tiên mà tôi muốn tìm hiểu tổng quan nhất về các lý thuyết, thuật toán và các ứng dụng cụ thể trong một domain nhỏ của **AI**, đó chính là **NLP**. Làm thế nào để máy tính có thể hiểu được ngôn ngữ tự nhiên ? Làm thế nào để máy tính có trí thông minh như con người ?

Tôi đã từng nghe rằng: Nếu bạn phải `trả lời` lần 2 cho cùng một câu hỏi, thì có lẽ 1 ý tưởng hay là đưa nó vào blog. Theo nguyên tắc này, tôi cũng muốn ghi chú lại các bước, câu trả lời cho câu hỏi: `Tôi có kiến thức khoa học trong ngành (*), và tôi muốn học NLP. Vậy tôi nên bắt đầu từ đâu?` Để chúng ta có bước khởi đầu thuận lợi và đầy cảm hứng.

Sau đây là các phương pháp mà tôi dự định tiếp cận theo cách của [@Melanie Tosik](https://medium.com/@melanietosik) và chia sẻ với các bạn, mà tôi nghĩ chúng ta có thể bắt đầu ngay bằng 1 khóa học căn bản, sau đó tự mình trải nghiệm và cài đặt lại các phương pháp để hiểu hơn về bản chất. Đây có thể đây là kim chỉ nam giúp tôi không bị lệch hướng và cũng hi vọng nó có ích cho những người mới như bạn và tôi:

Trước khi bắt đầu, chúng ta cần nhận thức được danh sách dưới đây thực sự là một điểm bắt đầu rất `chung`, cơ bản và có thể không đầy đủ. Để tránh tình huống bị ngập tràn trong một núi thông tin, tôi cố gắng thêm các chú thích bằng các mô tả ngắn gọn và ước lượng các mức độ khó khăn trong ngoặc đơn (sẽ được cập nhật chi tiết hơn khi tôi được trải nghiệm hết). Bằng cách tiếp cận từ trên xuống (Top-Down) và các kỹ thuật thực hành ngay bằng các ví dụ được cài đặt bằng Python có thể giúp chúng ta nắm được một cách tổng quát nhất. Hiểu từ thực tế đến (quay trở về) lý thuyết!

Khóa học Online
===============

* [Dan Jurafsky & Chris Manning: Natural Language Processing](https://www.youtube.com/watch?v=nfoudtpBV68&list=PL6397E4B26D00A269) [video giới thiệu căn bản]
* [Stanford CS224d: Deep Learning for Natural Language Processing](http://cs224d.stanford.edu/syllabus.html) [Các thuật toán ML nâng cao: Deep learning, NN for NLP]
* [Coursera: Introduction to Natural Language Processing](https://www.coursera.org/learn/natural-language-processing) [Khóa học giới thiệu NLP của trường ĐH Michigan]

Các thư viện và mã nguồn mở
===========================

* [spaCy](https://spacy.io/) [blog](https://explosion.ai/blog/) [Thư viện python mới nổi với những ví dụ tuyệt vời, các hướng dẫn và demo trực quan]
* [NLTK](http://www.nltk.org/) [book](http://www.nltk.org/book/) [Thường được sử dụng cho việc giảng dạy, nghiên cứu học thuật]
* [Stanford CoreNLP](https://stanfordnlp.github.io/CoreNLP/) [Bộ công cụ phân tích chất lượng cao, bằng Java]

Blog tiếng Anh
==============

* [natural language processing blog](https://nlpers.blogspot.com/) (Hal Daumé)
* [Google research blog](https://research.googleblog.com/)
* [Language log](http://languagelog.ldc.upenn.edu/nll/) (Mark Liberman)

Blog tiếng Việt
===============

* [Machine Learning cơ bản cho người mới bắt đầu - Vũ Hữu Tiệp PSU](http://machinelearningcoban.com) - [Blog](https://tiepvupsu.github.io)
* [Machine Learning trong Xử Lý Ngôn Ngữ Tự Nhiên - Nhóm Đông Du Nhật Bản](http://viet.jnlp.org/kien-thuc-co-ban-ve-xu-ly-ngon-ngu-tu-nhien/machine-learning-trong-nlp)
* [Machine Learning cho người mới bắt đầu - Ông Xuân Hồng JAIST](https://ongxuanhong.wordpress.com/)
* [Machine Learning book for Vietnamese - Nguyễn Xuân Khánh University of Maryland](https://ml-book-vn.khanhxnguyen.com/) [Blog](http://khanhxnguyen.com/blog), [Tutorials](http://khanhxnguyen.com/tutorials)

Books
=====

* [Speech and Language Processing](https://web.stanford.edu/~jurafsky/slp3/) (Daniel Jurafsky and James H. Martin) - sách bao gồm những lý thuyết cơ bản
* [Foundations of Statistical Natural Language Processing](https://nlp.stanford.edu/fsnlp/) (Chris Manning and Hinrich Schütze) - các phương pháp thống kê
* [Introduction to Information Retrieval](https://nlp.stanford.edu/IR-book/) (Chris Manning, Prabhakar Raghavan and Hinrich Schütze) - sách hay về xếp hạng và tìm kiếm ngữ nghĩa
* [Neural Network Methods in Natural Language Processing](https://www.amazon.com/Network-Methods-Natural-Language-Processing/dp/1627052984) (Yoav Goldberg) - giới thiệu chi tiết hướng tiếp cận NN, phiên bản [primer (pdf)](http://u.cs.biu.ac.il/~yogo/nnlp.pdf)

Kỹ thuật khác
=============

* [How to build a word2vec model in TensorFlow](https://www.tensorflow.org/versions/master/tutorials/word2vec) - tutorial
* [Deep Learning for NLP resources](https://github.com/andrewt3000/dl4nlp) - dữ liệu mới nhất cho Deep learning, được tổ chức theo các topic
* [Last Words: Computational Linguistics and Deep Learning — A look at the importance of Natural Language Processing](http://mitp.nautil.us/article/170/last-words-computational-linguistics-and-deep-learning) - (Chris Manning) article
* [Natural Language Understanding with Distributed Representation](https://github.com/nyu-dl/NLP_DL_Lecture_Note/blob/master/lecture_note.pdf) (Kyunghyun Cho) các ghi chú về ML/NN tiếp cận bài toán Natural Language Understanding (NLU)
* [Quora: How do I learn Natural Language Processing?](https://www.quora.com/How-do-I-learn-Natural-Language-Processing)

DIY - Dữ liệu và các dự án (mục nhúng tay)
======================================

Với tập dữ liệu được tạo và public bởi **Nicolas Iderhoff**. Chúng ta là những người mới cần phải nhúng tay để thực sự bắt đầu làm việc trong lĩnh vực *NLP*. Dưới đây là danh sách các bài toán `NLP` cần giải được đề xuất bởi [Melanie Tosik](https://medium.com/@melanietosik):

* Xây dựng bộ [gán nhãn từ loại POS](https://en.wikipedia.org/wiki/Part-of-speech_tagging) (Part-of-Speech) dựa trên [mô hình Markov ẩn](https://en.wikipedia.org/wiki/Hidden_Markov_model) (HMM)
* Cài đặt thuật toán [CYK](https://en.wikipedia.org/wiki/CYK_algorithm) để phân tích bài toán [phân tích văn phạm phi ngữ cảnh](https://en.wikipedia.org/wiki/Context-free_grammar) (Context-free grammars)
* Xây dựng bộ phân lớp [Naive Bayes](https://en.wikipedia.org/wiki/Naive_Bayes_classifier) cho bài toán [lọc Spam](https://en.wikipedia.org/wiki/Naive_Bayes_spam_filtering)
* Xây dựng bộ kiểm tra chính tả [spell checker](https://en.wikipedia.org/wiki/Spell_checker) dựa trên kỹ thuật [edit distances] giữa các từ vựng với nhau.
* Xây dựng bộ sinh văn bản dựa vào [chuỗi Markov](https://en.wikipedia.org/wiki/Markov_chain)
* Xây dựng một mô hình thống kê [Topic model](https://en.wikipedia.org/wiki/Topic_model) sử dụng mô hình sinh [latent Dirichlet allocation](https://en.wikipedia.org/wiki/Latent_Dirichlet_allocation) (LDA)
* Sử dụng [word2vec] để sinh ra word embeddings từ tập ngữ liệu lớn (large text corpus), từ: [Wikipedia](https://en.wikipedia.org/wiki/Wikipedia:Database_download).

Chủ đề NLP trên mạng xã hội
===========================

* Twitter: [#nlproc](https://twitter.com/hashtag/nlproc), [list of NLPers](https://twitter.com/jasonbaldridge/lists/nlpers) (by Jason Baldrige)
* Reddit: [r/LanguageTechnology](https://www.reddit.com/r/LanguageTechnology)
* Medium: [Nlp](https://medium.com/tag/nlp)

Acknowledgment
==============

* Original Source: [How to get started in NLP](https://medium.com/towards-data-science/how-to-get-started-in-nlp-6a62aa4eaeff)
