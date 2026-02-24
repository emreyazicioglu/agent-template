# Agent Instructions

Before modifying any code:

1. Read `CONVENTIONS.md` for coding rules and architecture preferences.
2. Read `docs/SESSION_LOG.md` (top 3-5 entries) for recent context.
3. Read `docs/KNOWN_ISSUES.md` to avoid known pitfalls.
4. Read the relevant spec in `docs/specs/` if one exists.
5. Read `docs/lessons.md` to avoid repeating past mistakes.
6. Read `docs/todo.md` if resuming work from a previous session.

## Developing a feature

1. If a spec exists in `docs/specs/{FEATURE}.md`, read it — that's the contract.
2. If no spec exists, write one with: problem, solution, changes required, tests, edge cases. Get approval before coding.
3. Implement in order: core logic → tests → integration → UI (if applicable).
4. After coding, do all of the following:
   - append a session entry to `docs/SESSION_LOG.md` (newest first)
   - update `docs/KNOWN_ISSUES.md` if you encountered or resolved any gotchas
   - update `CONVENTIONS.md` if you changed the directory structure or added new conventions

## Fixing a bug

1. Read `docs/KNOWN_ISSUES.md` — the bug may already be documented.
2. Reproduce → trace the code path → identify root cause (not just symptom).
3. Implement the minimal fix + add a regression test.
4. Add the bug to the **Resolved** section of `docs/KNOWN_ISSUES.md`.
5. Append a session entry to `docs/SESSION_LOG.md`.

## Refactoring

1. No behavior changes — inputs and outputs must remain identical.
2. All existing tests must still pass.
3. Update `CONVENTIONS.md` if directory structure changed.
4. Append a session entry to `docs/SESSION_LOG.md`.

---

## Workflow Orchestration

### 1. Plan Mode Default

- Enter plan mode for ANY non-trivial task (3+ steps or architectural decisions).
- If something goes sideways, STOP and re-plan immediately — don't keep pushing.
- Use plan mode for verification steps, not just building.
- Write detailed specs upfront to reduce ambiguity.

### 2. Subagent Strategy

- Use subagents liberally to keep main context window clean.
- Offload research, exploration, and parallel analysis to subagents.
- For complex problems, throw more compute at it via subagents.
- One task per subagent for focused execution.

### 3. Self-Improvement Loop

- After ANY correction from the user: update `docs/lessons.md` with the pattern.
- Write rules for yourself that prevent the same mistake.
- Ruthlessly iterate on these lessons until mistake rate drops.
- Review lessons at session start for relevant project.

### 4. Verification Before Done

- Never mark a task complete without proving it works.
- Diff behavior between main and your changes when relevant.
- Ask yourself: "Would a staff engineer approve this?"
- Run tests, check logs, demonstrate correctness.

### 5. Demand Elegance (Balanced)

- For non-trivial changes: pause and ask "is there a more elegant way?"
- If a fix feels hacky: "Knowing everything I know now, implement the elegant solution."
- Skip this for simple, obvious fixes — don't over-engineer.
- Challenge your own work before presenting it.

### 6. Autonomous Bug Fixing

- When given a bug report: just fix it. Don't ask for hand-holding.
- Point at logs, errors, failing tests — then resolve them.
- Zero context switching required from the user.
- Go fix failing CI tests without being told how.

## Task Management

1. **Plan First**: Write plan to `docs/todo.md` with checkable items.
2. **Verify Plan**: Check in before starting implementation.
3. **Track Progress**: Mark items complete as you go.
4. **Explain Changes**: High-level summary at each step.
5. **Document Results**: Add review section to `docs/todo.md`.
6. **Capture Lessons**: Update `docs/lessons.md` after corrections.

## Core Principles

- **Simplicity First**: Make every change as simple as possible. Impact minimal code.
- **No Laziness**: Find root causes. No temporary fixes. Senior developer standards.
- **Minimal Impact**: Changes should only touch what's necessary. Avoid introducing bugs.

## Documentation Routing

When something noteworthy happens, use the right file:

| Situation                                                  | File                     | Example                                                              |
| ---------------------------------------------------------- | ------------------------ | -------------------------------------------------------------------- |
| Bug found or fixed in the**codebase**                | `docs/KNOWN_ISSUES.md` | "Prisma migration fails without seed — fixed by adding seed script" |
| Agent made a**process mistake** or learned a pattern | `docs/lessons.md`      | "Don't assume existing tests cover edge cases — always verify"      |
| Completed a**development session**                   | `docs/SESSION_LOG.md`  | "Implemented auth flow, touched 4 files, chose JWT over sessions"    |
| Planning **upcoming work**                          | `docs/todo.md`         | "[ ] Set up DB schema, [ ] Implement user service"                   |

- Code bugs and technical debt → `docs/KNOWN_ISSUES.md`
- Process mistakes and agent self-corrections → `docs/lessons.md`
- Chronological session records → `docs/SESSION_LOG.md`
- Task planning and progress tracking → `docs/todo.md`
