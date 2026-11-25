# End to end

One pass from "it builds" to a reviewed PR, proven in the real product. The
other steps do the work; this one sets their order and the bar between them.

1. Build the change on a branch, in its own worktree where the repo uses
   them. Run the repo's type-check, lint and the tests for what you touched.
2. Review it (`review.md`) and fix what that finds.
3. Check it end to end through the real product path:
   - Run what the user runs, with the consumer's real configuration: a local
     stack or a shared dev environment, not mocks or a separate harness.
   - UI: a real browser with the repo's supported test sign-in, your own
     headless one, never a window someone is watching. Keep before and after
     screenshots for the PR.
   - A contract between services: assert what the downstream side receives.
   - Model calls: read the captured traces.
   - Missing setup, missing auth or a skipped assertion is not a pass. Write
     down what you could not check.

   If this finds a problem, fix it and review the changed code again.
4. Open the PR (`pr.md`) with the screenshots on it and the review ask out.
5. Report the PR, what the end-to-end check showed, and what you could not
   verify, in a few lines. Merging still needs the user's word.
