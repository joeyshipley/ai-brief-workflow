# Brief Creation

**Purpose:** Convert human intent into a structured brief through conversation.

Briefs are worked across multiple sessions. They must be self-resuming: every session loads the brief and picks up where it left off.

---

## Workflow

### 1. Understand Intent

Ask these questions to extract the brief invariants:

| Question | Maps To |
|----------|---------|
| "What are you building or changing?" | Goal |
| "What's broken or missing today?" | Problem |
| "How will you know it works?" | Success Signal |
| "What can't change?" | Constraints |

**Listen for:**
- Uncertainty -> capture in Open Questions
- Clarity -> ready for phase breakdown
- User impact -> capture in Problem / Success Signal

### 2. Capture Unknowns

Ask: "What don't we know yet?"

Record in Open Questions. These drive research in each phase.

### 3. Break into Phases

Work with the user to identify logical chunks:
- Each phase has a clear goal (what it achieves)
- **Phase goals are outcomes, not solutions.** Write what changes, not what you'll implement. Research determines the how.
- **Phases beyond Phase 1 are tentative.** They represent best-guess direction. Research often changes the plan. That's the point.
- Phases are sequential -- later phases may depend on earlier findings
- Don't over-plan -- 2-4 phases is usually enough to start

**Project-specific checks:** Read `.workflow/config.md` section **Brief Creation Checks**. Apply each listed check during phase planning. These are project-specific constraints that every brief in this project must consider.

### 4. Create Brief

**File location:** Read `.workflow/config.md` section **Briefs Directory** for the path.

**Naming:** `[category]_[feature].md`

**Template:** `.claude/docs/workflow/brief-template.md`

**Fill in:**
- Goal, Problem, Success Signal, Constraints (invariants)
- Phase table with goals
- Open Questions
- Leave per-phase sections empty (filled during work)

### 5. Next Steps

Tell the user:
> "Brief created at `[path]`. Ready to start Phase 1 research, or saving for later?"

**If start now:** Begin Phase 1 using `.claude/docs/workflow/phase-workflow.md`
**If later:** Brief saved for new session

---

## Existing Brief

If the user references an existing brief:
1. Read the brief
2. Find current phase (first incomplete phase)
3. Resume work using `.claude/docs/workflow/phase-workflow.md`
