# Prompts for applying the AGENTS template

Work with [`AGENTS.en.md`](../AGENTS.en.md) in this repo: for a new project / when taking over an existing project, copy the matching block and send it to your AI.

## New project — paste this

```
Using AGENTS.en.md from this repo as the skeleton, generate an AGENTS.md for this new project:
fill in only the project slots (where the gate commands live, skill mapping, project-specific red lines); keep the skeleton's rules and criteria as-is — do not rewrite, do not add process.
Also create the files it depends on: README (with a "Common Commands" section), docs/00-product-direction.md, .gitignore.
Every path and command must really exist; if unsure, come ask me — never invent.
For step 0, use the grilling skill (the one-round-of-questions kind) instead of grill-me.
```

## Taking over an existing project — paste this

```
Using AGENTS.en.md from this repo as the baseline, produce an AGENTS.md for this repository. Process:
1) Recon only, no file writes yet: git status; language / package manager and lockfiles; the actually working lint/format/test/CI commands (verify each one; explain any that do not run); existing docs; whether AGENTS.md / CLAUDE.md / .cursor / nested rule files already exist.
2) Give me a difference list: which commands/paths must be replaced with the real ones; which clauses the current state does not satisfy (mark as "target" + a gradual plan); which existing rules to merge; where it conflicts with the template.
3) After I confirm, write to disk: AGENTS.md (repo root, ≤70 lines) + README "Common Commands" section + docs/00-product-direction.md pointer; merge rather than overwrite existing rules; verify commands before writing them down.
```