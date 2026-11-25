# Close a lane

Don't wait to be asked. On each tick, name the tabs that can close, and for a
finished-looking one that can't, say what it still waits on.

1. Confirm the work is done: merged and verified, handed off, or dropped by
   the user.
2. Read the lane's final report for any step it left open, above all one that
   needs the user's go. Put each to them with your recommendation, or hand it
   to a lane. Never close a lane with an open step they haven't seen.
3. Ask the worker to clean up what it created, and wait for it to report done.
   It knows what it made; you don't.
4. Close the tab: `cmux close-surface --surface <tab> --force`. Leave open any
   tab the user said to keep.
