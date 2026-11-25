# Start a worker

Only when the user asks for the lane, or for a review someone asked of them
by name (`tick.md`).

1. Write the brief to a file: the goal, what is already decided or ruled out,
   where the work lives, and the end state. Add the paragraph from
   `worker.md`, filled in. Never switch off a step the worker's own skill
   requires unless the user said to. Don't make the end state a report file
   unless they asked: the worker reports in its own tab, short.
2. Pick the agent, model and effort the job needs, and read the account's
   limits before every start and resume. Pass the model explicitly: a resumed
   session may have run on one that is now out of room. When one family's
   limits are tight, drop a level of effort and lean on the other families
   for reviews. Leave a running lane on its model: switching re-reads its
   whole context.
3. Pick the machine. Use the local one only when the work needs it
   (simulators, local sign-ins, a browser the user watches), otherwise a
   cloud machine that can run the lane. Ask before creating a new one.
4. Long inline commands get rejected, so put the launch in a script that runs
   the agent with the brief, then open it in a new tab:
   - here: `cmux new-surface --type terminal --pane <pane> --command 'exec
     /bin/zsh <launcher>'`
   - on a cloud machine: `cmux surface new-terminal --machine <machine> --name
     "<lane>" -- <command>`

   Put the tab where the user would: read their layout and place it beside
   related work.
5. Name the tab after the lane (`cmux rename-tab --surface <tab> "<lane>"`),
   and read its screen once to confirm it started.

Every machine with workers pulls the same skills (`git pull --ff-only`) on
each tick, so all workers follow the same rules.
