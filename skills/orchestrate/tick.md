# Tick

One check of every worker. Run it when asked, and on a timer with whatever
the agent has for that (a loop or a scheduled job).

1. Drain the Feed, then read every worker: `cmux read-screen --surface <tab>
   --lines 40`, or its transcript when the screen is scrolled. A worker that
   can't post to the Feed gets read every time. Note each one as running,
   finished, waiting on the user, stalled (it said it would do approved work,
   then stopped with nothing running), or stuck on a dialog or a usage limit.
2. Act only within what the user already approved:
   - stalled: nudge it to carry on with that work
   - stuck on a limit: move the work, or tell the user if it can't move
   - a PR ready for review or re-review: its worker writes the ask, after
     checking it isn't already there (draft or send, by the mode)
   - finished: see `close.md`
3. Sweep for what is new since the last tick: the user's sweep skill, or
   their messages, mentions, replies in threads they are in, code review and
   issue tracker. Read chats by activity, not unread count: the user may have
   read them elsewhere. Take the window's start from the clock, never a
   guessed time. Pass each new item to the worker that owns it. What no
   worker owns goes to the user.
4. A review someone asks of the user by name is already their work: start a
   lane for it and tell them. For a re-review, resume the session that did
   the first one if it is recent. A review lane that can't start leads the
   next report, with what would unblock it.
5. Report once. First each open decision, numbered, in a sentence or two with
   your pick. Then what was done or staged, then what else changed. Name PRs
   by what they do. Name the tabs that can close. Suggest a few lanes worth
   starting, with your pick. If nothing changed, say so in one line.

A worker's "urgent" is a claim. Check it against the user's decisions and
what actually breaks before passing it on. Show a new draft once, with where
it is and its text. A saved draft is never an outstanding ask: read the
thread for what was posted before reporting its state.
