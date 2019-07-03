---
title: AMR - Tiến tới tương lai chuyển hóa tri thức
date: 2017-09-27T00:00:00Z
draft: true
share: true

# View.
#   1 = List
#   2 = Compact
#   3 = Card
view: 2
tags:
- AMR
- Guidelines
- amrisi
categories:
- NLP

# Optional header image (relative to `static/img/` folder).
header:
  caption: ""
  image: ""
---

https://github.com/amrisi/amr-guidelines/blob/master/amr.md
https://amr.isi.edu/

wordnet thì một từ có bao nhiêu nghĩa
probank thì nó bảo với nghĩa của một động từ, thì arg0 là gì
arg1 là gì
trong ví dụ kia thì inspire được chọn nghĩa 01
với nghĩa này arg0 là "được truyền cảm hứng bởi điều gì" (cooking her faimly and her dog)
arg1 là ai được truyền cảm hứng (một người tên là Rachael Ray)
(y)
vậy mình có argN đúng ko ?
N > 0 😀

anh nhìn nó định nghĩa thằng run này
vì dụ thằng run-03, nghĩa giống như kiểu (chạy quảng cáo)
(y)

thì nó định nghĩa hết arg1 là hàng hóa
arg2 là giá
arg3 là đứa
arg3 là đứa mua
uh

ý là bọn này ở level cao quá rồi
ý em là họ hoàn thiện rồi đúng ko ?
còn mình sẽ phải thực hành ở level-1 ?

ý em là khi câu đã được parse dưới dạng này, thì nó rất sát với việc biểu diễn ngữ nghĩa rồi
ví dụ với pos tag, anh chẳng có gì nhiều ngoài các danh động tính từ
với dependency parsing, anh cũng biết động từ này trỏ đến danh từ kia các kiểu
với named entity recognition, anh sẽ biết được text này mentions đến ai, tổ chức nào
với semantic role labelling anh sẽ biết ai, làm gì
nhưng với thằng amr, thì kiểu như "hiểu" được hết
😍
1
tất nhiên nó có nhiều limitation
nhưng nếu parse câu dưới dạng này, thì quá khủng rồi
quá hấp dẫn để thử nghiệm 😀

em cũng chưa biết bắt đầu từ đâu
nhưng nếu một ngày chỉ cần parse được 5 câu này thôi
em nhầm
một ngày annnote được 5 câu này
chắc sẽ bằng annote 100 câu pos tag

mỗi cái là thằng này lại yêu cầu wordnet với propbank
tiếng Việt làm gì có resource nào
có bộ wordnet
nhưng ko open

vậy mới khó

Thủ tục gán nhãn AMR
====================

Cho 1 câu: The dog ate the bone that he found
-> Hãy tìm biểu diễn AMR của câu trên
Các bước và thủ tục:

1. Tìm từ focus
- Ta có được động từ chính: eat
-> graph_b1:
(e / eat-01)

2. Tìm các thực thể có quan hệ với eat
- Ta có thực thể quan hệ: dog, bone
-> graph_b2:
(a / eat-01
    :ARG0 (d / dog)
    :ARG1 (b / bone))

3. Tìm quan hệ ngược với trên mỗi thực thể
+ Ta chỉ thấy có 1 quan hệ ngược với thực thể, là: tìm thấy (find) -> xương (bone)
+ Thực thể dog ko có quan hệ ngược tham chiếu
-> vậy có graph_b3:
(a / eat-01:
    ARG0: (d / dog)
    ARG1: (b / bone
        ARG1-of: (f / find-01)))

4. Bổ sung các quan hệ có thể đổi chỗ (phân lại)
+ Con chó - tìm thấy
(a / eat-01:
    ARG0: (d / dog)
    ARG1: (b / bone
        ARG1-of: (f / find-01:
                    ARG0: d)))
