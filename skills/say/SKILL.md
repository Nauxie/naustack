---
name: say
description: Write anything that goes out under the user's name - a chat message, reply, bump or review ask, or a review of someone else's pull request. Use for every draft or post in a chat app, and whenever asked to review another person's PR.
---

# Say

Words that go out under the user's name. Read the file for what you are
writing.

| Writing | Read |
|-|-|
| A chat message, reply, bump or review ask | `message.md`, then `voice.md` |
| A review of someone else's PR | `review-comment.md` |

These hold for both:

- Keep it short. Agent drafts run several times longer than what a person
  types. Start from one sentence and add a line only when the reader cannot
  act without it. Leave out how the fix works, what was tested, and the
  background.
- The reader has none of this session's context. Say what a thing is before
  you link it, and never use a label they have not seen.
- If a fact is uncertain, say so. Never invent a commitment or an approval.

## When the user corrects a draft

A correction is first a check: find the rule the draft broke. Most edits are
already covered (too long, detail the reader didn't need), so apply that rule
next time and add nothing. Change this skill only when the user states a rule
or the same edit comes back a second time, and then sharpen the line that
should have caught it. A pile of one-off cases buries the principles.

Users often edit a saved draft before sending it. When the posted text differs
from your draft, read the difference for the rule you missed. A redraft starts
from their latest text, keeps every edit, and never re-adds what they cut.
