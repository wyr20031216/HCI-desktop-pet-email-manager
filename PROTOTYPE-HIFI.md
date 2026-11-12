# MailPet · Hi-Fi 高保真原型操作流程（v3.0 · 气泡单面板）

对应文件：`prototype.html`（v3.0，含启发式评估问题 1–15 全部改进） · 在线版：<https://wyr20031216.github.io/HCI-desktop-pet-email-manager/prototype.html>
Medium-Fi（v2.1 双面板架构）的结构说明见 `PROTOTYPE-MEDIUM.md`

---

## 0. 总入口与全局操作

| 操作 | 方式 |
| --- | --- |
| 打开 / 关闭功能气泡 | 单击桌宠；或工具栏「✦ MailPet」按钮；或快捷键 `Alt+P` |
| 宫格 → 详情 | 点击六个功能磁贴之一进入；顶部「‹」或 `Esc` 返回宫格，再按 `Esc` 关闭气泡 |
| 右键桌宠菜单 | 打开功能面板 / 打开任务管理 / 免打扰 / 稍后提醒 / 设置 / 隐藏到托盘 |
| 拖动桌宠 | 按住左键拖动，位置记忆在浏览器本地（刷新恢复）；位移 ≥4px 不触发开合 |
| 隐藏 / 恢复 | 菜单「隐藏到托盘」→ 右下角气泡「点击恢复」 |
| 点击外部 | 气泡非模态，点击气泡外任意处即关闭 |

桌宠五状态（FR-07）：待机 ✦ / 待确认（琥珀角标 n）/ 临期（红角标 n + 脉动）/ 成功（绿 ✓，2.2s 瞬态）/ 免打扰（灰 ☾）。「减少动画」开启时关闭脉动与弹出动画。

---

## 1. 今日面板

1. 单击桌宠 → 宫格 → 「今日面板」。
2. **统计四宫格**：全部未完成 / 今日到期·未完成 / 全部待确认 / 今日完成。点击任一数字 → 自动跳到任务管理并套用同口径筛选（如点「今日到期」→ 任务页显示今日到期且未完成的任务）。
3. **临期任务卡**（今天 17:00 截止的小组报告）：
   - 「查看任务」→ 跳邮件页并定位该邮件的 AI 分析
   - 「稍后提醒」→ 见 §3 稍后提醒流程
   - 「完成」→ 卡片转「已完成」，17:00 提醒取消；出现「恢复为待处理」可撤销
4. **待确认卡**（Assignment 2）：「确认任务」→ 转为待处理（11 月 15 日，提醒排期）；「查看依据」→ 跳邮件页看原文证据。
5. **等待条件**：「条件已满足，开始处理」→ 等待任务转为待处理，可继续完成。
6. 卡片上「截止」与「下次提醒」分别标注；设置过稍后提醒后出现「修改 / 取消提醒」入口。

## 2. 邮件

1. 宫格 → 「邮件」。页面从上到下：搜索框、邮件列表、项目标签、当前邮件 AI 分析、AI 重点依据。
2. **切换邮件**：点列表任一封（或 Outlook 左侧邮件列表）→ 右侧阅读区、AI 分析、项目标签同步切换。
3. **搜索**：输入关键词实时过滤列表。
4. **AI 分析卡**：任务标题与状态（待确认/临期/…）、摘要、截止时间（不确定时标注「只识别到日期，具体时间待确认」）、字段来源、原文证据引用（「查看原文位置」定位到阅读区段落）。
5. **修改任务**：弹窗内「截止方式」选 全天任务（仅日期）或 指定时间（日期＋时刻）；底部实时显示「提醒将依据 ×× 计算」。
6. **项目标签**：「管理当前邮件标签」→ 勾选/取消已有项目（规则按项目匹配时使用，见 §4）。
7. **AI 重点依据**：底部四封重点邮件卡，附「为什么重要」标签；点卡片跳转该邮件的分析区。

## 3. 任务管理

1. 宫格 → 「任务管理」。
2. **筛选与搜索**：时间范围（全部时间 / 今日到期 / 今日完成）× 状态（全部 / 未完成 / 待确认 / 待处理 / 等待条件 / 已完成）可组合；搜索框支持任务名称与来源；结果行实时显示口径与数量；无匹配时提供「清除搜索和筛选」。
3. **确认任务**：待确认卡「确认」→ 转待处理（今日面板与角标联动）。
4. **完成与撤销**：「完成」→ 标签转已完成、按钮变「撤销完成」；再点恢复待处理，提醒恢复待命。今日面板中的对应卡片同步。
5. **稍后提醒（完整流程，对应评估 #2/#3/#4）**：
   1. 点「稍后提醒」→ 弹窗顶部显示任务名与截止时间（今天 17:00）
   2. 选项：`30 分钟后 · 今天 10:15（推荐）` / `今天 15:00 · 截止前 2 小时` / `明天 09:00 · ⚠ 晚于截止时间` / `自定义…（选择日期和时间）`
   3. 选晚于截止的选项（含自定义越界）→ 下方出现红色警告；点保存 → 「再次确认」对话框 → 确认后才生效
   4. 成功提示写明「已设置下次提醒：××时间」；任务卡分别标注「截止」与「下次提醒」，附「修改 / 取消提醒」
6. **等待条件**：「条件已满足，开始处理」转待处理；「修改检查时间」弹 datetime 选择器。
7. **手动建任务**：必填任务名称（空则提示），可选截止日期；创建后可按名称搜索。

## 4. 纠正与规则

1. 宫格 → 「纠正与规则」。顶部「当前邮件判断」随所选邮件实时更新。
2. **双向纠正（评估 #12）**：修改字段（重要性 / 是否需要处理 / 适用对象 / 是否提示行动）→ 「修改为」列出该字段的正反两向选项（重要↔普通、需要处理↔不需要处理…）。「试一试：把漏判邮件改为需要处理」演示漏判纠正。
3. **适用范围**：仅当前邮件 / 同一发件人 / 同一项目（项目范围需先给邮件添加项目标签；下拉下方折叠说明「如何给邮件添加项目标签」，可直接「管理当前邮件标签」后返回继续）。
4. **预览影响范围**：显示匹配条件、预计受影响封数、修改前后判断对比；未选项目标签时阻止并提示。
5. **确认（评估 #6）**：范围=仅当前邮件时按钮为「确认修改此邮件」（隐藏未来邮件说明）；可复用范围时为「启用规则（仅未来邮件）」。
6. **已启用规则卡**：「暂停规则」↔「恢复规则」（状态标签同步）；「撤销本次修改」→ 弹窗说明将回到版本 1 及影响范围，确认后规则标记已撤销（评估 #7）。

## 5. 效果验证（含退化修复闭环，评估 #8）

1. 宫格 → 「效果验证」：正确结果 8/10、改善 +3、未受影响 6、判断变差 1；启用前后对比进度条。
2. **退化样本 07**（补交课程材料被规则误判为无需处理）：
   - 「查看邮件」→ 打开样本邮件，附「← 返回样本 07 的验证结果」
   - 「对比判断」→ 表格对比 原始判断 / 规则处理后 / 正确判断，说明误判原因
   - 「调整规则范围」→ 跳规则页并进入修复模式（上下文提示「正在修复样本 07」）
3. **修复**：范围改为「仅当前邮件」或换项目（不能仍命中原规则）→ 预览 → 「保存范围并返回验证」。
4. 「重新检查规则效果」→ 9/10、判断变差归零、样本 07 标记「已修复」。

## 6. 系统设置

1. 宫格 → 「系统设置」。
2. **提醒与桌宠**：免打扰开关（右键菜单与底部按钮同步）；自动开启时段；「免打扰时仍提醒即将到期任务」；桌宠置顶；减少动画；五状态预览演示工具。
3. **邮箱连接**：Outlook 宿主授权（Graph · Mail.Read 只读）；不保存密码；只读不改服务器状态；可查看权限 / 断开账号。
4. **同步范围**：初始时间范围与最多同步邮件数；**模型状态**：本地模型，不可用时回退手动处理；**数据与隐私**：本地存储说明与清理入口。

---

## 需求映射

| 本原型能力 | 需求条款 |
| --- | --- |
| 弹窗四类统计 + 宫格直达 + 任务卡就地操作 | FR-02、FR-05 |
| 邮件 AI 分析 + 原文证据 + 重点依据 | FR-03 |
| 不确定字段标注、不做猜测 | FR-04 |
| 提醒失效 / 撤销恢复 / 稍后提醒不改状态 / 等待条件 | FR-05、FR-06 |
| 桌宠五状态 / 右键菜单 / 拖拽记忆 / 托盘 / 键盘 | FR-07 |
| 双向纠正 + 三种范围 + 影响预览 + 规则启停/撤销 | FR-08、FR-09 |
| 固定测试集检查与退化修复闭环 | FR-10 |
| 只读授权、本地数据、日志脱敏 | FR-01（适配）、FR-11 |
| 模型不可用回退手动建任务 | FR-12 |

## 与 Medium-Fi（v2.1）的主要差异

- **单气泡架构**：删除 Outlook 任务窗格侧边栏，六个功能页（今日 / 邮件 / 任务 / 规则 / 验证 / 设置）全部收入桌宠气泡，两级导航（宫格 → 详情）。
- 免打扰从独立宫格磁贴收敛为：右键菜单 + 气泡底部按钮 + 设置页。
- 评估 1–15 全部改进仅在 Hi-Fi 版实现（精确截止时刻、晚于截止警告与二次确认、自定义提醒、下次提醒摘要、完成撤销、规则措辞与操作拆分、退化修复闭环、术语白话化、可读性、统计口径、任务搜索、项目标签指引等）。

## 已知限制

- 所有数据为内置演示状态，提醒不真实调度（以 toast 表达意图）；不连接真实邮箱。
- 真实加载项中，Office.js 不支持跨窗格悬浮层——本原型的气泡需运行于加载项页面内；状态机、层级与流程可直接映射。
- 依赖 Pointer Events、localStorage、CSS Grid；无外部库与网络请求。

---

# English Version · MailPet Hi-Fi Prototype Walkthrough (v3.0 · single-bubble panel)

Companion file: `prototype.html` (v3.0, includes all fixes for heuristic-evaluation issues 1–15) · Live: <https://wyr20031216.github.io/HCI-desktop-pet-email-manager/prototype.html>
Structure notes for the Medium-Fi (v2.1 two-panel) version: see `PROTOTYPE-MEDIUM.md`

---

## 0. Entry Points & Global Interactions

| Interaction | How |
| --- | --- |
| Open / close the feature bubble | Click the pet; or the "✦ MailPet" toolbar button; or `Alt+P` |
| Grid → detail page | Click one of the six tiles; "‹" at the top or `Esc` returns to the grid, another `Esc` closes the bubble |
| Pet right-click menu | Open panel / Open Tasks / DND / Remind later / Settings / Hide to tray |
| Drag the pet | Hold left button; position persists in localStorage (restored on reload); moves ≥4px don't toggle the panel |
| Hide / restore | Menu "Hide to tray" → click the bottom-right chip to restore |
| Click outside | The bubble is non-modal — clicking anywhere outside closes it |

Pet's five states (FR-07): Idle ✦ / Pending (amber badge n) / Due soon (red badge n + pulse) / Success (green ✓, 2.2s transient) / DND (gray ☾). "Reduce motion" disables pulse and pop-in animations.

## 1. Today

1. Click the pet → grid → "Today".
2. **Stat cards**: All open / Due today · open / All pending / Done today. Clicking a number jumps to Tasks with that exact filter applied.
3. **Due-soon card** (group report due Today 17:00):
   - "View task" → jumps to Mail and scrolls to that email's AI analysis
   - "Remind later" → see §3
   - "Done" → card flips to Done, the 17:00 reminder is cancelled; "Restore to To do" undoes it
4. **Pending card** (Assignment 2): "Confirm task" → becomes To do (Nov 15, reminder scheduled); "View evidence" → opens the email's source quote.
5. **Waiting**: "Condition met — start now" → the waiting task becomes To do.
6. Cards label "Deadline" and "Next reminder" separately; after snoozing, "Edit / Cancel reminder" links appear.

## 2. Mail

1. Grid → "Mail". Page layout top-to-bottom: search, email list, project tags, AI analysis of the current email, AI highlights.
2. **Switching emails**: click any list item (or Outlook's own mail list) → reading pane, AI analysis and tags all follow.
3. **Search**: filters the list as you type.
4. **AI analysis card**: task title & status, summary, deadline (uncertain ones labeled "date only — exact time unconfirmed"), field source, evidence quote ("View in email" scrolls to the passage).
5. **Edit task**: the modal's "Due type" offers All-day (date only) or Specific time (date + time); a live hint shows what the reminder will be based on.
6. **Project tags**: "Manage tags for this email" → check/uncheck existing projects (used by project-scoped rules, see §4).
7. **AI highlights**: four flagged emails with "why it matters" chips; clicking a card jumps to that email's analysis.

## 3. Tasks

1. Grid → "Tasks".
2. **Filters & search**: time range (All time / Due today / Done today) × status (All / Open / Pending / To do / Waiting / Done), combinable; search covers task names and sources; the scope line updates live; the empty state offers "Clear search & filters".
3. **Confirm task**: a Pending card's "Confirm" → To do (Today panel and pet badge update in sync).
4. **Done & undo**: "Done" → tag flips, button becomes "Undo"; clicking again restores To do and re-arms reminders.
5. **Remind later (full flow, evaluation #2/#3/#4)**:
   1. Click "Remind later" → the modal header shows task name and deadline (Today 17:00)
   2. Options: `In 30 min · Today 10:15 (recommended)` / `Today 15:00 · 2h before due` / `Tomorrow 09:00 · ⚠ past the deadline` / `Custom… (pick date & time)`
   3. Choosing a past-deadline option (including out-of-window customs) shows a red warning; saving then requires a "Confirm again" dialog
   4. The success toast states the next reminder time; task cards label "Deadline" and "Next reminder" separately with "Edit / Cancel reminder" links
6. **Waiting**: "Condition met — start now" flips it to To do; "Edit check time" opens a datetime picker.
7. **Manual task**: title required (empty shows a hint), optional due date; searchable by name after creation.

## 4. Corrections & Rules

1. Grid → "Corrections & Rules". The "Current judgment" panel follows the selected email.
2. **Two-way correction (evaluation #12)**: pick a field (Importance / Needs action? / Applies to / Action tip?) → "New value" lists both directions (Important↔Normal, Needs action↔No action needed…). "Try it: mark a missed email as needing action" demos fixing a miss.
3. **Scope**: This email only / Same sender / Same project (project scope requires tagging first; a collapsible "How do I tag an email?" sits right below, with a direct "Manage tags" shortcut that returns here).
4. **Preview impact**: match condition, estimated affected count, before/after judgment; blocked with a hint if no project tag is selected.
5. **Confirm (evaluation #6)**: with "This email only" the button reads "Apply to this email" (future-emails note hidden); reusable scopes read "Enable rule (future only)".
6. **Enabled-rule card**: "Pause rule" ↔ "Resume rule" (status tag follows); "Undo this change" → a modal explains the revert-to-v1 scope before confirming (evaluation #7).

## 5. Validation (with the regression-fix loop, evaluation #8)

1. Grid → "Validation": 8/10 correct, +3 improved, 6 unaffected, 1 worse; before/after progress bars.
2. **Regression Sample 07** (missing-materials email wrongly set to no-action):
   - "View email" → opens the sample, with a "← back to Sample 07 results" link
   - "Compare" → a table of Original / After rule / Correct plus the misjudgment cause
   - "Adjust rule scope" → jumps to Rules in repair mode (context banner "Fixing Sample 07")
3. **Fix**: switch scope to "This email only" or an unrelated project (must no longer hit the rule) → preview → "Save scope & return".
4. "Re-run check" → 9/10, worse drops to zero, Sample 07 marked "fixed".

## 6. Settings

1. Grid → "Settings".
2. **Reminders & pet**: DND toggle (right-click menu and footer button stay in sync); auto schedule; "Still remind confirmed tasks due within 24h during DND"; keep-pet-on-top; reduce motion; five-state preview tool.
3. **Mailbox connection**: Outlook host consent (Graph · Mail.Read read-only); no password storage; read-only; view permissions / disconnect.
4. **Sync scope**: initial window and max email count; **Model**: local model, manual fallback when unavailable; **Data & privacy**: local-storage notes and a cleanup entry.

---

## Requirement Mapping

| Prototype capability | Requirement |
| --- | --- |
| Four stat groups in the bubble + grid shortcuts + in-card task actions | FR-02, FR-05 |
| Email AI analysis + source evidence + highlights | FR-03 |
| Uncertain fields labeled, never guessed | FR-04 |
| Reminder invalidation / undo-restore / snooze never changes status / waiting conditions | FR-05, FR-06 |
| Pet five states / right-click menu / drag memory / tray / keyboard | FR-07 |
| Two-way correction + three scopes + impact preview + rule pause/undo | FR-08, FR-09 |
| Fixed test-set checks with the regression-fix loop | FR-10 |
| Read-only consent, local data, sanitized logs | FR-01 (adapted), FR-11 |
| Manual-task fallback when the model is unavailable | FR-12 |

## Key Differences vs. Medium-Fi (v2.1)

- **Single-bubble architecture**: the Outlook task-pane sidebar is removed; all six feature pages (Today / Mail / Tasks / Rules / Validation / Settings) live inside the pet bubble with two-level navigation (grid → detail).
- DND is no longer a separate tile: it lives in the right-click menu, the bubble footer button, and Settings.
- All evaluation fixes 1–15 exist only in Hi-Fi (exact due times, past-deadline warnings with double confirm, custom reminders, next-reminder summaries, complete-undo, rule wording & action split, the regression-fix loop, plain-language terms, readability, stat scopes, task search, project-tag guidance, etc.).

## Known Limitations

- All data is built-in demo state; reminders aren't really scheduled (toasts convey intent); no real mailbox is connected.
- In a real add-in, Office.js doesn't allow cross-pane floating layers — the bubble would run inside the add-in page; the state machine, hierarchy and flows map directly.
- Depends on Pointer Events, localStorage, CSS Grid; no external libraries or network requests.
