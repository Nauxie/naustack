# Merge

From a final check, through the merge, to the change verified where it
deployed. Then stop.

## Two limits

- Merge only the PRs the user named in this request. Green checks, an
  approval, your own plan, or permission from an earlier session are not their
  word.
- Stop at the first environment the merge deploys to. Never start a promote to
  the next one, not even as a plan or a dry run: it ships everything since the
  last release, not only this change.

## Before

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
pushed later rides along. A stack merges bottom-up, and a child never goes in
before its parent has landed.

## Verify

- Find the deploy the merge started and confirm the released commit is yours
  or a descendant of it. Your own run being green is not that.
- Check the behaviour the PR changed, in that environment. A green deploy and
  a health check show the service started, not that the change works.
- Read fresh logs for new errors since the deploy.

## If something fails

Stop merging anything that depends on it, and keep the evidence. Retry only
what is clearly transient. A revert, a redeploy or a repair is the user's
call: say what is live, what is broken, and what you recommend.
