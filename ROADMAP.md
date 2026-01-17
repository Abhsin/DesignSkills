# Design Skills for AI-Native Product Development

## Vision

Solo devs and small teams are using AI to build apps at unprecedented speed, but products often lack user-centered thinking because AI loses that context. These skills inject design thinking into the AI-assisted development workflow, ensuring products are grounded in real user needs and validated assumptions.

**Tagline:** "Design skills for builders, not analysts."

## The Problem

Current AI coding workflows skip critical pre-build validation:

```
Today:    Idea → Code → Ship → Hope it works
Better:   Idea → Validate → Define → Build → Evaluate → Iterate
```

Existing skills (PRD generators, business analysis) focus on **documenting decisions** after they're made. We focus on **making better decisions** before building.

## Positioning vs. Existing Skills

| Business Analysis Skills | Our Skills |
|--------------------------|------------|
| Business-centered | User-centered |
| Comprehensive frameworks | Modular interventions |
| Enterprise scale | Solo dev / small team |
| Document the analysis | Validate before building |
| Strategic planning | Tactical action |
| Hours to complete | Minutes to complete |
| Stakeholder alignment | User truth |

**The pitch:**
> "PRD skills help you document decisions. Design thinking skills help you make better decisions to document."

---

## The Complete Pipeline

```
Pre-Planning → PRD → UX Doc → Prompts → Code → Evaluate
```

### Visual Flow (Consolidated)

```
┌─────────────────────┐
│   PRE-PLANNING      │  ← Our skills (validate before building)
│                     │
│  problem-framing    │  ✅ Done
│  user-modeling      │  ✅ Done (includes user discovery)
│  assumption-mapping │  ✅ Done
│  ideation           │  🔲 Next (HMW + rapid ideation)
│  solution-scoping   │  ✅ Done (includes MVP + prototyping)
│  competitor-scan    │  🔲 Optional (P2)
└──────────┬──────────┘
           ↓
┌─────────────────────┐
│      PRD            │  ← Our skill (lean documentation)
│                     │
│  prd-generation     │  ✅ Done
└──────────┬──────────┘
           ↓
┌─────────────────────┐
│    UX SPEC          │  ← Our skill (comprehensive UX definition)
│                     │
│  ux-specification   │  ✅ Done
│  (includes flows,   │     (covers user-flows, ui-inventory,
│   components,       │      interaction-spec, content-structure)
│   interactions)     │
└──────────┬──────────┘
           ↓
┌─────────────────────┐
│    PROMPTS          │  ← Our skill (bridge to code)
│                     │
│  prompt-export      │  ✅ Done
│  (includes spec     │     (covers spec-to-prompt, context-packaging,
│   conversion,       │      incremental-build-plan)
│   context,          │
│   sequencing)       │
└──────────┬──────────┘
           ↓
┌─────────────────────┐
│     CODE            │  ← Claude Code (existing)
└──────────┬──────────┘
           ↓
┌─────────────────────┐
│    EVALUATE         │  ← Our skills (validate after building)
│                     │
│  heuristic-eval     │  ✅ Done
│  critique           │  🔲 Next
│  usability-test     │  🔲 Next
│  accessibility      │  🔲 Optional (P2)
└─────────────────────┘
```

---

## Consolidated Skill Set

**Total: 13 skills** (down from 19 through consolidation)

### Phase 1: Pre-Planning Skills (5-6 skills)

**Purpose:** Validate the idea before investing in building.

| Skill | What It Does | Status | Priority |
|-------|--------------|--------|----------|
| `problem-framing` | Extract problem statements, target users, JTBD from fuzzy ideas | ✅ Done | P0 |
| `user-modeling` | Research, recruit, and model user behavior (includes user discovery) | ✅ Done | P0 |
| `assumption-mapping` | Surface and prioritize risky assumptions for validation | ✅ Done | P0 |
| `ideation` | Reframe problems (HMW) and generate solution concepts (rapid ideation) | 🔲 Next | P1 |
| `solution-scoping` | Prioritize features, define MVP boundaries, plan prototypes | ✅ Done | P0 |
| `competitor-scan` | Analyze competitive landscape and identify gaps | 🔲 Optional | P2 |

**Consolidation notes:**
- `user-modeling` absorbed `user-discovery` - now includes recruitment strategies
- `solution-scoping` absorbed `prototype-planning` - now includes validation planning
- `ideation` merges `hmw-reframing` + `rapid-ideation` - single divergent thinking skill

---

### Phase 2: Documentation Skills (2 skills)

**Purpose:** Document requirements and design decisions.

| Skill | What It Does | Status | Priority |
|-------|--------------|--------|----------|
| `prd-generation` | Generate lean PRDs with user stories, features, acceptance criteria | ✅ Done | P0 |
| `ux-specification` | Define flows, screens, components, interactions, and states | ✅ Done | P0 |

**Consolidation notes:**
- `ux-specification` absorbed `user-flow-mapping`, `ui-inventory`, `interaction-spec`, `content-structure`
- Single comprehensive UX documentation skill instead of 4 separate ones

---

### Phase 3: Prompt Skills (1 skill)

**Purpose:** Bridge design artifacts to code generation.

| Skill | What It Does | Status | Priority |
|-------|--------------|--------|----------|
| `prompt-export` | Convert specs into sequenced prompts with context and checkpoints | ✅ Done | P0 |

**Consolidation notes:**
- `prompt-export` absorbed `spec-to-prompt`, `context-packaging`, `incremental-build-plan`
- Single skill handles entire spec-to-code bridge

---

### Phase 4: Evaluation Skills (4 skills)

**Purpose:** Validate what was built.

| Skill | What It Does | Status | Priority |
|-------|--------------|--------|----------|
| `heuristic-evaluation` | Systematic usability review using Nielsen's 10 heuristics | ✅ Done | P0 |
| `critique` | Structured feedback using Likes/Wishes/Wonders or Rose/Thorn/Bud | 🔲 Next | P1 |
| `usability-test-guide` | Create test scripts, tasks, and observation templates | 🔲 Next | P1 |
| `accessibility-audit` | WCAG compliance checking with issue identification | 🔲 Optional | P2 |

**No consolidation:** These serve distinct purposes at different stages.

---

## Current Progress

### ✅ Completed Skills (8/13 core)

1. **problem-framing** - Problem statements and target users
   - Status: ✅ Complete
   - Missing: Reference examples

2. **user-modeling** - User personas and scenarios
   - Status: ✅ Complete
   - Missing: Reference examples, user discovery content

3. **assumption-mapping** - Assumption prioritization
   - Status: ✅ Complete
   - Has: references/validation-methods.md, references/examples.md

4. **solution-scoping** - MVP definition and feature prioritization
   - Status: ✅ Complete
   - Missing: Reference examples, prototype planning content

5. **prd-generation** - Product requirements documentation
   - Status: ✅ Complete (renamed from prd-gen)
   - Missing: Reference examples

6. **ux-specification** - Comprehensive UX documentation
   - Status: ✅ Complete (renamed from ux-gen)
   - Missing: Reference examples

7. **prompt-export** - Sequenced prompt generation
   - Status: ✅ Complete
   - Missing: Reference examples

8. **heuristic-evaluation** - Usability review
   - Status: ✅ Complete
   - Has: references/frameworks.md, references/examples.md

**Completion: 62% of core skills (8/13)**

---

### 🔲 Next Skills to Build (5 remaining)

**Wave 1: Ideation (P1)**
9. **ideation** - Problem reframing + solution generation
   - Combines HMW questions with rapid ideation
   - Method: SCAMPER framework, divergent thinking
   - Output: 8-12 solution concepts, HMW questions
   - Time estimate: 2-3 hours

**Wave 2: Evaluation (P1)**
10. **critique** - Structured design feedback
    - Framework: Likes/Wishes/Wonders or Rose/Thorn/Bud
    - Output: Balanced feedback document
    - Time estimate: 1-2 hours

11. **usability-test-guide** - User testing preparation
    - Output: Test script, task list, recruitment guide
    - Time estimate: 2-3 hours

**Wave 3: Optional (P2)**
12. **competitor-scan** - Competitive analysis
    - Output: Landscape summary, differentiation opportunities
    - Time estimate: 2-3 hours

13. **accessibility-audit** - WCAG compliance
    - Framework: WCAG 2.1 guidelines
    - Output: Issue list with fixes
    - Time estimate: 2-3 hours

---

## Priority Actions

### Immediate (Complete existing skills)
1. **Add reference files** to 6 skills missing them:
   - problem-framing/references/examples.md
   - user-modeling/references/examples.md
   - solution-scoping/references/frameworks.md + examples.md
   - prd-generation/references/examples.md + templates.md
   - ux-specification/references/examples.md + patterns.md
   - prompt-export/references/examples.md + sequencing.md

2. **Expand existing skills** with absorbed content:
   - user-modeling: Add user discovery/recruitment section
   - solution-scoping: Add prototype planning section

**Time estimate:** 3-4 hours
**Impact:** Makes 8 skills production-ready

---

### Short-term (Fill critical gaps)
3. **Build `ideation` skill** (merges HMW + rapid ideation)
   - Fills gap between problem definition and solution scoping
   - Time estimate: 2-3 hours

4. **Build `critique` skill**
   - Complements heuristic-evaluation with structured feedback
   - Time estimate: 1-2 hours

**Time estimate:** 3-5 hours
**Impact:** 10/13 skills complete (77%)

---

### Long-term (Complete the set)
5. **Build `usability-test-guide`**
6. **Build `competitor-scan`** (if needed)
7. **Build `accessibility-audit`** (if needed)

**Time estimate:** 4-6 hours
**Impact:** 13/13 skills complete (100%)

---

## Skill Architecture Standards

All skills follow Anthropic's best practices:

### Structure
```
skill-name/
├── SKILL.md              # Core instructions (<500 lines)
└── references/
    ├── frameworks.md     # Detailed methodology (optional)
    ├── examples.md       # Worked examples
    └── templates.md      # Output templates (optional)
```

### SKILL.md Template
```markdown
---
name: skill-name
description: [What it does]. Use when [triggers].
---

# Skill Name

Brief description (1 sentence).

## Why This Exists

Single sentence explaining the value.

## Input Requirements

What the skill needs to work effectively.

## Workflow

Step-by-step process.

## Output Format

Structured template showing expected output.

## Adaptation Guidelines

How to adjust for different project sizes.

## Handoff

What happens next, which skills this feeds into.
```

### Design Principles
- **Concise:** SKILL.md under 500 lines, details in references
- **Modular:** Each skill standalone, composable with others
- **Actionable:** Output is a next step, not a document
- **Fast:** Minutes, not hours
- **Adaptive:** Adjusts to user expertise

---

## Success Metrics

### For Individual Skills
- Triggers correctly (no false positives/negatives)
- Completes in <10 minutes for typical use
- Output is actionable (user knows what to do next)
- Works across Haiku/Sonnet/Opus

### For the System
- Users complete pre-planning before building
- Fewer pivots after building starts
- Higher user satisfaction with shipped products
- Skills compose naturally in workflows

---

## Eliminated Skills (Merged)

These were in the original roadmap but have been consolidated:

### Merged into `user-modeling`:
- ❌ `user-discovery` - User recruitment and research planning

### Merged into `solution-scoping`:
- ❌ `prototype-planning` - Prototype fidelity and validation planning
- Note: Previously called `mvp-scoping` in roadmap

### Merged into `ux-specification`:
- ❌ `user-flow-mapping` - User flows and journeys
- ❌ `ui-inventory` - Component cataloging
- ❌ `interaction-spec` - Interaction details
- ❌ `content-structure` - Content planning

### Merged into `prompt-export`:
- ❌ `spec-to-prompt` - Spec conversion
- ❌ `context-packaging` - Context organization
- ❌ `incremental-build-plan` - Build sequencing

### Merged into new `ideation` skill:
- ❌ `hmw-reframing` - How Might We questions
- ❌ `rapid-ideation` - Solution concept generation

**Consolidation benefits:**
- Reduced from 19 to 13 skills (32% reduction)
- Less context switching for users
- More cohesive workflows within skills
- Easier to maintain and update

---

## Changelog

- 2026-01-16: Major consolidation - reduced from 19 to 13 skills through strategic merging
- 2026-01-16: Completed 8 core skills (problem-framing, user-modeling, assumption-mapping, solution-scoping, prd-generation, ux-specification, prompt-export, heuristic-evaluation)
- 2026-01-16: Renamed prd-gen → prd-generation, ux-gen → ux-specification for discoverability
- 2026-01-16: Trimmed "Why This Exists" sections to single sentences per best practices
- 2025-01-13: Added hmw-reframing, rapid-ideation, prototype-planning skills (19 total)
- 2025-01-13: Initial roadmap created
- 2025-01-13: assumption-mapping and heuristic-evaluation completed
