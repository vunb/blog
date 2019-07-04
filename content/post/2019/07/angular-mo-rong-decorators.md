---
title: Angular - Mở rộng Decorators
date: 2019-07-04T00:00:00Z
draft: true
share: true

# View.
#   1 = List
#   2 = Compact
#   3 = Card
view: 2
tags:
- Angular
- Decorators
- Sofware Development
categories:
- Angular

# Optional header image (relative to `static/img/` folder).
header:
  caption: "Source: [Custom Decorators for Angular](https://netbasal.com/95aeb87f072c)"
  image: "dev/decorator.png"
---

Bài post này giả sử bạn đã có background về `Angular` và `Decorators` rồi nhé!

Ý tưởng chính trong bài viết này là bạn cần viết ra một Decorator mới cho ứng dụng để bổ sung thông tin cho Component, thường là component hoặc property của component. Ví dụ: Thống kê người dùng view tới component này bao nhiêu lần trong tháng vừa rồi? Hay trước khi khởi tạo cập nhật trạng thái user đang có những quyền gì?

Như vậy Decorator là một kỹ thuật có thể giúp chúng ta làm được việc này. Sau đây, thì ta sẽ implement một Logger cho phép ghi log khi một component được mở ra hoặc người dùng rời khỏi.

NgLog Class Decorator
=====================

Sau đây là đoạn mã khai báo decorator giúp chúng ta hook vào lifecycle của một component: `ngOnInit`, `ngOnDestroy`, `ngOnChanges`.

{{< highlight ts "linenos=inline" >}}
import { environment } from "../environments/environment";
export function NgLog() : ClassDecorator {
  return function ( constructor : any ) {
    if( !environment.production ) {
      // You can add/remove events for your needs
      const LIFECYCLE_HOOKS = [
        'ngOnInit',
        'ngOnChanges',
        'ngOnDestroy'
      ];
      const component = constructor.name;

      LIFECYCLE_HOOKS.forEach(hook => {
        const original = constructor.prototype[hook];

        constructor.prototype[hook] = function ( ...args ) {
          console.log(`%c ${component} - ${hook}`, `color: #4CAF50; font-weight: bold`, ...args);
          original && original.apply(this, args);
        }
      });
    }

  }
}
{{< / highlight >}}

Khi sử dụng chỉ cần khai báo decorator `NgLog` trên component mà bạn muốn tracking.

{{< highlight ts "linenos=inline" >}}
@Component({
  selector: 'posts-page',
  template: `
    <posts [posts]="posts$ | async"></posts>
  `
})
@NgLog()
export class PostsPageComponent {
  constructor( private store : Store<any> ) {
    this.posts$ = store.select('posts');
  }
}

    
@Component({
  selector: 'posts',
  template: `
    <p *ngFor="let post of posts">{{post.title}}</p>
  `
})
@NgLog()
export class PostsComponent implements OnInit {
  @Input() posts = [];
}
{{< / highlight >}}

