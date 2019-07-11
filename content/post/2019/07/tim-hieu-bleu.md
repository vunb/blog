---
title: Tìm hiểu về độ đo BLEU
date: 2019-07-10T00:00:00Z
draft: false
share: true
katex: true
markup: "mmark"

tags:
- BLEU
- Bilingual Evaluation Understudy

categories:
- NLP
---

BLEU là viết tắt của **Bilingual Evaluation Understudy**.

BLEU thường được sử dụng trong bài toàn dịch máy (**Machine Translation**) như một độ đo hay một hệ số điểm khi so sánh một bản dịch (candidate translation) với một hay nhiều bản dịch tham khảo (reference translation). Mặc dù vậy, BLEU cũng có thể được sử dụng để đánh giá cho các bài toán sinh văn bản (text generation) như:

- **Language generation**
- **Image caption generation**
- **Text summarization**
- **Speech recognition**

Nói một cách nôm na thì bạn cần chấm điểm một câu, biết trước một câu mẫu thì bạn dùng BLEU. BLEU có giá trị trong khoảng $$ (0.0, 1.0) $$. $$ 1.0 $$ tức là perfect match, đúng hoàn toàn, còn $$ 0.0 $$ tức là perfect mismatch, bạn không đúng tí nào cả. 

Các ưu điểm của BLEU có thể kể đến là:
- Nhanh và chi phí tính toán thấp
- Dễ hiểu
- Không phụ thuộc vào ngôn ngữ
- Có độ tương đồng cao với cách đánh giá của con người
- Được sử dụng rộng rãi

## Phương pháp tính

Cách tính của BLEU cũng khá đơn giản. Phương pháp đếm số matching **n-grams** của candidate và reference (hoặc match trên bất kỳ reference nào nếu như có nhiều reference), kết quả sẽ là số match chia cho số từ của candidate. Các match này không phụ thuộc vào vị trí, do vậy BLEU không sử dụng word order. Càng match nhiều tức là càng tốt. 

Tuy nhiên, nếu chỉ đếm số từ match thông thường sẽ nảy sinh ra việc một từ match với reference nhưng được lặp lại nhiều lần trong candidate (gọi là overgenerate "resonable" words trong paper [BLEU: a Method for Automatic Evaluation of Machine Translation](http://www.aclweb.org/anthology/P02-1040.pdf)). 

~~~~
# overgenerated example
reference = 'this is an example'
candidiate = 'this this this this'
~~~~

Do đó, khi đếm matching **n-grams** cần chú ý cả số lần xuất hiện của từ trong reference, một từ trong reference khi được match rồi thì không nên match nữa.

BLEU còn được dùng để đánh giá một **corpus** (tập hợp của các sentence, hay một đoạn văn) khá là tốt. Đầu tiên là tính số match với từng câu. Cộng các số này rồi chia cho tổng số n-gram từ các câu là ra **modified precision score** cho test corpus

$$ \frac{\sum_{C \epsilon \{Candidates\}} \sum_{\textit{n-gram} \epsilon C} Count_{clip}(\textit{n-gram})}{\sum_{C' \epsilon \{Candidates\}} \sum_{\textit{n-gram'} \epsilon C'} Count(\textit{n-gram'})} $$

Không có gì là hoàn hảo nên cũng không có bản dịch hoàn hảo. Điểm của người dịch cũng không phải lúc nào cũng là $$1.0$$. Điểm BLEU phụ thuộc vào số lượng cũng như chất lượng của của các reference, đây cũng là những yếu tố có thể gây ra khó khăn cho việc tính điểm trên dataset.

## Tính BLEU với NLTK

**Python Natural Language Toolkit library (NLTK)** cung cấp cho bạn một số hàm để tính toán BLEU bao gồm cả sentence và corpus

~~~~
# two references for one sentence
from nltk.translate.bleu_score import sentence_bleu
reference = [['this', 'is', 'a', 'test'], ['this', 'is' 'test']]
candidate = ['this', 'is', 'a', 'test']
score = sentence_bleu(reference, candidate)
print(score) # output: 1.0

# two references for the 1st sentence and one reference for the 2nd sentence
from nltk.translate.bleu_score import corpus_bleu
references = [[['this', 'is', 'a', 'test'], ['this', 'is' 'test']], [['this', 'is', 'my', 'blog']]]
candidates = [['this', 'is', 'a', 'test'], ['this', 'is', 'my', 'house']]
score = corpus_bleu(references, candidates)
print(score) # output: 0.7231269021297695
~~~~

## Cumulative and Individual BLEU

NLTK cho phép bạn có thể đặt các trọng số  (**weights**) khác nhau cho các **n-grams** khác nhau để tính điểm BLEU cuối cùng. Dựa và trọng số này ta chia ra cumulative và individual BLEU.

~~~~
# n-gram individual BLEU
from nltk.translate.bleu_score import sentence_bleu
reference = [['this', 'is', 'a', 'test']]
candidate = ['this', 'is', 'a', 'test']
print('Individual 1-gram: %f' % sentence_bleu(reference, candidate, weights=(1, 0, 0, 0)))
print('Individual 2-gram: %f' % sentence_bleu(reference, candidate, weights=(0, 1, 0, 0)))
print('Individual 3-gram: %f' % sentence_bleu(reference, candidate, weights=(0, 0, 1, 0)))
print('Individual 4-gram: %f' % sentence_bleu(reference, candidate, weights=(0, 0, 0, 1)))
# Individual 1-gram: 1.000000
# Individual 2-gram: 1.000000
# Individual 3-gram: 1.000000
# Individual 4-gram: 1.000000
~~~~

**weights** là 1 tuple thể hiện trọng số tương ứng với từng i-gram score ở vị trí i-th.

Thông thường, trong các bài báo nghiên cứu, để so sánh các kiến trúc khác nhau trên một benchmark dataset, **cumulative BLEU-1, BLUE-2, BLEU-3, BLEU-4** được sử dụng với các weight như sau:

~~~~
# cumulative BLEU scores
from nltk.translate.bleu_score import sentence_bleu
reference = [['this', 'is', 'small', 'test']]
candidate = ['this', 'is', 'a', 'test']
print('Cumulative 1-gram: %f' % sentence_bleu(reference, candidate, weights=(1, 0, 0, 0)))
print('Cumulative 2-gram: %f' % sentence_bleu(reference, candidate, weights=(0.5, 0.5, 0, 0)))
print('Cumulative 3-gram: %f' % sentence_bleu(reference, candidate, weights=(0.33, 0.33, 0.33, 0)))
print('Cumulative 4-gram: %f' % sentence_bleu(reference, candidate, weights=(0.25, 0.25, 0.25, 0.25)))
# Cumulative 1-gram: 0.750000
# Cumulative 2-gram: 0.500000
# Cumulative 3-gram: 0.632878
# Cumulative 4-gram: 0.707107
~~~~

Bạn có thể đọc thêm paper [BLEU: a Method for Automatic Evaluation of Machine Translation](http://www.aclweb.org/anthology/P02-1040.pdf), Work examples trong [bài gốc](https://machinelearningmastery.com/calculate-bleu-score-for-text-python/) để hiểu rõ hơn về BLEU.

## Acknowledgment

Nguồn bài viết của: [Trung Nghĩa](https://github.com/lego1st)

* Source: [101 BLEU score trong Xử lý văn bản](https://lego1st.github.io/nlp/mlearning/2019/02/16/bleu-101.html)

## References

* [A Gentle Introduction to Calculating the BLEU Score for Text in Python](https://machinelearningmastery.com/calculate-bleu-score-for-text-python/)
* [BLEU - Wikipedia](https://en.wikipedia.org/wiki/BLEU)
* [BLEU: a Method for Automatic Evaluation of Machine Translation](http://www.aclweb.org/anthology/P02-1040.pdf)
