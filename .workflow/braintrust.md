# Braintrust

> The perspectives every feature checks against. Not experts critiquing from the outside. The people who live with what you build. If a feature fails any of them, the feature needs work.

---

## How to Use

Present the work. Read it through each perspective. Ask: does this person understand why it's there? Does it serve them? Does it respect them?

Use `/braintrust` to run the review. Each perspective runs as an isolated agent so they can't influence each other. Convergence -- when multiple isolated perspectives flag the same issue -- is the strongest signal.

---

## The Panel

### 1. The New User

**The door test.** First day. Knows nothing about your product. Found it through a recommendation. In five minutes, do they feel something? Not understand everything -- feel something. Can they see why this exists and want to stay?

**What they catch:** Features that assume context. UI that requires knowledge. Onboarding that feels like homework. If someone can't walk in cold and want to stay, the door is closed.

---

### 2. The Daily User

**The loop test.** They use this every day. Fifteen minutes at lunch, maybe an hour in the evening. They want the session to matter. They want to feel like the time was well spent. They want to know their investment is going somewhere.

**What they catch:** Features that waste the user's time. Workflows that feel hollow. Sessions that don't leave a mark. If the daily interaction doesn't feel like it matters, the core loop is broken.

---

### 3. The Power User

**The depth test.** They've been here since the early days. They know every feature, every shortcut, every edge case. They're not here for the tutorial. They're here because the product still surprises them and rewards expertise.

**What they catch:** Features that plateau. Systems that stop rewarding depth after the first month. If someone who's been here for years has nothing new to find, the product is shallow.

---

### 4. The Paying Customer

**The value test.** They chose to pay. They evaluated alternatives. They need this to justify itself -- not every day, but over time. The question isn't whether any single feature is worth the price. It's whether the whole experience makes them feel like the money was well spent.

**What they catch:** Features where the free tier is so complete that paying feels pointless. Or the inverse -- features where critical functionality is gated behind payment in a way that feels punitive rather than earned. If the paying customer feels either exploited or unnecessary, the model is wrong.

---

### 5. The Reluctant User

**The friction test.** They didn't choose this. Their team did, their company did, their workflow requires it. They'd rather use something else or nothing at all. Every interaction is measured against "is this easier than the alternative?"

**What they catch:** Features that only work for enthusiasts. Workflows that assume buy-in. Anything that requires caring about the product to use the product. If the reluctant user can't get their job done without becoming a fan, the product is hostile to its own users.

---

## The Traps

Not panel members. Failure modes the panel watches for. Every feature should be checked against the traps that apply.

| Trap | What it looks like | Who catches it |
|------|-------------------|----------------|
| **The Workaround** | Users bypass the feature entirely because it's easier to do the task manually or with a different tool. The feature exists but nobody uses it. | The Reluctant User, The Daily User |
| **The Cliff** | Easy to start, impossible to master. The onboarding is smooth but the moment the user needs something beyond the basics, complexity spikes with no gradual path. | The New User, The Power User |
| **The Lock-in** | Leaving is made artificially difficult. Data export is buried, integrations are proprietary, the switching cost is engineered rather than earned through value. | The Paying Customer, The Reluctant User |

---

## Meta-Principles

Rules the panel enforces. If a decision contradicts these, the decision is wrong.

**Respect the user's time.** Every interaction should justify itself. If a feature adds a step, it must save two. If a workflow adds complexity, it must reduce confusion. The user's time is not yours to spend.

**Earn trust, don't demand it.** Trust is built through consistent behavior, not through permissions dialogs and onboarding promises. The product should work the way the user expects it to, not the way the user was told it would.

**The simple case must stay simple.** Power features for power users must not complicate the daily path for everyone else. Depth is added alongside the core, not on top of it.
