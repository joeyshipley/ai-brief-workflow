# Phase Workflow

**Purpose:** Guide work within a single phase of a brief. Every phase follows the same rhythm regardless of project type.

---

## Starting a Phase

1. Read the brief. Identify the current phase (first phase with "Not Started" status).
2. Update the phase status to **In Progress**.
3. **Write the Checkpoint:** Record the current assumptions, the planned approach, and what you expect to find. This is a snapshot -- it will be compared against when the phase ends.
4. Begin research.

## Working the Phase

### Research

Investigate what needs to be understood before doing the work. This varies by phase type:
- **Engineering:** Read code, understand patterns, identify constraints
- **Design:** Gather references, study comparable systems, identify trade-offs
- **Exploration:** Search, read, consult sources, build understanding

Record findings as you go. Don't wait until research is "complete" to start writing Findings.

### Findings -> Adjustments

When research reveals something that changes the approach:
1. Record the finding
2. Record the adjustment (what changed and why)
3. If the adjustment affects later phases, note it -- but don't rewrite later phases yet

### Work Plan

Once research is sufficient, create the work plan. Be specific enough that work can proceed without re-reading the research:
- **Code projects:** Atomic tasks. Test-implement pairs where the project uses TDD. Match the project's methodology.
- **Design projects:** Proposals, reviews, decisions to make
- **Asset/production work:** Steps, review gates, deliverables
- **Research/exploration:** Synthesis tasks, documents to produce

### Execute

Do the work. Update the Work Plan items as they complete.

### Review (Dual-Lens)

When the phase's work is done, review through both lenses before marking complete:

**Lens 1 -- Big picture + dependencies:**
- Does this output serve the brief's Goal?
- Did anything change that invalidates or reshapes later phases?
- Any upstream/downstream impacts?

**Lens 2 -- Implementation details:**
- Is the work correct and complete for this phase's scope?
- Anything rough that will compound?

Record the review in the phase's Review section.

## Completing a Phase

1. Fill in the **Done** section with what actually shipped/produced.
2. Compare Done against the **Checkpoint.** Note any divergence -- this is learning, not failure.
3. Update the phase status to **Complete**.
4. If the review identified changes to later phases, update the phase table now.

## Conflict Resolution

Any time you load prior decisions from earlier phases or sessions:
> "Does anything decided since contradict what was just loaded?"

Surface conflicts before proceeding. Don't silently override or silently continue with stale context.
