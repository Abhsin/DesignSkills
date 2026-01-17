# Assumption Mapping Examples

Worked examples showing the assumption mapping process end-to-end.

## Contents
- Example 1: SaaS productivity tool
- Example 2: Mobile consumer app
- Example 3: Internal tool for team

---

## Example 1: SaaS Productivity Tool

**Context**: Solo dev building an AI meeting notes tool.

**User said**: "I'm building an AI that joins meetings and generates summaries. Busy professionals will pay $20/month because they hate taking notes."

### Extracted Assumptions

| # | Assumption | Type | Impact | Uncertainty |
|---|------------|------|--------|-------------|
| 1 | Professionals hate taking meeting notes | Desirability | 5 | 3 |
| 2 | AI-generated summaries are accurate enough | Feasibility | 5 | 4 |
| 3 | Users will let a bot join their meetings | Usability | 5 | 4 |
| 4 | $20/month is acceptable price point | Viability | 4 | 3 |
| 5 | IT departments will approve the tool | Feasibility | 4 | 4 |
| 6 | Users will read the summaries | Desirability | 3 | 3 |
| 7 | Summaries replace manual notes entirely | Desirability | 3 | 4 |

### Priority Matrix Result

**Validate First (High Impact + High Uncertainty)**:
- #2: AI accuracy
- #3: Bot joining acceptance
- #5: IT approval

**Validate Later**:
- #1: Note-taking pain (likely true, lower uncertainty)
- #4: Price point

**Monitor**:
- #6, #7: Important but not blocking

### Recommended Tests

1. **AI accuracy** → Technical spike: Process 10 real meeting recordings, have users rate summary quality (4 hours)
2. **Bot acceptance** → 5 interviews: "Would you add a recording bot to your team meetings?" (2 hours)
3. **IT approval** → Talk to 2 IT admins about security requirements (1 hour)

---

## Example 2: Mobile Consumer App

**Context**: Designer building a habit tracking app.

**User said**: "I want to build a habit tracker that uses AI to suggest optimal habit timing. People will use it daily because building habits is hard."

### Extracted Assumptions

| # | Assumption | Type | Impact | Uncertainty |
|---|------------|------|--------|-------------|
| 1 | People want help building habits | Desirability | 4 | 2 |
| 2 | AI timing suggestions improve habit formation | Desirability | 5 | 5 |
| 3 | Users will grant calendar/activity access | Usability | 4 | 3 |
| 4 | Daily engagement is achievable | Desirability | 5 | 4 |
| 5 | Free + premium model is viable | Viability | 4 | 3 |
| 6 | App Store discovery is sufficient | Viability | 3 | 4 |

### Priority Matrix Result

**Validate First**:
- #2: AI timing value (highest uncertainty, core differentiator)
- #4: Daily engagement

**Validate Later**:
- #3: Permission acceptance
- #5: Monetization model

**Safe to Assume**:
- #1: Habit help demand (well-established market)

### Recommended Tests

1. **AI timing value** → Wizard of Oz test: Manually suggest times to 10 users, track if compliance improves vs control (1 week)
2. **Daily engagement** → Fake door: Build bare-bones tracker, measure Day 7 retention (1 week)

---

## Example 3: Internal Tool

**Context**: Engineer building a deployment dashboard for their team.

**User said**: "Our team wastes time checking multiple systems for deployment status. I'll build a unified dashboard."

### Extracted Assumptions

| # | Assumption | Type | Impact | Uncertainty |
|---|------------|------|--------|-------------|
| 1 | Team actually checks multiple systems | Desirability | 4 | 2 |
| 2 | Unified view saves meaningful time | Desirability | 4 | 3 |
| 3 | All systems have accessible APIs | Feasibility | 5 | 3 |
| 4 | Team will adopt a new tool | Usability | 4 | 3 |
| 5 | Dashboard stays maintained | Viability | 3 | 4 |
| 6 | Read-only access is sufficient | Desirability | 3 | 2 |

### Priority Matrix Result

**Validate First**:
- #3: API accessibility (blocking if false)

**Validate Later**:
- #2: Time savings value
- #4: Team adoption

**Safe to Assume**:
- #1: Current behavior (easily observable)
- #6: Read-only needs (can add actions later)

### Recommended Tests

1. **API accessibility** → Spend 2 hours checking each system's API docs and auth requirements
2. **Time savings** → Shadow 2 teammates during deployment, measure current time spent

---

## Pattern: Assumption Extraction from Common Phrases

| When user says... | Extract this assumption... |
|-------------------|---------------------------|
| "Everyone needs..." | Some people need this |
| "It's obvious that..." | Users understand this without explanation |
| "They'll just..." | Users will take this action without friction |
| "We can easily..." | This is technically straightforward |
| "People already pay for..." | Price point is validated by competitors |
| "Nobody wants to..." | Pain point is universal and severe |
| "Once they see it..." | Value is self-evident on first use |
| "We'll figure out..." | This unknown won't block progress |
