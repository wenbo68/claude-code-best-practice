# Filesystem Overview

- Date: 2026-06-04
- Summary: A best-practices reference repository for Claude Code (and adjacent CLI agents like Codex/Gemini), demonstrating patterns for skills, subagents, commands, hooks, MCP servers, and orchestration workflows. It is documentation- and asset-heavy — a curated reference and presentation collection ("from vibe coding to agentic engineering") rather than an application codebase, anchored by a Weather System example built on the Command → Agent → Skill architecture.

## Structure

```
claude-code-best-practice/
├── .gitignore                                  — git ignore rules
├── .mcp.json                                   — project MCP server configuration
├── CLAUDE.md                                   — guidance for Claude Code working in this repo
├── LICENSE                                     — repository license
├── README.md                                   — main entry doc with concept tables, tips, badges
├── .claude/                                     — Claude Code config: agents, commands, skills, hooks, settings (leaf)
├── .codex/                                       — Codex CLI agent config (leaf)
├── .git/                                         — git internals (leaf)
├── .github/                                       — GitHub workflows / repo config (leaf)
├── !/                                            — shared media assets (mascots, badges, tags) used across docs
│   ├── claude-jumping.svg                        — Claude mascot art
│   ├── claude-speaking.svg                       — Claude mascot art
│   ├── codex-jumping.svg                         — Codex mascot art
│   ├── codex-speaking.svg                        — Codex mascot art
│   ├── gemini-jumping.svg                        — Gemini mascot art
│   ├── gemini-speaking.svg                       — Gemini mascot art
│   ├── root/                                     — top-of-README hero/trending assets
│   │   ├── boris-slider.gif                      — Boris Cherny slider animation
│   │   ├── boris-slider.psd                      — source PSD for slider
│   │   ├── github-trending-day.svg              — "trending #1" badge
│   │   └── github-trending.png                   — trending screenshot
│   ├── tags/                                     — SVG badge/label icons referenced throughout README
│   │   └── (a.svg, best-practice.svg, boris-cherny.svg, claude.svg, … many badge SVGs)
│   ├── thumbnail/                                — video/presentation thumbnails & HTML mockups
│   │   ├── 50k-stars.html                        — milestone thumbnail page
│   │   ├── daily-workflows.html                  — thumbnail page
│   │   ├── presentation-1.png                    — presentation thumbnail
│   │   ├── video-1.png                           — video thumbnail
│   │   ├── video-2.png                           — video thumbnail
│   │   └── video.psd                             — source PSD
│   └── video-presentation-transcript/            — transcript artifacts for workflow video
│       ├── 1-video-workflow.html                — rendered transcript
│       └── 1-video-workflow.md                   — markdown transcript
├── agent-teams/                                  — multi-agent "agent teams" example
│   ├── agent-teams-prompt.md                     — prompt defining the agent-team workflow
│   └── output/                                    — generated example outputs
│       ├── dubai-time.svg                        — sample generated SVG
│       └── output.md                             — sample run output
├── best-practice/                                — written best-practice guides per Claude Code feature
│   ├── claude-cli-startup-flags.md              — CLI startup flag guidance
│   ├── claude-commands.md                        — commands best practices
│   ├── claude-mcp.md                             — MCP servers best practices
│   ├── claude-memory.md                          — memory/CLAUDE.md best practices
│   ├── claude-power-ups.md                       — power-up tips
│   ├── claude-settings.md                        — settings.json best practices
│   ├── claude-skills.md                          — skills best practices
│   ├── claude-subagents.md                       — subagents best practices
│   └── assets/                                    — images for the best-practice guides
│       ├── claude-memory/                         — memory guide images
│       │   └── claude-memory-monorepo.jpg
│       └── claude-power-ups/                      — power-up guide images
│           ├── dial-the-model-1.png
│           ├── dial-the-model-2.png
│           ├── dial-the-model-3.png
│           └── powerup-menu.png
├── changelog/                                     — dated changelogs & verification checklists per topic
│   ├── agent-collections/changelog.md
│   ├── best-practice/                             — per-feature best-practice changelogs
│   │   ├── claude-commands/changelog.md
│   │   ├── claude-settings/                       — settings changelog + checklist
│   │   │   ├── changelog.md
│   │   │   └── verification-checklist.md
│   │   ├── claude-skills/changelog.md
│   │   ├── claude-subagents/                      — subagents changelog + checklist
│   │   │   ├── changelog.md
│   │   │   └── verification-checklist.md
│   │   └── concepts/                              — concepts changelog + checklist
│   │       ├── changelog.md
│   │       └── verification-checklist.md
│   ├── cross-model-workflows/changelog.md
│   ├── development-workflows/changelog.md
│   └── skill-collections/changelog.md
├── development-workflows/                         — reusable dev workflow patterns
│   ├── cross-model-workflow/                      — using multiple models together
│   │   ├── cross-model-workflow.md
│   │   └── assets/cross-model-workflow.png
│   └── rpi/                                       — Research-Plan-Implement workflow
│       ├── rpi-workflow.md
│       └── rpi-workflow.svg
├── implementation/                               — concrete worked implementations of the concepts
│   ├── claude-agent-teams-implementation.md
│   ├── claude-commands-implementation.md
│   ├── claude-goal-implementation.md
│   ├── claude-scheduled-tasks-implementation.md
│   ├── claude-skills-implementation.md
│   ├── claude-subagents-implementation.md
│   └── assets/                                    — screenshots illustrating implementations
│       ├── impl-agent-teams.png
│       ├── impl-goal-claude.png
│       ├── impl-goal-codex.png
│       ├── impl-loop-1.png
│       └── impl-loop-2.png
├── orchestration-workflow/                        — Weather System orchestration demo + generated output
│   ├── orchestration-workflow.gif               — animated flow demo
│   ├── orchestration-workflow.md                — Command→Agent→Skill flow explanation/diagram
│   ├── orchestration-workflow.svg               — flow diagram
│   ├── output.md                                 — generated weather run output
│   └── weather.svg                               — generated weather card SVG
├── presentation/                                  — slide decks & talk assets (HTML decks + images)
│   ├── 2026-04-25-gdg-kolachi-cli-claude-code-gemini/index.html  — GDG Kolachi talk deck
│   ├── claude-code-best-practice/index.html      — best-practice talk deck
│   ├── vibe-coding-to-agentic-engineering/index.html — main talk deck
│   └── assets/                                    — imagery for the decks
│       ├── concepts/                              — concept illustrations (vibe-coding, agents, claudemd, context, skills, workflow)
│       ├── hallucination/                         — hallucination example screenshots
│       ├── harness/                               — harness/tool-calling limitation images
│       ├── introduction/                          — speaker intro assets (Shayan, Umaid)
│       ├── llm/                                   — LLM explainer diagrams (tokens, basic/advanced)
│       └── logo/                                  — gemini & github logos
├── reports/                                       — deep-dive research reports on Claude/LLM topics
│   ├── claude-advanced-tool-use.md
│   ├── claude-agent-command-skill.md
│   ├── claude-agent-memory.md
│   ├── claude-agent-sdk-vs-cli-system-prompts.md
│   ├── claude-global-vs-project-settings.md
│   ├── claude-in-chrome-v-chrome-devtools-mcp.md
│   ├── claude-skills-for-larger-mono-repos.md
│   ├── claude-spinner-verbs-and-tips.md
│   ├── claude-usage-and-rate-limits.md
│   ├── learning-journey-weather-reporter-redesign.md
│   ├── llm-day-to-day-degradation.md
│   ├── why-harness-is-important.md
│   └── assets/                                    — diagrams/screenshots for the reports
│       ├── agent-command-skill-1.jpg
│       ├── agent-command-skill-2.png
│       ├── llm-degradation-2.png
│       ├── llm-degradation.png
│       ├── programmatic-tool-calling-diagram.svg
│       └── sdk-vs-cli-diagram.svg
├── tips/                                          — curated tip roundups from Boris Cherny & Thariq
│   ├── claude-boris-10-tips-01-feb-26.md
│   ├── claude-boris-12-tips-12-feb-26.md
│   ├── claude-boris-13-tips-03-jan-26.md
│   ├── claude-boris-15-tips-30-mar-26.md
│   ├── claude-boris-2-tips-10-mar-26.md
│   ├── claude-boris-2-tips-25-mar-26.md
│   ├── claude-boris-6-tips-16-apr-26.md
│   ├── claude-thariq-tips-16-apr-26.md
│   ├── claude-thariq-tips-17-mar-26.md
│   └── assets/                                    — numbered screenshot sets per tip thread
│       ├── boris-26-1-3/   (0.png … 13.png)
│       ├── boris-26-2-1/   (0.png … 10.png)
│       ├── boris-26-2-12/  (0.webp … 12.webp)
│       ├── boris-26-3-10/  (0.png, 1.png)
│       ├── boris-26-3-25/  (1.png, 2.png)
│       ├── boris-26-3-30/  (0.png … 15.png)
│       ├── boris-26-4-16/  (0.png … 6.png)
│       ├── thariq-26-3-17/ (1.png … 27.png)
│       └── thariq-26-4-16/ (1.png … 19.png)
├── tutorial/                                      — onboarding/setup tutorial by day
│   ├── day0/                                      — install/setup per OS
│   │   ├── README.md
│   │   ├── linux.md
│   │   ├── mac.md
│   │   ├── windows.md
│   │   └── assets/login.png
│   └── day1/README.md                            — first-day tutorial
└── videos/                                        — notes/transcripts from Claude Code talks & podcasts
    ├── claude-boris-lennys-podcast-19-feb-26.md
    ├── claude-boris-pragmatic-engineer-04-mar-26.md
    ├── claude-boris-ryan-peterman-15-dec-25.md
    ├── claude-boris-y-combinator-17-feb-26.md
    ├── claude-cat-every-29-oct-25.md
    ├── claude-dex-mlops-community-24-mar-26.md
    ├── claude-karpathy-ai-engineer-02-may-26.md
    └── claude-matt-pocock-24-apr-26.md
```
