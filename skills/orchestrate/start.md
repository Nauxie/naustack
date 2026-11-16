# Start a worker

Only when the user asks for the lane.

1. Write the brief to a file: the goal, what is already decided or ruled out,
   where the work lives, and the end state. Add the paragraph from
   `worker.md`, filled in.
2. Pick the agent, model and effort for the job, and the machine whose account
   has room for it (see `SKILL.md`).
3. Long inline commands get rejected, so put the launch in a script that runs
   the agent with the brief, then open it in a new tab:
   - here: `cmux new-surface --type terminal --pane <pane> --command 'exec
     /bin/zsh <launcher>'`
   - on a cloud machine: `cmux surface new-terminal --machine <machine> --name
     "<lane>" -- <command>`
4. Name the tab after the lane (`cmux rename-tab --surface <tab> "<lane>"`),
   and read its screen once to confirm it started.
