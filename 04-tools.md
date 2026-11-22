# 检索资料与开发工具

> 这一节解决一个问题：**遇到需求时，怎么在十分钟内找到能用的东西**，而不是从零硬写。
> 记录格式固定为：关键词 → 链接 → 解决什么问题 → 为什么选它 → 有没有真用。

## 一、检索方法：关键词怎么来

从需求里抠四个东西，再拼起来：

```
对象 + 动作 + 技术词 + 场景
```

例：要给城市卡片加"距离排序" → `vanilla js sort by distance`、`geolocation 距离排序 前端`

再加修饰词，结果立刻不一样：`awesome`、`boilerplate`、`example`、`vs`、`site:github.com`、`in:readme`。

三个渠道各有各的用法：

| 渠道 | 怎么用 | 看什么 |
|---|---|---|
| GitHub / Gitee | 按 star **和最近更新时间**排 | README、目录结构、Issues 里的坑、license |
| Agent 生态 | MCP 服务器列表、Skill 示例仓库、插件市场 | 解决什么问题、要什么权限、适不适配我的 Agent |
| 官方文档 / 插件市场 | 先看文档再看社区 | 是否解决当下痛点、学习成本 |

## 二、开源项目

| 关键词 | 资源 | 解决什么 | 值得借鉴的点 | 用了吗 |
|---|---|---|---|---|
| `vanilla js practice projects` | [wesbos/JavaScript30](https://github.com/wesbos/JavaScript30) | 30 个纯原生 JS 小练习 | 不引框架怎么组织事件与状态；每个项目一个文件夹，结构很干净 | 跑了第 1 个 |
| `awesome javascript list` | [sindresorhus/awesome](https://github.com/sindresorhus/awesome) | 各类资源的总索引 | 想找某个方向的库，先来这里按分类翻，比乱搜快 | 用过 |
| `leaflet 轻量地图` | [Leaflet/Leaflet](https://github.com/Leaflet/Leaflet) | 在网页里嵌地图 | 如果二期要在地图上标点，它比整套地图 SDK 轻得多 | 未用（备选） |

> 判断一个开源项目值不值得用，我只看三件事：最近一次提交是不是半年前以后、Issues 里有没有人回、license 能不能商用。三条缺一条就换。

**第一个例子跑通了**（鼓机）：九个方块对应九个音效，HTML 用 `data-key` 把按键和音频配对，JS 只做三件事——监听 `keydown`、按 keyCode 找到对应 `<audio>`、加 `.playing` 类让 CSS 闪一下。

就这 20 行，把"**数据挂在 DOM 上**"这个思路讲透了：不用记数组下标，元素自己带着身份。以后做城市卡片，也可以给每张卡挂 `data-id`，点击时直接读出来。

## 三、Agent 扩展

| 关键词 | 资源 | 解决什么 | 适配性 | 用了吗 |
|---|---|---|---|---|
| `MCP servers list` | [modelcontextprotocol/servers](https://github.com/modelcontextprotocol/servers) | 官方维护的 MCP 服务器合集（文件、数据库、Git 等） | 只要 Agent 支持 MCP 就能接；我现在的需求都在本地文件里，暂时用不上 | 未装 |
| `agent skill examples` | [anthropics/skills](https://github.com/anthropics/skills) | 官方 Skill 示例，看别人怎么写 `SKILL.md` | 结构可以直接照抄：元数据 + 指令 + 示例 | 看了结构 |

**为什么暂时不装**：这周的需求——整理笔记、批改答案、写文档——都在本地文件和对话里，没有要连的外部系统。等做项目要连数据库、要调地图接口时再装，那时才知道该装哪个。

## 四、开发工具

| 关键词 | 工具 | 解决什么 | 为什么选它（vs 同类） | 用了吗 |
|---|---|---|---|---|
| `chrome devtools 调试` | [Chrome DevTools](https://developer.chrome.com/docs/devtools) | 看元素、改样式、抓网络、打日志 | 浏览器自带，不用装；比在代码里 `console.log` 快十倍 | 用过 |
| `git gui windows` | [GitHub Desktop](https://desktop.github.com) | 图形化提交、看 diff、切分支 | 比命令行直观，适合看"这次改了哪些行"；但复杂操作还得回命令行 | 未用 |
| `vs code git 面板` | VS Code 内置源代码管理 | 一个按钮 add + commit、点冲突文件直接选保留哪边 | 和编辑器一体，不用切窗口；处理冲突比命令行快 | 用过 |
| `api 测试 工具` | [Thunder Client](https://www.thunderclient.com)（VS Code 插件） | 调接口、看返回 | 比 Postman 轻，装在编辑器里；二期接接口时用 | 未用 |
| `免费部署 静态站` | [GitHub Pages](https://pages.github.com) | 把静态页面挂到公网 | 仓库即站点，不用买服务器；city-list 就是这么上线的 | 用过 |
| `浏览器兼容 查询` | [Can I use](https://caniuse.com) | 查某个 CSS/JS 特性能不能用 | 比凭印象猜靠谱，写兼容代码前先查 | 用过 |

## 五、试用记录：VS Code 的 Git 面板 vs 命令行

两个都用了，感受差别挺明显：

| 对比项 | 命令行 | VS Code 面板 |
|---|---|---|
| 提交 | `git add .` + `git commit -m "..."` 两条 | 填信息点一下，`add` 自动做了 |
| 看改动 | `git diff` 刷屏 | 左边点文件，右边并排高亮 |
| 解决冲突 | 手动改文件删标记 | 文件里直接点"采用当前 / 采用传入 / 两个都留" |
| 切分支 | `git switch xxx` | 左下角点一下选 |
| 出错时 | 报错原文能直接搜 | 错误提示被折叠，不容易看到细节 |

**结论**：日常提交和解决冲突用面板更快；**理解原理、排查问题必须回到命令行**。面板是把命令包了一层，它不会告诉你 `add` 和 `commit` 是两步——这也是为什么先用命令行练，再用插件。

## 六、试用记录：从零到公网可访问

city-list 从本地文件夹到 `https://mianbao721.github.io/city-list/` 可访问，全程没用服务器：

1. 仓库 Settings → Pages → 选分支 → 保存
2. 等 1 分钟，链接生效
3. 推送即更新，不需要重新部署

**踩的坑**：路径必须用相对路径，写成 `/docs/preview.png` 在 Pages 上会 404（因为站点挂在子路径下）；图片放进 `docs/` 才能被一起发布。

## 七、检索复盘

- **搜不到的时候**，八成是关键词太口语化："怎么让网页好看"搜不出东西，"css card hover animation example"才行。
- **中文搜不到就换英文**，前端生态的英文资料密度高一个量级。
- **别只看 star**：一个 2 万星但两年没提交的项目，坑可能比 200 星的新项目多。
- 找到东西之后，**先跑最小例子**再往项目里搬，不然调试成本翻倍。
