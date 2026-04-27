# Digital Health Idea Generator

Autonomous idea generation via Claude Code, running on a GitHub Actions schedule.
Each run generates one new idea, scores it, writes a detail file, and commits everything back to this repo.

---

## How it works

```
GitHub Actions (cron)
        ↓
Claude Code reads .claude/routines/generate-health-idea.md
        ↓
Reads ideas_table.md → learns from high Author Score patterns
        ↓
Generates 5 candidates → eliminates any failing hard disqualifiers
        ↓
Selects best → scores → writes ideas/<slug>.md
        ↓
Appends row to ideas_table.md
        ↓
git commit + push → back to this repo
```

---

## Repository structure

```
.
├── .claude/
│   ├── commands/
│   │   └── generate-health-idea.md   # Slash command (run manually in Claude Code)
│   └── routines/
│       └── generate-health-idea.md   # Routine (run by GitHub Actions)
├── .github/
│   └── workflows/
│       └── generate-health-idea.yml  # Scheduler + runner
├── ideas/
│   └── <slug>.md                     # One file per idea (auto-created)
└── ideas_table.md                    # Master table (auto-updated)
```

---

## The self-learning mechanism

The routine reads `ideas_table.md` before every run and looks for ideas with **Author Score ≥ 8**.

**How to make it smarter over time:**

1. After each run, open the generated idea file in `ideas/`
2. Change the `Author Score` row to your actual rating
3. Optionally add a comment line below the scores table: `<!-- High because: passive wearable signal + employer payer + no regulatory friction -->`
4. Commit the edit

On the next run, Claude Code will read your scores and comments, extract the patterns, and weight new ideas toward what you've rated highly. The more ideas you score, the stronger the signal.

**The system learns by reading, not fine-tuning** — all pattern extraction happens at inference time from the repo contents.
