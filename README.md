# Resume Tailor Skill README
## 用户手册 / User Manual（双语版）

---

## 1. 本 Skill 是做什么的？
## 1. What does this Skill do?

**中文**
Resume Tailor Skill 是一个用于**定制化生成和润色求职简历**的 Skill 包。
它适用于常规求职场景，尤其适合校招、实习、初级岗位和标准正式投递场景。

使用时，你通常只需要：

1. 放入你的旧简历、母版简历、模板、照片或补充材料
2. 在对话中提供目标岗位 JD
3. 告诉 Agent 你是否有额外要求，例如语言、篇幅、是否保留照片等

Skill 会基于主规则自动完成：

- 内容筛选与重组
- 岗位匹配优化
- Summary / 个人简介定制
- 中英文改写
- 一页 A4 控制
- 模板化排版
- HTML 可审阅成品输出

它的默认目标不是只给你一段建议文字，而是尽量直接给你一份**可以打开、预览、审阅、打印检查并继续修改的简历成品**。

**English**
Resume Tailor Skill is a skill package for **customizing and refining job application resumes**.
It is designed for standard job-seeking scenarios, especially campus recruitment, internships, entry-level roles, and formal applications.

In most cases, you only need to:

1. Put in your old resume, master resume, templates, photo, or supporting materials
2. Provide the target job description in chat
3. Tell the Agent any extra requirements, such as language, length, or whether to keep the photo

The Skill will then automatically help with:

- content selection and restructuring
- job-targeted tailoring
- Summary / Profile rewriting
- Chinese-English resume adaptation
- one-page A4 control
- template-based layout
- HTML review-ready output

Its default goal is not just to give you text suggestions, but to deliver a **resume draft that can be opened, reviewed, previewed, print-checked, and further revised**.

---

## 2. 这个 Skill 包里通常有什么？
## 2. What is usually included in this Skill package?

**中文**
一个标准 Skill 包通常包含以下内容：

| 文件 / 目录 | 作用 |
|---|---|
| `Resume Tailor Skill.md` | 主规则文档，定义 Agent 实际如何执行（通用版） |
| `Invocation Prompt Template.md` | 调用辅助文档，帮助你更方便地发起任务 |
| `README.md` | 用户手册（本文件） |
| `CLAUDE.md` | Claude Code 项目指令，启动时自动读取 |
| `AGENTS.md` | 跨 AI 工具通用指令（兼容 Codex CLI、Cursor 等） |
| `.claude/skills/resume-tailor/SKILL.md` | Claude Code 专用技能执行规则 |
| `source/` | 放真实内容材料，例如旧简历、母版简历、项目说明 |
| `templates/` | 放排版模板，例如中文模板、英文模板、HTML 模板 |
| `assets/` | 放照片、图标等辅助资源 |

**补充说明**
实际执行时，Agent 会优先根据你的说明和文件内容理解每份材料的用途，而不会只根据文件放在哪个目录里来机械判断。
因此，即使文件临时放错位置，通常也仍然可以被正确识别和使用。

> 注意：目录名和文件名主要用于组织，不一定是唯一标准。
> Agent 会优先根据你的说明、文件内容和结构来判断用途。

**English**
A standard Skill package usually includes:

| File / Folder | Purpose |
|---|---|
| `Resume Tailor Skill.md` | Main rule document defining how the Agent works (universal version) |
| `Invocation Prompt Template.md` | Helper document for triggering or structuring tasks |
| `README.md` | User manual (this file) |
| `CLAUDE.md` | Claude Code project instructions, auto-loaded on startup |
| `AGENTS.md` | Cross-tool compatible instructions (works with Codex CLI, Cursor, etc.) |
| `.claude/skills/resume-tailor/SKILL.md` | Claude Code skill execution rules |
| `source/` | Real content files such as old resumes, master resumes, and project notes |
| `templates/` | Layout files such as Chinese templates, English templates, or HTML resume templates |
| `assets/` | Photos, icons, and other supporting visual resources |

**Additional note**
During execution, the Agent mainly identifies each file by your instructions and the content itself, rather than relying only on which folder it is placed in.
So even if a file is temporarily placed in the wrong folder, it can usually still be identified and used correctly.

> Note: folder names and file names are mainly for organization and are not rigid requirements.
> The Agent should primarily identify file roles based on your instructions, the content itself, and the file structure.

---

## 3. 使用前你需要准备什么？
## 3. What should you prepare before using it?

**中文**
建议你至少准备以下材料：

### 必备
- 一份真实的旧简历或母版简历
- 一个目标岗位 JD

### 建议提供
- 中文模板
- 英文模板
- 照片
- 项目 / 实习 / 教育 / 技能补充材料
- 你希望保留、删除或强化的说明

一般来说，材料越完整，输出结果越稳定、越贴合岗位。

**English**
It is recommended that you prepare at least the following:

### Required
- one real old resume or master resume
- one target job description

### Recommended
- a Chinese template
- an English template
- a photo
- supporting materials for projects, internships, education, or skills
- notes on what you want to keep, remove, or emphasize

In general, the more complete your materials are, the more stable and relevant the final result will be.

---

## 4. 应该怎么使用？
## 4. How should you use it?

**中文**

### 方式一：通用方式（适用于 ChatGPT / Gemini / 其他 Agent 平台）

#### 第一步：放入你的材料
你可以把自己的文件放入对应目录中：

- 真实内容材料放入 `source/`
- 模板放入 `templates/`
- 照片等资源放入 `assets/`

即使临时放错目录，通常也不用太担心，Agent 会尽量根据内容识别。

#### 第二步：在对话中发送 JD
在聊天中直接发给 Agent 目标岗位 JD。
同时你也可以补充说明，例如：

- 输出中文还是英文
- 是否必须一页 A4
- 是否保留照片
- 是否直接出最终版
- 哪些经历要强化
- 哪些内容需要删减
- 是否只要文案，不要排版版

#### 第三步：查看输出结果
如果你没有特别说明输出格式，Skill 默认会生成：

- **HTML 可审阅成品**

若未提供可用模板，Skill 会优先生成结构清晰、正式、可打印检查的默认 HTML 版本。

你可以直接打开它，先预览、审阅和打印检查，再决定是否继续微调。

---

### 方式二：Claude Code（推荐）

如果你使用 Claude Code，部署和使用更加简单：

#### 第一步：进入项目目录并启动
```bash
cd resume-tailor-skill
claude
```
Claude Code 会自动读取 `CLAUDE.md`，立刻理解整个项目上下文。

#### 第二步：调用技能
```
/resume-tailor
```
或者直接在对话中描述任务，例如：
```
请根据以下 JD 帮我定制简历：[粘贴 JD]
```

#### 第三步：查看输出
与通用方式相同，默认输出 HTML 可审阅成品。

> 更多平台的部署方式请参考 `PLATFORM_DEPLOYMENT_GUIDE.md`。

**English**

### Option A: Universal (for ChatGPT / Gemini / other Agent platforms)

#### Step 1: Put in your materials
You may place your files into the suggested folders:

- real content materials in `source/`
- templates in `templates/`
- photos or visual assets in `assets/`

Even if some files are placed in the wrong folder, the Agent will usually still try to identify them by content.

#### Step 2: Send the job description in chat
Provide the target job description directly in the conversation.
You may also add instructions such as:

- whether the output should be in Chinese or English
- whether it must stay within one A4 page
- whether to keep the photo
- whether to directly generate the HTML review-ready draft
- which experiences should be emphasized
- which parts should be reduced or removed
- whether you only want the text-only draft instead of the HTML review-ready draft

#### Step 3: Review the output
If you do not specify a different format, the Skill will by default generate:

- **an HTML review-ready resume draft**

If no usable template is provided, the Skill will prioritize generating a clear, formal, and print-checkable default HTML version.

You can open it directly, review it, preview it, and print-check it before asking for further revisions.

---

### Option B: Claude Code (Recommended)

If you use Claude Code, deployment and usage are simpler:

#### Step 1: Enter the project directory and start
```bash
cd resume-tailor-skill
claude
```
Claude Code will auto-load `CLAUDE.md` and immediately understand the full project context.

#### Step 2: Invoke the skill
```
/resume-tailor
```
Or simply describe the task in chat:
```
Please tailor my resume to this JD: [paste JD]
```

#### Step 3: Review the output
Same as the universal method — default output is an HTML review-ready draft.

> For deployment on other platforms, see `PLATFORM_DEPLOYMENT_GUIDE.md`.

---

## 5. 默认输出为什么是 HTML 可审阅成品？
## 5. Why is the default output an HTML review-ready draft?

**中文**
默认输出 HTML，不只是为了"展示"，更是为了方便你在正式导出 PDF 之前进行检查。

默认 HTML 成品通常具备以下用途：

- 直接在不同智能体界面中打开
- 预览整体版式
- 审阅内容和信息密度
- 使用打印功能检查输出效果
- 在正式文件生成前及时发现问题并沟通修改

这样设计的原因是：
不同浏览器、不同电脑系统、不同打印链路在导出 PDF 时，可能出现轻微版式差异，例如：

- 页边距变化
- 字体显示差异
- 行距和宽度变化
- 换页点变化
- 照片轻微偏移
- 局部内容压缩或溢出

因此，建议你在拿到 HTML 版本后，先做一次：

1. 页面预览
2. 打印预览
3. 版式检查

确认没有明显问题后，再作为正式投递版本使用。

**English**
The default HTML output is not only for display. It is mainly designed to let you inspect the resume before exporting it as a final PDF.

A default HTML resume draft is useful because it allows you to:

- open it directly in different Agent interfaces
- preview the overall layout
- review content density and structure
- use print preview to inspect the output
- catch layout issues before the final file is exported

This matters because different browsers, operating systems, and print pipelines may introduce small layout differences when exporting to PDF, such as:

- margin changes
- font rendering differences
- line-height or width differences
- page break shifts
- slight photo displacement
- local compression or overflow

For this reason, it is recommended that after receiving the HTML version, you first do:

1. page preview
2. print preview
3. layout checking

Then confirm or request revisions before using it as the final application version.

---

## 6. 你可以怎么对 Agent 下指令？
## 6. What can you say to the Agent?

**中文**
你可以直接使用类似下面的话：

- 按这个 JD 改简历
- 帮我做这个岗位版本
- 生成英文版简历
- 帮我压缩到一页 A4
- 不要照片版
- 保留项目经历，弱化活动经历
- 强化数据分析相关内容
- 先给我文案版，不用排版
- 直接出最终版
- 按中文模板重做

你不需要一次性把所有要求都说全。
如果没有特别说明，Skill 会按默认规则继续执行。

**English**
You can directly use instructions such as:

- Tailor my resume to this JD
- Make a version for this role
- Generate an English version
- Compress it to one A4 page
- Remove the photo
- Keep project experience and reduce activity experience
- Strengthen the data analysis part
- Give me the text-only draft first
- Directly generate the HTML review-ready draft
- Redo it using the Chinese template

You do not need to specify every rule all at once.
If nothing special is stated, the Skill will proceed using its default logic.

---

## 7. Skill 默认会替你做哪些事情？
## 7. What will the Skill normally do for you?

**中文**
在正常情况下，Skill 会自动完成以下任务：

- 识别真实内容材料
- 识别模板和照片资源
- 解析目标岗位 JD
- 判断哪些内容该保留、强化、压缩或删除
- 重写 Summary / 个人简介
- 润色教育、项目、实习和技能表达
- 控制整体为正式、清晰的一页 A4
- 输出可预览、可打印检查的 HTML 成品

**English**
Under normal use, the Skill will automatically help with:

- identifying your real content materials
- identifying templates and photo assets
- parsing the target job description
- deciding what to keep, emphasize, compress, or remove
- rewriting the Summary / Profile
- refining education, project, internship, and skills wording
- keeping the resume formal, clear, and within one A4 page
- generating an HTML draft that supports review and print checking

---

## 8. 你还可以额外指定什么？
## 8. What else can you additionally specify?

**中文**
你可以进一步说明：

- 输出语言：中文 / 英文 / 双语
- 输出形式：HTML 成品 / 文案版
- 是否保留照片
- 是否严格控制为一页
- 哪些内容必须保留
- 哪些内容要删除
- 哪些项目或技能要重点强调
- 你偏好的模板风格
- 你希望更正式、简洁或更自然的表达方式

**English**
You can further specify:

- output language: Chinese / English / bilingual
- output format: HTML review-ready draft / text-only draft
- whether to keep the photo
- whether to strictly stay on one page
- which parts must be kept
- which parts should be removed
- which projects or skills should be highlighted
- which template style you prefer
- whether you want the wording to be more formal, concise, or natural

---

## 9. 使用建议
## 9. Practical tips

**中文**

### 9.1 尽量提供完整、真实的材料
Skill 会基于你的真实信息做重组与优化，而不是代替你编造经历。

### 9.2 JD 尽量给完整文本
相比只提供岗位名称，直接提供完整 JD 往往能得到更准确的定制结果。

### 9.3 有明确偏好就直接说明
例如：

- 教育经历放前面
- 不要照片
- 强化数据分析
- 弱化与岗位不相关的经历
- 英文表达尽量自然简洁

### 9.4 在正式导出前先做预览和打印检查
建议重点检查：

- 是否超页
- 是否换页异常
- 是否有内容溢出
- 字体是否正常
- 照片比例是否合适
- 页边距是否稳定
- 整体是否过于拥挤

**English**

### 9.1 Try to provide complete and truthful materials
The Skill works by restructuring and refining your real information, not by inventing experiences for you.

### 9.2 Provide the full JD whenever possible
A full job description usually leads to more accurate tailoring than only providing a job title.

### 9.3 State clear preferences directly
For example:

- put education first
- remove the photo
- emphasize data analysis
- reduce less relevant experiences
- keep the English wording concise and natural

### 9.4 Do preview and print checks before final export
It is recommended to check:

- whether it exceeds one page
- whether page breaks look wrong
- whether any content overflows
- whether fonts display correctly
- whether the photo ratio looks right
- whether margins are stable
- whether the overall layout feels too crowded

---

## 10. 使用时需要注意什么？
## 10. Important notes

**中文**

### 10.1 README 不是执行规则文档
README 是给用户看的使用手册。
真正决定 Agent 如何执行的文档取决于你使用的平台：

| 平台 | 执行规则文档 |
|---|---|
| Claude Code | `CLAUDE.md` + `.claude/skills/resume-tailor/SKILL.md` |
| ChatGPT / Gemini / 其他 | `Resume Tailor Skill.md`（通用完整版） |
| Codex CLI / Cursor / 其他 AI 编码工具 | `AGENTS.md` |

### 10.2 文件名不是死板要求
你不一定必须使用完全相同的文件名。
只要材料内容明确，通常都可以被识别。

### 10.3 Skill 默认要求真实性
Skill 不会默认虚构经历、夸大职责或伪造结果。
如果信息不足，通常会优先保守处理。

### 10.4 默认规则主要适用于标准求职简历
如果你要做的是学术 CV、研究型长简历、作品集风格简历或高年资管理岗简历，建议额外说明，因为默认版式可能不完全适配。

**English**

### 10.1 The README is not the execution rule document
The README is a user manual.
The document that actually defines how the Agent works depends on your platform:

| Platform | Execution Rule Document |
|---|---|
| Claude Code | `CLAUDE.md` + `.claude/skills/resume-tailor/SKILL.md` |
| ChatGPT / Gemini / Others | `Resume Tailor Skill.md` (universal full version) |
| Codex CLI / Cursor / Other AI coding tools | `AGENTS.md` |

### 10.2 File names are not rigid requirements
You do not have to use exactly the same file names.
As long as the material itself is clear enough, it can usually still be identified.

### 10.3 The Skill assumes truthfulness by default
It does not normally invent experiences, exaggerate responsibilities, or fabricate results.
If information is incomplete, it will usually proceed conservatively.

### 10.4 The default logic is mainly for standard job resumes
If you are preparing an academic CV, research CV, portfolio-style resume, or senior management resume, you should explicitly say so, because the default layout assumptions may not fully fit.

---

## 11. 常见问题
## 11. Frequently asked questions

**中文**

### Q1：我只有一份旧简历，可以用吗？
可以。
只要它是真实内容来源，Skill 就可以基于它进行定制和润色。

### Q2：我没有英文模板怎么办？
通常仍然可以继续处理。
Skill 会优先保证结构清晰、内容真实和版式稳定，并尽量生成可用版本。

### Q3：我只想先看文案，不想看成品，可以吗？
可以。
你只要明确说"先给我文案版，不用排版"即可。

### Q4：JD 一定要做成文件上传吗？
不需要。
直接在对话里发送 JD 就可以。

### Q5：为什么不是直接给 PDF？
因为 HTML 更适合先做可视化审阅和打印检查。
在正式导出 PDF 之前，HTML 更方便你发现问题并及时沟通修改。

### Q6：Claude Code 和通用方式有什么区别？
Claude Code 可以自动读取项目规则并通过斜杠命令调用技能，无需手动粘贴规则。
通用方式需要你手动将 `Resume Tailor Skill.md` 上传或粘贴到对话中。
两者的执行规则和输出效果一致。

**English**

### Q1: I only have one old resume. Can I still use this Skill?
Yes.
As long as it is a truthful content source, the Skill can use it for tailoring and refinement.

### Q2: What if I do not have an English template?
The process can usually still continue.
The Skill will prioritize clear structure, truthful content, and stable formatting, and try to produce a usable fallback version.

### Q3: Can I ask for only the text-only draft first instead of the HTML review-ready draft?
Yes.
Just clearly say that you want a text-only draft first and do not need the formatted output yet.

### Q4: Do I have to upload the JD as a file?
No.
You can simply send the JD directly in the conversation.

### Q5: Why not directly output PDF?
Because HTML is better for visual review and print checking first.
Before final PDF export, HTML makes it easier to catch issues and request revisions in time.

### Q6: What is the difference between Claude Code and the universal method?
Claude Code auto-loads project rules and supports slash command invocation, so you don't need to manually paste rules.
The universal method requires you to upload or paste `Resume Tailor Skill.md` into the conversation.
Both methods follow the same execution rules and produce the same output quality.

---

## 12. 推荐使用流程
## 12. Recommended workflow

**中文**
推荐你按下面顺序使用：

1. 放入旧简历或母版简历
2. 放入模板和照片
3. 在对话中发送目标岗位 JD
4. 说明你的额外要求
5. 获取 HTML 可审阅成品
6. 先做预览和打印检查
7. 如有问题，及时提出修改
8. 确认后用于正式投递或导出 PDF

**English**
A recommended workflow is:

1. Put in your old resume or master resume
2. Add templates and photo
3. Send the target JD in chat
4. State any extra requirements
5. Receive the HTML review-ready draft
6. Do preview and print checks first
7. Request revisions if needed
8. Confirm it before formal submission or PDF export

---

## 13. 进一步了解 / Further reading
## 13. Further reading

**中文**

| 需求 | 参考文档 |
|---|---|
| 了解执行规则 | `Resume Tailor Skill.md` |
| 标准化发起任务 | `Invocation Prompt Template.md` |
| Claude Code 部署 | `CLAUDE.md` + `.claude/skills/resume-tailor/SKILL.md` |
| 多平台部署指南 | `PLATFORM_DEPLOYMENT_GUIDE.md` |
| 设计文档 | `Resume Tailor Skill PRD v1.0 (CN-EN).md` |

如果你只是想快速使用本 Skill，阅读本 README 即可。

**English**

| Need | Reference |
|---|---|
| Understand execution rules | `Resume Tailor Skill.md` |
| Standardized task invocation | `Invocation Prompt Template.md` |
| Claude Code deployment | `CLAUDE.md` + `.claude/skills/resume-tailor/SKILL.md` |
| Multi-platform deployment guide | `PLATFORM_DEPLOYMENT_GUIDE.md` |
| Design document | `Resume Tailor Skill PRD v1.0 (CN-EN).md` |

If you only want to use the Skill quickly, this README is enough.

---