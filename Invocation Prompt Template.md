# Invocation Prompt Template.md
## 调用提示模板 / Invocation Prompt Template（双语精简版，v1.0）

---

## 1. 文件用途 / Purpose

**中文**  
本文件用于帮助用户或外部 Agent **快速发起 Resume Tailor Skill 任务**。  
它是一个**调用模板文件**，不是执行规则文档。

实际执行时，仍以以下文件为准：

- `Resume Tailor Skill.md`

**English**  
This file helps users or external Agents **quickly invoke Resume Tailor Skill tasks**.  
It is an **invocation template file**, not the execution rule document.

During actual execution, the following file remains the main rule source:

- `Resume Tailor Skill.md`

---

## 2. 极简调用模板 / Minimal Template

**中文示例**

请根据我提供的材料和下面这个 JD，帮我定制简历。  

JD：  
[粘贴岗位描述]

补充要求：  
- [可选填写]

**English Example**

Please tailor my resume based on the materials I provided and the following JD.  

JD:  
[paste the job description]

Additional requirements:  
- [optional]

---

## 3. 最终版调用模板 / HTML Review-Ready Draft Template

**中文示例**

请根据我提供的材料和下面这个 JD，直接生成最终简历版本。  

JD：  
[粘贴岗位描述]

要求：  
- 控制在一页 A4  
- 保持正式投递风格  
- 输出 HTML 可审阅成品  
- 便于预览和打印检查  
- 不要虚构或夸大内容

**English Example**

Please generate an HTML review-ready draft of my resume based on the materials I provided and the following JD.  

JD:  
[paste the job description]

Requirements:  
- keep it within one A4 page  
- maintain a formal application style  
- output an HTML review-ready draft  
- make it suitable for preview and print checking  
- do not invent or exaggerate content

---

## 4. 文案版调用模板 / Text-Only Template

**中文示例**

请根据我提供的材料和下面这个 JD，先帮我完成简历文案优化，暂时不要排版。  

JD：  
[粘贴岗位描述]

要求：  
- 重写 Summary / 个人简介  
- 优化项目、实习、教育和技能表达  
- 帮我判断哪些内容该保留、删除或强化  
- 暂时不要生成 HTML 成品

**English Example**

Please help me optimize the resume wording based on the materials I provided and the following JD. No formatted draft is needed yet.  

JD:  
[paste the job description]

Requirements:  
- rewrite the Summary / Profile  
- improve the wording of projects, internships, education, and skills  
- suggest what should be kept, removed, or emphasized  
- do not generate the HTML draft yet

---

## 5. 英文版调用模板 / English Version Template

**中文示例**

请根据我提供的材料和下面这个 JD，帮我生成英文简历版本。  

JD：  
[粘贴岗位描述]

要求：  
- 输出英文  
- 保持正式、简洁、自然  
- 根据岗位重写 Summary / Profile  
- 优化项目和实习 bullet  
- 尽量控制在一页 A4  
- 输出 HTML 可审阅成品

**English Example**

Please generate an English resume version based on the materials I provided and the following JD.  

JD:  
[paste the job description]

Requirements:  
- output in English  
- keep the tone formal, concise, and natural  
- rewrite the Summary / Profile for the role  
- improve project and internship bullets  
- keep it within one A4 page if possible  
- output an HTML review-ready draft

---

## 6. 常用补充短指令 / Common Add-On Instructions

**中文**
你也可以直接补充类似下面的短指令：

- 保留照片
- 去掉照片
- 强化数据分析相关内容
- 弱化不相关经历
- 教育经历放前面
- 项目经历放前面
- Summary 写得更简洁一点
- 英文表达自然一点
- 不要太像 AI 写的
- 先给文案版
- 直接出最终版

**English**
You may also add short instructions such as:

- keep the photo
- remove the photo
- strengthen data-analysis-related content
- reduce less relevant experience
- place education first
- place projects first
- make the Summary more concise
- make the English wording more natural
- avoid sounding too AI-generated
- give me the text version first
- directly generate the HTML review-ready draft

---

## 7. 最简单的用法 / Simplest Usage

**中文**
如果你不想组织太多内容，直接说：

按这个 JD 帮我改简历，并直接出最终版。  
[粘贴 JD]

**English**
If you do not want to structure too much, you can simply say:

Please tailor my resume to this JD and directly generate the HTML review-ready draft.  
[paste the JD]

---