# Platform Deployment Guide
## 多平台部署指南（双语版）

---

本文档说明如何在不同 AI 平台上部署和使用 Resume Tailor Skill。
This guide explains how to deploy and use Resume Tailor Skill on different AI platforms.

---

## 项目文件总览 / File Overview

```
resume-tailor-skill/
├── CLAUDE.md                              ← Claude Code 自动读取
├── AGENTS.md                              ← 跨 AI 工具通用指令
├── .claude/skills/resume-tailor/
│   └── SKILL.md                           ← Claude Code 技能文件
├── Resume Tailor Skill.md                 ← 通用完整版执行规则
├── Invocation Prompt Template.md          ← 调用模板
├── README.md                              ← 用户手册
├── source/                                ← 真实简历材料
├── templates/                             ← 简历模板
└── assets/                                ← 照片和视觉资源
```

### 不同平台使用不同文件 / Which files for which platform

| 平台 / Platform | 使用的文件 / Files Used |
|---|---|
| Claude Code | `CLAUDE.md` + `.claude/skills/resume-tailor/SKILL.md` |
| ChatGPT (Custom GPT) | `Resume Tailor Skill.md` |
| Gemini (Gem) | `Resume Tailor Skill.md` |
| Claude Project (Web) | `Resume Tailor Skill.md` |
| Codex CLI / Cursor / Aider | `AGENTS.md` |
| 其他 Agent 平台 / Others | `Resume Tailor Skill.md` |

---

## 1. Claude Code

**最推荐的方式。** 自动加载，支持斜杠命令。

### 部署步骤 / Deployment

```bash
# 1. 克隆或下载项目
git clone https://github.com/AubynWang/resume-tailor-skill.git

# 2. 把你的材料放入对应目录
#    source/    ← 旧简历、母版简历、项目说明
#    templates/ ← 中文模板、英文模板
#    assets/    ← 照片

# 3. 进入项目目录并启动 Claude Code
cd resume-tailor-skill
claude
```

### 使用 / Usage

```
# 方式 A：斜杠命令
/resume-tailor

# 方式 B：直接对话
请根据以下 JD 帮我定制简历：[粘贴 JD]
```

### 验证 / Verification

```
/skills
# 确认列表中出现 resume-tailor
```

### 工作原理 / How it works
- Claude Code 启动时自动读取 `CLAUDE.md`（项目上下文）
- 用户调用 `/resume-tailor` 时追加读取 `SKILL.md`（执行规则）
- 两个文件配合工作，无需手动粘贴任何内容

---

## 2. ChatGPT — Custom GPT

适合想要创建一个可复用 GPT 的用户。

### 部署步骤 / Deployment

1. 打开 [ChatGPT](https://chat.openai.com) → 左侧菜单 → **Explore GPTs** → **Create**
2. 在 **Instructions** 栏中，粘贴 `Resume Tailor Skill.md` 的完整内容
3. 在 **Knowledge** 栏中，上传以下文件：
   - `Invocation Prompt Template.md`
   - 你的模板文件（来自 `templates/`）
4. 设置 GPT 名称，例如：`Resume Tailor`
5. 设置描述，例如：`Tailor truthful resumes to job descriptions`
6. 保存并发布（或设为私有）

### 使用 / Usage

1. 打开你创建的 GPT
2. 上传你的简历材料（来自 `source/`）和照片（来自 `assets/`）
3. 在对话中发送 JD 和要求
4. 获取输出

### 注意事项 / Notes
- ChatGPT 的 Knowledge 文件有大小限制
- 每次对话需要重新上传 `source/` 中的材料（除非放在 Knowledge 中）
- Instructions 栏有字符限制，如果 `Resume Tailor Skill.md` 过长，可适当精简

---

## 3. Gemini — Gem

适合 Google 生态用户。

### 部署步骤 / Deployment

1. 打开 [Gemini](https://gemini.google.com) → **Gem Manager** → **Create Gem**
2. 在 **Instructions** 中粘贴 `Resume Tailor Skill.md` 的完整内容
3. 设置 Gem 名称和描述
4. 保存

### 使用 / Usage

1. 打开你创建的 Gem
2. 上传简历材料和模板
3. 在对话中发送 JD 和要求
4. 获取输出

### 注意事项 / Notes
- Gemini Gem 的 Instructions 字符限制可能较严格
- 如需精简，优先保留 §3（Core Behavioral Principles）、§11（Section Rewriting Rules）、§15（Default Output Policy）、§21（Non-Negotiable Constraints）
- 文件上传能力取决于 Gemini 版本

---

## 4. Claude Project（Web 版）

适合在 Claude 网页端使用项目功能的用户。

### 部署步骤 / Deployment

1. 打开 [Claude](https://claude.ai) → **Projects** → **New Project**
2. 在 **Project Instructions** 中粘贴 `Resume Tailor Skill.md` 的完整内容
3. 在 **Project Knowledge** 中上传：
   - `Invocation Prompt Template.md`
   - 模板文件（来自 `templates/`）
   - 简历材料（来自 `source/`）
   - 照片（来自 `assets/`）
4. 命名项目并保存

### 使用 / Usage

1. 进入项目
2. 在对话中发送 JD 和要求
3. 获取输出

### 注意事项 / Notes
- Project Knowledge 中的文件在每次对话中自动可用
- 比 ChatGPT 更方便，不需要每次重新上传材料
- Instructions 字符限制较宽裕

---

## 5. Codex CLI / Cursor / Aider / 其他 AI 编码工具

这些工具会自动读取项目根目录的 `AGENTS.md`。

### 部署步骤 / Deployment

```bash
# 确保 AGENTS.md 在项目根目录
cd resume-tailor-skill
ls AGENTS.md  # 确认文件存在
```

### 使用 / Usage

启动对应工具后，直接在对话中描述任务即可。
工具会自动读取 `AGENTS.md` 作为项目上下文。

---

## 6. 其他 Agent 平台（通用方式）

对于不支持自动读取配置文件的平台：

### 部署步骤 / Deployment

1. 将 `Resume Tailor Skill.md` 的内容粘贴到系统提示词（System Prompt）中
2. 或上传为知识文件（Knowledge File）
3. 将材料文件上传到对话中

### 使用 / Usage

在对话中发送 JD 和要求即可。

---

## 快速选择指南 / Quick Selection Guide

| 你的情况 / Your Situation | 推荐平台 / Recommended |
|---|---|
| 有 Claude Code，想要最佳体验 | **Claude Code** |
| 习惯用 ChatGPT，想做可复用 GPT | **ChatGPT Custom GPT** |
| 习惯用 Claude 网页版 | **Claude Project** |
| 习惯用 Gemini | **Gemini Gem** |
| 用 Cursor / Codex CLI 写代码 | **AGENTS.md 自动加载** |
| 临时使用，不想配置 | **任意平台 + 手动粘贴规则** |

---

## 常见问题 / FAQ

### Q: 不同平台的输出效果一样吗？
核心规则一致，但不同 LLM 的表达风格和排版细节可能略有差异。
建议无论使用哪个平台，都在拿到 HTML 后做一次预览和打印检查。

### Q: 我可以同时在多个平台部署吗？
可以。所有平台共享同一套材料（`source/`、`templates/`、`assets/`），
只是读取的规则文件不同。

### Q: 更新了规则后需要重新部署吗？
- Claude Code：修改文件后下次启动自动生效
- ChatGPT GPT：需要更新 Instructions
- Claude Project：需要更新 Project Instructions
- Gemini Gem：需要更新 Instructions

---