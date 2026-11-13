# naustack

The skills I run my coding agents with, cut down to the process. Every file is
short on purpose, and nothing in it depends on a company, a repo or a tool.
They load in Claude Code, Codex, and any other agent that reads `SKILL.md`
skills.

```
.
├── AGENTS.md            always on: how to work, how to report
├── ship                 a change, from branch to merged
│   ├── pr               open or update a PR, watch it, react
│   ├── review           review your own branch until a fresh reviewer finds nothing
│   ├── merge            merge what was named, verify it where it deployed
│   └── cleanup          remove what the session created, nothing else
├── say                  words sent under your name
│   ├── message          a chat message in your voice, drafted or sent
│   └── review-comment   someone else's PR, merge call first
└── scan                 read-only sweeps
    ├── refresh          what is open or waiting on you
    └── alerts           what alerted, how bad, and whether it will recur
```

## How it is organized

Each folder is one skill, built as a tree. `SKILL.md` is the trunk: it says
when the skill applies, which branch to read, and the rules every branch
shares. Each branch is one file for one step.

An agent keeps only the trunk's description in context. It reads the trunk
when the skill applies and a branch when it reaches that step, so a long
workflow costs a few lines until it is needed.

`AGENTS.md` is the root: the rules that are always on, which the skills assume.

## Install

```sh
git clone https://github.com/Nauxie/naustack
cd naustack

for skill in ship say scan; do
  ln -s "$PWD/$skill" ~/.claude/skills/$skill   # Claude Code
  ln -s "$PWD/$skill" ~/.agents/skills/$skill   # Codex
done
```

Then copy what you want from `AGENTS.md` into your own global instructions
(`~/.claude/CLAUDE.md`, `~/.codex/AGENTS.md`).

## Make it yours

The skills leave out everything local on purpose: who reviews what, branch
names, the release path, your voice. Put those in your repo's own `AGENTS.md`,
which the skills tell the agent to read first. When an agent gets something
wrong, add the correction to the skill it belongs to.
