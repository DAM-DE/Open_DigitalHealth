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

## One-time setup

### 1. Add your Anthropic API key to GitHub Secrets

Go to: `Settings → Secrets and variables → Actions → New repository secret`

- Name: `ANTHROPIC_API_KEY`
- Value: your key from console.anthropic.com

### 2. Enable Actions write permissions

Go to: `Settings → Actions → General → Workflow permissions`

Select: **Read and write permissions**

### 3. Adjust the schedule (optional)

Edit `.github/workflows/generate-health-idea.yml`, line 8.

```yaml
- cron: '0 8 * * 1'        # Every Monday 08:00 UTC
- cron: '0 9 * * *'        # Daily 09:00 UTC
- cron: '0 8 * * 1,4'      # Mon + Thu 08:00 UTC
```

### 4. Trigger the first run manually

Go to: `Actions → Generate Digital Health Idea → Run workflow`

This confirms everything is wired correctly before the schedule kicks in.

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

---

## Running manually (without the schedule)

If Claude Code is installed locally:

```bash
# As a slash command inside a Claude Code session
/generate-health-idea

# Or directly from terminal
claude --dangerously-skip-permissions \
  --print \
  "$(cat .claude/routines/generate-health-idea.md)"
```

---

## Troubleshooting

| Symptom | Likely cause | Fix |
|---|---|---|
| Action fails with 401 | API key not set | Add `ANTHROPIC_API_KEY` to repo secrets |
| Action fails with 403 on git push | Write permissions off | Enable read+write in Actions settings |
| Idea file not created | Claude didn't complete | Check Actions log; try manual trigger |
| Duplicate ideas appearing | Table not being read | Confirm `ideas_table.md` is committed |
