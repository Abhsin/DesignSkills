# FocusFlow Test Artifacts

Complete end-to-end test suite for DesignSkills pipeline validation.

## Overview

This directory contains a complete project that flows through all 8 DesignSkills:

```
Raw Idea → problem-framing → user-modeling → assumption-mapping
→ solution-scoping → prd-generation → ux-specification → prompt-export
→ [Build] → heuristic-evaluation
```

## Project: FocusFlow

**Concept:** A Chrome extension that helps remote workers stay focused by blocking distracting websites during self-defined focus sessions.

**Key differentiation:** 5-minute bypass cooldown creates behavioral friction without being completely restrictive.

---

## Artifacts Included

### 00-raw-idea.md
**Input for:** problem-framing
**Content:** Initial fuzzy product concept
**Use:** Feed this directly into /problem-framing skill

### 01-problem-framing-output.md
**Input for:** user-modeling, solution-scoping
**Content:** Structured problem statement, target user, JTBD, assumptions
**Quality check:** Problem statement follows WHO/WHAT/WHEN format ✓

### 02-user-modeling-output.md
**Input for:** assumption-mapping, solution-scoping, prd-generation
**Content:** 3 behavior-based personas with scenarios and insights
**Quality check:** Personas based on behavior (not demographics) ✓

### 03-assumption-mapping-output.md
**Input for:** solution-scoping decisions
**Content:** 12 assumptions ranked by risk, validation plan with timeline
**Quality check:** Assumptions are testable, prioritization includes cost/confidence ✓

### 04-solution-scoping-output.md
**Input for:** prd-generation
**Content:** Feature inventory (20 features), MoSCoW prioritization, MVP definition, explicit cuts
**Quality check:** Must-Have features are truly essential, Won't-Have section exists ✓

### 05-prd-output.md
**Input for:** ux-specification
**Content:** Complete PRD with user stories, features, acceptance criteria, goals with metrics
**Quality check:** User stories in proper format, acceptance criteria testable ✓

### 06-ux-specification-output.md
**Input for:** prompt-export
**Content:** 6 screens defined with flows, states, components, interactions
**Quality check:** Flows show happy/error paths, states documented (loading, error, success) ✓

### 07-prompts-output.md
**Input for:** Claude Code (build)
**Content:** 8 sequenced prompts with goals, checkpoints, and context
**Quality check:** Each prompt has verification checkpoint, dependencies clear ✓

### 08-ui-mockup-description.md
**Input for:** heuristic-evaluation
**Content:** Text description of Block Page UI for usability review
**Quality check:** Enough detail for heuristic evaluation ✓

---

## How to Use These Artifacts

### Full Pipeline Test (Recommended)

Test the complete workflow from start to finish:

1. **Start with raw idea:**
   ```
   /problem-framing
   [Paste content from 00-raw-idea.md]
   ```

2. **Use output as input for next skill:**
   ```
   /user-modeling
   [Paste content from 01-problem-framing-output.md]
   ```

3. **Continue through pipeline:**
   - `/assumption-mapping` ← Use problem framing + user modeling outputs
   - `/solution-scoping` ← Use all previous outputs
   - `/prd-generation` ← Use problem framing + user modeling + solution scoping
   - `/ux-specification` ← Use PRD
   - `/prompt-export` ← Use UX spec + PRD
   - [Build with Claude Code using prompts]
   - `/heuristic-evaluation` ← Use UI mockup description

### Individual Skill Test

Test a single skill in isolation:

```
/skill-name
[Paste content from corresponding input file]
```

**Example:** Test prd-generation only
```
/prd-generation
[Paste from 01-problem-framing-output.md + 02-user-modeling-output.md + 04-solution-scoping-output.md]
```

---

## Expected Outcomes

### Success Criteria

Each skill should produce output that:
- **Matches format** of the provided artifact (structure, sections, detail level)
- **Is actionable** (clear next steps or feeds into next skill)
- **Is specific** (not vague or generic)
- **Takes <10 minutes** to complete

### Quality Benchmarks

Compare skill output against provided artifacts:

| Artifact | Lines | Sections | Completeness |
|----------|-------|----------|--------------|
| Problem Framing | ~60 | 7 core sections | Problem statement, user, JTBD, alternatives |
| User Modeling | ~200 | 3 personas + insights | Personas, scenarios, design implications |
| Assumption Mapping | ~150 | 12 assumptions | Risk matrix, validation plan |
| Solution Scoping | ~180 | 20 features | MoSCoW, MVP definition, cuts |
| PRD | ~140 | 8+ sections | User stories, features, metrics |
| UX Specification | ~220 | 6 screens | Flows, screens, components, states |
| Prompts | ~100 | 8 prompts | Sequence, goals, checkpoints |

---

## Validation Tests

### Test 1: Information Continuity

**Goal:** Verify information flows correctly between skills

**Method:**
- Problem statement from problem-framing should appear in PRD ✓
- Personas from user-modeling should appear in PRD user stories ✓
- MVP features from solution-scoping should match PRD Must-Haves ✓
- Screens in UX spec should match features in PRD ✓

**Expected:** No contradictions, no information loss

---

### Test 2: Consistency Check

**Goal:** Verify skills don't produce conflicting outputs

**Method:**
- Target user is consistent across all artifacts ✓
- Feature priorities align (solution-scoping Must-Have = PRD Must-Have) ✓
- Success metrics are consistent ✓
- Constraints are respected throughout ✓

**Expected:** Same decisions reinforced, not contradicted

---

### Test 3: Completeness Check

**Goal:** Verify each artifact has all required sections

**Method:**
- Check against TESTING.md expected output structure
- Count sections, validate format

**Expected:** All artifacts have complete sections, no placeholders

---

### Test 4: Integration Points

**Goal:** Verify skills reference each other correctly

**Method:**
- Check "feeds into" and "receives from" statements
- Verify handoff sections exist

**Expected:** Clear pipeline connections documented

---

## Common Issues to Watch For

### Problem Framing
- ❌ Vague problem statement ("people need better tools")
- ✅ Specific WHO/WHAT/WHEN format

### User Modeling
- ❌ Demographic personas ("Sarah, 32, lives in Brooklyn")
- ✅ Behavior-based personas with scenarios

### Assumption Mapping
- ❌ Untestable assumptions ("users want this")
- ✅ Specific, testable assumptions with validation methods

### Solution Scoping
- ❌ Everything marked "Must Have"
- ✅ Honest prioritization with explicit cuts

### PRD
- ❌ Vague acceptance criteria ("works well")
- ✅ Testable criteria ("completes in <2 seconds")

### UX Specification
- ❌ Missing states (only happy path)
- ✅ All states documented (loading, error, empty, success)

### Prompts
- ❌ No verification checkpoints
- ✅ Each prompt has clear goal + checkpoint

---

## Adapting for Your Own Tests

To create your own test suite:

1. **Start with a real project idea** (something you'd actually build)
2. **Run through each skill** manually or with Claude
3. **Save outputs** as you go (name them 01-, 02-, etc.)
4. **Document** what worked and what didn't
5. **Compare** against expected structure from TESTING.md

---

## Metrics Tracking

Track these for validation:

- **Time per skill:** Should be <10 min each
- **Completeness:** % of expected sections present
- **Quality:** Specific vs vague (subjective 1-5 rating)
- **Integration:** Does output feed cleanly into next skill? (yes/no)
- **Actionability:** Can you proceed based on output? (yes/no)

---

## Questions Answered by This Test Suite

- ✅ Do skills work individually?
- ✅ Do skills compose into a workflow?
- ✅ Is output quality consistent?
- ✅ Does information flow without loss?
- ✅ Can a real project be planned end-to-end?

---

## Next Steps After Testing

If test succeeds:
- Skills are production-ready ✅
- Can share publicly or use for real projects
- Document lessons learned

If test reveals issues:
- Identify which skill(s) failed
- Compare against expected output
- Refine skill instructions
- Re-test

---

**Last Updated:** 2026-01-16
**Test Status:** Ready to run
**Expected Duration:** 90 minutes for full pipeline test
