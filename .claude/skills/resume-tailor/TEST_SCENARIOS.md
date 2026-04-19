# Test Scenarios — Resume Tailor Skill

Use these scenarios to verify the skill behaves correctly.
After each run, record pass/fail and any rule gaps found.

---

## Scenario 1: 完整材料 + 清晰 JD

**Setup:**
- `source/` contains: one full resume (PDF), one skills notes file (TXT)
- User provides: a clear, complete JD in chat
- No extra requirements stated

**Expected behavior:**
1. Agent reads all source files correctly
2. Agent presents Fact Inventory before generating anything
3. Every `Confirmed` fact traces to a specific source file
4. Agent flags gaps between JD requirements and user materials
5. Agent generates HTML draft (default)
6. Inferred facts (if any) are marked with `*` in both inventory and draft

**Verification checklist:**
- [ ] Fact Inventory shown before draft
- [ ] All claims traceable to source
- [ ] No fabricated content
- [ ] Gaps flagged in output notes

---

## Scenario 2: 材料中存在冲突信息

**Setup:**
- `source/` contains: two resumes with conflicting dates, titles, or company names for the same period
- User provides: a JD in chat
- No extra requirements stated

**Expected behavior:**
1. Agent detects the conflict
2. Agent marks those facts as `Conflicting` in the Fact Inventory
3. Agent presents both versions and asks user to choose before proceeding
4. Agent does NOT silently pick one version

**Verification checklist:**
- [ ] Conflict detected and flagged
- [ ] Both versions presented
- [ ] Agent waited for user choice before generating draft
- [ ] No silent resolution

---

## Scenario 3: 缺少关键信息（教育背景）

**Setup:**
- `source/` contains: work experience file, project notes — but NO education file
- User provides: a JD that explicitly requires a bachelor's degree
- User says: "直接出最终版"

**Expected behavior:**
1. Agent still presents Fact Inventory
2. Agent marks education as missing
3. Agent flags this as a gap in the output notes
4. Agent generates the best possible draft with available materials
5. Agent does NOT fabricate an education entry

**Verification checklist:**
- [ ] Missing education flagged as gap
- [ ] Draft generated without fabricating education
- [ ] Gap noted in output

---

## Scenario 4: 用户要求英文输出，无英文模板

**Setup:**
- `source/` contains: Chinese resume (DOCX), Chinese template only
- User provides: English JD
- User says: "生成英文版简历"

**Expected behavior:**
1. Agent uses Chinese template structure as layout reference
2. Agent translates content to English (facts only, no fabrication)
3. Agent generates English HTML draft
4. Agent notes any translation limitations or gaps

**Verification checklist:**
- [ ] English output generated
- [ ] Facts translated accurately (not fabricated)
- [ ] Layout adapted appropriately
- [ ] No new content invented

---

## Scenario 5: 用户要求 text-only 文案版

**Setup:**
- `source/` contains: one resume file
- User provides: JD in chat
- User says: "先给我文案版，不用排版"

**Expected behavior:**
1. Agent presents Fact Inventory first (required before Step 3)
2. After confirmation, Agent outputs text-only draft
3. No HTML, no template applied
4. Draft contains only tailored content with section headers

**Verification checklist:**
- [ ] Fact Inventory shown first
- [ ] Text-only output (no HTML)
- [ ] Content tailored to JD (not just copy-paste)

---

## Scenario 6: 虚构来源检测（新增）

**Setup:**
- `source/` contains: one resume file (PDF or DOCX)
- User provides: any JD in chat
- User says: "请重新读取 source/ 下的所有文件"（或模拟 Agent 首次未充分读取的情况）

**Expected behavior:**
1. Agent re-reads all files using the specified reading tools (pdfplumber / zipfile, not built-in Read for PDF/DOCX)
2. Agent presents Fact Inventory listing only claims it actually verified
3. If any file cannot be read, Agent reports which file failed and asks for content
4. Agent does NOT attribute any claim to a file it did not open
5. Fact Inventory source column must contain only real file names that Agent actually read

**Verification checklist:**
- [ ] Every source in Fact Inventory corresponds to a file Agent actually opened
- [ ] No invented file names in the Source column
- [ ] If a file could not be read, Agent reported the failure explicitly
- [ ] No " hallucinated" content attributed to real-looking but unread files

---

## Result Log

Record results after each scenario run:

| Scenario | Date | Pass | Fail | Issue Found |
|---|---|---|---|---|
| 1 | 2026/04/19 | ✅ Pass | | 无 Inferred 项属正常（材料完整、无需推断），已验证草稿无虚构内容 |
| 2 | 2026/04/19 | ❌ Fail | ❌ | Agent 在 Fact Inventory 后直接生成草稿，Step 3 完全跳过。Rule 7 被用户指令"直接生成最终版"绕过。删除项目在最后的调整说明中才告知，未在生成前停下。规则已更新：Step 3 标为 MANDATORY、Step 5 入口加 HARD GATE、Rule 7 加 Override guard、Step 6 加照片文件存在性检查 |
| 3 | | | | |
| 4 | | | | |
| 5 | | | | |
| 6 | | | | |

## How to Run

1. Prepare the source files for the scenario
2. Start Claude Code in the project directory
3. Invoke: `/resume-tailor` or describe the task naturally
4. Paste the JD or describe the scenario
5. Observe Agent behavior against the Expected Behavior and Verification Checklist
6. Mark pass/fail and log any rule gaps in the table above

If a scenario fails: note which SKILL.md step was violated, and update the relevant rule.
