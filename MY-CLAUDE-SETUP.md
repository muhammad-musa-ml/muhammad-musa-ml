# My Claude Code setup

*Muhammad Musa · [iammusa.vercel.app](https://iammusa.vercel.app) · [@muhammad-musa-ml](https://github.com/muhammad-musa-ml) · updated September 27, 2026*

I've used Claude Code since April 30, and the setup around it has turned into something I maintain like a codebase. Some notes on it.

| Measure | Value |
|:---|:---|
| Sessions on disk | 203, plus 1,997 subagent runs |
| Tool calls | 105,352 |
| Tokens generated | about 188 million |
| Tokens read from the prompt cache | about 62.7 billion |
| Busiest day (UTC) | September 6: 35 sessions, 13,627 tool calls |
| Claude model versions in the logs | 9 |
| Methodology skills I wrote | 15 |
| Rules promoted from mistake ledgers | 37 |
| Hooks | 12 |
| Recurring scheduled agents | 4 |

Old logs rotate out (the oldest one left is from May 8), so the transcript numbers run low.

## Skills and the mistake log

The fifteen skills are playbooks for different kinds of work, from debugging and planning to research and writing, and a routing table in my global `CLAUDE.md` tells a session which one to open.

The part I'd keep if I had to drop the rest is the mistake log. A project keeps a ledger; sessions read it before starting and add an entry the moment they catch a mistake. When a lesson turns out to apply everywhere, it moves into my global instructions, which now hold 37 of them. Some are about my own habits and some are about this particular Windows machine. A command piped into `tail`, for example, hands back `tail`'s exit code, so a broken build can look fine. And here `grep -i` together with `-F` crashes without printing anything, which a careless script will read as zero matches.

## Workflow

Bigger projects run on [GSD](https://gsd-build-get-shit-done.mintlify.app/) (Get Shit Done), a spec-driven workflow for Claude Code; I'm on v1.41.2. It breaks a phase into small plans and gives each one a fresh subagent, the idea being that one long conversation gets worse as it goes. I also use its review commands for security, UI and eval coverage.

## resume-gauntlet

My Claude Code plugin for writing resumes I can defend in an interview. It reads my project folders and repos, drafts bullets, and sends them through eight verifiers that run on a different model family than the one that wrote them. A bullet with no evidence behind it gets rejected. It's at v0.7.0 with a test suite of 6,567 tests, I'm the only committer, and it's private for now. It can also look for jobs and draft outreach, but sending or submitting stays my call.

## Scheduled agents

A nightly market briefing (it can place an order, but only once I've approved it), a job scan that saves new postings along with the keywords their screening systems look for, a twice-daily sync for one of my projects, and a quarterly reminder to update a visa-sponsorship table.

## Guardrails

Twelve hooks run inside the harness itself. The one closest to my research scans the files an agent reads for prompt injection. Others check commits and writes. For outside services I prefer a proper MCP server (GitHub, Supabase, Slack and so on) and only drive a browser or the desktop when nothing else can do the job.

## Small habits

Experiments go into throwaway git worktrees. For open-ended design I'll build a few versions of the same brief and keep one. And since cache reads outnumber generated tokens roughly 333 to 1 in my logs, I try to structure sessions so the cache stays warm.

---

<sub>A script walks every session log on disk and totals messages, tool calls and tokens (days are UTC). The config counts come from listing the skill, hook and scheduled-task folders.</sub>
