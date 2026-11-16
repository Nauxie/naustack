# naustack

The skills I use to run my coding agents. They install as a plugin in Claude
Code and Codex, and load in any other agent that reads `SKILL.md`.

```
.
├── AGENTS.md                always on: how to work, how to report
└── skills
    ├── ship                 a change, from branch to merged
    │   ├── pr               open or update a PR, watch it, react
    │   ├── review           review your own branch until a fresh reviewer finds nothing
    │   ├── merge            merge what was named, verify it where it deployed
    │   └── cleanup          remove what the session created, nothing else
    ├── say                  words sent under your name
    │   ├── message          a chat message in your voice, drafted or sent
    │   └── review-comment   someone else's PR, merge call first
    ├── scan                 read-only sweeps
    │   ├── refresh          what is open or waiting on you
    │   └── alerts           what alerted, how bad, and whether it will recur
    └── orchestrate          one session that runs the others (needs cmux)
        ├── start            launch a worker for a lane
        ├── tick             check every worker, pass on what is new
        ├── close            end a finished lane
        └── worker           what every worker's brief ends with
```

## Install

Claude Code, version 2.1.275 or later:

```sh
claude plugin install naustack --marketplace Nauxie/naustack
```

Codex:

```sh
codex plugin marketplace add Nauxie/naustack
codex plugin add naustack@naustack
```

Either way you get four skills: `naustack:ship`, `naustack:say`,
`naustack:scan` and `naustack:orchestrate`. Together they add about 280 tokens
to a session until one of them is used.

`orchestrate` needs [cmux](https://cmux.com): it is how the orchestrator lists,
reads, messages, starts and closes the other sessions, here or on a cloud
machine.

To update later:

```sh
claude plugin marketplace update naustack && claude plugin update naustack
codex plugin marketplace upgrade naustack
```

For any other agent, clone the repo and link the skill folders into wherever
it reads skills:

```sh
git clone https://github.com/Nauxie/naustack
ln -s "$PWD"/naustack/skills/* ~/.agents/skills/
```

A plugin installs the skills only. Copy what you want from `AGENTS.md` into
your own global instructions (`~/.claude/CLAUDE.md`, `~/.codex/AGENTS.md`).

## How it is organized

Each folder under `skills/` is one skill, built as a tree. `SKILL.md` is the
trunk: it says when the skill applies, which branch to read, and the rules
every branch shares. Each branch is one file for one step.

An agent keeps only the trunk's description in context. It reads the trunk
when the skill applies and a branch when it reaches that step, so a long
workflow costs a few lines until it is needed.

`AGENTS.md` is the root: the rules that are always on, which the skills assume.

## Make it yours

Put your specifics in your repo's `AGENTS.md`, which the skills read first: who
reviews what, branch names, the release path, your voice. When an agent gets
something wrong, add the fix to the skill it belongs to.

## License

[MIT](LICENSE)
