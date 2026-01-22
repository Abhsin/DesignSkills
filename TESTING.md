# Testing DesignSkills

Guide for testing and validating the quality of DesignSkills.

---

## Testing Philosophy

Skills are tested at three levels:
1. **Structural** - Does the skill follow best practices?
2. **Functional** - Does the skill produce the expected output?
3. **Quality** - Is the output useful and actionable?

---

## Level 1: Structural Testing

### Automated Checks

Run these checks to verify skill structure:

```bash
# Check all skills have required files
for skill in Skill/*/; do
  if [ ! -f "$skill/SKILL.md" ]; then
    echo "Missing SKILL.md in $skill"
  fi
done

# Check frontmatter exists
for skill in Skill/*/SKILL.md; do
  if ! grep -q "^---" "$skill"; then
    echo "Missing frontmatter in $skill"
  fi
done

# Check file length (should be <500 lines)
for skill in Skill/*/SKILL.md; do
  lines=$(wc -l < "$skill")
  if [ $lines -gt 500 ]; then
    echo "$skill is $lines lines (over 500 limit)"
  fi
done
```

### Manual Checklist

For each skill, verify:

- [ ] Has YAML frontmatter with `name` and `description`
- [ ] Description includes triggers and use cases
- [ ] SKILL.md is under 500 lines
- [ ] Has "Why This Exists" (1 sentence)
- [ ] Has clear workflow or steps
- [ ] Has output template or format
- [ ] Has integration points documented
- [ ] Reference files exist (if mentioned)
- [ ] No XML tags in frontmatter

**Score:** Pass all items = ✅ Production-ready structure

---

## Level 2: Functional Testing

### Real-World Scenario Tests

Test each skill with actual use cases.

#### Test 1: problem-framing

**Input:** "I want to build a better todo app"

**Expected Output:**
- Problem statement extracted
- Target user identified
- Jobs-to-be-done listed
- Current alternatives documented
- Key assumptions surfaced
- Success criteria defined

**Quality Checks:**
- [ ] Problem statement follows "WHO has WHAT problem WHEN" format
- [ ] Target user is specific (not "everyone")
- [ ] Assumptions are testable
- [ ] Output is actionable (can feed into next skill)

**Test command:**
```
/problem-framing

[Paste the prompt: "I want to build a better todo app for people who forget tasks"]
```

---

#### Test 2: user-modeling

**Input:** Raw user research notes or interview transcripts

**Expected Output:**
- 2-3 behavior-based personas
- Scenarios with trigger moments
- Goals, pain points, current behavior
- Insights and design implications

**Quality Checks:**
- [ ] Personas based on behavior, not demographics
- [ ] Scenarios are specific (not abstract use cases)
- [ ] Includes divergences (what makes personas different)
- [ ] Design implications are actionable

**Test command:**
```
/user-modeling

[Provide interview notes or user research data]
```

---

#### Test 3: assumption-mapping

**Input:** Product idea or feature concept

**Expected Output:**
- List of 10-15 assumptions
- Priority ranking (highest risk first)
- Suggested validation methods
- Cost/confidence matrix

**Quality Checks:**
- [ ] Assumptions are specific and testable
- [ ] Prioritization makes sense (risk × importance)
- [ ] Validation methods are practical
- [ ] Identifies which assumptions to test first

**Test command:**
```
/assumption-mapping

[Describe product idea or feature]
```

---

#### Test 4: solution-scoping

**Input:** Feature brainstorm or product concept

**Expected Output:**
- Feature inventory (all considered features)
- MoSCoW prioritization (Must/Should/Could/Won't)
- MVP definition
- Explicit cuts documented

**Quality Checks:**
- [ ] Must-Have features are truly essential
- [ ] Won't-Have section exists (explicit cuts)
- [ ] MVP definition is clear and testable
- [ ] Scope creep triggers identified

**Test command:**
```
/solution-scoping

[Provide feature ideas or product concept]
```

---

#### Test 5: prd-generation

**Input:** Output from problem-framing, user-modeling, and solution-scoping

**Expected Output:**
- Complete PRD with all sections
- User stories in proper format
- Features with acceptance criteria
- Goals with metrics

**Quality Checks:**
- [ ] Problem statement is clear
- [ ] Success metrics are measurable
- [ ] User stories follow "As a... I want... so that..." format
- [ ] Acceptance criteria are testable
- [ ] Out of Scope section exists

**Test command:**
```
/prd-generation

[Provide upstream artifacts or raw concept]
```

---

#### Test 6: ux-specification

**Input:** PRD or product requirements

**Expected Output:**
- User flows with diagrams
- Screen definitions with layouts
- Component specifications
- Interaction details
- States documented

**Quality Checks:**
- [ ] Flows show happy path and error paths
- [ ] Screens include states (loading, error, empty, success)
- [ ] Components are reusable
- [ ] Interactions specify triggers and feedback
- [ ] Responsive behavior documented

**Test command:**
```
/ux-specification

[Provide PRD or requirements]
```

---

#### Test 7: prompt-export

**Input:** UX spec and/or PRD

**Expected Output:**
- Sequenced prompts.md file
- Each prompt with goal and checkpoint
- Logical build order
- Tech stack specified

**Quality Checks:**
- [ ] Prompts build on each other (dependencies clear)
- [ ] Each prompt has verification checkpoint
- [ ] Prompts are self-contained
- [ ] Build order makes sense (setup → core → polish)

**Test command:**
```
/prompt-export

[Provide UX spec and/or PRD]
```

---

#### Test 8: heuristic-evaluation

**Input:** Screenshot, URL, or description of interface

**Expected Output:**
- Issues categorized by heuristic
- Severity ratings (0-4)
- Prioritized recommendations
- Strengths identified

**Quality Checks:**
- [ ] Issues are specific (not generic advice)
- [ ] Severity ratings make sense
- [ ] Recommendations are actionable
- [ ] Uses Nielsen's 10 heuristics correctly

**Test command:**
```
/heuristic-evaluation

[Share screenshot or describe interface]
```

---

## Level 3: Quality Testing

### End-to-End Workflow Tests

Test the full pipeline with a real project concept.

#### Workflow Test 1: Simple Project

**Scenario:** "I want to build a recipe scaling app"

**Full Pipeline:**
1. `/problem-framing` → Get clear problem statement
2. `/solution-scoping` → Define MVP features
3. `/prd-generation` → Generate PRD
4. `/ux-specification` → Create UX spec
5. `/prompt-export` → Generate prompts.md
6. [Build with prompts]
7. `/heuristic-evaluation` → Review result

**Success Criteria:**
- [ ] Each skill produces output in <10 minutes
- [ ] Outputs feed naturally into next skill
- [ ] Final prompts.md is buildable
- [ ] No major information gaps
- [ ] Quality increases at each step

---

#### Workflow Test 2: Medium Project

**Scenario:** "I want to build a task tracker for freelancers"

**Full Pipeline:**
1. `/problem-framing` → Define problem and user
2. `/user-modeling` → Create personas from research
3. `/assumption-mapping` → Surface risks
4. `/solution-scoping` → Prioritize features
5. `/prd-generation` → Full PRD
6. `/ux-specification` → Complete UX spec
7. `/prompt-export` → Development prompts
8. [Build with Claude Code]
9. `/heuristic-evaluation` → Evaluate UI

**Success Criteria:**
- [ ] Pipeline handles complexity well
- [ ] Skills compose without friction
- [ ] Outputs reference each other correctly
- [ ] No redundant work across skills
- [ ] Total time <3 hours for all steps

---

## Testing with Different Users

### Test Persona 1: First-time User

**Goal:** Can they use skills without prior knowledge?

**Test:**
1. Give user no context except skill names
2. Ask them to use `/problem-framing` with an idea
3. Observe: Do they understand the output? Do they know what to do next?

**Success:** User completes task without asking for help

---

### Test Persona 2: Experienced Developer

**Goal:** Do skills add value vs. what they'd do naturally?

**Test:**
1. Ask developer to define a problem without skill
2. Ask them to use `/problem-framing` for same problem
3. Compare outputs

**Success:** Skill output is more structured, specific, and actionable

---

### Test Persona 3: Non-technical User

**Goal:** Are skills accessible to product managers, designers?

**Test:**
1. Give PM a product idea
2. Walk through `/problem-framing` → `/user-modeling` → `/solution-scoping`
3. Observe: Do they understand the process? Is output useful?

**Success:** Non-technical user can complete pre-planning workflow

---

## Regression Testing

### After Updating a Skill

Run this checklist:

1. **Structural check:** Verify file still passes structural tests
2. **Functional check:** Run test scenario for that skill
3. **Integration check:** Test handoff to next skill in pipeline
4. **Cross-reference check:** Verify other skills referencing this one still work

### After Adding a New Skill

1. **Structural check:** New skill passes all structural tests
2. **Functional check:** Create 3 test scenarios
3. **Integration check:** Test with upstream and downstream skills
4. **Documentation check:** README and ROADMAP updated

---

## Automated Test Suite (Future)

### Proposed Structure

```
tests/
├── structural/
│   ├── check-frontmatter.sh
│   ├── check-file-length.sh
│   └── check-references.sh
├── functional/
│   ├── problem-framing.test.md
│   ├── user-modeling.test.md
│   └── ...
└── integration/
    ├── simple-workflow.test.md
    └── full-workflow.test.md
```

### Test Scenarios

Each `.test.md` file contains:
- Input prompt
- Expected output structure
- Quality checks
- Pass/fail criteria

**Example: `problem-framing.test.md`**

```markdown
# Test: problem-framing with vague idea

## Input
"I want to build a better email client"

## Expected Output Structure
- [ ] Problem statement (WHO/WHAT/WHEN format)
- [ ] Target user (specific, not "everyone")
- [ ] Jobs to be done (functional, emotional, social)
- [ ] Current alternatives (at least 2)
- [ ] Key assumptions (at least 3)
- [ ] Success criteria (measurable)

## Quality Checks
- [ ] Problem is specific (not "email is hard")
- [ ] Target user has behavioral traits
- [ ] Assumptions are testable

## Pass Criteria
All structural elements present + 2/3 quality checks pass
```

---

## Performance Benchmarks

### Speed Targets

| Skill | Target Time | Acceptable Range |
|-------|-------------|------------------|
| problem-framing | 5 min | 3-10 min |
| user-modeling | 10 min | 7-15 min |
| assumption-mapping | 5 min | 3-8 min |
| solution-scoping | 8 min | 5-12 min |
| prd-generation | 8 min | 5-15 min |
| ux-specification | 12 min | 8-20 min |
| prompt-export | 8 min | 5-12 min |
| heuristic-evaluation | 10 min | 7-15 min |

**Full pipeline:** <90 minutes for complete workflow

### Quality Targets

Each skill output should achieve:
- **Completeness:** 90%+ of expected sections present
- **Specificity:** No vague or generic statements
- **Actionability:** Clear next steps defined
- **Accuracy:** Follows established frameworks correctly

---

## User Acceptance Testing

### Feedback Collection

After testing, gather feedback on:

1. **Clarity:** Was the skill's purpose clear?
2. **Ease of use:** Could you complete it without help?
3. **Output quality:** Was the output useful?
4. **Integration:** Did it work well with other skills?
5. **Time:** Was completion time acceptable?

**Rating scale:** 1-5 (1 = Poor, 5 = Excellent)

**Target:** Average ≥4.0 across all dimensions

---

## Bug Reporting Template

When you find issues:

```markdown
**Skill:** [skill-name]
**Issue:** [Brief description]
**Input:** [What you provided]
**Expected:** [What should have happened]
**Actual:** [What actually happened]
**Severity:** [Low/Medium/High/Critical]
```

---

## Testing Checklist Summary

Before marking a skill as "production-ready":

- [ ] Passes all structural checks
- [ ] Tested with 3+ real scenarios
- [ ] Output matches expected format
- [ ] Quality checks pass (specific, actionable, complete)
- [ ] Integrates with upstream/downstream skills
- [ ] Completes in acceptable time
- [ ] Reference files exist and are helpful
- [ ] Tested across different model tiers (Haiku/Sonnet/Opus)
- [ ] User feedback collected and positive

**Only mark as production-ready when all items checked.**

---

## Continuous Improvement

### After Each Test Session

1. Document what worked well
2. Document what didn't work
3. Identify improvement opportunities
4. Update skill or references based on findings
5. Re-test to verify improvements

### Monthly Review

1. Run full integration test suite
2. Check for outdated examples or references
3. Verify cross-references between skills
4. Update based on user feedback
5. Check for new best practices from Anthropic

---

## Quick Test Commands

Copy-paste these to run quick tests:

**Structural test:**
```bash
# Check all skills have required structure
for skill in Skill/*/SKILL.md; do
  echo "Checking $skill..."
  grep -q "^---" "$skill" && echo "✓ Has frontmatter" || echo "✗ Missing frontmatter"
  lines=$(wc -l < "$skill")
  [ $lines -lt 500 ] && echo "✓ Under 500 lines ($lines)" || echo "✗ Too long ($lines lines)"
done
```

**Quick functional test:**
```
/problem-framing
I want to build a better way for people to remember to drink water throughout the day
```

**Integration test:**
```
/problem-framing → [get output]
/solution-scoping → [use problem-framing output]
/prd-generation → [use both outputs]
```

Good luck testing! 🧪
