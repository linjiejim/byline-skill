# byline-skill

[English](README.md) · **中文**

**把"先采访、再代笔"做成一个 agent skill。** 给它一个主题，它先做功课，用几个有针对性的问题采访你，再根据你确认过的回答，以你自己的口吻写出一篇成稿。文章里的每一个观点，都是你真正持有、并确认过的。

它能在 [Claude Code](https://claude.com/claude-code) 或任何能加载 skill 的 agent 里运行。它把常见的 AI 写作流程反了过来：不是 *AI 先写、你来改*，而是 **AI 提问、你回答、AI 代笔**。写作最难的从来不是遣词造句，而是想清楚；有结构的提问替你完成这部分工作。

## 唯一一条铁律

> **对话不等于确认。** 哪怕你在这次会话里已经把想法聊透了，byline-skill 仍然会采访你。聊天是有价值的输入，但任何判断在你通过问答确认之前都不会进文章。这是守住"署名诚实"的那道闸，也是整件事的意义所在。

## 快速上手

```bash
git clone <你的仓库地址> byline-skill
# 作为 skill 安装，例如软链到 agent 的 skills 目录：
ln -s "$PWD/byline-skill" ~/.claude/skills/byline-skill
```

然后用任一方式建立你的档案：

- **拷模板填写**：
  ```bash
  cd byline-skill && cp examples/*.md profile/
  # 编辑 profile/author.md、profile/voice.md、profile/work.md
  ```
- **或者直接跑**，让 skill 在第一次运行时采访你，自动生成 `profile/author.md` 和 `profile/work.md`。把 `work.md` 指向你已有写作的位置（一个文件夹或一个网址），这样声音就有了真实来源。

调用方式：直接对 agent 说"采访我，写一篇关于 X 的文章"，或在 Claude Code 里用 `/byline-skill`。

## 你需要维护的文件

`profile/` 下的一切都是你的，且已被 gitignore，所以你 fork 出去也不会泄露个人信息：

| 文件 | 内容 |
|------|------|
| `profile/author.md` | 你是谁：只放身份和背景。 |
| `profile/voice.md` | 你的语言、标点、结构和 house format。 |
| `profile/work.md` | 你过去的写作在哪，外加每篇一行的索引。 |
| `profile/publish.md` | *可选。* 成稿要写到哪。不写这个文件就止步于 `drafts/`。 |

声音和立场每次都从你的**真实旧文**重新提取（索引在 `work.md`），而不是依赖一段静态描述，所以永远不会过时。真正复利的资产，是你这一整批作品本身。

## 目录结构

```
SKILL.md                  主循环（load → research → 采访 → 起草 → 引用 → 自查 → 发布）
references/
  interview-method.md     怎么问：问题类型、追问逻辑
  drafting.md             声音、出处、两段式引用
  red-lines.md            不可碰的红线 + 交付前自查清单
examples/                 拷进 profile/ 用的模板（随仓库入库）
profile/                  你的私有数据（gitignore）
drafts/                   生成的文章（gitignore）
```

## 产出与发布

byline-skill 会把成稿写到 `drafts/<slug>.md`，纯 Markdown。如果你建了 `profile/publish.md`，它还会按你的格式把文件写进你的博客/仓库。**它绝不动 git**（不 commit、不 push），所以不会有任何文章在你没过目的情况下，就以你的名义上线。审阅和发布，由你来。

## 诚实的局限

skill 不是银弹，得看清楚：

- **署名没有结构性保障。** 同一个 agent 既采访又起草，所以它*有可能*"好心"地替你把话说完。一个专门做的 app 能从结构上杜绝这件事，skill 不能。Phase 5 对照 `references/red-lines.md` 的自查是唯一的替代，所以每次都得老实做。
- **犀利的追问很难。** 模型能稳定地问出合格的问题；但"抓到你自己都没察觉的矛盾"，是这套方法在使劲、却还没完全解决的部分。
- **引用需要你核。** "自查清单"不是可选项；AI 找引用有幻觉风险。
- **它仍然是文字。** 它捕捉不到面对面采访里的犹豫和语气。跨会话带着你的上下文意味着要问的问题更少，但这只能部分弥补。

## 为什么是 skill，而不是一个产品

托管的 app 看不到你过去的作品，也就没法让新文章站在旧文章之上、和它们交叉印证。写作是复利的，而这种复利只长在本地。大多数会写东西的人，手里已经有一个趁手的 agent；杠杆在于把一套打磨过的 SOP 叠加到他们已经在用的工具上，而不是再去学一个凑合的新 UI。而且 skill 可定制、可版本管理：你的声音、格式、发布规则都是你自己拥有、能用 git 管起来的纯文本文件。这个项目做的，就是把核心 SOP 提炼出来，把其余的最大限度交还给你。

## 许可证

MIT，见 [LICENSE](LICENSE)。
