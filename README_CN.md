# 📝 Obsidian AI Notes

> 通过自然语言指令管理 Obsidian 笔记的 AI 工作流

**Obsidian AI Notes** 是一个 AI Skill，让你通过简单指令（如 `-day`、`-note`、`-week`）自动创建、归类和管理结构化的 Obsidian 笔记。

**特点：** 中文为主，英文兼容，根据你的语言自动输出对应语言内容。

---

## 🚀 快速开始

```bash
# 1. 克隆仓库
git clone https://github.com/michelllsm/obsidian-ai-notes.git

# 2. 告诉 AI 助手
-setup

# 3. 选择语言
# A: 中文  B: English  C: Auto-detect

# 4. 开始记笔记
-note 介绍 obsidian-ai-notes skill可以哪些具体的应用场景
```

---

## ✨ 核心指令

| 指令        | 中文别名         | 用途    | 输出目录             |
| --------- | ------------ | ----- | ---------------- |
| `-day`    | `-每日笔记`      | 每日记录  | `📅每日笔记/`        |
| `-note`   | `-主题`        | 主题沉淀  | `📚主题笔记/`        |
| `-week`   | `-每周笔记`      | 周复盘   | `📆每周笔记/`        |
| `-task`   | `-待办`, `-跟踪` | 任务跟踪  | `📋待跟踪任务/`       |
| `-tool`   | `-工具`        | 工具卡片  | `🛠️tools/`      |
| `-output` | `-创作`, `-输出` | 创作输出  | `📝创作输出/`        |
| `-input`  | `-灵感`, `-输入` | 灵感记录  | `📚主题笔记/`        |
| `-update` | `-迭代`        | 工作流优化 | `💡笔记工作流优化idea/` |

> **提示:** 使用 `-` 前缀加强指令识别。忘记加 `-`？AI 会理解清晰的意图或询问确认。

---

## 🌍 语言支持

Skill 自动检测你的语言偏好并适配：

| 语言 | 文件夹示例 | 输出语言 |
|------|-----------|---------|
| 🇨🇳 中文 | `📅每日笔记/`, `📚主题笔记/` | 纯中文 |
| 🇺🇸 English | `📅Daily/`, `📚Topics/` | Pure English |

**检测方式:**
1. 显式声明（Explicit statement）
2. 系统上下文（System context）
3. 对话分析（Conversation analysis）
4. 默认中文（Default: Chinese）

---

## 📁 文件夹结构

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

---

## 🔧 安装要求

- [Obsidian](https://obsidian.md/download)（免费）
- **推荐:** [Obsidian CLI](https://github.com/YakDao/obsidian-cli)  
  （`npm install -g obsidian-cli`）

> 没有 CLI？AI 会自动切换到文件系统模式，基础功能正常。

---

## 🧩 扩展 Skill

开箱完成后，可安装以下 Skill 扩展能力：

| Skill | 效果 | 建议级别 |
|-------|------|---------|
| 小红书 | 搜索/读取小红书笔记 → 一键入库 | 推荐 |
| X (Twitter) | 搜索推文/线程 → 归档到主题笔记 | 推荐 |
| YouTube Full | 视频字幕摘要 → 自动归档 | 推荐 |
| Agent Reach | 多平台聚合搜索 | 推荐 |

---

## 📐 模板策略

- 模板内有双语注释（方便理解字段含义）
- 实际输出时根据你的语言只保留单一语言
- 所有模板可直接编辑，修改立即生效

---

## ⚙️ 自动化

- 完成第一篇 `-day` 后：询问是否开启每日自动化
- 累计三篇笔记后：询问是否开启周复盘自动化

支持：内置定时任务 / cron / GitHub Actions

---

## 📂 项目结构

```
obsidian-ai-notes/
├── README.md              # 英文文档
├── README_CN.md           # 本文档（中文）
├── SKILL.md               # AI 执行规范
├── LICENSE                # MIT
├── .gitignore
├── templates/             # 双语标注模板
│   ├── daily-note每日笔记.md
│   ├── weekly-review每周复盘.md
│   ├── topic-note主题笔记.md
│   └── task任务.md
└── docs/                  # 详细文档
    ├── skill-installation-table.md / Skill标准安装表.md
    └── automation-notifications.md / 自动化与通知方案.md
```

---

## 🤝 贡献

欢迎 Issue 和 PR！常见方向：
- 模板改进
- 新语言支持
- Bug 修复

---

## 📄 许可证

[MIT](./LICENSE)

---

> **说明:** 本 Skill 设计为通用规则，可自由修改以适应你的工作流。详见 [SKILL.md](obsidian-ai-notes-github/SKILL.md)。

---

**English version:** [README.md](obsidian-ai-notes-github/README.md)
