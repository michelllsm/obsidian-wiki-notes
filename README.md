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

# 3. Follow the guided setup (5 phases, ~5 min)
# 4. Start taking notes!
-day
```

---

## ✨ Core Commands

| Command | Aliases | When to use | Output Folder |
|---------|---------|-------------|---------------|
| `-day` | `-daily` | Record today's learnings, problems, and tomorrow's plan | `📅Daily/` |
| `-note` | `-topic` | Save articles, videos, podcasts — any external content worth keeping | `📚Topics/` |
| `-week` | `-weekly` | End-of-week review: what shipped, what learned, what's next | `📆Weekly/` |
| `-task` | `-todo` | Track a task with status, context, and next action | `📋Tasks/` |
| `-tool` | — | Document a new tool or technique you discovered | `🛠️Tools/` |
| `-output` | `-out`, `-create` | Your original content: articles, posts, creative work | `📝Output/` |
| `-input` | `-inspiration` | Quick-capture a fleeting idea or inspiration | `📚Topics/` |
| `-update` | `-iterate` | Ideas for improving your note workflow itself | `💡Ideas/` |
| `-compile` | `-synthesize` | Merge multiple notes on a topic into one structured overview | `📚Topics/synthesis/` |
| `-check` | `-health` | Scan your vault for orphan notes, missing links, stale content | _(report only)_ |
| `-classify` | `-sort` | AI scans your inbox and files each item to the right folder | from `📎Clippings/` |

> **Tip:** Use `-` prefix to strengthen command recognition. Forgot the `-`? AI will understand clear intent or ask for confirmation.

---

## 📁 Folder Structure

```
<vault>/
├── 📅Daily/              # -day
├── 📚Topics/             # -note, -input (collected content)
│   └── synthesis/        # -compile (AI-compiled overviews)
├── 📆Weekly/             # -week
├── 📋Tasks/              # -task
├── 📝Output/             # -output (your original work — never mixed with collected)
├── 🛠️Tools/             # -tool
├── 💡Ideas/              # -update
├── 📎Clippings/          # Inbox + raw archive (Web Clipper dumps here, -classify processes)
└── obsidian-ai-notes skill配置/  # Skill configuration (editable)
```

**Key design principle:** Collected content (`📚Topics/`) and original output (`📝Output/`) are always separate. You always know what's yours.

---

## 🌍 Language Support

The Skill automatically detects your language preference:

| Language | Folder Example | Output |
|----------|---------------|--------|
| 🇨🇳 中文 | `📅每日笔记/`, `📚主题笔记/` | 纯中文 |
| 🇺🇸 English | `📅Daily/`, `📚Topics/` | Pure English |

---

## 🔄 Updates & Customization

### How to Update

```bash
git pull origin main
```

Your customizations are **always protected** — AI merges updates intelligently without overwriting your changes. See SKILL.md § 7 for details.

### How to Customize

Edit any file in `obsidian-ai-notes skill配置/` directly, or tell your AI:

```
Help me modify the daily note template to add a "mood" field
```

Changes take effect immediately.

---

## 🧩 Extension Skills

After setup, install these to supercharge your workflow:

| Skill | What it does | Level |
|-------|-------------|-------|
| xiaohongshu | Search & collect Xiaohongshu (RedNote) content → auto-archive | Recommended |
| youtube-full | YouTube transcripts, search, channels → auto-archive | Recommended |
| video-summary | Multi-platform video summary (Bilibili, Douyin, YouTube, local) | Recommended |
| agent-reach | AI internet access: 16+ platforms (Twitter/X, Reddit, Bilibili, etc.) | Recommended |
| agent-browser | Browser automation: screenshots, form filling, data extraction | Recommended |
| find-skills | Discover new Skills from the marketplace | Recommended |
| self-improving-agent | Auto-record errors and improve over time | Recommended |

---

## 🔧 Requirements

- [Obsidian](https://obsidian.md/download) (Free)
- **Recommended:** [Obsidian CLI](https://github.com/YakDao/obsidian-cli) (`npm install -g obsidian-cli`)

> No CLI? AI automatically falls back to filesystem mode.

---

## 📄 License

[MIT](./LICENSE)

---

> **Note:** This Skill is designed as general rules. Feel free to modify to fit your workflow. See [SKILL.md](SKILL.md) for the full AI execution spec.

**中文版:** [README_CN.md](README_CN.md)
