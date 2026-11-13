# Cleanup

Clean only what this session created or started: worktrees, branches,
processes, build outputs, temp files, containers, scheduled jobs, drafts.
Build that list from the session's own history. If you can't tell whether you
made something, it is not yours.

1. Inventory first, with each item's state. Whether its PR is merged, closed
   or still open decides what can go.
2. Decide each item: finished goes, still needed stays with a reason, not
   yours is reported only. Never clear a shared cache.
3. Ask before deleting uncommitted or unpushed work, the remote branch of an
   unmerged PR, a key someone else might use, or anything outward-facing.
4. Clean in this order:
   - stop your processes by the exact id you started, never by name or pattern
   - delete temp files that hold credentials
   - remove finished worktrees and their branches
   - remove their build outputs, your containers, and the remaining temp files
   - cancel your scheduled jobs, and tell the user about unsent drafts instead
     of deleting them
5. Verify every item: directory gone, process gone, port free, branch gone.

Report one line per item: cleaned, kept and why, left over and not yours,
needs the user.
