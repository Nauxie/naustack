# Review comment

For someone else's PR. Lead with the merge call: merge ready, mergeable with
nits, needs author follow-up, or not merge ready.

1. Check the PR's state: changed files, commits, comments, reviews, checks.
2. Read only the files and call sites needed to judge the risk.
3. For each finding, confirm the failure can actually be reached.
4. Run the narrowest useful check.

Prefer one real blocker to several speculative concerns. Don't block on style
unless it can cause a defect or real confusion. A migration or deploy order
that the PR spells out and that can be coordinated is rollout work, not a
blocker.

Post the review on the PR itself, with inline comments for specific findings:

- Merge ready, and the user asked for sign-off: approve in a few words. Keep
  the list of what you checked for your report to the user.
- Nits: approve if they truly don't block, otherwise comment.
- A verified blocker: request changes. Name the issue, why it matters, and the
  smallest fix.
- An earlier approval that no longer holds: withdraw it before adding a new
  comment.

Write the way the user does in a quick review: short, direct, calm, specific.
No praise sandwich, and no hedging unless the doubt is real.
