# agents-md-playbook

A general-purpose "how we work" charter for AI coding agents (Codex / Claude Code, etc.): single source of truth, commit only when green, gates, and a staged process — how to work, on one page.

**English** | [中文](README.md)

## Download

| Version | File | Download |
|---|---|---|
| **English** | [`AGENTS.en.md`](AGENTS.en.md) | [View](AGENTS.en.md) / [Download .md (Raw)](https://raw.githubusercontent.com/JasonBuildAI/agents-md-playbook/main/AGENTS.en.md) |
| 中文版 | [`AGENTS.zh-CN.md`](AGENTS.zh-CN.md) | [浏览](AGENTS.zh-CN.md) / [直接下载 .md（Raw）](https://raw.githubusercontent.com/JasonBuildAI/agents-md-playbook/main/AGENTS.zh-CN.md) |

Usage: download the file, drop it into your project root, rename it to `AGENTS.md`, then replace the "slots" (product source-of-truth path, where gate commands live, skill mapping, project red lines) with your project's real setup.

## What it is

A one-page "how to work" charter: rules and process only, no product features. It covers:

- **Single source of truth**: one authoritative source per fact; everywhere else, only pointers;
- **Commit only when green**: one unit of change, one commit; "seen red, green counts" and "uncommitted means unfinished";
- **Gates**: tests + static checks + formatting; the single source of truth for commands lives in README;
- **Staged process**: clarify → requirements → design → breakdown → consistency check → implement → verify; compressible, never reversible, with a fast lane for quick fixes;
- **Engineering baselines**: secrets, dependencies, migrations, releases, and "say first, then do" for irreversible actions.

## Where it comes from & what it is

This template is a **distillation** that combines:

- **OpenAI's official articles**: guidance on AGENTS.md and agentic workflows;
- **Claude (Anthropic) official articles**: best practices for Claude Code / CLAUDE.md;
- **Google's engineering handbook**: engineering practices (code review, testing, commit discipline, etc.);
- **Community skills**: ideas from `grill-me`, `superpowers`, and similar;
- **SDD (Spec-Driven Development)**: the requirements → design → breakdown spec workflow.

To be clear: **this is still a personal view** — it is not an official standard of any organization named above, nor a complete quotation of their material; it is a selection of the parts that can actually be enforced, twisted into one page you can use directly. **It will keep evolving** — anything awkward or missing gets changed over time. Issues / PRs welcome.

## Apply prompts

Send these to your AI to apply the template: generate an AGENTS.md for a **new project**, or retrofit an **existing project**.

- English: [`prompts/apply.en.md`](prompts/apply.en.md)
- 中文版: [`prompts/apply.zh-CN.md`](prompts/apply.zh-CN.md)

## Layout

```
AGENTS.en.md             English template
AGENTS.zh-CN.md          Chinese template (original)
prompts/apply.en.md      English apply prompts
prompts/apply.zh-CN.md   Chinese apply prompts
README.en.md             This file (English)
README.md                Chinese README
LICENSE                  MIT
```

## License

[MIT](LICENSE)