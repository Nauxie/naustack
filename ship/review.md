# Review

A review loop on your own branch, so a bot or a person doesn't have to catch
it. For someone else's PR, use the `say` skill instead.

1. Pin down the target: branch, base, PR, changed files, check status,
   existing comments.
2. Map the diff by subsystem and risk, and name the invariants it touches: API
   contracts, data shape, auth, error handling, migrations, tests.
3. Give each subagent one lane (correctness, data flow, security, tests, or
   one subsystem) and ask for concrete findings only: where, the reachable
   failure, how severe, the smallest fix.
4. Verify every finding against the code before editing. Drop the ones whose
   failure can't be reached.
5. Fix what is real and in scope with the smallest change that keeps
   behaviour. Add a test where the bug would be easy to bring back.
6. Run type-check, lint and the tests for what you touched.
7. Hand the new diff to a reviewer with fresh context. Don't tell it what was
   already found: a reviewer told what was found tends to confirm it.

Stop when a fresh reviewer finds no blocker and nothing that should be fixed.
Narrow edge cases and nits don't start another round: list them and let the
user decide. Run the end-to-end check once, on the final head.

Stay in scope. Fix what the branch introduced, not what looks imperfect nearby.
