# YApi 使用流程规范



> 编写时间： 2020年12月29号
>
> 编写人： 张周伟
>
> 文档版本： 第一版
>

本文主要定义了 YApi 使用过程的标准。

参考文档：

- [RESTful API 设计指南](http://www.ruanyifeng.com/blog/2014/05/restful_api.html)
- [API 接口定义规范【EMSoft】](https://github.com/1msoft/em-standard-js/blob/master/docs/API%E6%8E%A5%E5%8F%A3%E5%AE%9A%E4%B9%89%E8%A7%84%E8%8C%83.md)



## 项目分组创建

- 项目分组应以 **<u>大类业务名称</u>** 创建
- 一些基础服务（例如**权限服务**、**文件服务**等通用服务）应单独被分至一个分组中



## 项目成员的加入方式

由于每个项目的成员是 <u>分组下的成员</u> 与 <u>项目下的成员</u> 之并集，为了便利及安全

- 在业务分组中，仅在项目中添加成员并为其分配相应权限
- 在基础服务分组中，在分组中添加成员并为其分配相应权限



## 接口分类规范

- 每个项目都应含有名称为「待审核」的接口分类

- 接口分类应以 **接口的类型** 命名，并标注该类接口之地址

  ```
  聊天服务 api/v1/chat
  视频课程资讯 api/v1/video-info
  ```



## 接口添加

- 每个新接口应添加在「待审核」分类下

- 接口名称应含有该接口的作用（如新增、删除、查询、修改等），若多个接口名称可能造成混乱，应标注场景。

  ```
  新增用户
  删除用户
  用户登录（场景：WEB端登入）
  获取用户列表
  ```

- 接口路径应参照 [RESTful API 设计指南 ](http://www.ruanyifeng.com/blog/2014/05/restful_api.html)与 [API 接口定义规范【EMSoft】](https://github.com/1msoft/em-standard-js/blob/master/docs/API%E6%8E%A5%E5%8F%A3%E5%AE%9A%E4%B9%89%E8%A7%84%E8%8C%83.md) 中相关内容设计

**添加完成后，应至相应接口的「编辑」界面进行接口的进一步编辑。**

- 状态应置为「未完成」

- 根据实际需求写「请求参数设置」

  - 必须正确区分「必填」「非必填」项

  - 尽量给出每一项参数的示例以及备注

    - | Headers：     |        |          |      |       |
      | ------------- | ------ | -------- | ---- | ----- |
      | 参数名称      | 参数值 | 是否必须 | 示例 | 备注  |
      | Authorization | 123456 | 是       |      | token |

    - | Query：   |          |      |          |
      | --------- | -------- | ---- | -------- |
      | 参数名称  | 是否必须 | 示例 | 备注     |
      | pageSize  | 否       | 10   | 页面大小 |
      | pageIndex | 否       | 1    | 页面索引 |

    - | Body:  |        |          |        |                         |                          |
      | :----- | ------ | -------- | ------ | ----------------------- | ------------------------ |
      | 名称   | 类型   | 是否必须 | 默认值 | 备注                    | 其他信息                 |
      | icon   | string | 非必须   |        | 图标的文件服务 URL 连结 |                          |
      | status | string | 非必须   | 0      | 0为未发布，1为已发布    | 值域信息可以参见相关文档 |

- 根据需求及 [API 接口定义规范【EMSoft】](https://github.com/1msoft/em-standard-js/blob/master/docs/API%E6%8E%A5%E5%8F%A3%E5%AE%9A%E4%B9%89%E8%A7%84%E8%8C%83.md) 写「返回数据设置」

  > **参数定义：** 以下字段必传
  >
  > - code: 接口操作响应码【也可以使用respCode或者status字段】
  > - message：结果信息
  > - data：业务数据，object 或者 array
  > - errors：错误信息



## 接口审核流程

1. 添加接口到「待审核」分类
2. 经过 <u>接口定义评审</u> 后将接口移至相应分类中
3. 接口开发完成后通知相关人员进行审核
4. 审核通过后将接口的状态更改为「已完成」



## YApi 之 Mock 使用

有时接口开发速度未跟上前端进度时，前端可使用 Mock 功能返回之假数据帮助开发。

**步骤如下**

1.  进入对应接口页面
2.  进入「高级Mock」Tab
3.  点击「添加期望」后会跳出相应弹窗
4.  在**基本信息**中填写 <u>期望名称</u> 后，根据需要填写 <u>IP过滤</u> 和 <u>参数过滤</u>
   - <u>IP过滤</u> 的作用是 仅响应所填写的IP地址发送的请求报文
   - <u>参数过滤</u> 的作用是 请求报文中必须含有该参数才返回响应报文
5.  填写**响应信息**
   - 需注意正确设置 Body 中 data 的数据结构

































