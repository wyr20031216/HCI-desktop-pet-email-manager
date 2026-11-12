# MailPet · Phase 2 README (Medium-Fi Prototype Checkpoint)

CSC5056 Human-Computer Interaction · Assignment 2 · Graduate Team 6  
Prototype: `prototype-medium.html` (v2.1, two-panel architecture)  
Version note: this is the Phase 2 Medium-Fi README; the final version is the `Hi-Fi-README.md` in the same folder.  
Online prototype: <https://wyr20031216.github.io/HCI-desktop-pet-email-manager/prototype-medium.html>

MailPet is an Outlook desktop email assistant for students and researchers. It provides a low-interruption, on-demand entry point through a desktop pet, turning emails into tasks with source evidence, user confirmation, reminders, and undo. When an AI judgment needs correction, users can preview the impact scope, enable a rule, and later review validation results.

This stage uses the **Medium-Fi v2.1 two-panel prototype**: a pet quick-popup for everyday entry, and an Outlook task pane for six feature views. Emails, AI analysis, reminders, and rule validation all use built-in demo data; no real mailbox is connected.

---

## 1. Access and setup

- Prototype hub: <https://wyr20031216.github.io/HCI-desktop-pet-email-manager/>
- Phase 2 Medium-Fi prototype: <https://wyr20031216.github.io/HCI-desktop-pet-email-manager/prototype-medium.html>

---

## 2. Target device

- Device: Windows 10/11 desktop or laptop.
- Host: Outlook desktop; the prototype simulates task-pane and in-page overlay interactions for an Outlook add-in.
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
- Confirm a task and edit its title, due date, estimated effort, and reminder;
- Correct an AI judgment, choose a scope, preview the impact, and review validation results;
- Know how to pause or undo an enabled rule.

### 3.4 Three task flows

**T1 · Simple task: find an email that needs action**

- Click the desktop pet to open the feature grid.
- Open "Mail highlights" and review each email's tags and "why it matters" evidence.
- Click an email card to read the body and AI analysis in the Outlook reading pane.
- Check the summary, action items, deadline, and source evidence.

**T2 · Moderate task: confirm an action item and set a reminder**

- Click "Confirm" in "Current tasks".
- In the task editor, edit the title, due date, estimated effort, and reminder.
- Use "Snooze" to choose a preset time if needed.
- Click "Done" to move the task to the completed state.

**T3 · Complex task: correct an AI judgment and validate a rule**

- Open "Corrections & Rules" and modify the AI judgment.
- Choose a scope: this email only / same sender / same project.
- Review the impact preview: match conditions and potentially affected emails.
- Enable the rule; it can later be paused, or the validation page can be used to review results.

### 3.5 Phase 2 scope note

The Medium-Fi prototype covers the three flows above and six feature views, but it does not include features added only in final Hi-Fi v3.0, such as exact times, undo-complete, the degraded-result repair loop, or two-way correction.

---

## 4. Operating instructions

### 4.1 Pet and global interactions

| Action | Behavior |
| --- | --- |
| Left-click the pet | Open or close the feature panel |
| Right-click the pet | Open the menu: quick panel, full panel, Do Not Disturb, snooze, settings, hide to tray |
| Drag the pet | Move it anywhere on the desktop; position is restored from `localStorage` after refresh |
| Hover over the pet | Show a one-line status summary |
| `Alt+P` | Toggle the feature panel |
| `Esc` | Return from a detail page to the grid, then close the panel |
| "Hide to tray" | Hide the pet and show a restore chip at the bottom-right |
| "✦ MailPet" toolbar button | Expand or collapse the Outlook task pane |

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

1. Click the pet → feature grid (badges: To confirm 3 / Mail highlights 4 / Due soon 1).
2. Open "Mail highlights" → review "Why it matters" tags → open a card to see the source email and evidence.
3. Go back → open "Current tasks" → click "Confirm" → watch the badge change from 3 to 2 and the pet flash green before returning to idle.
4. Open "Do Not Disturb" → enable it → the pet turns gray and the grid tile dims.
5. Right-click the pet → try the quick panel, full panel, Do Not Disturb, snooze, settings, and hide-to-tray.
6. Use the "✦ MailPet" toolbar button to expand or collapse the task pane; `Alt+P` toggles the panel; `Esc` goes back step by step.
7. In the task-pane "Rules" view, correct a judgment, choose a scope, preview the impact, and enable the rule.
8. In "Validation", review the fixed test set's before/after comparison and improved/degraded results.

### 4.4 Simulated interactions and preset data

- Demo date: 9 November; last sync: 09:42.
- Five demo emails: course assignment, project team, academic seminar, library, teaching assistant notice.
- Tasks, rules, test samples, and reminders are all built-in data.
- Reminders are not really scheduled; toasts and state changes only express intent.
- Email bodies are rendered as untrusted text; the quote area includes a note.
- No real mailbox is connected, and server read/delete/move states are not modified.
