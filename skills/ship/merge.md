# Merge

From a final check, through the merge, to the change verified where it
deployed. Then stop. This is for repos that release to users. In a personal
sandbox, a plain merge is enough.

## Two limits

- Merge only the PRs the user named in this request. Green checks, an
  approval, your own plan, or permission from an earlier session are not their
  word.
- Stop at the first environment the merge deploys to. Never start a promote to
  the next one, not even as a plan or a dry run: it ships everything since the
  last release, not only this change.

## Before

- Read how the repo merges and releases, every time. It changes.
- Re-check each PR now: head commit, required checks, approvals, open threads.
  If commits landed after the approval, re-read the diff.
- Work out what the merge will deploy. If it reaches further than usual, say
  so and wait.
- A change that only works if two things deploy at the same moment is not
  ready.
- If a check is failing or an approval is missing, don't bypass it. Fix what
  is yours, or report what is blocking.

## Merge

Use the repo's normal path, pinned to the head commit you checked, so nothing
pushed later rides along. A merge queue can drop a PR for a failure in the
batch that isn't its own: read the run before re-queueing. A stack merges
bottom-up, and a child never goes in before its parent has landed.

## Verify

- Find the deploy the merge started and confirm the released commit is yours
  or a descendant of it. Your own run being green is not that.
- Check the behaviour the PR changed, in that environment. A green deploy and
  a health check show the service started, not that the change works.
- Read fresh logs for new errors since the deploy, and the result of any
  scheduled post-deploy check. Don't trigger one that spends a budget.

## After

Remove the PR's worktree, branch and build output without being asked, once
nothing in them is uncommitted or still running. Report what merged, what you
saw in the environment, what you could not check, and that later
environments were not touched.

## If something fails

Stop merging anything that depends on it, and keep the evidence. Retry only
what is clearly transient. A revert, a redeploy or a repair is the user's
call: say what is live, what is broken, and what you recommend.
