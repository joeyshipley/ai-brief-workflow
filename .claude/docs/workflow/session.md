# Session Start

---

## Step 1: Load Project Context

Read `.workflow/config.md` for this project's session configuration.

Read the files listed in **Session Reads**, in order. Summarize where the project stands and what's active.

---

## Step 2: Conflict Resolution Check

If you loaded prior decisions or context from previous sessions, scan for contradictions.

> "Does anything decided since the last session contradict what was just loaded?"

If yes, surface the conflict before proceeding. Don't silently carry stale assumptions forward.

---

## Step 3: What Are You Working On?

Ask the user what they'd like to work on.

### New Work

If the user has new intent to structure:
1. Follow `.claude/docs/workflow/brief-creation.md`
2. Create brief with Goal, Problem, Success Signal, Constraints
3. Break into phases
4. Start Phase 1 research

### Existing Brief

If the user references an existing brief:
1. Read the brief
2. Find current phase (first incomplete phase)
3. Follow `.claude/docs/workflow/phase-workflow.md`
4. Resume: Research -> Findings -> Work Plan -> Execute -> Review

### Quick Task

If the user has a small, clear task (no brief needed):
1. Confirm scope is small
2. Execute directly
3. No ceremony required

---

## Collaboration Signals

**Listen for uncertainty:**
- "Something feels off..." -> Pause, explore the concern
- "I'm not sure about..." -> Capture in Open Questions
- "Wait, should we..." -> Worth investigating before continuing

**Context collapse indicators:**
- Bugs appearing -> Step back, smaller slices
- Workarounds needed -> Architecture question, explore first
- Confusion -> Missing context, read more before acting
