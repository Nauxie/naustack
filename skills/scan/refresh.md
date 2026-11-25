# Refresh

What is open: who is waiting on the user, what moved, and what they should do
next.

1. Work from the sources every time. A refresh built on an earlier one misses
   things.
2. Find the workstreams: every running agent session and every open PR. For
   each, note what it is doing and whether it is running, waiting on the user,
   or finished, and flag a session close to its usage limit. Read past session
   transcripts too: a promise made in chat is often already kept in a session
   that has since closed.
3. Sweep chat, code review and the issue tracker for the window: every direct
   and group message, every thread the user posted in or was tagged in, every
   PR of theirs or awaiting their review, every issue assigned to them that
   changed. Give the slow sources to subagents if you have them.
4. Cross-check before calling anything open. Plans move between sources: a
   date agreed in one chat gets changed in another, a review asked for in a
   thread gets answered on the PR. Report the latest version and where it came
   from.

## Report

A session heading toward a production release without the user's word goes
first. Then group by workstream, most pressing first. Not by source, and not
by priority. For each one: what it is doing, its PR's review and check state,
and its open items with who is waiting, on what, since when, and the next
step. Then work that fits no workstream yet, with what a new session would do
(start it only on their yes), then news that needs no action.

Write every item so it stands alone: what is pending in plain words, why it
matters now, what is ready, and the one decision needed. Name the people.
Name an issue by its title and link, not its id. Never refer to an item by a
label from an earlier report.

Keep to engineering work and what sits next to it. Leave out personal and
admin items, and what the user said they would handle themselves. After the
first refresh of the day, cover only what changed, plus a short list of what
still needs them.
