# Resume Tailor Skill PRD v1.0
## 产品需求文档 / Product Requirements Document（CN-EN）

---

## 1. 项目名称 / Project Name

**中文**  
Resume Tailor Skill

**English**  
Resume Tailor Skill

---

## 2. 项目定位 / Product Positioning

**中文**  
Resume Tailor Skill 是一个面向求职简历定制场景的规则型 Skill 包。  
它的目标不是只做简历点评或提供零散建议，而是尽量将用户提供的真实材料转化为**岗位定制、结构清晰、表达专业、可继续审阅和打印检查的简历成品或文案草稿**。

它主要适用于：

- 校招
- 实习申请
- 初级岗位求职
- 标准正式投递场景
- 中英文简历改写与适配

**English**  
Resume Tailor Skill is a rule-based skill package designed for job-resume tailoring scenarios.  
Its purpose is not merely to comment on resumes or provide scattered suggestions, but to transform truthful user-provided materials into a **role-targeted, clearly structured, professionally worded, review-ready resume draft or text draft**.

It is mainly intended for:

- campus recruitment
- internship applications
- entry-level job applications
- standard formal submission scenarios
- Chinese-English resume adaptation and rewriting

---

## 3. 项目目标 / Product Goals

**中文**  
本项目的主要目标包括：

1. 基于用户提供的真实材料完成岗位定制化简历生成  
2. 支持旧简历、母版简历、模板、照片和补充材料的综合利用  
3. 能根据 JD 自动完成内容筛选、重组、压缩和重点强化  
4. 默认输出 HTML 可审阅成品，便于用户预览和打印检查  
5. 在用户仅需文案时输出 text-only draft  
6. 保持内容真实性，不虚构、不夸大、不伪造  
7. 兼顾一页 A4 控制、正式风格和可复用性

**English**  
The major goals of this project are:

1. generate role-targeted resumes based on truthful user-provided materials  
2. support integrated use of old resumes, master resumes, templates, photos, and supplementary materials  
3. automatically perform content filtering, restructuring, compression, and emphasis based on the JD  
4. default to an HTML review-ready draft for preview and print checking  
5. output a text-only draft when the user only wants content optimization  
6. preserve truthfulness and avoid fabrication or exaggeration  
7. balance one-page A4 control, professional style, and reusability

---

## 4. 非目标 / Non-Goals

**中文**  
本项目默认不以以下目标为核心：

- 虚构用户经历或结果
- 自动生成高风险不实履历
- 面向学术 CV、研究型长简历或作品集型设计简历的深度专用支持
- 替代用户做正式法律声明
- 保证所有浏览器或系统下导出 PDF 时绝对零差异

**English**  
The project is not primarily intended to:

- fabricate user experience or results
- generate misleading or high-risk false resume content
- deeply specialize in academic CVs, long research CVs, or design portfolio resumes by default
- replace the user in making formal legal declarations
- guarantee perfectly identical PDF export behavior across all browsers and systems

---

## 5. 目标用户 / Target Users

**中文**  
目标用户主要包括：

- 有旧简历或母版简历，希望快速定制岗位版本的求职者
- 需要中英文简历改写的人
- 希望控制在一页 A4 且用于正式投递的人
- 希望通过模板快速生成 HTML 可审阅成品的人
- 希望在不同 Agent 或工作流中复用同一套简历定制规则的人

**English**  
Target users mainly include:

- job seekers who already have an old resume or master resume and want a targeted version quickly
- users who need Chinese-English resume rewriting
- users who want a formal one-page A4 application resume
- users who want an HTML review-ready draft generated from templates
- users who want to reuse a stable resume-tailoring rule set across different Agents or workflows

---

## 6. 核心设计原则 / Core Design Principles

**中文**  
本项目遵循以下核心原则：

- 真实性优先
- 用户指令优先
- 岗位相关性优先
- 文件角色识别应基于内容，不应机械依赖目录名
- 模板是辅助约束，不是绝对主导
- 默认输出应便于预览、审阅和打印检查
- 执行规则应高密度、可复用、低歧义

**English**  
This project follows these core principles:

- truthfulness first
- user instruction first in operation
- job relevance first in tailoring
- file role identification should be content-based rather than mechanically folder-based
- templates are supporting constraints, not absolute authority
- default outputs should support preview, review, and print checking
- execution rules should be high-density, reusable, and low-ambiguity

---

## 7. 典型输入 / Typical Inputs

**中文**  
系统可能接收到以下一种或多种输入：

- 旧简历
- 母版简历
- 半成品简历
- 中文模板
- 英文模板
- HTML 模板
- 照片
- 图标或其他视觉资源
- 项目说明
- 实习说明
- 教育信息
- 技能清单
- 证书信息
- 岗位 JD
- 用户额外偏好说明

**English**  
The system may receive one or more of the following inputs:

- old resumes
- master resumes
- partial resume drafts
- Chinese templates
- English templates
- HTML templates
- photos
- icons or other visual assets
- project descriptions
- internship descriptions
- education information
- skills lists
- certificate information
- job descriptions
- additional user preference instructions

---

## 8. 文件角色识别需求 / File Role Identification Requirements

**中文**  
Skill 不应只根据目录名来判断文件用途。  
它应结合以下信号综合判断：

- 用户说明
- 文件内容
- 文件名线索
- 目录结构
- 版式和格式线索
- 文件类型与资源特征

可能识别出的角色包括：

- `source`
- `template`
- `dual-role`
- `assets`
- `unknown-but-usable`

即使文件临时放错目录，只要内容可识别，系统仍应尽量正确使用。

**English**  
The Skill should not identify file roles only by folder names.  
It should combine the following signals:

- user instructions
- file content
- file naming cues
- directory structure
- formatting and layout cues
- file type and asset characteristics

Possible file roles include:

- `source`
- `template`
- `dual-role`
- `assets`
- `unknown-but-usable`

Even if a file is temporarily placed in the wrong folder, the system should still try to use it correctly when the content is recognizable.

---

## 9. 核心功能需求 / Core Functional Requirements

**中文**

### 9.1 内容识别与提取
- 能识别真实内容材料
- 能提取教育、项目、实习、工作和技能信息
- 能在多个来源之间去重与合并
- 对冲突信息采取保守处理

### 9.2 JD 解析与岗位适配
- 能识别岗位职责、技能要求、偏好条件和关键词
- 能根据 JD 调整内容保留、压缩、强化和排序
- 能重写更贴合岗位的 Summary / 个人简介

### 9.3 模板与版式处理
- 能识别模板结构、语言和布局习惯
- 能在模板适用时进行复用
- 模板不可用时能生成默认结构化版本
- 输出结果应适合预览和打印检查

### 9.4 输出形态控制
- 默认输出 HTML 可审阅成品
- 用户要求仅文案时输出 text-only draft
- 能控制正式、清晰、简洁的表达风格
- 能在适用场景下尽量控制为一页 A4

**English**

### 9.1 Content identification and extraction
- identify truthful content materials
- extract education, project, internship, work, and skills information
- deduplicate and merge across multiple sources
- resolve conflicting information conservatively

### 9.2 JD parsing and role adaptation
- identify job responsibilities, required skills, preferred qualifications, and keywords
- adjust content retention, compression, emphasis, and ordering based on the JD
- rewrite a more role-targeted Summary / Profile

### 9.3 Template and layout handling
- identify template structure, language, and layout habits
- reuse templates when appropriate
- generate a default structured version when no usable template exists
- make outputs suitable for preview and print checking

### 9.4 Output form control
- default to an HTML review-ready draft
- output a text-only draft when the user asks for wording only
- maintain a formal, clear, and concise style
- keep the resume within one A4 page when appropriate

---

## 10. 默认输出策略 / Default Output Strategy

**中文**  
当用户要求“直接生成”“出最终版”“做成正式可看版本”或未明确反对格式化输出时，系统默认输出：

- **HTML 可审阅成品**

当用户明确表示“先给文案”“不要排版”“只改内容”时，系统默认输出：

- **text-only draft**

**English**  
When the user asks to “generate directly,” “make the final version,” “produce a finished resume,” or does not explicitly reject formatted output, the default should be:

- **an HTML review-ready draft**

When the user clearly asks for wording only, no formatting yet, or content optimization first, the default should be:

- **a text-only draft**

---

## 11. 为什么默认输出 HTML / Why HTML Is the Default

**中文**  
默认输出 HTML 的原因不是只为了展示，而是为了方便：

- 页面预览
- 结构审阅
- 打印预览
- 输出检查
- 在正式导出 PDF 之前发现版式问题

由于不同浏览器、系统和打印链路可能产生轻微差异，HTML 更适合作为用户确认前的中间成品。

**English**  
HTML is the default not just for display, but because it supports:

- page preview
- structural review
- print preview
- output checking
- catching layout issues before final PDF export

Since different browsers, systems, and print pipelines may introduce slight differences, HTML is more suitable as a review-ready intermediate deliverable.

---

## 12. 约束条件 / Constraints

**中文**  
系统必须遵守以下约束：

- 不虚构内容
- 不夸大未经支持的结果
- 不捏造技能或证书
- 不将模板占位符当作用户真实信息
- 不为了模板而牺牲可读性和真实性
- 不在信息不足时进行高风险推断

**English**  
The system must obey the following constraints:

- do not fabricate content
- do not exaggerate unsupported results
- do not invent skills or certifications
- do not treat template placeholders as user truth
- do not sacrifice readability and truthfulness for template fidelity
- do not make high-risk inferences when information is insufficient

---

## 13. 典型使用流程 / Typical Workflow

**中文**

1. 用户提供旧简历、母版简历、模板、照片等材料  
2. 用户在对话中发送岗位 JD  
3. 系统识别文件角色和真实内容  
4. 系统根据 JD 完成内容筛选、重写和重组  
5. 系统在模板可用时进行版式复用  
6. 默认输出 HTML 可审阅成品  
7. 用户预览、审阅和打印检查  
8. 用户提出进一步修改意见  

**English**

1. the user provides old resumes, master resumes, templates, photos, and other materials  
2. the user sends the target JD in chat  
3. the system identifies file roles and truthful content  
4. the system filters, rewrites, and restructures content based on the JD  
5. the system reuses templates when appropriate  
6. the system outputs an HTML review-ready draft by default  
7. the user previews, reviews, and print-checks it  
8. the user requests further revisions if needed  

---

## 14. 成功标准 / Success Criteria

**中文**  
一个成功的输出通常应满足：

- 内容真实
- 更贴合目标岗位
- 结构清晰
- 表达自然、正式、简洁
- 一页 A4 控制合理
- 支持预览和打印检查
- 不出现明显虚构、溢出或严重排版失衡

**English**  
A successful output should usually be:

- truthful
- better aligned with the target role
- clearly structured
- naturally and professionally worded
- reasonably controlled within one A4 page
- suitable for preview and print checking
- free from obvious fabrication, overflow, or severe layout imbalance

---

## 15. 风险与注意事项 / Risks and Notes

**中文**  
需要注意的风险包括：

- 用户源材料本身信息不足
- 多份简历之间存在冲突
- 模板可视化质量不稳定
- 浏览器导出 PDF 时产生轻微版式变化
- 用户对“最终版”的理解与系统默认 HTML 成品概念不一致

因此系统应尽量保持：

- 保守推断
- 清晰提示
- 稳定结构
- 便于用户继续修订的输出形式

**English**  
The main risks include:

- insufficient source information
- conflicts across multiple resume files
- unstable visual quality in templates
- slight layout changes during browser-to-PDF export
- mismatch between user expectations of a “final version” and the system default of an HTML review-ready draft

Therefore, the system should favor:

- conservative inference
- clear signaling
- stable structure
- outputs that remain easy to revise

---

## 16. 文档关系 / Document Relationships

**中文**  
本 PRD 用于说明产品目标、范围和设计原则。  
它不是实际执行规则文件。  
实际执行应以以下文档为准：

- `Resume Tailor Skill.md`

用户快速使用时，也可以参考：

- `README.md`
- `Invocation Prompt Template.md`

**English**  
This PRD explains the product goals, scope, and design principles.  
It is not the actual execution rule file.  
Actual execution should follow:

- `Resume Tailor Skill.md`

For quick usage, users may also refer to:

- `README.md`
- `Invocation Prompt Template.md`

---