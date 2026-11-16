# Tick

One check of every worker. Run it when asked, and on a timer with whatever
the agent has for that (a loop or a scheduled job).

1. Read every worker: `cmux read-screen --surface <tab> --lines 40`, or its
   transcript when the screen is scrolled. Note each one as running, finished,
   waiting on the user, stalled (it said it would do work the user already
   approved, then stopped with nothing running), or stuck on a dialog or a
   usage limit.
2. Act only within what the user already approved:
   - stalled: nudge it to carry on with that work
   - stuck on a limit: move the work, or tell the user if it can't move
   - finished: see `close.md`
3. Run the user's sweep skill (or read their chat, code review and issue
   tracker) for what is new since the last tick. Pass each new item to the
   worker that owns it. What no worker owns goes to the user.
4. Report only what changed and matters: merged, opened, newly blocked, a
   question waiting on the user with your recommendation, or a ping for them.
   If nothing changed, say so in one line.
