Read `.workflow/braintrust.md` to load the panel, traps, and meta-principles.

The Braintrust is a set of perspectives that every feature checks against. They represent the people who use, depend on, and are affected by what you're building. If a feature fails any of them, the feature needs work.

## Step 1: Gather Input

Ask the user:
1. What feature, system, or decision should the panel review?
2. **Full panel** or a **focused set?** If focused, which perspectives?
3. Should the review also check against **The Traps** (failure modes the panel watches for)?

## Step 2: Prepare the Review Brief

Write a short summary of what's being reviewed -- the feature/system description, enough context for each perspective to evaluate independently. If relevant docs exist, note which ones each agent should read.

## Step 3: Create Scratch Folder

Create a dated folder for this review's scratch files:

**Path:** `.workflow/scratch/YYYY-MM-DD_braintrust_[subject-slug]/`

Each agent will write its findings to a file in this folder.

## Step 4: Launch Independent Reviews

**Every perspective runs as its own isolated agent so no perspective can influence another.**

For each selected perspective, launch an Agent with subagent_type "general-purpose". Each agent receives:
- The full text of ONLY its panel member's description from `.workflow/braintrust.md` (who they are, what they catch)
- The meta-principles section
- The traps section (if the user requested trap checks -- include which traps this perspective is responsible for catching)
- The review brief from Step 2
- Any docs relevant to the feature

Each agent's prompt should instruct it to:
1. Embody this perspective fully. You are this person. Read the feature through your eyes.
2. Answer: Do you understand why this feature is there? Does it serve you? Does it respect you?
3. Apply your specific test
4. Check whether the feature violates any meta-principle
5. Flag any trap patterns you're responsible for catching (if traps were requested)
6. **Write your findings** to `.workflow/scratch/[dated-folder]/[perspective-slug].md`
7. Return a structured report:
   - **Verdict:** Passes / Concern / Fails
   - **Reasoning:** Why, in this person's voice
   - **Trap flags:** Any trap patterns detected (or "None")

The scratch file should contain the full reasoning, not just the summary. This is the permanent record of the review.

**Launch all agents in parallel** (single message, multiple Agent tool calls). For large panels, launch the first batch and use run_in_background for the rest.

## Step 5: Compile Results

Once all agents return:

1. **Read all scratch files** from the dated folder.

2. **Collect all verdicts** into a summary table:

| Perspective | Verdict | Key Concern |
|-------------|---------|-------------|
| [Name] | Passes / Concern / Fails | [One-line summary or "None"] |

3. **Surface all failures and concerns** -- group by theme, not by perspective. A concern from two different perspectives about the same issue reinforces the signal.

4. **Note convergence** -- when multiple isolated perspectives independently flag the same issue without seeing each other's assessment, that's a strong signal. Call it out explicitly.

5. **Write a synthesis file** to `.workflow/scratch/[dated-folder]/synthesis.md` with the summary table, themed concerns, convergence notes, and any recommendations.

6. **Present to the user** with the summary table first, then themed concerns with convergence notes, then point them to the scratch folder for full per-perspective reports.
