# PR

Three phases: open or update, watch, react. The user should never have to ask
"any reviews yet?"

## Open or update

1. Never work on the default branch. Branch first.
2. Start from `git status`. Group changes into commits by what they do, each
   with a message that says what changed and why. No AI co-author line.
3. Push. If the branch already has a PR, the push is the update. Don't open a
   second one.
4. Before asking anyone, review it yourself (`review.md`) until nothing real
   is left. A slower round of your own is cheaper than a round with people.
   Don't tag usage-priced review bots unasked.
5. Open it ready, written for a reviewer, or as a draft where the repo keeps
   PRs drafts until a local check passes. Request reviewers the moment it is
   ready, and confirm they were requested: a PR with nobody on it just sits.
6. One PR per deployable change, even a large one. Stack only when deploy
   order forces it or the user asks, keep the stack short, say why in each
   PR, and treat every PR in it the same way.
7. If it changes how the UI looks, post before and after screenshots from the
   real app, desktop and mobile, cropped to the change.
8. Ask for review where the team asks, through the `say` skill, unless an ask
   for this PR is already there. Give the user the PR URL, who was requested,
   and where the ask is.

## Watch

Start a watcher that blocks until something needs attention (a check, a
review, a comment, a conflict, a merge, removal from the merge queue) and then
exits. When you restart it, start from the time of the last event, so a
review that lands while you fix is still reported. If your agent can't be
woken by a background job, keep the turn open on it. If nothing is watching
any more, say so.

## React

Triage every event first: fetch every review thread, review body, comment and
check on every PR in the stack, old rounds included, and check each claim
against the current head. Then:

- Checks failed: read the log and find the cause. Fix it if the branch caused
  it. If it is flaky or unrelated, say so with the evidence and re-run.
- Comments or changes requested: fix what is real and in scope, and review the
  whole diff again, not only the fix. Give each mechanism a fix adds its own
  boundary tests. Fix a minor point the second time it is raised. Push, reply
  on every thread, resolve the fixed ones, and re-request review.
- Pushbacks: resolve one yourself only once that reviewer has approved. Leave
  it open under a request for changes, before any verdict, or when it declines
  something they called blocking.
- Every finding of a request for changes fixed and answered: dismiss that
  review with a pointer to the fix. A dismissal is not an approval.
- A design disagreement, scope growth, or a comment that rests on a
  misreading: stop and ask the user, with a recommendation. Before changing a
  deliberate decision, recover why it was made.
- Conflict or branch behind: update it the way the repo says, re-run the quick
  checks, push.
- Removed from the merge queue: read the failing run, say whether the branch
  or a flake caused it, fix or re-run, and re-queue under the same merge word.
- Approved, checks green, no open threads: stop and say it is ready to merge.
  Never merge from here.

Never call feedback addressed while any item on any PR in the stack is open.
