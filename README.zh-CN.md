[🇰🇷 한국어](README.ko.md) · [🇺🇸 English](README.md) · [🇨🇳 中文](README.zh-CN.md)

# Lucian UX/UI Prompt

![Lucian UX/UI Prompt: 480 interactive UI elements](.github/cover.png)

480 个可交互的 UI 元素，先在线试用，再以 AI 提示词或可直接运行的代码带进你的项目：80 个 Essentials（Google 与社交账号登录、Cookie 横幅、定价、FAQ、结账，以及提示词输入框、@提及选择器、Agent 步骤等 AI 模式），200 个网站版块与动效，200 个界面组件，从按钮、图表到工作流界面。每个元素都支持浅色/深色主题、鼠标、触摸和键盘操作，并支持减弱动效。零依赖。

**在线画廊（中文）：[uxui.xizanghuapi.cn](https://uxui.xizanghuapi.cn/)** · 原站：[lucianlabs.dev/uxui-prompt](https://lucianlabs.dev/uxui-prompt/)

> 中文版说明：本仓库另有中文版画廊，语言可切换韩文 / 英文 / 中文。中文通过每个元素文件头的 `<!-- @zh {...} -->`（格式与 `@en` 相同）提供。

## 包含什么

全部 480 个元素都在一个库里，分成 27 个分类。编号能看出元素的来源：

| 编号 | 是什么 | 举例 |
| --- | --- | --- |
| 401–480 | **Essentials**（新增）：聚焦、可直接用于生产环境的组件 | Google 登录 · 社交账号登录（Kakao、Naver、Apple、Google）· 邮箱登录 · 注册 · Cookie 横幅与偏好设置 · 条款同意 · 页眉 · 页脚 · 主视觉 · 定价 · FAQ · 轻提示 · 确认弹窗 · 日期选择器 · 文件上传 · 商品卡片 · 迷你购物车 · 韩国支付方式 · 优惠券 · 提示词输入框 · @提及选择器 · 思考中文字 · Agent 步骤 · 工具授权 · 滑动确认 · 签名板 · 表情选择器 · 颜色选择器 · PIN 键盘 |
| 201–400 | 网站版块与动效 | 文字动效 · 主视觉与背景 · 导航 · 滚动动效 · 版块与内容 · 口碑证明 · 电商与定价 · 表单与输入 · 应用界面 · 搭建工具 · 光标与悬停 · 促销与奖励 · 数据动效 |
| 001–200 | 界面组件与工作界面 | 按钮 · 开关与选择器 · 输入与搜索 · 菜单与标签页 · 卡片与内容 · 登录与注册 · 提醒与反馈 · 加载与进度 · 空状态与报错 · 组件与图表 · 布局、日程与设计工具 · 文档与数据编辑 · 数据分析 · 流程与系统 |

在画廊里，**全部**先展示 80 个 Essentials，接着是网站最常用的元素（Cookie 同意、页眉、主视觉、行动号召、FAQ、定价、用户评价、页脚），然后是表单与电商组件、应用界面、促销、图表、展示特效和专业工具。顺序在 [`src/popular.json`](src/popular.json) 里。用分类药丸筛选，或点侧边栏的**已收藏**查看收藏的元素，也可以用底部的搜索栏，用英文或韩文搜索。

## 怎么用

1. 打开画廊，试用某个元素。每个元素滚动到屏幕里时都会播放一段简短演示，你随时可以接手操作。点卡片上的展开图标，或点 **滑动浏览**，可以全屏逐个翻看元素。
2. 点卡片下方的 **Claude** 或 **Codex**，按钮会变成**已复制**：复制到的提示词包含该元素的完整可运行代码和接入说明。
3. 粘贴到你的 AI 编程工具（Claude Code、Codex、Cursor 等）里，填上 `[Insertion point]`（如果要替换已有元素，再填 `[Replacement target]`），发送即可。

Agent 会先确认你的框架、样式和主题配置，再把元素移植成组件，把 `--ux-*` 颜色 Token 对应到你的主题变量上，并汇报它改了什么、哪些没能检查。

如果你想自己移植，卡片上的 **复制代码** 会给你原始的 HTML、CSS 和 JS。先点卡片名字可以查看提示词和代码，或点 **下载代码文件** 保存为带主题切换的独立 HTML 文件。

卡片上的书签会把元素存到侧边栏的 **已收藏** 里（只保存在你的浏览器中，不用账号）。卡片上的太阳/月亮按钮只切换这一张卡片的浅色/深色。

要链接到某个具体元素，在网址后加上它的编号：`https://lucianlabs.dev/uxui-prompt/#001`。

## 让 AI 编程 Agent 直接用

安装 [lucian-uxui skill](https://github.com/Seokwoooo/lucian-uxui)，你的 Agent 就能自己搜索这个库、把元素移植过去：

```sh
npx skills add Seokwoooo/lucian-uxui
```

然后这样问就行："Build a landing page for my coffee subscription. Use the lucian-uxui skill and prefer its elements."（“帮我做一个咖啡订阅的落地页，用 lucian-uxui skill，优先用它的元素。”）Skill 读取 [`api/v1/`](api/v1) 里的静态数据，这些数据由 `src/elements` 生成，也发布在 `https://lucianlabs.dev/uxui-prompt/api/v1/`。

## 本地运行

只需要 Node.js，不用安装任何依赖包。

```sh
git clone https://github.com/BuDingSM/lucian-uxui-prompt.git
cd lucian-uxui-prompt
node src/build.mjs
open prompt-uxui-lab/index.html
```

构建会检查每个元素，并把整个画廊写成一个自包含的 HTML 文件。

## 元素格式

每个元素是一个文件，`src/elements/NNN-slug.html`。编号 `001`–`200` 是界面组件，`201`–`400` 是网站版块与动效，`401`–`480` 是 Essentials。

```html
<!-- @meta {"title":"…","category":"버튼","summary":"…","hint":"…","shape":"square","tags":["button"]} -->
<!-- @demo [["wait",400],["tap",".u001-btn"],["wait",1200]] -->
<!-- @en {"title":"…","summary":"…","hint":"…","map":[["계속하기","Continue"]]} -->
<!-- @zh {"title":"…","summary":"…","hint":"…","map":[["계속하기","继续"]]} -->
<style>.u001{…} .u001-btn{…}</style>
<div class="ux u001">…</div>
<script>(() => { const root = document.currentScript.previousElementSibling; … })();</script>
```

- `@meta`：标题、分类、简介和提示。韩文是源语言，`category` 必须是 [`src/build.mjs`](src/build.mjs) 里列出的分类之一。可选字段：`shape`（`square` 或 `tall` 两种卡片形状）、`hue` 和 `hue2`（卡片光晕颜色，默认用分类的颜色）、`fluid`（元素宽度跟随容器）。
- `@demo`：自动播放演示的步骤：`wait`、`tap`、`hold`、`hover`、`leave`、`glide`、`drag`、`key`、`type`、`erase`、`set`、`scroll`、`reset` 和 `js`。演示里需要区分语言的文字用 `{"ko":"…","en":"…","zh":"…"}` 写。
- `@en`：英文标题和简介，以及把元素代码本地化的字符串对照表。
- `@zh`：中文标题和简介，以及把元素代码本地化的字符串对照表，格式与 `@en` 相同，对照表 key 是韩文原文。
- 每个 CSS 选择器都以 `.uNNN` 为前缀，`@property` 名称以 `--uNNN-` 开头，脚本通过 `document.currentScript` 找到自己的根节点，所以元素之间不会互相干扰。
- 颜色只用 [`src/tokens.css`](src/tokens.css) 里的 `--ux-*` Token，浅色和深色各有一套值。
- [`src/order.json`](src/order.json) 规定每个合集内的展示顺序，完成度高的元素排在前面。某个合集列在里面时，其中的每个元素都必须恰好出现一次。

`node src/build.mjs` 会拒绝任何违反上述规则的文件。

## 许可证

[MIT](LICENSE) © 2026 Seokwoooo。个人项目和商业项目都可以使用。从画廊复制的代码开头有一行注释，注明来源和许可证，请保留它。
