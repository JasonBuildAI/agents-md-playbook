# AGENTS.md

This page is only about **how to work**: rules and process. What the product should do — the single source of truth is `docs/00-product-direction.md`; directories, commands, and configuration — the single source of truth is `README.md`.
**Keep exactly one authoritative source per fact; everywhere else, only point to it.** If two places disagree, merge them first, then continue.

## Hard Requirements

1. **One unit of change, one commit.** A "unit" = a change you can state in one sentence and verify independently; if you cannot state it in one sentence, you have mixed several things together — split it first. **Commit only when everything is green** (red is a working state; green is the commit state); uncommitted means unfinished.
2. **Write commit messages in English**, following Conventional Commits: `feat:` / `fix:` / `refactor:` / `perf:` / `docs:` / `test:` / `chore:` / `build:` / `ci:`; one commit uses only one prefix and does only one thing; the first line says what changed — add a one-line body if the "why" needs explaining.
3. **Docs are always Markdown** — never introduce a second documentation format; paths, commands, and names in docs must actually exist — verify before writing.
4. **Land the change in one shot.** Every carrier of this change must go into the same commit: code, every call site, tests, front-end assets (including mechanical sync items such as cache/version numbers), config samples, and the docs that describe it.
   **Test: search the repository for the old name / old behavior — if you find it, the change is not finished.**
   When the change itself is a doc change, a standalone `.md` commit does not count as splitting; but you must **not** defer docs that should have been synced into a later commit.
5. **Read before you act**: `docs/00-product-direction.md`; when touching system-level content (data, interfaces, persona/copy rules, etc.), also read the corresponding design docs (`docs/0X-*.md`; the "changing what → read which doc" mapping lives only in README). A capability marked **target** in docs does not count as implemented; once landed, update the status to **current**.

## Engineering Baselines

Secrets live only in `.env` and the deployment environment — never committed, never in logs; dependencies only through the package manager, lockfile kept in sync; every data migration ships with a rollback; releases get a tag + one CHANGELOG line each; you decide which test layer things land in, but the gates must cover them.
**Irreversible actions (deleting data, pushing to public repos, releasing, touching secrets): say first, then do.** When unsure, choose the conservative, rollbackable option, and record the decisions and commands in README/docs.

## Gates — Must Run After Every Change

- **All green = every gate command passes**: tests + static checks + formatting; the single source of truth for these commands is the "Common Commands" section of README.
- During iteration, run the minimal check first (single test / single file); **when a unit wraps up, run the full set once**.
- Once red has been seen, green only counts if you actually saw it turn green; announcing "done / fixed" requires pasting the command output — no inferring.

## Process — grill-me to clarify, SDD to specify, superpowers to do it right

**Quick fixes** (typos, comments, a single constant, pure formatting): make the change directly, skip every step below; gates and commits still apply.
All other changes go through the steps; **steps can be compressed, but the order never reverses**. Artifacts on disk: one spec with two sections (requirements → design), one plan (task list); location follows project convention.

| # | Step | What to do | Default method | Artifact |
|---|---|---|---|---|
| 0 | Clarify | One question at a time, until the acceptance criteria can be written down | `grill-me` | decision summary |
| 1 | Requirements spec | Write only "what, why, how we will know it is done" — **no tech**; self-review for ambiguity when done + read it through once | — | spec · requirements |
| 2 | Technical design | Only now talk tech: architecture, interfaces, data; if unsure, loop back to questioning | `superpowers:brainstorming` | spec · design |
| 3 | Breakdown | tasks → files → test points → **commit boundaries** | `superpowers:writing-plans` | plan |
| 4 | Consistency check | requirements ↔ design ↔ task list: contradictions, omissions, scope creep | SDD analyze criteria | check result |
| 5 | Implementation | red → green → refactor; for bugs, find the root cause first; if a plan exists, follow it in order | `superpowers:test-driven-development` / `systematic-debugging` / `subagent-driven-development` / `executing-plans` | code + tests |
| 6 | Verification wrap-up | paste evidence; review as needed | `superpowers:verification-before-completion` / `requesting-code-review` | command output |

- **Compression rule**: for small changes, merge steps 1 and 2 into a single section (a dozen lines of spec); steps 3 and 4 are only needed when "it does not fit in one commit / spans modules / is easy to get out of order"; when skipped, the acceptance sentence in the spec is your build instruction, and step 4's three criteria fold into the final self-review of the spec.
- **Order discipline**: the requirements section never contains tech choices; the design section must not introduce features absent from the requirements (YAGNI).
- **Every spec answers**: what changes; acceptance (a test that will fail, or a command that proves it); what is explicitly not being done; how to roll back.
- **Check criteria**: every requirement is owned by some task in the list; no task adds a feature outside the spec; the design covers all requirements.
- **Specs are alive; once landed, docs are the truth**: if any step reveals that earlier thinking was wrong, go back and fix it before continuing (this is not a waterfall); after a change lands, its conclusions go into README / docs — the spec and plan are records of that round, not a second authority.
- **Entry discipline**: before acting, check whether a suitable skill exists (`superpowers:using-superpowers`); if so, read it first, then use it. Skill definitions live in their own SKILL.md files — they are not copied here. If this page conflicts with a skill, this page wins; note in the spec / commit that this is a deliberate override.

## Initialization (once per new project)

- Write `.gitignore` and README (with the gate commands) first → first commit → push to GitHub.
- Wire the gates into CI; the default branch only accepts all-green merges.
