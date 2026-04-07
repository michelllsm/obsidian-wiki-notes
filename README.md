# 📝 Obsidian AI Notes

> **中文：** 通过自然语言指令管理 Obsidian 笔记的 AI 工作流  
> **EN:** AI-powered Obsidian workflow via natural language commands

**Obsidian AI Notes** 是一个 AI Skill，让你通过简单指令（如 `-day`、`-note`、`-week`）自动创建、归类和管理结构化的 Obsidian 笔记。

**特点：** 中文为主，英文兼容，根据你的语言自动输出对应语言内容。

---

## 🚀 快速开始 / Quick Start

```bash
# 1. 克隆仓库 / Clone repo
git clone https://github.com/michelllsm/obsidian-ai-notes.git

# 2. 告诉 AI 助手 / Tell your AI assistant
-setup

# 3. 选择语言 / Select language
# A: 中文  B: English  C: Auto-detect

# 4. 开始记笔记 / Start taking notes
-day 今天学习了 Obsidian AI Notes
```

---

## ✨ 核心指令 / Core Commands

| 指令<br>Command | 中文别名 | 英文别名 | 用途<br>Purpose |
|----------------|---------|---------|----------------|
| `-day` | `-每日笔记` | `-daily` | 每日记录 / Daily log |
| `-note` | `-主题` | `-topic` | 主题沉淀 / Topic note |
| `-week` | `-每周笔记` | `-weekly` | 周复盘 / Weekly review |
| `-task` | `-待办`, `-跟踪` | `-todo`, `-remind` | 任务跟踪 / Task tracking |
| `-tool` | `-工具` | — | 工具卡片 / Tool card |
| `-output` | `-创作`, `-输出` | `-out`, `-create` | 创作输出 / Content creation |
| `-input` | `-灵感`, `-输入` | `-inspiration` | 灵感记录 / Capture inspiration |
| `-update` | `-迭代` | `-iterate` | 工作流优化 / Workflow improvement |

> **提示 / Tip:** 使用 `-` 前缀加强指令识别。忘记加 `-`？AI 会理解清晰的意图或询问确认。

---

## 🌍 语言支持 / Language Support

Skill 自动检测你的语言偏好并适配：

| 语言<br>Language | 文件夹示例<br>Folder Example | 输出语言<br>Output |
|-----------------|---------------------------|------------------|
| 🇨🇳 中文 | `📅每日笔记/`, `📚主题笔记/` | 纯中文 |
| 🇺🇸 English | `📅Daily/`, `📚Topics/` | Pure English |

**检测方式 / Detection:**
1. 显式声明（Explicit statement）
2. 系统上下文（System context）
3. 对话分析（Conversation analysis）
4. 默认中文（Default: Chinese）

---

## 📁 文件夹结构 / Folder Structure

### 中文用户 / Chinese Users
```
<vault>/
├── 📅每日笔记/          # -day
├── 📚主题笔记/          # -note, -input
├── 📆每周笔记/          # -week
├── 📋待跟踪任务/        # -task
├── 📝创作输出/          # -output
├── 🛠️tools/           # -tool
├── 💡笔记工作流优化idea/ # -update
└── .ai-notes/          # Skill 配置
```

### 英文用户 / English Users
```
<vault>/
├── 📅Daily/            # -day
├── 📚Topics/           # -note, -input
├── 📆Weekly/           # -week
├── 📋Tasks/            # -task
├── 📝Output/           # -output
├── 🛠️Tools/           # -tool
├── 💡Ideas/            # -update
└── .ai-notes/
```

---

## 🔧 安装要求 / Requirements

- [Obsidian](https://obsidian.md/download)（免费 / Free）
- **推荐 / Recommended:** [Obsidian CLI](https://github.com/YakDao/obsidian-cli)  
  （`npm install -g obsidian-cli`）

> 没有 CLI？AI 会自动切换到文件系统模式，基础功能正常。
> No CLI? AI falls back to filesystem mode, basic functions work.

---

## 🧩 扩展 Skill / Extension Skills

开箱完成后，可安装以下 Skill 扩展能力：

| Skill | 中文效果 | EN Effect |
|-------|---------|-----------|
| 小红书 / Xiaohongshu | 搜索/读取小红书笔记 → 一键入库 | Search/read notes → one-click import |
| X (Twitter) | 搜索推文/线程 → 归档到主题笔记 | Search tweets/threads → archive |
| YouTube Full | 视频字幕摘要 → 自动归档 | Video transcripts → auto-archive |
| Agent Reach | 多平台聚合搜索 | Multi-platform aggregation |

---

## 📐 模板策略 / Template Strategy

- 模板内有双语注释（方便理解字段含义）
- 实际输出时根据你的语言只保留单一语言
- 所有模板可直接编辑，修改立即生效

**Templates have bilingual comments for clarity, but output is single-language based on your preference.**

---

## ⚙️ 自动化 / Automation

- 完成第一篇 `-day` 后：询问是否开启每日自动化
- 累计三篇笔记后：询问是否开启周复盘自动化

支持：内置定时任务 / cron / GitHub Actions

---

## 📂 项目结构 / Project Structure

```
obsidian-ai-notes/
├── README.md              # 本文档 / This file
├── SKILL.md               # AI 执行规范（中文为主，英文附后）
├── LICENSE                # MIT
├── .gitignore
├── templates/             # 双语标注模板
│   ├── daily-note.md
│   ├── weekly-review.md
│   ├── topic-note.md
│   └── task.md
└── docs/                  # 详细文档（中文）
    ├── 自动化与通知方案.md
    └── Skill标准安装表.md
```

---

## 🤝 贡献 / Contributing

欢迎 Issue 和 PR！常见方向：
- 模板改进 / Template improvements
- 新语言支持 / New language support
- Bug 修复 / Bug fixes

---

## 📄 许可证 / License

[MIT](./LICENSE)

---

> **说明 / Note:** 本 Skill 设计为通用规则，可自由修改以适应你的工作流。详见 [SKILL.md](./SKILL.md)。
