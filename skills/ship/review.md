# Review

A review loop on your own branch, so a bot or a person doesn't have to catch
it. For someone else's PR, use the `say` skill instead.

1. Pin down the target: branch, base, PR, changed files, check status,
   existing comments.
2. Map the diff by subsystem and risk, and name the invariants it touches: API
   contracts, data shape, auth, error handling, migrations, tests.
3. Give each subagent one lane (correctness, data flow, security, tests, or
   one subsystem), at high effort, and ask for concrete findings only: where,
   the reachable failure, how severe, the smallest fix.
4. For a non-trivial change, add a pass from another model family (below).
5. Verify every finding against the code before editing. Drop the ones whose
   failure can't be reached.
6. Fix what is real and in scope with the smallest change that keeps
   behaviour. Add a test where the bug would be easy to bring back.
7. Run type-check, lint and the tests for what you touched.
8. Hand the new diff to a reviewer with fresh context. Don't tell it what was
   already found: a reviewer told what was found tends to confirm it.

Stop when a fresh reviewer finds no blocker and nothing that should be fixed.
Narrow edge cases and nits don't start another round: list them and let the
user decide. Run the end-to-end check once, on the final head. The ask for a
human review doesn't wait for later rounds: once CI is green and the first
round's blockers are fixed, it can go out.

Before calling it done, check every existing review thread, review body and
bot comment, old rounds included, against the current head.

Stay in scope. Fix what the branch introduced, not what looks imperfect nearby.

## Another model family

One family misses what another catches. Pick the reviewer for each change
from the families that are not yours (Claude, GPT through Codex, Gemini
through Antigravity), by what the change needs and how that reviewer's
findings held up before. A hard change (large, concurrent, money, auth) gets
both. Run it headless in the background, in a checkout of the head, told not
to edit files. Ask it only for defects it can show are reachable, with the
failing input and the smallest fix: no style or speculative hardening. If
it's out of usage, use the other, or skip it and say so. Never block on it.
Say which kept findings came from which family.
