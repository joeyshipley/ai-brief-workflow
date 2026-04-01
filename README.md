# Brief Workflow

A portable, AI-agnostic workflow system for structured collaboration between humans and AI across multiple sessions. Brief-driven development: the brief is the unit of work, the persistent context, and the defense against hallucination.

## The Problem

AI context windows compress and reset. When they do, the AI loses track of decisions, assumptions, and progress. It fills the gaps with confident fabrication. The longer the session, the worse the drift. The more sessions a task spans, the more state gets lost between them.

The brief system prevents this by externalizing state into structured documents that survive any context reset. Close a session, start a new one, load the brief -- everything is where you left it.

## How It Works

Two layers:

**Portable layer (`.claude/`)** -- The workflow engine. Commands, workflow docs, brief template. Copy to any project.

**Project layer (`.workflow/`)** -- Project-specific configuration. Which files to read on session start, what checks to apply during brief creation, where briefs are stored.

## Commands

| Command | What it does |
|---------|-------------|
| `/session` | Start a session. Loads project context, asks what to work on. |
| `/brief-create` | Create a new brief from intent. Guided conversation to capture Goal, Problem, Success Signal, Constraints, and Phases. |
| `/brief-check` | Validate current findings against the problem statement and success signals. Mid-phase sanity check. |
| `/phase-next` | Advance to the next phase. Compares checkpoint vs outcome, reviews later phases. |
| `/brief-complete` | Close a brief. Learning extraction, rule promotion check, mark complete. |
| `/braintrust` | Design review panel. Runs each perspective from `.workflow/braintrust.md` as an isolated agent against a feature or decision. |

## Setup

### Step 1: Copy the portable layer into your project

Copy the `.claude/` directory from this repo into your project root:

```
your-project/
  .claude/
    commands/         -- Command stubs (session, brief-create, brief-check, phase-next, brief-complete, braintrust)
    docs/workflow/    -- Workflow docs and brief template
```

If you're not using Claude Code, skip `.claude/commands/` and wire the workflow docs into your AI tool's command system instead. The docs themselves are tool-agnostic.

### Step 2: Copy the project layer

Copy the `.workflow/` directory from this repo into your project root:

```
your-project/
  .workflow/
    config.md         -- Project-specific settings (you'll edit this)
    braintrust.md     -- Perspective panel for design reviews (you'll edit this)
    briefs/           -- Where active briefs are stored
    briefs/completed/ -- Where completed briefs are moved
    scratch/          -- Agent working files and review outputs
```

### Step 3: Edit `.workflow/config.md` for your project

This is the interface between the workflow engine and your project. Open it and update:

**Session Reads** -- List the files the AI should read at the start of every session. These are your project's context files -- whatever someone needs to read to understand where the project is and what's active.

```markdown
## Session Reads
1. `README.md`
2. `docs/ROADMAP.md`
```

**Brief Creation Checks** -- Project-specific checks to run when planning a new brief. These are questions the AI asks during phase planning. If your project has architectural boundaries, compliance requirements, or domain rules that every brief should consider, list them here.

```markdown
## Brief Creation Checks
- **API boundary check:** If the work changes a public API, note which consumers may be affected.
- **Migration check:** If the work touches the database schema, include a migration phase.
```

Or just leave it as "None." if your project doesn't need special checks yet.

**Work Categories** -- What kinds of work happen in your project. Displayed during session start to help route the user.

```markdown
## Work Categories
- **Backend:** API, database, services
- **Frontend:** UI, components, styling
- **Infrastructure:** CI/CD, deployment, monitoring
- **Documentation:** Guides, API docs, architecture docs
```

**Project Commands** -- Any project-specific commands you've added beyond the workflow commands.

### Step 4: Edit `.workflow/braintrust.md` for your product

The included braintrust panel is a generic starting point (New User, Daily User, Power User, Paying Customer, Reluctant User). Replace these with the real perspectives for your product -- the people who use, depend on, and are affected by what you build.

For each perspective, define:
- **Who they are** -- a short scenario that makes them real
- **Their test** -- the specific lens they evaluate through
- **What they catch** -- the failure modes only they would notice

Also update the **Traps** (common failure modes) and **Meta-Principles** (rules the panel enforces) to match your product's values.

### Step 5: Start a session

Run `/session`. The AI reads your config, loads your project context, and asks what you want to work on.

- **New work** -- `/brief-create` walks you through capturing a brief
- **Existing brief** -- pick up where you left off in the current phase
- **Quick task** -- no ceremony, just do it

## The Brief

A brief is a self-contained work specification that spans multiple sessions. Each phase follows the same rhythm:

**Checkpoint** -- Snapshot assumptions at phase start.
**Research** -- Investigate what needs understanding.
**Findings** -- What you learned.
**Adjustments** -- What changed and why.
**Work Plan** -- Concrete tasks (code, design, assets, research -- whatever fits).
**Review** -- Dual-lens: big picture + dependencies, then implementation details.
**Done** -- What actually shipped, compared against checkpoint.

At brief completion: **Learning Log** (what surprised us, what to change) and **Rule Candidates** (principles worth promoting to project rules).

The brief template lives at `.claude/docs/workflow/brief-template.md`. The `/brief-create` command reads it automatically.

## The Braintrust

A design review system where each perspective runs as its own isolated agent. No perspective sees another's assessment. When multiple isolated perspectives independently flag the same issue, that convergence is a strong signal.

The panel lives at `.workflow/braintrust.md`. Run `/braintrust` to launch a review. Results are written to dated folders in `.workflow/scratch/`.

## Principles

- **The brief is the state.** Not the conversation, not the AI's memory. The brief.
- **Phase goals are outcomes, not solutions.** Write what changes, not what you'll implement. Research determines the how.
- **Phases beyond Phase 1 are tentative.** Research often changes the plan. That's the point.
- **Conflict resolution on every context load.** Any time prior decisions are loaded: "Does anything decided since contradict this?"
- **Checkpoint at every phase boundary.** Write what you expect at the start. Compare against what happened at the end.
- **Learning extraction at completion.** Every brief teaches something. Capture it before closing.

## AI-Agnostic

This system is markdown files with conventions. The workflow docs, brief template, project config, and braintrust panel contain no references to any specific AI tool, model, or platform. The `.claude/commands/` stubs are the only Claude Code-specific piece -- replace them with your tool's equivalent command format and everything else works unchanged.

## License

MIT
