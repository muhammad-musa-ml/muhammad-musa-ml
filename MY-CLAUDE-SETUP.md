# My Claude Code Setup

*Muhammad Musa · [iammusa.vercel.app](https://iammusa.vercel.app) · [@muhammad-musa-ml](https://github.com/muhammad-musa-ml) · last updated July 11, 2026*

Most people use Claude Code as a faster way to write code. I run it as an operating system.

There's a doctrine layer that governs *how* the agent thinks, a workflow engine that plans and verifies before it builds, a plugin I authored and shipped on top of the platform, agents that run on cron while I sleep, and twenty tool integrations that give it hands. This page is the inventory — and in keeping with the rest of my work, every claim on it is a receipt: a real file in my config, a real number recomputed from my transcripts, or a real artifact you can look at.

---

## The numbers

Recomputed on July 11, 2026 by streaming every transcript currently on disk (805 MB of session logs). First session: April 30, 2026 — ten weeks ago. These figures are conservative: transcripts older than early May have already rotated out of retention.

| Metric | Value |
|---|---|
| Sessions on disk | 236 — plus **1,204 subagent transcripts** they spawned |
| Transcript messages | 137,500+ (my turns, the agent's turns, and the tool traffic between them) |
| Tool calls executed by the agent | 44,800+ |
| Tokens generated | ~120 million |
| Tokens read through prompt cache | ~20.5 **billion** (another ~1.0 billion written into it) |
| Busiest single day | July 8: 25 sessions, 16,731 messages, 5,143 tool calls |
| Most parallel day | June 23: **57 distinct sessions** touched in one day |
| Longest thread | one Wumi Health session, 10,680 messages across four days (July 1–4) |
| Claude model versions in the transcripts | 7, across three generations — Opus 4.8 is the workhorse (17.2 B of those cache reads) |
| Skills in my global library | 80 (**13 of which I authored**) |
| Custom subagents defined | 61 |
| Hook scripts active | 12, including a custom statusline |
| Scheduled autonomous agents | 4 |
| MCP servers reachable in one session | 20 |
| Plugins I've built and shipped | 1 (and it's a big one — see below) |
| Startup built end-to-end with this stack | Wumi Health — **5 of 12 phases closed, 51/51 plans, 545/545 DB tests green locally *and* on cloud** |

For scale: when I last snapshotted these numbers in mid-June, they read 74 sessions, 34.5 million generated tokens, and 5 billion cache reads. Three weeks later every one of those has roughly tripled. The curve is compounding, not flattening — and the reason it *can* compound is everything below: parallel sessions, isolated worktrees, subagent fleets, and agents that keep working when I close the laptop.

---

## The setup, in six layers

```
1. Doctrine    — global CLAUDE.md + 13 methodology skills I authored
2. Workflow    — GSD: spec-driven planning, execution, verification
3. Product     — resume-gauntlet: my own published Claude Code plugin
4. Automation  — scheduled agents, loops, background tasks
5. Integration — 20 MCP servers (GitHub, Supabase, Gmail, Robinhood…)
6. Safety      — hooks that gate writes, scan reads, validate commits
```

### 1 · I don't just prompt the agent — I wrote its doctrine

The highest-leverage thing in my setup isn't a tool. It's thirteen **methodology manuals** I had Claude write about its own working methods, now installed as skills that load automatically in every session, in every project.

The prompt that started it: *assume you're leaving forever, and you can only leave behind your manuals.* Claude proposed 55 topics; we consolidated them into what is now 13 skills — 70 files of dense, imperative playbooks — and wired a router table into my global `CLAUDE.md` so any session knows exactly which manual to open for the work in front of it:

`orient-fable` (entering unfamiliar code) · `debug-fable` (the diagnostic loop) · `plan-fable` (decomposition and tradeoffs) · `build-fable` (greenfield to integrations) · `design-fable` (APIs, schemas, concurrency) · `change-safely-fable` (refactors, upgrades, releases) · `verification-fable` (never claim done without proof) · `research-fable` (version-dated, source-ranked truth) · `communicate-fable` (writing for the reader) · `frontend-fable` (UI craft) · `llm-systems-fable` (prompts, RAG, agents, evals) · `footguns-fable` (time, unicode, money, messy data) · and the newest, `evolve-fable`.

**`evolve-fable` is the keystone.** It's the meta-skill that makes the whole system self-correcting: any project can carry a mistake ledger (`claude_learning.md`) that the agent must read in full at session start, every qualifying mistake gets logged *in the same turn it's caught* — before the fix is even claimed done — lessons that generalize get promoted into the global `CLAUDE.md`, and when a mistake traces back to a skill's own instructions, the skill itself gets repaired. The setup doesn't just have rules; it has a mechanism for growing them.

On top of the manuals sit six **standing rules** that bind every session, whether or not a skill is loaded:

1. Never claim something works without having run or observed it.
2. Never fix a bug you haven't reproduced — and add the regression test after.
3. The codebase's conventions beat the agent's preferences.
4. Make the smallest change that achieves the goal; write adjacent improvements down instead of doing them.
5. Stop and confirm before anything irreversible, destructive, or outward-facing.
6. In any project with a mistake ledger, read it at session start and log mistakes the turn they're caught.

Most people's `CLAUDE.md` says "use TypeScript, be concise." Mine is a constitution — with an amendment process.

### 2 · Spec-driven workflow: GSD

Day-to-day engineering runs on [GSD (Get Shit Done)](https://gsd-build-get-shit-done.mintlify.app/) — the spec-driven development system for Claude Code, v1.41.2 in my install. Its core insight is **context-rot management**: instead of one long conversation that slowly degrades, every task is planned into atomic units and executed by fresh subagents with clean context windows, committed atomically, verified goal-backward.

My install carries 66 GSD commands and 33 specialized agents (researchers, planners, executors, verifiers, security auditors, UI auditors), and I use the full lifecycle: `/gsd-new-project` → `/gsd-plan-phase` → `/gsd-execute-phase` → `/gsd-verify-work`, with `/gsd-code-review`, `/gsd-secure-phase`, and `/gsd-eval-review` as quality gates. For AI features specifically, `/gsd-ai-integration-phase` produces an AI-SPEC design contract — failure modes, eval dimensions, guardrails — *before* any model call gets written.

### 3 · I build **on** Claude Code, not just with it: resume-gauntlet

The strongest evidence I understand this platform is that I shipped a product on it. **resume-gauntlet** (v0.6.0, MIT) is my own Claude Code plugin — installed from my own plugin marketplace — that turns raw notes, repos, and offer letters into interview-defensible resumes. The development tree has already outgrown the shipped version: **40 skills, 28 agents, 5 hooks, 10 scripts**, a DeepEval evaluation suite, CI, and docs.

- An **8-verifier adversarial gauntlet**: a simulated recruiter 6-second screen, a skeptical hiring manager, an ATS parse simulator (Workday/Greenhouse/Taleo/iCIMS/Lever), a plausibility auditor, a tense checker, an AI-fingerprint detector, a 0–100 scorecard, and an advisory "could you defend this claim with an artifact?" buildability auditor.
- **Anti-sycophancy by architecture**: the model that writes bullets is *required at runtime* to be a different model family from the models that judge them (Sonnet writes, Opus verifies in my config). A model grading its own homework is a known failure mode — so the plugin makes it impossible.
- **Provenance enforcement**: every bullet must carry `source_refs` back to real evidence, or a grounding verifier blocks the commit. Honesty isn't a vibe here; it's a schema.
- **Compliance gates before outreach**: CAN-SPAM/GDPR consent checks, per-channel acknowledgments, API keys routed to the OS keychain instead of plaintext settings.

That's not prompt engineering. That's LLM-systems engineering — multi-agent orchestration, eval harnesses, model-mixing policy, and safety gates, packaged and versioned.

### 4 · Agents that work while I sleep

Four scheduled agents run without me:

- **Premarket trading briefing** — reads my live Robinhood portfolio, watchlists, and options chains over MCP and drafts a brief before U.S. market open. (It reads and analyzes; trades stay human.)
- **Job scan** — sweeps Greenhouse/Lever/Ashby boards and aggregators for AI roles, with a visa-sponsorship filter.
- **Sponsor-prior refresh** — keeps the sponsorship-likelihood table behind that filter current.
- **Symbol zone-entry watch** — a one-off market watcher spun up for a specific setup.

Add `/loop` for self-pacing recurring work inside a session, and background tasks for anything long-running. A meaningful share of those 1,204 subagent transcripts was never typed by me.

### 5 · MCP: giving the agent hands

Twenty MCP servers were reachable in the very session that wrote this page: **GitHub**, **Supabase**, **Slack**, **Gmail**, **Google Calendar**, **Google Drive**, **Canva**, **Google Stitch** (design generation), **Robinhood**, a job-search connector, **Dart/Flutter tooling**, **Claude in Chrome** (real browser control), **Computer Use** (the desktop itself), a scheduled-tasks server, the MCP registry, Apify (bundled with my plugin for contact discovery), plus the harness's own browser, visualization, and session-management servers.

The craft isn't collecting connectors — it's routing: dedicated API-backed MCP first, browser automation second, pixel-level computer use last. Fast and precise beats slow and general.

### 6 · Safety: hooks on every dangerous edge

Twelve hook scripts run at the harness level, where the model can't forget them:

- A **prompt-injection scanner on every file the agent reads** (`gsd-read-injection-scanner.js`). I research indirect prompt injection academically in my graduate security coursework at UW–Madison (CS 763) — so my own daily tooling assumes hostile file content by default.
- **Pre-write guards** (prompt guard, read guard, workflow guard) that gate every `Write`/`Edit` before it lands.
- A **commit validator** on every git commit, a **context monitor** after heavy tool use, **session-state restoration** on start, and a custom statusline showing workflow state.

If a safety behavior matters, I don't ask the model to remember it. I make the harness enforce it.

---

## Session technique

The habits that separate running an agent from *operating a fleet*:

- **Parallel variant racing.** My portfolio site is the survivor of three: I ran the same brief in three separate repos as three concurrent builds, then kept the best. When generation is cheap, selection is the skill.
- **Worktree isolation.** Agent experiments run in disposable git worktrees on their own branches, so parallel work can't stomp the main tree — several of my sessions live entirely inside `.claude/worktrees/`.
- **Model mixing on purpose.** Seven Claude model versions appear in my transcripts, spanning three generations. Opus 4.8 (with the 1M-token context window enabled) as the daily workhorse, the Claude 5 family — Fable 5 and Sonnet 5 — adopted the week it shipped for judgment-heavy and high-volume work respectively, Haiku for cheap mechanical passes — and writer/verifier splits wherever judgment matters.
- **Multi-agent workflows as a default, not a stunt.** Fan-out research sweeps, adversarial verification panels where independent skeptics try to refute each finding, judge panels for design alternatives. 1,204 subagent transcripts in ten weeks is what that looks like on disk.
- **Persistent memory.** A file-based memory directory with an index the agent maintains across sessions, plus a generated developer profile so every session already knows how I like decisions made (recommend and own it), explanations delivered (teach the fundamentals), and instructions treated (precisely).
- **Cache-aware economics.** Twenty and a half billion of my tokens were cache reads — two orders of magnitude more than everything else combined. Structuring sessions so context stays warm is the difference between a setup that scales and one that burns budget.

---

## Case study: building a startup end to end — Wumi Health

The setup above isn't hypothetical. It's currently building **Wumi Health** — the digital-health startup I co-founded and lead as CEO (Wumi Health (Private) Limited, SECP-incorporated in Islamabad, 2025): a multi-sided, mobile-first EHR/HMIS for Pakistan that unifies patients, doctors, labs, pharmacies, and clinic admins around a CNIC-anchored record and a QR health card. Claude Code is, in effect, the engineering org. Here's how a one-founder company ships like a team.

### The build, by the numbers

Flutter (Android/iOS/web) on a Supabase backend — Postgres with row-level security, storage, edge functions — developed against a local Docker stack and graduated to a cloud dev project before every phase closes. GSD manages the whole lifecycle: a **12-phase roadmap, 5 phases closed and 51 plans executed**, every requirement traced from `PROJECT.md` → `REQUIREMENTS.md` → `ROADMAP.md` → per-phase specs and plans. Receipts from Phase 4 — the clinician clinical loop, closed July 10, 2026:

- **545/545 pgTAP database tests** passing — run locally *and* re-run against the cloud project
- `flutter analyze` at **zero issues**; the full Flutter test suite green
- Supabase security advisors at **0 high-severity findings** on cloud
- **Four rounds of founder UAT on a real device** before the phase could close — which surfaced six close-gate bugs (all fixed and re-verified) and drove a full redesign of the record-vault reveal flow: unlock one item, the others stay locked, each behind its own PIN, with per-record, global, and five-minute auto re-lock
- A phase-close gate that is *automatic and mandatory*: every in-scope user flow walked green locally, then on cloud, then in a final sweep — the founder never has to ask

Compliance is grounded in Pakistani law first — PECA 2016 and the Personal Data Protection Bill 2023 — with RBAC, encryption, immutable audit logging, and WCAG-AA accessibility specified from day one, not retrofitted. Clinical tables carry a FHIR JSONB projection so records round-trip to the interoperability standard on export.

### The project CLAUDE.md is a constitution, not a config file

The repo's `CLAUDE.md` is titled "rules of engagement," and every rule in it is dated and traceable to a real incident. A sample:

- **No placeholders, no "TODO later," no fake data.** If something needs an external dependency, stop and say so — never paper over it.
- **"Challenge, don't just comply."** The agent is required to push back when a better architecture exists. Agreement is not the goal.
- **Fix a defect everywhere it occurs.** A bug fixed only where it was reported is *incomplete and blocking* — find every path that shares the root cause first.
- **Definition of Done:** clean build, zero failing tests, zero analyzer errors, and manual UAT on an Android emulator. This rule exists because a previous build's docs claimed "✅ complete" while the app couldn't compile. Never again.
- **Two-stage verification:** everything goes green on the emulator + local stack first, then the same migrations deploy to the cloud dev project and every flow is re-verified there — and every fix must be *cloud-portable* by construction. Production is never touched.
- **The mistake ledger is law.** The project runs `evolve-fable`'s learning loop: mistakes are logged the turn they're caught, and the ledger commit lands *with* the fix, not after it.

### The five-tool design gate

The rule I'm proudest of: **no screen is coded — in any phase — until the design gate passes.** Three steps, in order:

1. **Read the canon first.** `DESIGN-TOOLS.md`, `DESIGN-SYSTEM.md`, `UX-PATTERNS.md`, and the phase's UI spec — and offer the founder reference samples *before* generating anything.
2. **Run all five design tools, completely.** Each has a distinct role: **`ui-ux-pro-max`** sets direction (67 styles, 96 palettes, 57 font pairings); **Stitch** (Google's design MCP) generates on-brand breadth — screens bound to an uploaded design system, plus named variants; **Claude Design** (claude.ai/design) produces high-fidelity, actually-runnable HTML prototypes; **`gstack-design`** runs a designer's review rubric plus an AI-slop blacklist (distilled from Garry Tan's gstack); **`emil-design-eng`** and **`review-animations`** hold the motion bar (Emil Kowalski's animation craft). WCAG-AA contrast is *verified per text element* in light **and** dark — never asserted. Then 2–3 genuinely distinct options go to the founder, each shown in both modes.
3. **Persist every approved design** to the "Wumi Health — Design System" workspace on claude.ai/design via the `DesignSync` tool, so the canvas always holds the current approved truth.

This gate is a post-mortem turned into process. Three real failures — screens coded without reading the design docs, a review that was asserted instead of run (an unreadable dark-mode header shipped into an option set), and approved designs never persisted — each became a step that makes the mistake structurally impossible to repeat. That's the pattern behind my whole setup: **don't resolve to do better; change the system so worse can't happen.**

### A real design system, round-tripped between repo and canvas

The brand runs on a locked **three-theme system** (Sky Clinical default, plus Teal·Navy·Gold and Cyan·Peach), each in light and dark, user-switchable in-app. `DESIGN-SYSTEM.md` is the living record: no design decision is "done" until it's written there and mirrored token-for-token into `lib/core/theme/`. The Claude Design workspace holds the approved foundations, typography, components, and screen sets — named and synced. Stitch holds the exploration trail: a BASE composition plus named variants per screen, so every choice has a visible road-not-taken.

The design docs also plug into every GSD step: discuss-phase frames its questions from them, ui-phase inherits tokens instead of re-deriving them, plan-phase writes UI tasks against the component map, execute-phase maps designs to theme tokens (never raw hex), and verify/ui-review check the result against the same canon. One source of truth, consumed at six different altitudes.

### MCP depth, not MCP collecting

Two details that show what operating this stack actually takes:

- **MCP-first is a written rule**: anything Supabase (migrations, SQL, logs, advisors, type generation) or Flutter/Dart (analyze, pub, hot reload, widget inspector) goes through the dedicated MCP when it can, because API-backed beats shelling out.
- When Google's official remote Stitch endpoint wouldn't load — its tool schemas use JSON-Schema `$ref`/`$defs` that Claude Code's MCP client can't dereference, yielding zero tools — I diagnosed it, routed through a schema-normalizing proxy instead, and documented the decision *with the condition under which to revisit it*. Knowing why your tools break is the difference between using a stack and understanding one.

---

## What it has shipped

Ten weeks of receipts:

- **Wumi Health** — the startup build detailed above: 5 of 12 phases closed, 51 plans executed, a verified test pyramid from 545 pgTAP assertions to on-device E2E, and a design system synced to claude.ai/design.
- **[My portfolio site](https://iammusa.vercel.app)** — a 3D scroll-driven portfolio (Three.js neural constellation, 2,400 GPU-shaded particles) with an honesty-first AI twin grounded in a knowledge base, served for $0 on edge functions. Built through the pipeline above, chosen from three parallel builds.
- **resume-gauntlet** — the plugin described above: 40 skills, 28 agents, an eval suite, and a marketplace, versioned and licensed.
- **[MuFaaSat Photo Arcade](https://github.com/muhammad-musa-ml/mufaasat)** — a playful online photobooth where two people on two laptops can shoot one photo strip together, live. Conceived, built, and deployed to GitHub Pages in two days (July 9–10).
- **[A scroll-driven 3D portfolio](https://github.com/muhammad-musa-ml/faati-portfolio)** for a partner designer — the parallel-racing pipeline, rerun for a different person and brief.
- **LLM security research** — graduate work on indirect prompt injection (UW–Madison CS 763), which feeds directly back into the injection-scanning hooks in my daily setup.
- **Voice Agent** — an outreach-discovery pipeline that finds businesses via OpenStreetMap, enriches them with scraping plus LLM-judged quality signals, and writes verified-facts sidecars.
- **A course chatbot** built while TAing CS 320, daily market briefs, weekly job scans — and the thirteen methodology manuals themselves, written, audited, and now self-repairing via `evolve-fable`.

The honest productivity claim isn't "10x." It's stranger than that: the ceiling on my output stopped being my typing speed and started being the quality of my specifications, my verification gates, and my judgment about what's worth building. Those are the skills this setup is really made of.

---

## Colophon

This page practices what it documents: Claude Code recomputed every number by streaming the 805 MB of session transcripts on my disk, re-read my hooks, settings, plugin manifests, and project state files — then wrote this under `communicate-fable` rules (lead with the point, receipts over adjectives) and the standing rule that nothing gets claimed that wasn't observed. Drafted with Claude Fable 5, July 11, 2026.
