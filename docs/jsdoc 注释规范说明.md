### TS-CEHCK

#### 推荐使用`vscode`编辑器，其他编辑器需要而外插件

#### 使用

```
// @ts-check
let a = 1; // a被定为为number类型
a = {}; // a的类型被改变，当行将报错
```

#### 不足

- 只能作为提示工具使用
- 一些不合理检验
```
// 例
let text = '我是测试值';
isNaN(text) // 报错

// 修改
/**
 * 是否为NaN
 * @param {*} val 传入参数
 * @returns {Boolean}
 */
function hasNaN(val) { return isNaN(val) }
```

### JSDoc

#### 安装
```
npm install -g jsdoc
npm install --save-dev jsdoc
```

#### 插件

##### `vscode`插件
- `Add jsdoc comments`
- `Preview JSDOC` // 快速预览

#### 使用

- 命名
```
MyConstructor                 // 定义
MyConstructor#instanceMember  // 实例成员
MyConstructor.staticMember    // 静态成员
MyConstructor~innerMember     // 内部成员
```

- 定义

```
/**
 * Person
 * @constructor
 */
let Person = function () {
  /**
   * 实例成员-说 Person#say
   * @param {String} msg 消息
   */
  this.say = function (msg) {
    console.log(msg, '实例say');
    const innerMsg = say('我是内部方法调用产生的消息');
    console.log(innerMsg, '内部say');
  }

  /**
   * 实例成员-说 Person~say
   * @param {String} msg 消息
   */
  function say(msg) {
    console.log(msg, '内部say');
  }
}

/**
 * 实例成员-说 Person.say
 * @param {String} msg 消息
 */
Person.say = function (msg) {
  console.log(msg, '静态say');
}

var p = new Person();
p.say('我是实例');      // 我是实例 实例
Person.say('我是静态'); // 我是静态 静态
```

```
// 通用常量

/**
 * 计数器
 * @constant
 * @type {Number}
 * @default
 */
let count = 0;

// 通用函数

/**
 * 单号生成器
 * @function
 * @param {String} prefix 前缀
 * @returns {String}
 */
export const genBizCode = prefix => {
  const bizCode = `${prefix}${new Date().getTime()}`;
  return bizCode;
};

// 类

/**
 * 房屋选择器
 * @extends Component
 */
class HouseSelection extends Component {
  /**
   * 需要的props
   * @param {Object} props 参数
   * @param {Object} props.hideFields 获取所选择的房屋
   * @param {string} props.community 小区
   * @param {string} [props.building] 楼栋
   * @param {string[]=} props.selecedHouses 获取所选择的房屋
   * @param {string[]} [props.checkedHouses = ['checkid_1', 'check_2']] 默认已经选择的房屋
   * @callback callback
   */
  constructor(props) {
    super(props);
    this.state = {};
  }

  render() {
    return (
      <div></div>
    );
  }

  /**
   * 对每次加载的房屋信息进行处理
   * @function
   * @param {Object[]} res 数据
   * @returns {Object[]} 返回数据
   */
  HandleHousesOriginData = (res) => {
    return res;
  }
}
```

// 通用模块

```
// helper.js

// @ts-check
/**
 * 工具模块
 * @module Helper
 */

/**
 * 金额格式化
 * @param {Number|String} amount 金额
 * @returns {String} 格式化后的金额
 */
export function fmoney(amount) {
  ...code
  return '';
}

/**
 * 银行卡数字格式化 - 四个数字补一个空格
 * @param {String} val='' 输入值
 * @returns {String} 主账户号
 */
export function bankCardNo(val = '') {
  const mainAcctNo = val.replace(/(\d{4})/g, '$1 ');
  return mainAcctNo;
}
```

#### 本地生成文档

```
jsdoc <dir> -c /path/conf.json -r
-d <dir> --package <dir> --readme <dir>
<dir> 指定需要生成文档的目录
-r 递归目录
-d 指定生成文档的目录的文件
-c 指定配置文件
--package/-P 合并package.json 的name和version
--readme/-R 识别第一个README.md
```

### 其他
- 编辑器vscode
- editorconfig

### 问题
- `.js`文件的装饰支持有问题
```
// 错误提示
Stage 2 decorators may only be used with a class or a class method
```
