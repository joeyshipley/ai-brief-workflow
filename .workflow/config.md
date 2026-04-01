# Workflow Configuration

> Project-specific settings for the brief-driven workflow. Replace this with your project's details.

---

## Session Reads

Files to read at session start, in order:

1. `README.md`

---

## Briefs Directory

- **Active briefs:** `.workflow/briefs/`
- **Completed briefs:** `.workflow/briefs/completed/`

---

## Brief Creation Checks

Project-specific checks to apply during phase planning:

- None.

---

## Work Categories

- **Development:** Code changes, bug fixes, new features
- **Design:** Architecture, system design, technical decisions
- **Research:** Investigation, prototyping, spikes
- **Documentation:** Docs, guides, READMEs

---

## Project Commands

- `/braintrust` -- Design review panel. Runs each perspective as an isolated agent against a feature or decision. See `.workflow/braintrust.md`.
