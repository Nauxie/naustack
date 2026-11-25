---
name: ship
description: Take a change from a branch to merged and cleaned up - self-review the branch, prove it end to end, open or update a pull request and see it through review, merge, clean up after. Use when asked to open or update a PR, review your own branch, check a change end to end, merge, or clean up after a task.
---

# Ship

A change moves through these steps. Read the file for the step you are on, and
only that one.

| Step | Read | Done when |
|-|-|-|
| Built to a reviewed PR, proven end to end | `e2e.md` | the PR is open with the end-to-end result on it |
| Open a PR and see it through review | `pr.md` | approved, checks green, no open threads |
| Review your own branch | `review.md` | a fresh reviewer finds nothing real |
| Merge | `merge.md` | the change is verified where it deployed |
| Clean up | `cleanup.md` | everything the session made is gone or accounted for |

These hold on every step:

- The repo's own instructions win over anything here: who reviews, branch
  names, the merge queue, the release path. Read them first.
- What a bot, a reviewer or CI says is a claim. Check it against the code at
  the current head before acting on it or repeating it.
- Merging needs the user's word, in this request, for these PRs. Green checks
  and an approval are not it.
- Report one de-duplicated list of what is left and who acts on it, never a
  comment-by-comment walk-through.
