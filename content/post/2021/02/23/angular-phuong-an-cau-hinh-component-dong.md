---
title: Angular - Phương án cấu hình động thành phần component
date: 2021-02-23T08:03:52+07:00
draft: false
share: true

# View.
#   1 = List
#   2 = Compact
#   3 = Card
view: 2
tags:
- Angular
- Dynamic
- Component
categories:
- Angular
---

# 1. Nguyên cớ

Với sức mạnh của TypeScript và sự hoàn thiện của JavaScript nó đã cho phép chúng ta làm được nhiều thứ. Kể đến hệ thống Decorators mới nhất của TypeScript, đây là một tính năng hữu ích cho phép chúng ta khai báo, chỉnh sửa các thành phần của class, method, constructors, properties, hay parameters. 

Một phương diện ngày nay nếu giao diện web hay giao diện một chức năng người dùng có thể chỉnh sửa và cấu hình động theo cấu hình hoặc cài đặt riêng của cá nhân thì quả là những tiện ích tuyệt với; nâng cao trải nghiệm riêng của người dùng và khách hàng của các bạn.

## Mong muốn và nhu cầu

Khi ứng dụng một công nghệ như Angular, chắc hẳn chúng ta cũng có nhưng nhu cầu này, tức là cấu hình động các thành phần giao diện, không những thay đổi về sự nhìn, mà còn thay đổi về hành vi của chức năng component đó.

## Sự đáp ứng của công nghệ (Angular)

Đã rất lâu từ sau khi sự ra đời của Angular, quả thật từ 2016 cho đến nay thì Angular đã bước sang tuổi thứ 6. Do vậy đã có hàng loạt giải pháp đưa ra để đáp ứng nhu cầu trên, cho đến thời điểm hiện tại thì tôi thấy có 2 phương án khả thi nhất:

1. [Dynamically load template for a component #15275](https://github.com/angular/angular/issues/15275)
3. [Dynamic Components by selector with Ivy](https://indepth.dev/posts/1400/components-by-selector-name-angular)
2. [Provide a service to find component by name #33715](https://github.com/angular/angular/issues/33715)

## Dynamically load template for a component

Đây là phương án đưa trình biên dịch lên browser. Tuy đáp ứng được yêu cầu, xong một số tình huống không thể nạp được component mà không rõ nguyên nhân do phiên bản trình duyệt hay do chính cách xử lý của Compiler.

Ref:
* https://stackoverflow.com/q/46576727/1896897
* https://github.com/angular/angular/issues/15275

Demo:
* https://www.linkedin.com/pulse/compiling-angular-templates-runtime-dima-slivin/
* https://github.com/CharlesElGriego/angular-aot-dynamic-components

Trong khi các công nghệ khác support việc render component một cách native và đơn giản thì tôi cho rằng phương án này khá cồng kềnh và không phù hợp trong môi trường Production với số lượng lớn components.

## Provide a service to find component by name

Phương án này sử dụng kỹ thuật khai báo Decorator, tức là đánh dấu component nào là Dynamic/Động để cho phép nạp thành phần trong Runtime. Kỹ thuật này được khai báo và sử dụng như sau:

```ts
// type-manager.decorator.ts
const TYPE_MAP = new Map<string, any>(); // any should reactor to IDynamicComponent

export function TypeManagerDecorator(aType: string) {
    return function _TypeManagerDecorator<T extends { new(...args: any[]): TypeManager}>(constr: T) {
        TYPE_MAP.set(aType, constr);
    };
}

export function getComponent(aType: string) {
  return TYPE_MAP.get(aType);
}

// main.component.ts
// ...
getComponent(aType);
```

## Dynamic Components by selector with Ivy

To be update

## Đánh giá và kết luận

To be update
