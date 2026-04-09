---
name: obsidian-ai-notes
description: |
  This skill enables AI agents to create, organize, and manage structured Obsidian notes 
  through natural language commands like -day, -note, -week. Designed for Chinese users 
  with English compatibility. Supports bilingual output, template-driven note generation, 
  and progressive automation.

  Use when: User wants to take notes in Obsidian via AI, create daily/weekly logs, 
  track tasks, or build a structured knowledge base with AI assistance.
  Setup / onboarding: "-setup", "配置笔记工作流", "初始化 obsidian"
version: 1.0.0
author: smingliang
---

# SKILL: obsidian-ai-notes

> AI 执行规范：Obsidian 笔记工作流（中文为主，英文兼容）
> 版本：1.0.0 | 更新：2026-04-09

---

## 0. 触发条件

### 触发词
- **核心指令**: `-day`, `-note`, `-week`, `-task`, `-tool`, `-output`, `-input`, `-update`
- **中文别名**: `-每日笔记`, `-主题`, `-每周笔记`, `-待办`, `-跟踪`, `-工具`, `-创作`, `-输出`, `-灵感`, `-输入`, `-迭代`
- **自然语言**: "帮我记笔记", "创建每日记录", "写周复盘", "记录灵感", "跟踪任务"
- **开箱**: `-setup`, "配置笔记工作流", "初始化 obsidian"

### 笔记库优先原则

```
执行优先级：
1. <vault>/obsidian-ai-notes skill配置/SKILL.md（用户自定义）← 最高
2. 官方 Skill 文件（系统内置）
```

用户通过自然语言修改笔记库里的 SKILL.md，即时生效。

### 不触发场景
- 单纯询问 Obsidian 软件使用问题
- 导出/导入笔记文件（文件操作，非结构化创建）
- 询问 Markdown 语法

---

## 1. 核心指令

| 指令        | 别名                    | 用途    | 输出目录                          |
| --------- | --------------------- | ----- | ----------------------------- |
| `-day`    | `-daily`, `-每日笔记`     | 每日记录  | `📅每日笔记/` / `📅Daily/`        |
| `-note`   | `-topic`, `-主题`       | 主题沉淀  | `📚主题笔记/` / `📚Topics/`       |
| `-week`   | `-weekly`, `-每周笔记`    | 周复盘   | `📆每周笔记/` / `📆Weekly/`       |
| `-task`   | `-todo`, `-待办`, `-跟踪` | 任务跟踪  | `📋待跟踪任务/` / `📋Tasks/`       |
| `-tool`   | `-工具`                 | 工具卡片  | `🛠️tools/`                   |
| `-output` | `-out`, `-创作`, `-输出`  | 创作输出  | `📝创作输出/` / `📝Output/`       |
| `-input`  | `-灵感`, `-输入`          | 灵感记录  | `📚主题笔记/` / `📚Topics/`       |
| `-update` | `-iterate`, `-迭代`     | 工作流优化 | `💡笔记工作流优化idea/` / `💡Ideas/` |
| `-compile`| `-整合`, `-编译`         | 多篇笔记编译为结构化总览 | `📚主题笔记/综合/` / `📚Topics/synthesis/` |
| `-check`  | `-检查`, `-健康检查`      | 扫描笔记库，报告问题并建议优化 | 输出到对话（不生成文件） |
| `-归类`   | `-classify`, `-整理`    | 扫描收件箱，AI 逐篇归档到对应分类 | 从 `📎Clippings/` 到各分类 |

---

## 1.5 全局规则

### 1.5.1 YAML Frontmatter（强制）

**每篇笔记头部必须包含 YAML frontmatter**，无论是否使用模板：

```yaml
---
created: YYYY-MM-DDTHH:mm+08:00
modified: YYYY-MM-DDTHH:mm+08:00
type: daily | topic-external | topic-personal | weekly | task | tool | output | compile
source: 原始链接（如有）
tags: [标签1, 标签2]
---
```

各类型笔记的 frontmatter 略有不同（详见模板），但 `created`、`modified`、`type` 三个字段全类型强制。

### 1.5.2 反向链接（强制）

**AI 创建任何笔记时，必须**：
1. 扫描 `📚主题笔记/` 目录下的文件名列表
2. 如果有主题相关的已有笔记，自动在 `## 强相关资源` 中填入 `[[笔记名]]`
3. 如果是 `-compile` 产物，必须在 frontmatter 加 `sources: [[来源笔记1]], [[来源笔记2]]`

不管用不用模板，这条规则都生效。

### 1.5.3 收录与输出分离（强制）

```
📚主题笔记/     = 输入端：收录的外部内容 + 编译的综合文章
📝创作输出/     = 输出端：个人原创内容

绝不混放。
```

连接方式：创作输出的笔记用 `[[双向链接]]` 指向参考的主题笔记，并在 frontmatter 标注：
```yaml
references: [来源笔记1, 来源笔记2]
```

### 1.5.4 `-compile` 编译指令

**触发**：用户说 `-整合 xxx` 或 `-compile xxx`

**执行流程**：
1. AI 扫描 `📚主题笔记/` 中所有含相关标签/关键词的笔记
2. 提取每篇的核心要点（读 frontmatter + 摘要段）
3. 合并去重、理清逻辑关系、标注信息来源
4. 生成结构化综合文章，存入 `📚主题笔记/综合/`
5. 在产物中标注所有来源笔记的 `[[双向链接]]`

**产物格式**：
```yaml
---
created: ...
modified: ...
type: compile
sources: [来源笔记1, 来源笔记2, ...]
tags: [主题标签]
---
# xxx 知识总览

## 综合摘要
（整合所有来源后的 3-5 句总结）

## 核心内容
（结构化的合并要点）

## 来源笔记
- [[来源笔记1]]
- [[来源笔记2]]
```

**与 Karpathy 的区别**：Karpathy 每加一篇新资料自动更新全库（适合研究者）；这里采用手动触发（适合创作者），积累一段时间后集中整合。

### 1.5.5 `-check` 健康检查指令

**触发**：用户说 `-检查` 或 `-check`

**执行流程**：
1. 扫描全库文件列表
2. 输出报告：
   - 孤立笔记（没有任何 `[[链接]]` 指向或被指向）
   - 缺失 frontmatter 的笔记
   - 过期内容（超过 90 天未更新）
   - 重复主题（文件名或标签高度相似）
   - 空的收件箱待归类项
3. 给出建议：合并 / 归档 / 更新 / 删除

### 1.5.6 `-归类` 收件箱整理指令

**触发**：用户说 `-归类` 或 `-classify`

**执行流程**：
1. 扫描 `📎Clippings/` 中未归类的文件
2. 逐篇判断主题分类
3. 生成精简版笔记到 `📚主题笔记/`（按外部摘要模板）
4. 原始裁剪**保留在** `📎Clippings/` 不删除（作为原始档案）
5. 输出归类摘要

---

## 2. 开箱流程（5 Phase）

> **详细执行规范**见 `references/onboarding-phases.md`，执行开箱时**必须先读取该文件**。

### 概览

| Phase | 名称 | 关键动作 | 完成判定 |
|-------|------|---------|---------|
| 1 | 环境准备 + 语言检测 | 检测 Obsidian/CLI/Node；确认语言偏好 | 环境+语言均已确认 |
| 2 | Vault 接入 | 新建 or 接入已有知识库 | Vault 路径已确定 |
| 3 | 骨架初始化 + Skill 植入 | 创建文件夹骨架；植入 Skill 文件 | 骨架+Skill 就位 |
| 4 | 全局记忆 + 首条演示 | 写入 MEMORY.md；试跑一条指令 | 记忆已写入或跳过 |
| 5 | 扩展 Skill 推荐 | 推荐并安装扩展 Skill | 用户选择安装或跳过 |

### 核心规则
- 一次性输出检测结果+选项，减少来回追问
- 环境基线优先复用：`references/obsidian-环境检测与开箱基线.md`
- CLI 不可用时降级为文件系统模式，明确告知用户
- 自动化延迟触发：首篇 `-day` 后问日自动化，三篇笔记后问周自动化（详见 `references/automation-guide 自动化与通知方案.md`）

### Phase 3 完成后的骨架展示

当 Phase 3 完成后，向用户展示完整的笔记库结构：

```text
📦 你的笔记库骨架已搭建完成！
📦 Skill 文件已植入笔记库！位置：<vault>/obsidian-ai-notes skill配置/

<vault>/
├── 📅每日笔记/                    # -day 指令落点
│   └── YYYY-MM-DD.md
├── 📚主题笔记/                    # -note, -input 指令落点
│   ├── 综合/                      # -compile 编译产物
│   └── topic-name.md
├── 📆每周笔记/                    # -week 指令落点
│   └── YYYY-MM-DD-周复盘.md
├── 📋待跟踪任务/                  # -task 指令落点
│   └── task-name.md
├── 📝创作输出/                    # -output 指令落点（个人原创）
│   └── output-name.md
├── 🛠️tools/                      # -tool 指令落点
│   └── tool-name.md
├── 💡笔记工作流优化idea/           # -update 指令落点
│   └── idea-name.md
├── 📎Clippings/                   # 收件箱（-归类 扫描此处）
│   └── raw-clippings.md
└── obsidian-ai-notes skill配置/   # Skill 文件（可修改）
    ├── SKILL.md                   # 执行规范（用户自定义优先）
    ├── README.md                  # 使用说明
    ├── templates/                 # 笔记模板
    └── references/                # 参考文档

✅ 你可以：
• 用 -day/-note/-task 等指令快速创建笔记，AI 自动归类
• 像改笔记一样修改 SKILL.md，AI 会优先遵循你的自定义规则
• 直接修改 templates/ 下的模板，即时生效
• 所有笔记都是本地 Markdown，完全属于你
```

---

## 3. Vault 定位与跨空间执行

### Vault 路径检测（优先级）

```
1. MEMORY.md 配置的主 Vault 路径 → 使用（支持跨工作空间）
2. 当前工作空间含 .obsidian/ → 视为 Vault
3. 环境变量 OBSIDIAN_VAULT_PATH → 使用
4. 询问用户 → 记录到 MEMORY.md 全局复用
```

### 跨工作空间执行
当用户在非 Vault 工作空间使用指令：读取 MEMORY.md → 告知用户将操作主 Vault → 写入主 Vault。

### 工作空间 ≠ Vault 时
显式告知 → 提供选项：切换工作空间 / 配置路径 / 继续（不推荐）。

---

## 4. 语言检测与输出

### 检测优先级
1. 显式声明（"用中文" / "Use English"）
2. 系统上下文（IDENTITY.md / USER.md）
3. 对话语境分析
4. 默认中文

### 输出规则

| 检测语言 | 输出 | 文件夹名 |
|---------|------|---------|
| 中文 | 纯中文 | `📅每日笔记/` |
| 英文 | 纯英文 | `📅Daily/` |
| 其他 | 纯英文 | `📅Daily/` |

模板文件含双语注释（方便 AI 理解），实际输出只保留目标语言。

---

## 5. 文件夹结构

### 中文
```
<vault>/
├── 📅每日笔记/          # -day
├── 📚主题笔记/          # -note, -input
│   └── 综合/            # -compile 编译产物
├── 📆每周笔记/          # -week
├── 📋待跟踪任务/        # -task
├── 📝创作输出/          # -output（个人原创，不与收录混放）
├── 🛠️tools/            # -tool
├── 💡笔记工作流优化idea/ # -update
├── 📎Clippings/         # 收件箱 + 原始全文档案（-归类 扫描此处）
└── obsidian-ai-notes skill配置/
    ├── SKILL.md
    ├── templates/
    ├── references/
    └── README.md
```

### 英文
```
<vault>/
├── 📅Daily/         ├── 📚Topics/        ├── 📆Weekly/
│                    │   └── synthesis/
├── 📋Tasks/         ├── 📝Output/        ├── 🛠️Tools/
├── 💡Ideas/         ├── 📎Clippings/
└── obsidian-ai-notes skill配置/
```

---

## 6. 模板策略

### 优先级
```
1. obsidian-ai-notes skill配置/templates/（用户自定义）← 优先
2. 官方默认模板
```

用户修改模板后即时生效，更新 Skill 不会覆盖。

### 模板特点
- 文件内含双语注释（`<!-- ZH: ... | EN: ... -->`）
- 实际输出根据用户语言只保留单语
- 结构：必填模块 + 可选模块（默认仅输出必填）

---

## 7. 官方更新与合并机制

### 核心原则
- **用户配置永远不会被直接覆盖**
- 官方更新以独立文件夹 `obsidian-ai-notes 官方配置更新/` 送达
- 合并完成后自动清理

### 更新文件夹结构
```
obsidian-ai-notes 官方配置更新/
├── README.md       # 面向用户：为什么出现、怎么用
├── CHANGELOG.md    # 变更记录
├── version.txt     # 版本号
├── SKILL.md        # 官方最新 SKILL
├── templates/      # 官方最新模板
└── references/     # 官方最新参考文档
```

### AI 检测与提示
- **检测时机**：每次执行笔记指令时顺带检查
- **提示策略**：任务完成后提示（不打断当前指令），最多 3 次，超过不再主动提醒
- **用户可随时说「合并更新」手动触发**

### 合并策略

| 情况 | 策略 |
|------|------|
| 用户未改 + 官方有更新 | 直接替换 |
| 用户已改 + 官方没改 | 保留用户版本 |
| 双方都改了同区域 | 展示冲突，让用户选 |
| 新增文件 | 直接添加 |

### 合并后
1. 删除 `obsidian-ai-notes 官方配置更新/` 文件夹
2. 更新 SKILL.md 头部版本号
3. 输出合并摘要

### 多次更新堆叠
覆盖更新文件夹为最新版（不堆叠），CHANGELOG 保留完整历史，重置提醒次数。

---

## 附录：English Summary

**obsidian-ai-notes** — AI-powered Obsidian workflow Skill for Chinese users with English compatibility.

- 8 commands: `-day`, `-note`, `-week`, `-task`, `-tool`, `-output`, `-input`, `-update`
- 5-phase setup with CLI fallback
- Language auto-detection → single-language output
- User config never overwritten by updates
- Extensible via additional Skills

See full Chinese documentation above for execution logic.
