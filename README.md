# agents-md-playbook

一套给 AI 编程代理（Codex / Claude Code 等）的「干活规约」通用模板：单一真源、全绿才提交、闸门与分台阶流程——一页纸讲清"怎么干活"。

[English](README.en.md) | **中文**

## 下载

| 版本 | 文件 | 下载 |
|---|---|---|
| **中文版** | [`AGENTS.zh-CN.md`](AGENTS.zh-CN.md) | [浏览](AGENTS.zh-CN.md) / [直接下载 .md](https://github.com/JasonBuildAI/agents-md-playbook/releases/latest/download/AGENTS.zh-CN.md) |
| English | [`AGENTS.en.md`](AGENTS.en.md) | [View](AGENTS.en.md) / [Download .md](https://github.com/JasonBuildAI/agents-md-playbook/releases/latest/download/AGENTS.en.md) |

> 「下载」列点击后直接保存 `.md` 文件（Release 附件链接）；「浏览」列是在线查看。

用法：下载后放进你的项目根目录，重命名为 `AGENTS.md`，再把「槽位」（产品真源路径、闸门命令位置、技能映射、项目红线）替换成你项目的真实情况即可。

## 它是什么

一页纸的「怎么干活」规约：只讲规矩与流程，不讲产品功能。核心内容包括——

- **单一真源**：同一事实只保留一个权威出处，别处只放指针；
- **全绿才提交**：一个改动单位一个 commit，见过红、绿灯才算数，"没提交等于没做完"；
- **闸门**：测试 + 静态检查 + 格式，命令的唯一真源在 README；
- **分台阶流程**：澄清 → 需求规约 → 技术方案 → 拆分 → 一致性检查 → 实现 → 验证收尾；可压缩、不可倒序，小改动有「顺手改」快车道；
- **工程底线**：密钥、依赖、迁移、发版，以及"不可逆动作先说再做"。

## 来源与定位

这份模板是我结合以下内容后**浓缩成的精华**：

- **OpenAI 官方文章**：关于 AGENTS.md 与代理工作流的指引；
- **Claude（Anthropic）官方文章**：关于 Claude Code / CLAUDE.md 的最佳实践；
- **Google 开发手册**：工程实践（代码评审、测试、提交纪律等）；
- **社区 Skills**：`grill-me`、`superpowers` 等技能里的做法；
- **SDD（规格驱动开发）**：需求 → 方案 → 拆分的规约流程。

需要说清楚的是：**这依旧是个人看法**，不代表上述任何组织的官方标准，也不是对原文的完整引用；我只是把其中真正能执行的条款挑出来，拧成一份能直接用的规矩。**后续会不断更新**——用久了发现哪条别扭、哪条缺失，都会改。欢迎 issue / PR。

## 附加：套用提示词

想让 AI 按模板干活，可以把提示词直接发给它：为**新项目**生成 AGENTS.md，或在**接管旧项目**时对照改造。

- 中文版：[`prompts/apply.zh-CN.md`](prompts/apply.zh-CN.md)
- English: [`prompts/apply.en.md`](prompts/apply.en.md)

## 目录结构

```
AGENTS.zh-CN.md          中文版模板
AGENTS.en.md             English template
prompts/apply.zh-CN.md   中文版套用提示词
prompts/apply.en.md      English apply prompts
README.md                本文件（中文）
README.en.md             English README
LICENSE                  MIT
```

## License

[MIT](LICENSE)