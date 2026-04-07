# 📝 Obsidian AI Notes

> AI-powered Obsidian workflow via natural language commands

**Obsidian AI Notes** is an AI Skill that lets you create, organize, and manage structured Obsidian notes through simple commands like `-day`, `-note`, `-week`.

**Features:** Chinese-first, English-compatible, automatically outputs content based on your language preference.

---

## 🚀 Quick Start

```bash
# 1. Clone the repo
git clone https://github.com/michelllsm/obsidian-ai-notes.git

# 2. Tell your AI assistant
-setup

# 3. Select language
# A: 中文  B: English  C: Auto-detect

# 4. Start taking notes
-day Today I learned about Obsidian AI Notes
```

---

## ✨ Core Commands

| Command | Aliases | Purpose | Output Folder |
|---------|---------|---------|---------------|
| `-day` | `-daily` | Daily log | `📅Daily/` |
| `-note` | `-topic` | Topic note | `📚Topics/` |
| `-week` | `-weekly` | Weekly review | `📆Weekly/` |
| `-task` | `-todo`, `-remind` | Task tracking | `📋Tasks/` |
| `-tool` | — | Tool card | `🛠️Tools/` |
| `-output` | `-out`, `-create` | Content creation | `📝Output/` |
| `-input` | `-inspiration` | Capture inspiration | `📚Topics/` |
| `-update` | `-iterate` | Workflow improvement | `💡Ideas/` |

> **Tip:** Use `-` prefix to strengthen command recognition. Forgot the `-`? AI will understand clear intent or ask for confirmation.

---

## 🌍 Language Support

The Skill automatically detects your language preference and adapts:

| Language | Folder Example | Output |
|----------|---------------|--------|
| 🇨🇳 中文 | `📅每日笔记/`, `📚主题笔记/` | 纯中文 |
| 🇺🇸 English | `📅Daily/`, `📚Topics/` | Pure English |

**Detection Priority:**
1. Explicit statement
2. System context
3. Conversation analysis
4. Default: Chinese

---

## 📁 Folder Structure

```
<vault>/
├── 📅Daily/            # -day
├── 📚Topics/           # -note, -input
├── 📆Weekly/           # -week
├── 📋Tasks/            # -task
├── 📝Output/           # -output
├── 🛠️Tools/           # -tool
├── 💡Ideas/            # -update
└── .ai-notes/          # Skill configuration
```

---

## 🔧 Requirements

- [Obsidian](https://obsidian.md/download) (Free)
- **Recommended:** [Obsidian CLI](https://github.com/YakDao/obsidian-cli)  
  (`npm install -g obsidian-cli`)

> No CLI? AI will automatically fall back to filesystem mode. Basic functions still work.

---

## 🧩 Extension Skills

After setup, you can install these Skills to extend capabilities:

| Skill | Effect | Recommendation |
|-------|--------|----------------|
| Xiaohongshu | Search/read notes → one-click import | Recommended |
| X (Twitter) | Search tweets/threads → archive to topics | Recommended |
| YouTube Full | Video transcripts → auto-archive | Recommended |
| Agent Reach | Multi-platform aggregation | Recommended |

---

## 📐 Template Strategy

- Templates have bilingual comments (for field understanding)
- Actual output keeps only the target language based on your preference
- All templates are editable, changes take effect immediately

---

## ⚙️ Automation

- After first `-day`: Ask if enable daily automation
- After 3 notes: Ask if enable weekly review automation

Supports: Built-in scheduler / cron / GitHub Actions

---

## 📂 Project Structure

```
obsidian-ai-notes/
├── README.md              # This file (English)
├── README_CN.md           # Chinese documentation
├── SKILL.md               # AI execution spec
├── LICENSE                # MIT
├── .gitignore
├── templates/             # Bilingual annotated templates
│   ├── daily-note每日笔记.md
│   ├── weekly-review每周复盘.md
│   ├── topic-note主题笔记.md
│   └── task任务.md
└── docs/                  # Detailed docs
    ├── skill-installation-table.md / Skill标准安装表.md
    └── automation-notifications.md / 自动化与通知方案.md
```

---

## 🤝 Contributing

Issues and PRs welcome! Common directions:
- Template improvements
- New language support
- Bug fixes

---

## 📄 License

[MIT](./LICENSE)

---

> **Note:** This Skill is designed as general rules. Feel free to modify to fit your workflow. See [SKILL.md](obsidian-ai-notes-github/SKILL.md) for details.

---

**中文版:** [README_CN.md](README_CN.md)
