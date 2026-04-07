# Automation & Notifications

> Goal: Let users get started quickly, then gradually enable automation at the right time (avoid lengthy initial setup).

---

## 1) Recommended Principle (Manual First, Then Auto)

| # | Principle |
|---|-----------|
| 1 | **First setup does NOT require automation** — only confirm minimum essentials (path, naming, output preference). |
| 2 | **After first daily note**, ask if enable "Daily Note Automation". |
| 3 | **After 3 notes accumulated**, ask if enable "Weekly Review Automation". |
| 4 | Keep "dual mode": manual always available, auto is just enhancement. |

---

## 2) Built-in Automation (Priority)

If current platform has "built-in automation/scheduled task" capability, use it first.

### 2.1 Task A: Daily Note Automation (Optional)
- Name: `Daily Note Reminder/Generation`
- Frequency: Daily once (suggested evening)
- Trigger: `-day`
- Output: `📅Daily/`

### 2.2 Task B: Weekly Review Automation (Optional)
- Name: `Weekly Review`
- Frequency: Every Friday 22:30 (customizable)
- Trigger: `-week`
- Output: `📆Weekly/`

### 2.3 Notification
- Manual mode: No forced notification
- Auto mode: Send notification after successful generation

---

## 3) Cross-Platform Alternatives

### 3.1 Option A: cron + Local Script (macOS/Linux)
```cron
# Daily note at 21:30
30 21 * * * /usr/bin/python3 /path/to/scripts/run_daily_note.py

# Weekly review at Friday 22:30
30 22 * * 5 /usr/bin/python3 /path/to/scripts/run_weekly_review.py
```

### 3.2 Option B: GitHub Actions (Repository hosted)
```yaml
name: notes-automation
on:
  schedule:
    - cron: "30 13 * * *"   # UTC 13:30 = Beijing 21:30, Daily
    - cron: "30 14 * * 5"   # UTC 14:30 = Beijing 22:30, Friday
jobs:
  run:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Run notes workflow
        run: python scripts/run_notes_workflow.py
```

---

## 4) FAQ

**Q: Will automation affect manual recording?**  
A: No. Manual and auto can run in parallel.

**Q: Should I configure all automation at the start?**  
A: Not recommended. Get manual working first, then enable auto after triggers are met.

**Q: What if content is too long?**  
A: Ensure templates only enable [Required] sections.
