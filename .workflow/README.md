# Project Workflow Layer

This directory contains project-specific workflow state. It is separate from the portable workflow engine in `.claude/`.

## Structure

```
.workflow/
  config.md              -- Project-specific settings (edit this for your project)
  braintrust.md          -- Perspective panel for design reviews (edit for your product)
  briefs/                -- Active briefs (created by /brief-create)
  briefs/completed/      -- Completed briefs (moved here by /brief-complete)
  scratch/               -- Agent working files, review outputs, intermediate notes
```

## Config

`config.md` is the interface between your project and the portable workflow. Edit it to define:
- What files to read at session start
- Where briefs are stored
- Project-specific checks during brief creation
- What kinds of work happen in this project
- Any project-specific commands

## Briefs

Briefs are created by `/brief-create` using the template at `.claude/docs/workflow/brief-template.md`. They are named `[category]_[feature].md` and stored in `briefs/`. When completed via `/brief-complete`, they are moved to `briefs/completed/`.

## Braintrust

`braintrust.md` defines the perspectives your product checks against. These are the people who use, depend on, and are affected by what you build. The included panel is a generic starting point -- replace it with perspectives specific to your product.

Run `/braintrust` to launch a review. Each perspective runs as its own isolated agent so they can't influence each other.

## Scratch

Working files for agents and intermediate outputs. Braintrust reviews write each perspective's findings to a dated subfolder here (e.g., `scratch/2026-03-31_braintrust_onboarding-flow/`).
