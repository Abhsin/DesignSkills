# Prioritization Frameworks Reference

Detailed explanations of frameworks for feature prioritization and scope definition.

---

## Impact vs Effort Matrix

Map features by their expected impact and implementation effort to identify quick wins and avoid money pits.

### How It Works

Plot each feature on a 2x2 grid:

```
High Impact │  Big Bets     │  Quick Wins
            │               │
            │ (Plan first)  │ (Do first)
────────────┼───────────────┼─────────────
Low Impact  │  Money Pits   │  Easy Adds
            │               │
            │ (Cut these)   │ (Do last)
            └───────────────┴─────────────
              High Effort     Low Effort
```

### Quadrant Definitions

**Quick Wins (High Impact, Low Effort)**
- Do these first for MVP
- Validate assumptions quickly
- Build momentum
- Examples: Email login, basic search, simple filtering

**Big Bets (High Impact, High Effort)**
- Plan carefully, break into phases
- Include in MVP only if core to value prop
- Otherwise defer to v1.1 after validating Quick Wins
- Examples: Real-time collaboration, ML recommendations, complex workflows

**Easy Adds (Low Impact, Low Effort)**
- Do after Quick Wins if time permits
- Good for polish phase
- Don't let these delay launch
- Examples: Dark mode, export to PDF, profile avatars

**Money Pits (Low Impact, High Effort)**
- Cut entirely from MVP
- Only build if user research proves it's actually high impact
- Common trap: "Competitor has it so we need it"
- Examples: Custom themes, advanced analytics, integrations nobody asked for

### Estimation Tips

**Impact scoring:**
- Ask: "Does this solve the core problem?"
- Ask: "How many users need this?"
- Ask: "What's the revenue/retention impact?"
- Score 1-10 or High/Medium/Low
- When in doubt, ask users directly

**Effort scoring:**
- Consider: Development time, testing, edge cases
- Consider: Dependencies on other features
- Consider: Team skill level with required tech
- Score 1-10 or High/Medium/Low
- Add 50% buffer to developer estimates

### When to Use

- Starting a new project (prioritize initial features)
- Roadmap planning (decide what's next)
- Scope negotiation (defend cuts to stakeholders)
- Resource allocation (finite team, which work matters most)

### Pitfalls to Avoid

- **Everything in Quick Wins** — Be honest about effort. Complex features aren't "low effort."
- **Everything in High Impact** — Force rank. Not all features matter equally.
- **Ignoring dependencies** — "Low effort" features that require "high effort" infrastructure first
- **Individual scoring** — Different people see impact/effort differently. Score as a team.

---

## MoSCoW Method

Force explicit prioritization by categorizing every feature as Must, Should, Could, or Won't.

### Categories Defined

**Must Have**
- Product literally doesn't work without it
- Core value proposition depends on it
- Legal/compliance requirement
- MVP cannot ship without this

**Tests:**
- "Can users accomplish the primary goal without this?"
- "Would we be embarrassed to ship without this?"
- "Is this the reason users would pay/use this product?"

**Examples:**
- Task app: Create task, mark complete, view list
- Recipe scaler: Input servings, see scaled ingredients
- Login system: Authentication, password reset

---

**Should Have**
- Important but not critical
- Significant impact on UX
- MVP can ship without it but v1.1 should have it
- Users would notice if missing but wouldn't abandon product

**Tests:**
- "Would power users complain without this?"
- "Does this significantly reduce friction?"
- "Is there an acceptable workaround if we skip it?"

**Examples:**
- Task app: Due date filtering, task categories
- Recipe scaler: Save favorite recipes
- Login system: OAuth providers (Google, GitHub)

---

**Could Have**
- Nice to have
- Minimal impact if absent
- Build only if time/budget permits
- Polish, not function

**Tests:**
- "Would anyone notice if we never built this?"
- "Is this purely for delight, not utility?"
- "Are we building this because it's easy, not because it matters?"

**Examples:**
- Task app: Dark mode, custom themes
- Recipe scaler: Recipe notes field
- Login system: Profile pictures

---

**Won't Have (This Time)**
- Explicitly out of scope
- Document these to prevent scope creep
- May revisit in future versions
- Important to write these down

**Why Won't Have:**
- Too complex for current resources
- Doesn't align with core value prop
- Validating simpler approach first
- Needs user feedback before building

**Examples:**
- Task app: Team collaboration (building for solo use first)
- Recipe scaler: Meal planning calendar (focus on single recipe first)
- Login system: 2FA (defer until security is proven concern)

### Decision Process

For each feature:

1. Start by assuming it's **Won't Have**
2. Argue why it should be **Must Have**
3. If argument fails, try **Should Have**
4. If that fails, try **Could Have**
5. Default back to **Won't Have**

This forces you to justify inclusion, not exclusion.

### When to Use

- MVP definition (draw hard lines)
- Stakeholder alignment (get everyone to agree on priorities)
- Scope creep prevention ("We agreed this was Won't Have")
- Release planning (Must + Should = v1.0, Could = v1.1)

### Pitfalls to Avoid

- **Too many Must Haves** — If you have 20 "Must Have" features, your MVP is too big
- **No Won't Haves** — If everything is in scope, nothing is prioritized
- **Ignoring Should Haves** — These are your v1.1. Don't forget to plan for them.
- **Reclassifying mid-project** — Stick to your decisions unless new data emerges

---

## RICE Scoring

Quantitative framework for ranking features by Reach, Impact, Confidence, and Effort.

### Formula

```
RICE Score = (Reach × Impact × Confidence) / Effort
```

Higher score = higher priority

### Definitions

**Reach**
- How many users will this affect in a given time period?
- Measure: Number of users per quarter or per release
- Examples:
  - Feature used by all users daily: 1000 users/quarter
  - Feature used by 10% monthly: 30 users/quarter
  - Feature used once at signup: 500 users/quarter

**Impact**
- How much will this move the needle for each user?
- Scale: 3 = massive, 2 = high, 1 = medium, 0.5 = low, 0.25 = minimal
- Examples:
  - Massive (3): Solves primary pain point, users would pay for this alone
  - High (2): Significantly improves experience
  - Medium (1): Noticeable improvement
  - Low (0.5): Minor convenience
  - Minimal (0.25): Nice to have

**Confidence**
- How sure are you about Reach and Impact estimates?
- Scale: 100% = high, 80% = medium, 50% = low
- Examples:
  - High (100%): Strong user research, analytics data
  - Medium (80%): Some data, reasonable assumptions
  - Low (50%): Guess based on intuition

**Effort**
- How many person-months will this take?
- Measure: Total team time (design + dev + test)
- Examples:
  - 0.5 months: One developer, one week
  - 2 months: One developer, full sprint
  - 6 months: Two developers, three sprints

### Worked Example

**Feature: Add task due date filtering**

- **Reach:** 200 users will use this per quarter (out of 1000 total users)
- **Impact:** 2 (high impact for users who use it)
- **Confidence:** 80% (have interview data from 5 users)
- **Effort:** 1 month (straightforward UI + backend work)

```
RICE = (200 × 2 × 0.8) / 1 = 320
```

**Feature: Real-time task collaboration**

- **Reach:** 50 users will use this per quarter (small teams only)
- **Impact:** 3 (massive for those who use it)
- **Confidence:** 50% (speculative, no direct feedback)
- **Effort:** 6 months (WebSocket infrastructure, conflict resolution, etc.)

```
RICE = (50 × 3 × 0.5) / 6 = 12.5
```

**Conclusion:** Filtering scores 320, collaboration scores 12.5 → Build filtering first.

### When to Use

- Comparing many features (10+)
- Data-driven organizations
- Justifying priorities to stakeholders
- Feature backlogs with competing urgency

### Pitfalls to Avoid

- **False precision** — Don't spend hours debating if something is 1.7 or 1.8 impact
- **Ignoring qualitative factors** — Strategic bets don't always score high
- **Gaming the system** — Inflating Reach/Impact to push pet features
- **Effort underestimation** — Classic developer trap, always add buffer

---

## Kano Model

Classify features by how they affect user satisfaction to avoid building things users don't care about.

### Categories

**Must-Be Features (Basic Needs)**
- Users expect these
- Absence causes dissatisfaction
- Presence doesn't increase satisfaction (it's expected)
- These are table stakes

**Examples:**
- Login system: Password reset
- E-commerce: Shopping cart
- Task app: Create and view tasks
- Mobile app: Works without crashing

**Strategy:** Build these first, but don't over-invest. Users won't praise you for having them.

---

**Performance Features (Satisfiers)**
- More is better
- Linear relationship: better performance = more satisfaction
- Users can articulate these ("I wish it was faster/easier/cheaper")

**Examples:**
- Page load speed
- Search result relevance
- Number of integrations
- Price/value ratio

**Strategy:** Optimize these after Must-Be features. Diminishing returns kick in.

---

**Delighters (Attractive Features)**
- Users don't expect these
- Absence doesn't cause dissatisfaction
- Presence creates joy and differentiation
- Users can't ask for these (they don't know to want them)

**Examples:**
- Gmail's undo send
- Stripe's beautiful error messages
- Notion's slash commands
- GitHub's Copilot

**Strategy:** Sprinkle these in after core features work. These create word-of-mouth.

---

**Indifferent Features**
- Users don't care either way
- Building these is wasted effort
- Often what teams think users want vs. what users actually want

**Examples:**
- Features copied from competitors that your users don't need
- Over-customization options
- Metrics/analytics users never check
- Complex features with low adoption

**Strategy:** Cut these ruthlessly. Do user research to identify before building.

---

**Reverse Features**
- Presence actually causes dissatisfaction
- More is worse
- Rare, but important to catch

**Examples:**
- Too many notifications
- Forced tutorials that can't be skipped
- Auto-play videos
- Required social features in productivity tools

**Strategy:** Avoid entirely or make optional.

### How to Use Kano

**For each feature, ask users:**

1. **Functional question:** "How would you feel if this feature was present?"
   - I like it
   - I expect it
   - I'm neutral
   - I can tolerate it
   - I dislike it

2. **Dysfunctional question:** "How would you feel if this feature was NOT present?"
   - I like it
   - I expect it
   - I'm neutral
   - I can tolerate it
   - I dislike it

**Interpret responses:**
- Must-Be: Expect it present, dislike it absent
- Performance: Like it present, dislike it absent
- Delighter: Like it present, neutral if absent
- Indifferent: Neutral either way
- Reverse: Dislike it present

### When to Use

- Deciding between features with similar impact
- Understanding user expectations vs. opportunities
- Avoiding over-building
- Differentiating from competitors

### Pitfalls to Avoid

- **Confusing Must-Be with Delighter** — Just because you think it's cool doesn't mean users expect it
- **Over-indexing on Delighters** — Build Must-Be first
- **Ignoring Indifferent** — These waste time. Cut them.
- **Survey bias** — Users say they want features they won't actually use

---

## Value vs Complexity Matrix

Simplify prioritization for small teams by mapping features on value to user vs. complexity to build.

### How It Works

Similar to Impact/Effort but with tighter focus on user value and technical complexity.

```
High Value  │  Strategic    │  Low-Hanging
            │               │  Fruit
            │ (Plan & Bet)  │ (Do Now)
────────────┼───────────────┼─────────────
Low Value   │  Time Sinks   │  Fill-Ins
            │               │
            │ (Cut)         │ (Polish)
            └───────────────┴─────────────
              High Complex.   Low Complex.
```

### When to Use Instead of Impact/Effort

- Solo developer or small team (2-3 people)
- Simple product with clear user needs
- Want to move fast without overthinking

### Value Assessment

**High Value:**
- Directly solves primary user pain point
- Users have explicitly requested this
- Revenue-generating or retention-boosting
- Core differentiator from alternatives

**Low Value:**
- Nice to have
- Rare use case
- Aesthetic improvement
- Feature parity with competitor

### Complexity Assessment

**Low Complexity:**
- Uses existing patterns/components
- No new dependencies
- No data model changes
- Can ship in < 1 week

**High Complexity:**
- New technical domain (e.g., adding payments)
- Significant refactoring required
- New infrastructure (e.g., background jobs)
- Edge cases multiply

### Decision Rules

1. **Low-Hanging Fruit (High Value, Low Complexity)** → Do immediately
2. **Strategic (High Value, High Complexity)** → Plan carefully, potentially phase
3. **Fill-Ins (Low Value, Low Complexity)** → Do during polish/downtime
4. **Time Sinks (Low Value, High Complexity)** → Cut entirely

---

## Framework Selection Guide

### Which framework should you use?

**Impact vs Effort Matrix**
- Best for: Initial MVP scoping
- Team size: Any
- When: Starting from scratch with many ideas
- Output: Visual prioritization

**MoSCoW**
- Best for: Stakeholder alignment
- Team size: Any
- When: Need clear communication about what's in/out
- Output: Explicit categories

**RICE**
- Best for: Data-driven teams with many competing features
- Team size: 5+ people
- When: You have user data and analytics
- Output: Ranked list with scores

**Kano Model**
- Best for: Understanding user expectations
- Team size: Any
- When: Want to avoid building things users don't want
- Output: Feature classification

**Value vs Complexity**
- Best for: Solo devs and small teams
- Team size: 1-3 people
- When: Need to move fast
- Output: Quick prioritization

### Can you use multiple frameworks?

Yes, and often you should:

1. **Kano** → Identify Must-Be vs Delighter vs Indifferent
2. **Impact/Effort** → Prioritize Must-Be and Delighters
3. **MoSCoW** → Communicate scope to stakeholders

Or:

1. **RICE** → Score all features quantitatively
2. **MoSCoW** → Group top RICE scorers into Must/Should/Could

---

## Anti-Patterns

### The "Everything is High Priority" Trap
**Symptom:** Every feature scores high on impact/value
**Fix:** Force rank. Top 3 only.

### The "Analysis Paralysis" Trap
**Symptom:** Spending days scoring features instead of building
**Fix:** Set a 1-hour timebox. Rough estimates are fine.

### The "HiPPO" Problem (Highest Paid Person's Opinion)
**Symptom:** Prioritization based on who shouts loudest
**Fix:** Use frameworks to make decisions transparent and data-driven

### The "Pet Feature" Trap
**Symptom:** Features you want to build ranked higher than user needs
**Fix:** Involve users in scoring. Their priorities often differ from yours.

### The "Competitor Copycat" Trap
**Symptom:** Building features just because competitors have them
**Fix:** Ask "Do OUR users need this?" not "Do they have this?"
