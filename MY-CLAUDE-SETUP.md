# My Claude Code setup

*Updated September 27, 2026*

My first session was on April 30.

| Measure | Value |
|:---|:---|
| Sessions in my current logs | 203, plus 1,997 subagent runs |
| Tool calls | 105,352 |
| Tokens generated | 188 million |
| Input tokens served from the prompt cache | about 98% |
| Busiest day | September 24, with 12,018 tool calls |
| Claude models I've used | 9 |
| Skills I wrote | 15 |
| Rules learned from mistakes | 37 |
| Hooks | 12 |
| Scheduled agents | 4 |

Each skill is a playbook for a kind of work I do a lot, like debugging or planning, and a routing table in my global `CLAUDE.md` tells a session which one to open.

I keep a log of mistakes. Sessions read it before they start and add to it as soon as they catch something, and when a lesson turns out to matter everywhere it gets promoted to my global rules. One is plain shell behavior: pipe a command into `tail` and you get `tail`'s exit code, so a failed build can look fine. Another only applies to this laptop, where `grep -i` combined with `-F` crashes without printing anything. A script that doesn't check exit codes takes that as "no matches".

For anything past a quick fix I use [GSD](https://gsd-build-get-shit-done.mintlify.app/) (Get Shit Done), a spec-driven workflow for Claude Code. It breaks each phase into small plans and gives every plan a fresh subagent, which keeps context from rotting over one long conversation. I use its security and UI reviews too.

resume-gauntlet is a Claude Code plugin I wrote to turn my project folders and repos into resume bullets I can defend in an interview. One model family writes the bullets and eight verifiers from another family grade them, and a bullet that can't point to evidence gets thrown out. It also finds jobs and drafts outreach emails. It's private for now, at v0.7.0 with 6,567 tests.

Four agents run on timers: a nightly market briefing, a job scan that saves new postings and their ATS keywords, a twice-daily sync for one of my projects, and a quarterly reminder to update a visa-sponsorship table.

One of my hooks scans files for prompt injection when an agent reads them. If a service has an MCP server, like GitHub or Supabase, I use it instead of browser automation. Experiments go in throwaway git worktrees, and for design work I usually build a few versions of the same brief and keep the best one.
