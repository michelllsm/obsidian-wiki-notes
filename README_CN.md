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

# 3. 跟着引导完成（5步，约5分钟）
# 4. 开始记笔记！
-day
```

---

## ✨ 核心指令

| 指令 | 中文别名 | 什么时候用 | 输出目录 |
|------|---------|-----------|---------|
| `-day` | `-每日笔记` | 记录今天学到的、遇到的问题、明天要做的 | `📅每日笔记/` |
| `-note` | `-主题` | 收录文章、视频、播客——任何值得保留的外部内容 | `📚主题笔记/` |
| `-week` | `-每周笔记` | 周末复盘：做了什么、学了什么、下周计划 | `📆每周笔记/` |
| `-task` | `-待办`, `-跟踪` | 跟踪一个任务的状态、背景、下一步 | `📋待跟踪任务/` |
| `-tool` | `-工具` | 记录发现的新工具或技巧 | `🛠️tools/` |
| `-output` | `-创作`, `-输出` | 你的原创内容：文章、帖子、分享 | `📝创作输出/` |
| `-input` | `-灵感`, `-输入` | 快速捕捉一个转瞬即逝的灵感 | `📚主题笔记/` |
| `-update` | `-迭代` | 改进笔记工作流本身的想法 | `💡笔记工作流优化idea/` |
| `-compile` | `-整合`, `-编译` | 把同一主题的多篇零散笔记合并成一篇结构化总览 | `📚主题笔记/综合/` |
| `-check` | `-检查` | 扫描笔记库：找出孤立笔记、过期内容、缺失链接 | _(仅输出报告)_ |
| `-归类` | `-classify`, `-整理` | AI 扫描收件箱，逐篇判断分类并归档 | 从 `📎Clippings/` 到各分类 |

> **提示:** 使用 `-` 前缀加强指令识别。忘记加 `-`？AI 会理解清晰的意图或询问确认。

---

## 📁 文件夹结构

```
<vault>/
├── 📅每日笔记/                    # -day
├── 📚主题笔记/                    # -note, -input（收录的内容）
│   └── 综合/                      # -compile（AI 编译的主题总览）
├── 📆每周笔记/                    # -week
├── 📋待跟踪任务/                  # -task
├── 📝创作输出/                    # -output（你的原创，不与收录混放）
├── 🛠️tools/                      # -tool
├── 💡笔记工作流优化idea/           # -update
├── 📎Clippings/                   # 收件箱 + 原始全文档案（-归类 扫描此处）
└── obsidian-ai-notes skill配置/   # Skill 文件（可直接修改）
```

**核心设计原则：** 收录内容（`📚主题笔记/`）和原创输出（`📝创作输出/`）永远分开。你始终知道哪些是你写的。

---

## 🌍 语言支持

Skill 自动检测你的语言偏好并适配：

| 语言 | 文件夹示例 | 输出语言 |
|------|-----------|---------|
| 🇨🇳 中文 | `📅每日笔记/`, `📚主题笔记/` | 纯中文 |
| 🇺🇸 English | `📅Daily/`, `📚Topics/` | Pure English |

---

## 🔄 更新与自定义

### 更新

```bash
git pull origin main
```

你的自定义**始终受保护**——AI 智能合并更新，不会覆盖你的修改。详见 SKILL.md § 7。

### 自定义

直接编辑 `obsidian-ai-notes skill配置/` 里的任何文件，或者告诉 AI：

```
帮我修改每日笔记模板，加一个"心情"字段
```

修改立即生效。

---

## 🧩 扩展 Skill

开箱完成后，可安装以下 Skill 扩展能力：

| Skill | 效果 | 建议 |
|-------|------|------|
| xiaohongshu | 搜索/采集小红书内容 → 自动归档到笔记 | 推荐 |
| youtube-full | YouTube 转录/搜索/频道 → 自动归档 | 推荐 |
| video-summary | 多平台视频总结（B站/抖音/YouTube/本地） | 推荐 |
| agent-reach | AI 互联网访问：16+平台（Twitter/X、Reddit、B站等） | 推荐 |
| agent-browser | 浏览器自动化：截图、表单填写、数据提取 | 推荐 |
| find-skills | 发现更多实用 Skill | 推荐 |
| self-improving-agent | 自动记录错误并持续改进 | 推荐 |

---

## 🔧 安装要求

- [Obsidian](https://obsidian.md/download)（免费）
- **推荐:** [Obsidian CLI](https://github.com/YakDao/obsidian-cli)（`npm install -g obsidian-cli`）

> 没有 CLI？AI 会自动切换到文件系统模式，基础功能正常。

---

## 📄 许可证

[MIT](./LICENSE)

---

> **说明:** 本 Skill 设计为通用规则，可自由修改以适应你的工作流。详见 [SKILL.md](SKILL.md)。

**English version:** [README.md](README.md)
