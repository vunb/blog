---
title: Tích hợp chạy trên trình duyệt web, ngày 02/02/2021
linktitle: Chạy trên trình duyệt
toc: true
type: docs
date: "2021-02-02T12:05:52+07:00"
lastmod: "2021-02-02T12:05:52+07:00"
draft: false
menu:
  botscript-ai:
    parent: Ghi chép
    weight: 1

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 2
---

## Mở đầu và cảm tưởng cột mốc này

Trí thông minh (nhân tạo) cơ bản nhất của một robot tương tác với con người nằm ở chỗ nó có khả năng: Trích rút thông tin; Khai phá thông tin và Truy xuất thông tin phản hồi. 

Ở đây, chúng ta tập trung vào thuật ngữ **nhân tạo** để hiểu rõ thêm rằng, con người chúng ta đang cố gắng tạo ra hệ thống thông minh có khả năng bắt chước khả năng "nhận thức" của con người và có khả năng liên kết với trí thức (trí tuệ + nhận thức), thể hiện ở khả năng "học tập" và "giải quyết vấn đề". Hệ thống thông minh hay trí thông minh mà tôi đang cố gắng tạo ra, đó chính là BotScript.

Ngày nay, ngoài Turing test ra thì chúng ta đã có thước đo sự lúng túng (Perplexity), trung bình độ nhạy cá tính (SSA) và khả năng giao tiếp tự nhiên của đội quân robot thông minh này; Kể đến như: Meena (Google), Mitsuku, Cleverbot, XiaoIce, and DialoGPT. Tất nhiên, để tiệm cận được với con người thì còn chặng đường rất dài nữa.

![Perplexity](/img/botscript-ai/perplexity.png)

[Source: https://ai.googleblog.com/2020/01/towards-conversational-agent-that-can.html]

Trong khi [AMR](https://github.com/amrisi/amr-guidelines/blob/master/amr.md) còn đang được soạn thảo, cho đến khi nó ready thì còn rất nhiều việc phải làm.

BotScript không cố gắng vượt qua Meena hay những robot kể trên về khả năng giao tiếp. Xong, BotScript cũng đặt ra một mục tiêu to lớn đó là khả năng giải quyết vấn đề của con người, vấn đề của tổ chức. Tức là một hệ thống thông minh hướng nhiệm vụ.

## Khả năng chạy trên Trình duyệt Web

Cho đến thời điểm này BotScript đã có thể chạy trên trình duyệt web độc lập và đầy đủ các tính năng như khi chạy phía Server Backend.

Một số tính năng đặc biệt mạnh mẽ như:

1. Hệ thống plugins đa dạng và phong phú (free built-in và phiên bản trả phí commerce)
2. Khả năng giao tiếp với các hệ thống backend thông qua API (tương lai có thể hỗ trợ Websocket)
3. Khả năng lưu trữ nhật ký và truy vết các hội thoại
4. Truy cập vào kho tri thức miễn phí vào nền tảng [botscript.ai/kb?id=?](https://botscript.ai/kb)
5. Giao tiếp với người dùng thông qua Prompt tags, typings hoặc voice
6. Lập lịch, tự động phản hồi thông tin qua Browser Notification hoặc Chat Window.

Note:

* Prompt tags: là các thẻ được gợi ý trong hội thoại trao đổi với người mà người dùng có thể phản hồi bằng cách gõ tay, click vào thẻ tag hoặc ra lệnh bằng giọng nói.
* AMR: Phiên bản hiện tại Abstract Meaning Representation (AMR) 1.2.6 Specification

## Chương trình mẫu HTML

Bạn có thể truy cập và trải nghiệm tại đây: [play.botscript.ai/](https://play.botscript.ai/)

Phiên bản trình diễn (demo) ban đầu chỉ đơn giản là nhập sẵn các câu giao tiếp và trả lời, kết quả như hình sau:

![BotScript browser demo](/img/botscript-ai/bs-browser-demo.png)

Chương trình cài đặt cho kết quả trên:

```html
<!DOCTYPE html>
<html>

<head>
  <meta charset="UTF-8" />
  <title>Hello BotScript! - @Yeu.AI</title>
  <link rel="icon" href="data:,">
</head>

<body>
  <h1 id="greeting">BotScript: Hello World!</h1>
  <p id="messages"></p>
  <script src="botscript.ai.js"></script>
  <script src="botscript.plugins.js"></script>
  <script>
    const {BotScript, Request, TYPES} = BotScriptAI;
    const bot = new BotScript();
    // bot.parse('+ * \n - Hello World!\n - Yes?\n - How are you?');
    bot.parse('> addTimeNow');
    bot.parse(`
    @ geoip https://api.ipify.org/?format=json
    #- header: value
    #- header: value (2)

    # conditional command
    + what is my ip
    * true @> geoip
    - Here is your ip: $ip

    + what time is it
    - it is $time

    `);

    /**
     * parse data from URL.
     * */
    (async function () {
      await bot.parseUrl('https://raw.githubusercontent.com/yeuai/botscript/master/examples/basic.bot');
      await sendBot('what time is it');
      await sendBot('what is my ip');
      await sendBot(`I'm vunb`);
    })();

    /**
     * Send bot message and wait response.
     * */
    async function sendBot(message, id = 'messages') {
      const de = document.getElementById(id);
      const reply = await bot.handleAsync(new Request(message));

      let humReq = document.createElement("div");
      let botRes = document.createElement("div");
      humReq.append(`Human say: ${message}`);
      botRes.append(`Bot say: ${reply.speechResponse}`);
      de.append(humReq);
      de.append(botRes);
    }

    sendBot('Hello!');

  </script>
</body>

</html>
```

## Tham khảo

* Demo: https://play.botscript.ai/
* Source: https://github.com/yeuai/botscript
