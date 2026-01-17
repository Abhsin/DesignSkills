# Validation Methods Reference

Quick, lightweight ways to test assumptions before building.

## Contents
- Desirability validation
- Feasibility validation
- Viability validation
- Usability validation
- Choosing the right method

## Desirability Validation

**Question**: Do people actually want this?

### 5-User Interview (2-4 hours)
Ask 5 people who match your target user:
1. "Tell me about the last time you experienced [problem]"
2. "What did you do about it?"
3. "What was frustrating about that?"

**Success signal**: 4/5 describe the problem unprompted with emotional language.

### Fake Door Test (1-2 hours to set up)
Add a button/link for the feature that doesn't exist yet. Track clicks.

**Success signal**: >5% click-through indicates interest.

### Landing Page Test (4-8 hours)
Single page describing the value proposition with email signup.

**Success signal**: >10% email conversion from targeted traffic.

### Search Volume Check (30 minutes)
Check Google Trends, keyword tools for problem-related searches.

**Success signal**: Consistent or growing search volume.

---

## Feasibility Validation

**Question**: Can we actually build this?

### Technical Spike (2-8 hours)
Build the riskiest technical component in isolation.

**Success signal**: Core mechanism works, no blocking unknowns.

### API/Integration Check (1-2 hours)
Verify third-party services have required capabilities.

**Success signal**: Documentation confirms endpoints exist, rate limits are acceptable.

### Performance Prototype (4-8 hours)
Test with realistic data volumes.

**Success signal**: Response times within acceptable range at expected scale.

### Expert Consultation (1 hour)
Talk to someone who's built similar systems.

**Success signal**: No "that's impossible" or "that will take 10x longer than you think."

---

## Viability Validation

**Question**: Can this sustain itself?

### Competitor Pricing Scan (1-2 hours)
Document pricing of 5+ alternatives.

**Success signal**: Market supports price point needed for sustainability.

### Willingness-to-Pay Interview (2-4 hours)
Ask potential users: "What would you expect to pay?" then "Would you pay [2x that]?"

**Success signal**: Stated WTP covers costs with margin.

### Unit Economics Sketch (1-2 hours)
Calculate: Customer Acquisition Cost vs Lifetime Value.

**Success signal**: LTV > 3x CAC.

### Channel Feasibility Check (2-4 hours)
Research cost to reach target users through intended channels.

**Success signal**: CAC is sustainable at intended price point.

---

## Usability Validation

**Question**: Can people figure out how to use this?

### Hallway Test (30-60 minutes)
Show prototype to 3 people. Ask them to complete a task. Don't help.

**Success signal**: 2/3 complete task without assistance.

### First-Click Test (1-2 hours)
Show a screen, ask "Where would you click to [do X]?"

**Success signal**: >70% click the right area.

### 5-Second Test (1 hour)
Show design for 5 seconds, ask "What is this for?"

**Success signal**: >80% correctly identify the purpose.

### Think-Aloud Session (1-2 hours per user)
User narrates while using prototype. Note confusion points.

**Success signal**: No critical blockers, confusion is cosmetic not structural.

---

## Choosing the Right Method

| Time available | Desirability | Feasibility | Viability | Usability |
|----------------|--------------|-------------|-----------|-----------|
| < 1 hour | Search volume | API check | Competitor scan | 5-second test |
| 1-4 hours | 5 interviews | Expert call | WTP interview | Hallway test |
| 4-8 hours | Fake door | Technical spike | Unit economics | Think-aloud |
| 1-2 days | Landing page | Performance prototype | Channel test | Full usability study |

## Validation Anti-Patterns

**Asking friends and family** — They'll be nice, not honest.

**Asking "would you use this?"** — Everyone says yes. Ask about past behavior instead.

**Over-validating safe assumptions** — If failure is recoverable, just build it.

**Validating too many at once** — Focus on 1-2 critical assumptions per cycle.

**Waiting for perfect data** — Directional signal is enough to proceed or pivot.
