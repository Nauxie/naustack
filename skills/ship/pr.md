# PR

Three phases: open or update, watch, react. The user should never have to ask
"any reviews yet?"

## Open or update

1. Never work on the default branch. Branch first.
2. Start from `git status`. Group changes into commits by what they do, each
   with a message that says what changed and why. No AI co-author line.
3. Push. If the branch already has a PR, the push is the update. Don't open a
   second one.
4. Open it ready for review, not as a draft, written for a reviewer, and
   request reviewers in the same step. Confirm they were requested: a PR with
   nobody on it just sits.
5. If the change builds on another open PR, make it a real stack, and treat
   every PR in the stack the same way.
6. If it changes how the UI looks, post before and after screenshots from the
   real app, desktop and mobile, cropped to the change.
7. Give the user the PR URL and who was requested.

## Watch

Start a watcher that blocks until something needs attention (a check, a
review, a comment, a conflict, a merge) and then exits. Run it in the
background and wait for it. Don't poll. If nothing is watching any more, say
so.

## React

Triage every event first: fetch every review thread, review body, comment and
check on every PR in the stack, old rounds included, and check each claim
against the current head. Then:

- Checks failed: read the log and find the cause. Fix it if the branch caused
  it. If it is flaky or unrelated, say so with the evidence and re-run.
- Comments or changes requested: fix what is real and in scope, run the checks
  for what you touched, push, reply on every thread, resolve the fixed ones,
  leave pushbacks open, and re-request review.
- A design disagreement, scope growth, or a comment that rests on a
  misreading: stop and ask the user, with a recommendation. Before changing a
  deliberate decision, recover why it was made.
- Conflict or branch behind: update it the way the repo says, re-run the quick
  checks, push.
- Approved, checks green, no open threads: stop and say it is ready to merge.
  Never merge from here.
