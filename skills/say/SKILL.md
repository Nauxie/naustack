---
name: say
description: Write anything that goes out under the user's name - a chat message, reply, bump or review ask, or a review of someone else's pull request. Use for every draft or post in a chat app, and whenever asked to review another person's PR.
---

# Say

Words that go out under the user's name. Read the file for what you are
writing.

| Writing | Read |
|-|-|
| A chat message, reply, bump or review ask | `message.md` |
| A review of someone else's PR | `review-comment.md` |

These hold for both:

- Keep it short. Agent drafts run several times longer than what a person
  types. Leave out how the fix works, what was tested, and the background,
  unless the reader cannot act without it.
- The reader has none of this session's context. Say what a thing is before
  you link it, and never use a label they have not seen.
- If a fact is uncertain, say so. Never invent a commitment or an approval.
- When the user corrects a draft, add the correction to this skill, so every
  agent gets it.
