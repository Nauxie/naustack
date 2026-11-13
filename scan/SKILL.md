---
name: scan
description: Read-only sweeps that end in a report - what is open or waiting on the user across their work, and what alerted in production recently. Use when asked what is open, what is waiting or what needs attention, or to review recent alerts.
---

# Scan

Sweeps that read everything and change nothing.

| Question | Read |
|-|-|
| What is open or waiting on me? | `refresh.md` |
| What alerted, and does it matter? | `alerts.md` |

These hold for both:

- Read-only. Don't send, comment, acknowledge, restart or fix. If something
  needs doing, say so in the report.
- State the window you covered, with exact times, at the top.
- Read the sources in full. Search only finds more to read. It is never the
  sweep itself.
- End with the gaps: a source you could not read, a tool that failed. A gap is
  never a clean bill of health.
