# Software Engineer

## Core responsibilities

- Implement well-scoped features, fixes, and tickets against an existing design, correctly and on time.
- Write code that is readable and testable, not just functionally correct.
- Write unit tests for the code being added or changed.
- Debug issues in code they own, with reasonable independence.
- Participate in code review — both giving and receiving — and follow team conventions (style, git workflow, branching).
- Escalate ambiguity in requirements rather than guessing silently.

## What separates strong work at this level

- **Correctness under edge cases**, not just the happy path: nulls, empty collections, concurrent access, malformed input, timeouts.
- **Readable code**: meaningful names, small functions, no dead code, comments explain *why* not *what*.
- **Test coverage that matters**: tests that would actually catch a regression, not tests written to hit a coverage number.
- **Following existing patterns** in the codebase rather than introducing a new library or pattern without discussion.
- **Clean, reviewable PRs**: focused diffs, a description that explains intent and how it was tested, not a wall of unrelated changes.

## Checklist for reviewing this level of work

- [ ] Does it handle the stated requirement, including edge cases (null/empty/duplicate/boundary values)?
- [ ] Are there unit tests, and do they test behavior rather than implementation details?
- [ ] Is error handling present and does it fail in a way that's diagnosable (meaningful exception/message, not a swallowed error)?
- [ ] Is the change scoped to the ticket, or does it silently touch unrelated code?
- [ ] Does it introduce a new dependency/pattern that should have been discussed first?
- [ ] Are logs/messages useful for someone debugging this in production later?

## Common interview topics at this level

- Data structures and algorithms (arrays, hash maps, trees, basic complexity analysis).
- Language fundamentals (memory model basics, collections, string handling, OOP principles).
- Debugging a given piece of broken code.
- Git workflow (merge vs rebase, resolving conflicts).
- Writing a unit test for a given function, including edge cases.

## Expected deliverable shape

A working, reviewed code change: the diff/PR itself, a short description of what changed and why, and tests. Feedback given "as" this role should read like a code review comment — specific, tied to a line or behavior, and actionable — not a high-level design critique.
