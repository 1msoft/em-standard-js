# Emsoft-Front-end任务申领与代码提交规范

## 分支提交流程规范

### 任务特性

- `feat`: 卡片为新增功能或优化功能
- `fix`: 卡片本身就是个`bug`
- `docs`: 要新增文档或修改文档
- `style`: 修改代码排版格式，修改目录结构等
- `refactor`: 对原有代码的修改，达到提升性能、或者修复原有代码的问题；任务在第一次提交 commit 后，发现还需要修改/补充，再做一个提交；任务在代码审查后不通过，需要继续提交修改代码
- `perf | performance` 改善性能
- `test`: 新增测试代码
- `build`: `package.json`、`gulp`、`webpack`、`dockerfile` 等等相关构建文件的改动
- `ci`: 持续集成文件的改动，如travis等
- `chore`: 不影响逻辑代码或测试代码的修改的其他提交

### 分支命名规范

> 姓名开头字母/任务特性/任务简略描述<br/>
  例 项目首页布局修复 开发者-王小明

`Wxm/fix/homepage-layout`

### 卡片任务`commit`提交约定

1. 第一次使用`feat`

2. 在卡片还没有为 <font color=#a3a5a5>“已实现”</font> 状态下，若发现由于<font color=#ff1a59>测试/审查不通过</font>，或自测发生问题需要再次`commit`，统一用`refactor`

3. 若卡片为 <font color=#a3a5a5>“已实现”</font> 状态，无法继续使用该卡片进行`commit`，应该另外建卡片或者`bug`

### 缺陷任务`commit`提交约定

1. 第一次使用`fix`

2. 在缺陷任务还没有为 <font color=#a3a5a5>“已实现”</font> 状态下，若发现由于<font color=#ff1a59>测试/审查不通过</font>，或自测发生问题需要再次`commit`，统一用`refactor`

3. 若缺陷任务为 <font color=#a3a5a5>“已实现”</font> 状态，无法继续使用该缺陷进行`commit`，应该另外建`bug`

### `commit message`约定

1. 执行`git cz`

2. 选择任务特性
![选择任务特性](https://ws1.sinaimg.cn/large/005zMGWfly1g1yhnxtms1j30tm053gmb.jpg)

3. 修改范围简单描述
![修改范围简单说明](https://ws1.sinaimg.cn/large/005zMGWfly1g1yhqbrb2qj30n201k0so.jpg)

4. 进入`TAPD`任务卡片详情中，点击右上角 复制标题与链接

![标题与链接](http://ww1.sinaimg.cn/large/c0bd45d4gy1gcvxvlm4qsj207w05fdfu.jpg)

5. 多次回车至`git cz`完成本次`commit`

6. 提交代码`git push`

7. 提交`Pull requests`

> 到`github`对应项目下的`Pull requests`Tab页下创建新的`pull requests`, 标题部分内容取至`TAPD`任务卡片中的任务标题,`Reviewers`人员可选择对应结伴`review`伙伴.

ps: 打开`git push`后的`remote`中的地址,可以快速提交`PR`
![快速提交PR](https://ws1.sinaimg.cn/large/005zMGWfly1g1ynomv783j30s50613zt.jpg)

## jira工作流

### 任务看板

- 未开始

  当前任务栏下的任务可以进行指派，需指派对应人员，任务周期等，被指派人领取任务流转至进行中

- 进行中

  按任务描述(需求)完成任务，任务完成之后将卡片流转至已完成

- 已完成

  开发人员的任务到此完成了，接下去就是测试人员接受
- 已暂停
  若该卡片出现特殊原因无法继续进行，可流转至已暂停的状态下

### 缺陷

  项目开发过程中，存在的一些问题或者由测试人员反馈回来的不足

- 新建缺陷

```text
【菜单名称】任务描述                         发现版本   严重程度    优先级   状态    处理人

例： 【申报申请】【项目申请】申请表单下拉框问题   v1.0.0   一般         中     待解决   王小明
```

- 认领缺陷

  发现缺陷面板中含有待自己负责的任务缺陷，及时认领，标注`状态`，`指派人员`等

- 修复缺陷

  缺陷完成之后，及时更改缺陷状态，按`git工作流程`提交任务

### 相关文档

  项目开发过程中，含有一些与项目相关的文档，可在![svn对应项目](http://dev.1msoft.cn:3690/svn/develop/%e9%a1%b9%e7%9b%ae%e6%96%87%e6%a1%a3)查阅

## 基于 Node.js 构建项目的版本发布流程

### 版本发布需符合的前提条件

1. 版本对应 jira 迭代中的所有需求状态为`已完成` 或 `已关闭`
2. 版本对应 jira 迭代中的所有缺陷状态为`已关闭`
3. 版本对应 github 中的所有 pull request 均已合并
4. 需在项目发布分支上进行推送，请当前确认代码为最新，并且目前在发布分支下

### 版本发布流程

### 完善 /versions/[版本号] 中脚本和升级说明

1. 确认脚本是否齐全
2. 版本升级说明是否齐全

### 版本号规则：

- 版本号分为3位，格式为x.x.x，如1.0.0，若需要在头部增加v标识，则为：v1.0.0
  - 第1位 —— 系统经过大改版时使用或修改，比如从1.x.x => 2.x.x
  - 第2位 —— 系统更新功能等发生迭代后增加1
  - 第3位 —— 新版本发布后，存在需要修改的BUG或完善的地方

### 具体步骤：

1. 在项目根目录下安装【release】与【stanndard-version】

```
npm i --save-dev standard-version
```

```
npm i --save-dev release
```



2. 发布版本

在项目`package.json`中添加 npm script 命令

```
{
 "scripts": {
   "release": "standard-version"
 }
}
```

3. 使用

```
npm run release -- --release-as [版本号]
```

示例

```
npm run release -- --release-as 1.2.1
```

4. 将升级提交和生成的新版本 tag，一同推至 Github

```
git push --follow-tags origin [远端分支] 
```

示例

```
git push --follow-tags origin dev
```

5. GitHub发布

- 在Github仓库内进入【tags】找到发布的对应版本

![](./images/step1.png)



- 进入已推送至远程的tag

![](./images/step2.png)



- 点击【Create release from tag】![](./images/step3.png)



- 填写相关信息后点击【Public release】即完成tag发布



## 所需工具

### Node.js / NPM

#### 作用

项目基础运行环境

### commitizen

[https://github.com/commitizen/cz-cli](https://github.com/commitizen/cz-cli)

#### 作用

`git commit` 格式规范化

#### 安装

1. 全局安装

```shell
npm install -g commitizen
```

2. 在项目根目录进行初始化配置

```shell
commitizen init cz-conventional-changelog-emsoft --save --save-exact
```

#### 使用

`git commit`时，不使用 `git commit`， 改为 `git cz`，根据提示进行

### commitlint

https://github.com/conventional-changelog/commitlint

#### 作用

git commit 格式规范化自动检查

#### 安装

1. 安装 commitlint 和 husky

```shell
npm i --save-dev @commitlint/{config-conventional,cli}
npm i --save-dev husky
```

2. 在项目 package.json 中添加 commit hooks

```json
{
  "husky": {
    "hooks": {
      "commit-msg": "commitlint -E HUSKY_GIT_PARAMS"
    }
  }
}
```

### stanndard-version

[https://github.com/conventional-changelog/standard-version
](https://github.com/conventional-changelog/standard-version
)

#### 作用

版本自动化发布、根据 git commit 记录，自动化生成/更新 changelog 文件

#### 安装

1. 安装 stanndard-version

```shell
npm i --save-dev standard-version
```

2. 在项目`package.json`中添加 npm script 命令

```json
{
  "scripts": {
    "release": "standard-version"
  }
}
```

#### 使用

```bash
npm run release -- --release-as [版本号]
```
