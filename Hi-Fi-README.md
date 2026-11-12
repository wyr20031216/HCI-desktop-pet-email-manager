# MailPet · Outlook AI Email Assistant Prototype README

CSC5056 Human-Computer Interaction · Assignment 2 · Graduate Team 6  
Final version: `prototype.html` v3.0 (Hi-Fi)  
Phase 2 version: `prototype-medium.html` v2.1 (Medium-Fi, retained for fidelity comparison)

MailPet is an **Outlook desktop email assistant** for students and researchers. It provides a low-interruption, on-demand entry point through a desktop pet, turning emails into tasks with source evidence, user confirmation, reminders, and undo. When an AI judgment needs correction, users can preview the impact scope, enable a rule, and later review validation results, pause, or undo it.

This repository contains two interactive prototypes:

- **Hi-Fi v3.0**: a single-bubble architecture in which all six feature views live inside the pet bubble. It includes fixes for Phase 3 issues P1–P15.
- **Medium-Fi v2.1**: a two-panel architecture with a pet quick-popup and an Outlook task-pane sidebar. It is retained as the Phase 2 and design-process artifact.

Both prototypes use built-in demo data. They do not connect to a real mailbox or send real reminders.

---

## 1. Access and setup

- Prototype hub: <https://wyr20031216.github.io/HCI-desktop-pet-email-manager/>
- Hi-Fi prototype: <https://wyr20031216.github.io/HCI-desktop-pet-email-manager/prototype.html>
- Medium-Fi prototype: <https://wyr20031216.github.io/HCI-desktop-pet-email-manager/prototype-medium.html>

---

## 2. Target device

- Device: Windows 10/11 desktop or laptop.
- Host: Outlook desktop; the prototype simulates in-page floating layers and task-pane interactions for an Outlook add-in.
- Browser: Microsoft Edge or Google Chrome.
- Mobile is not supported; there is no phone layout or cross-device sync.

---

## 3. Context of use

### 3.1 Who: target users

- Primary users: students and researchers who receive course, supervisor, lab, conference, registration, and administrative emails in Outlook.
- Secondary users: light office users who need to track cross-team replies, material preparation, or similar follow-ups.

### 3.2 When and where

The product is used during everyday Outlook email processing on a Windows desktop. Typical situations include:

- Quickly checking which course or meeting emails need action before class;
- Reading a supervisor or project-team email and deciding what to reply, submit, or prepare;
- Receiving an administrative notice and deciding whether it applies to the user;
- Noticing an incorrect AI judgment and correcting the current email or later emails from the same sender or project.

### 3.3 What users should accomplish

Users should be able to independently:

- Find an email that needs action and see its summary, action items, deadline, and source evidence;
- Confirm a task and edit its due date/time, estimated effort, and reminder;
- Correct an AI judgment, choose a scope, preview the impact, and validate the result;
- Know how to undo or recover after any high-risk action.

### 3.4 Three task flows

**T1 · Simple task: find an email that needs action**

- Click the desktop pet to open the feature panel.
- Open "Mail" and review the current email, AI analysis, and "AI-highlighted items".
- Check the summary, action items, deadline, field source, and source evidence.
- Decide whether the email requires action from the user.

**T2 · Moderate task: confirm an action item and set a reminder**

- Click "Confirm" in "Today" or "Tasks".
- In the task editor, choose "All-day task" or "Specific time".
- Edit the due date/time, estimated effort, and reminder settings.
- Use "Snooze" if needed; if the reminder is later than the deadline, the system shows a risk warning.
- After completion, click "Undo complete" to restore the task to To do.

**T3 · Complex task: correct an AI judgment and validate a rule**

- Open "Corrections & Rules" and modify the AI judgment.
- Choose a scope: this email only / same sender / same project.
- Review the impact preview: match conditions, affected emails, and a control email.
- Enable the rule; it can be paused, resumed, or undone.
- In "Validation", review improved, degraded, and unchanged items in the fixed test set; for a degraded sample, view the email, compare judgments, or adjust the rule scope.

### 3.5 Usage path

> Find an important email → check source evidence → confirm the task → schedule a reminder → correct the judgment → preview the impact → validate the result

---

## 4. Operating instructions

### 4.1 Pet and global interactions

| Action | Behavior |
| --- | --- |
| Left-click the pet | Open or close the feature panel |
| Right-click the pet | Open the menu: open panel, open Tasks, Do Not Disturb, snooze, settings, hide to tray |
| Drag the pet | Move it anywhere on the desktop; position is restored from `localStorage` after refresh |
| Hover over the pet | Show a one-line status summary |
| `Alt+P` | Toggle the feature panel |
| `Esc` | Return from a detail page to the grid, then close the panel |
| "Hide to tray" | Hide the pet and show a restore chip at the bottom-right |
| Do Not Disturb | Gray out the pet and silence ordinary reminders; urgent tasks can optionally break through |

### 4.2 Five pet states

| State | Visual | Trigger |
| --- | --- | --- |
| Idle | Blue-purple gradient, no badge | No pending tasks and nothing due soon |
| Pending | Amber badge with a number | Pending tasks exist |
| Due soon | Red badge and pulsing ring | A task is due soon |
| Success | Green check, falls back after about 2.2 seconds | Confirmation or completion |
| Do Not Disturb | Gray moon | DND is on and has the highest priority |

States use "icon + number + text" rather than color alone.

### 4.3 Demo path for the three flows

1. Click the pet → feature grid (badges: To confirm 3 / Mail 4 / Due soon 1).
2. Open "Mail" → review "AI-highlighted items" and "Why it matters" → open a card to see the source email and evidence.
3. Go back → open "Today" or "Tasks" → click "Confirm" → watch the badge change from 3 to 2 and the pet flash green before returning to idle.
4. Open "Settings" or the right-click menu → enable "Do Not Disturb" → the pet turns gray and the tile dims.
5. Right-click the pet → try opening the panel, opening Tasks, snoozing, settings, and hiding to tray.
6. Press `Alt+P` to toggle the panel; press `Esc` to go back step by step.
7. In "Corrections & Rules", change the judgment → choose a scope → preview the impact → enable the rule.
8. In "Validation", review the fixed test-set results; for a degraded sample, view the email, compare judgments, and adjust the scope.

### 4.4 Differences in Medium-Fi v2.1

`prototype-medium.html` uses a two-panel structure:

- Pet quick-popup: feature grid plus "Mail highlights", "Current tasks", and "Full panel";
- The "✦ MailPet" toolbar button toggles the Outlook task pane;
- The task pane contains six views: Today / Mail / Tasks / Rules / Validation / Settings;
- See `Mid-Fi-README.md` and `PROTOTYPE-MEDIUM.md` for detailed operation.

Medium-Fi does not include features added only in v3.0, such as exact times, undo-complete, the degraded-result repair loop, or two-way correction.

### 4.5 Simulated interactions and preset data

- Demo date: 9 November; last sync: 09:42.
- Five demo emails: course assignment, project team, academic seminar, library, teaching assistant notice.
- Tasks, rules, test samples, and reminders are all built-in data.
- Reminders are not really scheduled; toasts and state changes only express intent.
- Email bodies are rendered as untrusted text; the quote area includes a note.
- No real mailbox is connected, and server read/delete/move states are not modified.

---

## 5. Design and interaction highlights

- **Low-interruption entry**: the pet stays resident but does not proactively pop up; ordinary email only updates the badge until the user opens it.
- **Source evidence**: summary, action items, deadline, and field source appear in the same email context and can be traced to the original text.
- **Uncertainty**: when only a date is available, the UI says "Only a date was recognized; the exact time needs confirmation" rather than inventing 23:59.
- **Time and reminders**: the task editor supports "All day / Specific time"; snooze shows the exact time and warns when an option is later than the deadline.
- **Rule scope**: "Edit this email only" is distinct from "Enable rule (future emails only)"; the impact preview includes match conditions, affected emails, and a control email.
- **Recoverability**: completion can be undone; rules can be paused, resumed, or reverted; the impact scope is explained before undoing.
- **Validation loop**: a fixed test set shows improved, degraded, and unchanged items; a degraded item links to viewing the email, comparing judgments, or adjusting the scope.
- **Accessibility**: semantic buttons, keyboard paths, `aria-label`, dual-channel status, and a reduced-motion switch.

---

## 6. Development plan

### 6.1 Current prototype

- Hi-Fi: single-file `prototype.html`, HTML + CSS + vanilla JavaScript.
- Medium-Fi: single-file `prototype-medium.html`, retaining the two-panel structure.
- No external libraries, network requests, or backend.
- Uses built-in demo data and `localStorage` for the pet position.

### 6.2 Planned implementation

- **Form factor**: Outlook add-in; main interactions take place in the add-in page/task pane.
- **Platform**: Outlook desktop on Windows 10/11.
- **Frontend**: Office.js + HTML/CSS/JavaScript; the team may migrate to TypeScript/React while preserving the state machine and interactions.
- **Mailbox access**: Microsoft Graph `Mail.Read` read-only consent; no password storage and no changes to server read/delete/move states.
- **AI analysis**: the email body is sent to an extraction module that outputs a summary, action items, deadline candidates, applicable audience, and evidence positions; model and prompt versions are stored with results.
- **Local data**: tasks, rules, test samples, reminder settings, and correction history are stored locally; the exact storage design will be decided during implementation.
- **Reminders**: the production version uses local reminder scheduling; the app cannot guarantee on-time reminders when it is not running or the device is asleep, and this must be explained in the UI.
- **Validation**: a fixed test set stores the original AI output, user expectations, and rule versions; previews and replays use the same base output.

### 6.3 Key technical challenges

- **Office.js cross-pane limitation**: Office.js does not support cross-pane floating layers; the pet and panel must run inside the add-in page/task pane, with in-page overlays.
- **Mailbox permissions and compatibility**: school or enterprise mailboxes may restrict add-ins or Graph permissions; the first release will only claim environments that have been tested.
- **Reminder reliability**: reminders cannot be guaranteed during app exit, sleep, or network loss; degradation and catch-up behavior must be defined.
- **Untrusted email content**: instructions inside emails must not change system rules or trigger network actions; HTML sanitization, plain-text-first rendering, and permission isolation are required.
- **Evidence validation**: structurally valid output is not necessarily correct; original-text citations, time fields, and uncertain states must be verified.
- **Rule impact scope**: same-sender and same-project rules need explainable match conditions; the default is the current email only, and any expansion requires preview and confirmation.
- **Accessibility**: color contrast, font size, keyboard paths, and screen-reader support still require real user testing.

### 6.4 Simulated components and replacements

| Current simulation | Future implementation |
| --- | --- |
| Five built-in emails | Graph mail sync / `.eml` import |
| Built-in AI analysis | Structured extraction by a local or cloud model |
| Toast reminders | Local reminder scheduling + system notifications |
| Fixed rules/validation samples | User rules, test sets, and replay records |
| `localStorage` pet position | Local settings persistence |
| Static task state | Local task database and transactions |

---

## 7. Limitations and accessibility

### 7.1 Known limitations

- No real mailbox connection, real sync, or real reminder delivery.
- No real AI calls; all analysis results are demo data.
- Server-side read, delete, and move states are not modified.
- Desktop only; no mobile, multi-account, or cross-device sync.
- Attachment content is not analyzed; attachments show an "Not analyzed" note.
- Rules only affect future matching emails; historical emails are not automatically recalculated.
- A production version needs credential protection, log redaction, data deletion, and permission revocation.

### 7.2 Accessibility

- Pet status uses icons, numbers, and `aria-label`, not color alone.
- Key actions use native buttons and inputs, with Tab focus and keyboard activation.
- `Alt+P` opens the panel; `Esc` closes or returns.
- A "Reduce motion" switch disables pulsing and movement animations.
- Font size, contrast, zoom, and screen-reader behavior still need testing on real devices; no WCAG or real-user accessibility claim is made.

---

## 8. Version history and evaluation

| Version | Main changes |
| --- | --- |
| v1.0 | Click the pet to open the sidebar |
| v2.0 | Quick bubble + five states + drag/tray + add-in consent |
| v2.1 | Feature grid, two-level interaction, compact mode, false-close/state-sync fixes; Phase 2 / Phase 3 evaluation version |
| v3.0 | Single-bubble panel, sidebar removed; fixes P1–P15 from Phase 3, including time, reminders, recovery, rule scope, two-way correction, waiting completion, task search, project tags, terminology, and readability |

**Phase 3 evaluation note**: the internal evaluation workbook records 15 violations (Problem #1–#15) for the v2.1 Medium-Fi prototype. v3.0 is the Phase 4 fix version; P1–P15 refer to problem numbers in that evaluation sheet, not user-test participant IDs (P01, P02).


