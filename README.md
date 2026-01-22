# DesignSkills

Design thinking skills for AI-assisted product development. These skills are currently made for Claude code only. I am updating it to work with most other agents!
## Installation

```bash
npx add-skill Abhsin/DesignSkills
```

That's it! All skills are now available in Claude Code.

---

## Available Skills
### Pre-Planning
- `/problem-framing` - Extract fuzzy ideas into clear problem statements
- `/user-modeling` - Build behavior-based personas from research
- `/assumption-mapping` - Surface and prioritize risky assumptions
- `/solution-scoping` - Prioritize features and define MVP boundaries

### Documentation
- `/prd-generation` - Generate lean PRDs with user stories
- `/ux-specification` - Define flows, screens, and interactions

### Prompts
- `/prompt-export` - Convert specs into sequenced build prompts

### Evaluation
- `/heuristic-evaluation` - Usability review using Nielsen's 10 heuristics

---

## Quick Start

### Full Pipeline
```
/problem-framing → Define the problem
/user-modeling → Create personas
/assumption-mapping → Identify risks
/solution-scoping → Prioritize features
/prd-generation → Generate PRD
/ux-specification → Define UX
/prompt-export → Create build prompts
[Build with Claude Code]
/heuristic-evaluation → Review usability
```

### Fast Iteration
```
/problem-framing → Validate idea
/solution-scoping → Define MVP
/prompt-export → Get build prompts
[Build with Claude Code]
```

---

## Example Output

**Problem Framing:**
> Freelance designers lose track of client deliverables when juggling 3+ projects simultaneously, leading to missed deadlines and damaged client relationships.

**UX Specification:**
```
Flow: Scale Recipe
1. User pastes recipe URL
2. System parses ingredients (2-3 sec)
3. User adjusts servings (2 → 6)
4. System recalculates quantities
5. User prints scaled recipe
```

**Prompts Export:**
```
Prompt 1: Setup React + Vite + TailwindCSS
Goal: Working dev environment
Checkpoint: Run npm run dev and see home page

Prompt 2: Create recipe parser...
```

---

## Output Files

Skills automatically save their outputs to preserve context:

```
your-project/
├── design/
│   ├── 01-problem-framing.md
│   ├── 02-user-modeling.md
│   ├── 03-assumption-mapping.md
│   ├── 04-solution-scoping.md
│   ├── 05-prd.md
│   ├── 06-ux-spec.md
│   └── 08-heuristic-evaluation.md
├── prompts.md
└── src/
```

All design artifacts are saved in the `design/` folder, making it easy for you and AI to reference previous decisions.

---

## Coming Soon

- `ideation` - Problem reframing and rapid ideation
- `critique` - Structured design feedback
- `usability-test-guide` - User testing scripts

---

## License

Apache 2.0

---

## Questions?

Open an issue or check individual skill documentation in the `Skill/` directory.
