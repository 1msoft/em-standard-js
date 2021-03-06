# Code Review Check List

```text
本文档为 Code Review 时的检查清单，仅作为参考；
目前仅有九大点，将逐渐丰富细节内容。
```

## 一、 通用约定

1. API 设计尽量符合 RESTful API 设计规范
2. git commit 符合 commitizen 中的规范

## 二、 CSS 约定

1. css 类名多单词情况，以 “-” 分割

## 三、 React 约定

1. react 组件头部必须有约定注释（详见 jsdoc 规范），标明正确的组件名称等
2. 组件设计合理性

## 四、 命名约定

1. 常量命名：全大写，多单词以 “_” 分隔
2. 函数名称命名：动宾结构，如 “判断有效性 checkValid”， “创建子账户 createSubAcct” 等
3. 布尔类型的变量命名：以 is、use、enable 等开头，如 isValid, usePrefix，enablePOS 等
4. 内部变量命名：若需区分内部变量与外部变量，可以 “_” 开头，但该方式命名但变量，仅限于内部调用使用

## 五、 函数编写约定

1. 方法头部必须有约定注释（详见 jsdoc 规范）
2. 方法内部，必须有业务逻辑注释（以 “//” 表示）

## 六、 性能问题

## 七、 异常处理、次要分支条件

## 八、 对别的模块的影响

## 九、 语法规范、注释
