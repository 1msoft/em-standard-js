# API接口定义规范

> 编写时间：2020年02月06号
>
> 编写人：黄志炜
>
> 文档版本：第一版【草稿】

基本接口共识来源于`RESTful`接口规范，在这个接口规范的基础上，我们做了一些细节补充的内部约定。

**参考文档：**

- [RESTful API 设计指南](http://www.ruanyifeng.com/blog/2014/05/restful_api.html)
- [理解RESTful架构](http://www.ruanyifeng.com/blog/2011/09/restful.html)

## URL规则约定

- url 中只能包含英文，允许使用英文简称【增加可读性】。不要使用汉语拼音
- 所有字母都使用小写字母
- 多个单词间使用 `-` （hyphen：连字符）分割。例如：`user-dtl`，不要使用`userDetail`或者`user_detail`

- url 的 path 部分，使用`系统/模块/操作`的格式，例如`app/account/login`
  - 系统，表示这个接口是给谁用的，比如：app、web、h5、we-app等。命名可以使用简称
  - 模块，表示系统的子模块，比如：account【账户】、project【项目】等。模块的名字使用全称，单数形式。
  - 操作，表示这个模块的具体的接口，比如创建用户，用户列表等接口。部分常用操作，可以使用习惯词语，比如`login`【登录】、`logout`【登出】

## JSON数据通讯约定

> 如果有机密功能，可以将正常的JSON加密后，使用Base64编码

### 字段命名

- 请采用小骆驼拼写法【lowerCamelCase】


### 数据类型

>  由于JSON对象来自于JavaScript语言，所以字段命名遵循JavaScript语言。前后端交互时，需要考虑JS语言的数值精确度。

| 数据库类型      | 映射JSON类型 | 说明                                               |
| --------------- | ------------ | -------------------------------------------------- |
| boolean         | number       | 值域：1【真】，0【false】；                        |
| boolean【备选】 | string       | 值域：Y【真】，N【假】                             |
| int             | number       |                                                    |
| long            | string       | 由于JSnumber的数值精度可能无法满足，所以使用string |
| 日期、时间      | string       |                                                    |
| 特殊的ID字段等  | string       |                                                    |

其它：

- 制定接口查询条件时，需要确定参数是否必须传输。例如在查询条件中，某查询条件为空，可以允许不传该字段，减少网络开销。


- 以及在响应前端数据时，部分参数不存在或为空时，该字段是否需要响应。通常遵循的原则是尽量全部响应，保证接口的通用性，数据定制部分交由前端来控制。


## 响应体约定

**参数定义：** 以下字段必传

- code: 接口操作响应码【也可以使用respCode或者status字段】
- message：结果信息
- data：业务数据，object 或者 array
- errors：错误信息

```JSON

{
    "code": 0,
    "message":"OK!",
    "data": object | array, 
    "errors": string | object,
}

```

### code

通常code默认使用两种值：

- 【0】：表示接口操作成功！message显示OK即可。
- 【-1】：表示接口操作失败！message部分可以显示具体的错误原因，例如密码错误。

特殊情况下，可以自行添加负数消息码；

正数的消息码，可以为一些枚举值；

### message

通常我们不维护code的信息对照表。直接在messge中响应消息码信息。

### data

业务数据，结构可以为对象和数组结构。

### errors

存放错误详情，无错误时为空。



## 通用约定

> 接口版本

1. 可以将接口版本放置在 URL 中
2. 将接口版本号放在 HTTP 头部中

> 





