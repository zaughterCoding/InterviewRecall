<p align="center">
  <img src=".github/logo.svg" alt="interview-recall" width="560">
</p>

<p align="center"><b>Java 后端八股二轮复习 · 基于 JavaGuide · 按你的简历和项目出题</b></p>

<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-MIT-blue" alt="MIT"></a>
  <img src="https://img.shields.io/badge/Agent%20Skills-compatible-orange" alt="Agent Skills">
  <img src="https://img.shields.io/badge/Claude%20Code%20%7C%20Codex%20%7C%20ChatGPT-supported-2563EB" alt="platforms">
</p>

# interview-recall：Java 后端八股二轮复习

一轮看完八股，合上书还是说不出来？这个 skill 让 AI 当你的辅导老师兼模拟面试官，用 **JavaGuide** 带你走一遍"主动回忆"式的二轮复习：**你查资料、合上资料口述，AI 原样记下你的原话，指出错在哪，再顺着你的思路整理成一份能讲出口的答案。**

适用于 Claude Code、Codex CLI、ChatGPT 桌面版；网页版 ChatGPT 也能用，但功能受限。

## 🆚 它和"让 AI 出几道八股题"有什么不同

| | 普通的 AI 出题 | interview-recall |
|---|---|---|
| 题从哪来 | 随机，或者按热门题 | 一份基于 JavaGuide 的**标准题库**（核心 12 个模块 120 题，另有 8 个可选模块 33 题），保证覆盖完整 |
| 先学什么 | 自己决定 | 先**审查你的简历和项目代码**，项目链路上的题排在最前面 |
| 题目长什么样 | 通用题干 | 结合你项目里真实的类、方法、脚本、行号出题，带"拷打"：拿资料和你的代码对质、推演故障、问取舍、追问简历里的数字 |
| 答完之后 | 给一份标准答案 | **保留原话 → 纠错表 → 顺着你思路的口述版（30 秒版 + 展开版）→ 按档位追问** |
| 之后 | 结束 | 第 1、3、7 天闭卷复述，答不顺就降档重来，直到全部达标 |

同一道题库题，不同人考的场景不同：同样是"分布式事务"，项目里用 Outbox 的人考本地消息表和双写一致，用 Seata 的人考 AT 模式和全局锁。

## 🔄 工作流程

```
配置 ─→ 审查简历和项目 ─→ 生成题目大纲 ─→ 出题 ─→ 你查资料、口述 ─→ 纠错 ─→ 口述版 ─→ 追问 ─→ 间隔复习
         （项目画像）       （按画像分优先级）  ↑                                              │
                                              └──── 暴露出前置知识缺口时，开补漏题先补 ←──────┘
```

1. **配置**：一轮问完 JavaGuide 路径、简历、追问深度等。追问深度有三档，会先讲清每一档的好处和代价，推荐「面试高频」。
2. **审查简历和项目**：项目经历的每一条 bullet 都要在代码里找到依据，写成 `01-项目画像.md`。简历写了但代码里没有的，会让你决定是改简历，还是自己补上实现。技能栏只当参考，因为很多人的技能栏写得又杂又泛。
3. **生成大纲**：从标准题库复制，题号和内容不改，只按画像分优先级。P0 只给项目链路上的题。
4. **一道题**：出题 → 你查资料、合上资料口述 → 原话存档 → 纠错 → 口述版 → 追问 → 更新掌握度。
5. **间隔复习**：到期的题闭卷复述，答不顺就降档重来。

想看实际效果，可以看 [assets/examples/example-question.md](assets/examples/example-question.md)，这是作者一道题的完整记录。

## 🧰 准备

1. **clone JavaGuide**。这个 skill 不附带 JavaGuide 的内容，需要你自己 clone 一份：

   ```bash
   git clone https://github.com/Snailclimb/JavaGuide.git
   ```

2. **准备简历**：Markdown、PDF、纯文本都行。
3. **准备项目代码**（强烈建议）：有代码，AI 才能审查出真实做法和问题，出的题才贴近你的项目。只有描述也能用，但项目相关的结论会标"未对照实现"。
4. **准备一个放笔记的目录**。

## 📦 安装

仓库根目录就是 skill 本身，直接 clone 到对应的 skills 目录即可。下面以个人全局安装为例；想只在某个笔记目录里用，就 clone 到那个目录下对应的位置。

### Claude Code

```bash
git clone https://github.com/zaughterCoding/InterviewRecall.git ~/.claude/skills/interview-recall
```

也可以把整个文件夹复制到下面任一位置：

- 个人全局：`~/.claude/skills/interview-recall/`
- 单个项目：`<你的笔记目录>/.claude/skills/interview-recall/`

在笔记目录里打开 Claude Code，输入 `/interview-recall` 开始。

### Codex CLI / ChatGPT 桌面版

```bash
git clone https://github.com/zaughterCoding/InterviewRecall.git ~/.agents/skills/interview-recall
```

也可以把整个文件夹复制到下面任一位置：

- 个人全局：`~/.agents/skills/interview-recall/`
- 单个项目：`<你的笔记目录>/.agents/skills/interview-recall/`

Codex CLI 里输入 `$interview-recall` 调用。ChatGPT 桌面版里，先建一个本地项目，把笔记目录设为主文件夹，再在对话框里输入 `@` 选择这个 skill。`agents/openai.yaml` 提供了在 ChatGPT 桌面版里显示的名称和默认提示词。

### ChatGPT 网页版（功能受限）

网页版不能直接安装独立的 skill，也读不到你电脑上的文件，可以用 **Project** 代替：

1. 新建一个 Project，把 `chatgpt/instructions.md` 的全文粘贴到 Project 的指令里。
2. 把这 9 个文件上传到 Project 的文件里：`SKILL.md`、`references/` 下的 3 个文件、`assets/` 下的 3 个模板、`assets/examples/` 下的 2 份示范。
3. 简历直接上传。项目代码需要你把关键文件贴给它；JavaGuide 由你自己按它给的路径打开阅读。
4. 网页版不能写文件，每道题结束后它会输出完整的笔记和大纲改动，由你粘贴保存。以后每开一个新对话，先上传你的 `学习配置.md` 和 `00-题目大纲.md`。

> 注：OpenAI 正在下线自定义 GPT（个人账号已经不能新建），所以这里用的是 Project，不是自定义 GPT。

## 🚀 开始使用

第一条消息这样写就行：

```
/interview-recall 开始复习。我的简历在 ./简历.md，项目代码在 ./my-project，JavaGuide 在 ./JavaGuide，笔记放 ./笔记。
```

在 Codex 里把 `/interview-recall` 换成 `$interview-recall`，在 ChatGPT 桌面版里换成 `@` 选择。

AI 会依次：确认配置 → 审查简历和项目，给你看项目画像 → 生成大纲 → 出第一道题。出完题它会停下来，等你查完资料、合上资料，再用自己的话讲。打字或者贴语音转文字都可以。

## 📝 生成的笔记

```
笔记/
├── 学习配置.md          # JavaGuide 路径、范围、追问深度等
├── 01-项目画像.md        # 简历和项目的审查结果，每条都定位到代码
├── 00-题目大纲.md        # 全部题目、优先级、进度、待复习
├── Redis.md             # 每个模块一个文件，存每道题的原话、纠错、口述版、追问
└── ...
```

## 🗂️ 文件说明

```
interview-recall/
├── SKILL.md                    # 主流程
├── LICENSE
├── .github/logo.svg            # README 用的 logo
├── agents/openai.yaml          # ChatGPT 桌面版的显示信息
├── references/
│   ├── syllabus.md             # 标准题库：基于 JavaGuide，核心模块 + 可选模块
│   ├── project-review.md       # 项目审查：方法、信号清单、项目画像格式
│   └── config.md               # 首次配置：问什么、追问三档的后果
├── assets/
│   ├── outline-template.md     # 题目大纲模板
│   ├── question-template.md    # 单题笔记模板
│   ├── readme-template.md      # 笔记目录说明页模板
│   └── examples/               # 作者的真实笔记，作为 few-shot 示范
│       ├── example-outline.md
│       └── example-question.md
└── chatgpt/instructions.md     # ChatGPT 网页版 Project 用的指令
```

## ❓ 常见问题

**为什么固定用 JavaGuide，不能换别的资料？**
固定资料，所有人的题目路径才能对齐，题库里每一题的出处也都核对过确实存在、有正文。JavaGuide 里只有付费简介、没有正文的页面，题库已经避开了；JavaGuide 没讲的知识点，会作为你的个人项目题追加，资料查官方文档。

**只想学一部分模块可以吗？**
可以。核心模块默认全学，可以删；可选模块（分布式组件、高可用、系统设计等）默认不学，可以加。简历上写了、但不在范围内的技术，AI 会提醒你。

**追问太细、太慢怎么办？**
把追问深度设为「面试高频」，每题只追 1～2 个面试真会问的问题。也可以只对某个模块调深。

**简历上写了，但代码里其实没做，会怎样？**
审查时会被指出来，让你决定是改简历，还是自己补上实现。选了补实现的，相关题目会先只考通用知识，等你写完代码再考项目部分。

## 💡 给新用户的建议

- **追问深度先选「面试高频」**：先把范围覆盖完，再对重点模块加深，比一开始就深挖更划算。
- **口述时别怕说错**：原话越真实，纠错越有用。不确定就直接说"不确定"。
- **一定要合上资料再讲**：边看边讲等于没练。

## 📄 许可证

[MIT](LICENSE)。

## 🙏 致谢

- 资料来自 [JavaGuide](https://github.com/Snailclimb/JavaGuide)（Apache 2.0），作者 Guide 及其贡献者。本 skill 只引用文件路径，不附带 JavaGuide 的内容。
- skill 格式遵循 [Agent Skills](https://agentskills.io/specification) 开放规范。
