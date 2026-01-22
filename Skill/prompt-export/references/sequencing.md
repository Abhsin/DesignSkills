# Prompt Sequencing Strategies

Guidelines for breaking projects into effective prompt sequences.

---

## Core Principles

### 1. One Logical Unit Per Prompt

**Good:** "Create the user authentication flow with login, signup, and password reset"
**Bad:** "Build the entire app"

**Why:** Claude works best with focused, concrete tasks.

### 2. Build Foundation First

**Correct order:**
1. Project setup + dependencies
2. Data models/types
3. Core functionality
4. UI components
5. Integration
6. Polish

**Wrong order:**
- Starting with UI before data structure is defined
- Adding features before core functionality works
- Polishing before testing basic flow

### 3. Include Checkpoints

Every prompt must have a verification step.

**Format:**
```
**Goal:** [What this achieves]
**Checkpoint:** [How to verify it worked]
- Action to test
- Expected result
```

### 4. Make Prompts Self-Contained

Each prompt should:
- State what exists (context)
- Request what's new (task)
- Specify acceptance criteria

**Good:**
> "We have a React app with routing set up. Create a dashboard component in `src/pages/Dashboard.jsx` that displays a list of users from the `/api/users` endpoint. Show loading state while fetching."

**Bad:**
> "Add the dashboard"

---

## Sequencing Patterns

### Pattern 1: Linear Build (Simple Projects)

**Use when:** Single feature, few dependencies, straightforward

**Structure:**
1. Setup
2. Core feature
3. UI
4. Polish

**Example: Todo App**
1. Setup React + local storage
2. Add/delete/complete todo functionality
3. UI components + styling
4. Persistence + edge cases

**Pros:** Simple, easy to follow
**Cons:** No parallelization opportunities

---

### Pattern 2: Layer by Layer (Full-Stack)

**Use when:** Frontend + backend, multiple integrations

**Structure:**
1. Setup both frontend and backend
2. Database + models
3. API endpoints
4. Frontend data layer
5. UI components
6. Integration
7. Polish

**Example: Blog Platform**
1. Setup React + Node + Postgres
2. Define Post, User, Comment models
3. Create REST API for posts
4. Fetch posts in frontend
5. Build post list + detail views
6. Connect everything
7. Error handling + loading states

**Pros:** Clean separation of concerns
**Cons:** Can feel slow (no visible progress until layer 5)

---

### Pattern 3: Vertical Slice (Feature by Feature)

**Use when:** Multiple independent features, want early wins

**Structure:**
1. Setup
2. Feature A (end-to-end)
3. Feature B (end-to-end)
4. Feature C (end-to-end)
5. Integration
6. Polish

**Example: Task Manager**
1. Setup
2. Create tasks (backend + frontend complete)
3. Mark tasks complete (backend + frontend complete)
4. Filter tasks (backend + frontend complete)
5. Integrate all features
6. Polish

**Pros:** Working features early, visible progress
**Cons:** Potential rework during integration

---

### Pattern 4: Risk-First (Complex Projects)

**Use when:** High technical uncertainty, unclear if approach will work

**Structure:**
1. Setup
2. Proof-of-concept for risky part
3. If POC works → full implementation
4. Other features
5. Integration
6. Polish

**Example: AI-Powered Recipe Parser**
1. Setup
2. **POC:** Test if recipe HTML parsing works for 3 sites
3. (If successful) Build full parser with error handling
4. Build scaling logic
5. Build UI
6. Integrate + polish

**Pros:** Validates approach early, reduces wasted effort
**Cons:** Requires discipline to not skip POC

---

## Dependency Management

### Rule: Dependencies Must Be Built First

**Correct:**
1. User authentication
2. **Then:** User profile editing (depends on auth)

**Wrong:**
1. User profile editing
2. User authentication (profile can't work without auth)

### Identifying Dependencies

Ask: "What must exist for this prompt to work?"

**Example:** "Add checkout flow"

**Dependencies:**
- Products must be defined (data model)
- Shopping cart must work (add/remove items)
- Payment integration must be configured

**Correct sequence:**
1. Define Product model
2. Create shopping cart
3. Configure Stripe
4. Build checkout flow

---

## Checkpoint Design

### Checkpoint Types

**1. Visual Checkpoint**
- "Navigate to `/dashboard` and see user list"
- Good for UI-heavy prompts

**2. Functional Checkpoint**
- "Click 'Add Task' button and verify task appears in list"
- Good for interaction testing

**3. Technical Checkpoint**
- "Run `npm test` and all tests pass"
- Good for logic/utility functions

**4. Data Checkpoint**
- "Check database: `SELECT * FROM users` shows new user"
- Good for backend/database work

### Checkpoint Best Practices

**Be specific:**
- ❌ "Make sure it works"
- ✅ "Click login button with valid credentials and verify redirect to dashboard"

**Include expected results:**
- ❌ "Test the API"
- ✅ "Call `GET /api/users` and verify returns array of users with 200 status"

**Make them quick:**
- ❌ "Deploy to production and test end-to-end"
- ✅ "Run locally and test in browser DevTools"

---

## Prompt Length Guidelines

### How Long Should Each Prompt Be?

**Too short (<50 words):**
- Lacks context
- Unclear acceptance criteria
- Leads to follow-up questions

**Too long (>300 words):**
- Overwhelming
- Multiple unrelated tasks bundled
- Hard to verify completion

**Goldilocks zone (100-200 words):**
- Clear context
- Single focused task
- Concrete acceptance criteria
- Testable checkpoint

### When to Split a Prompt

Split if the prompt asks for:
- Multiple screens/components (split by component)
- Multiple independent features (split by feature)
- Both frontend and backend work (split by layer, unless vertical slice)
- More than 3 acceptance criteria (likely too much)

---

## Common Sequencing Mistakes

### Mistake 1: Jumping to UI Too Early

**Wrong:**
1. Setup
2. Build beautiful dashboard UI
3. Add backend API

**Right:**
1. Setup
2. Define data models
3. Build backend API
4. Build dashboard UI (now you know what data you have)

**Why:** UI is easier when you know the data structure.

---

### Mistake 2: Too Many Features in One Prompt

**Wrong:**
> "Build user authentication with login, signup, password reset, email verification, two-factor auth, and OAuth with Google and GitHub"

**Right:**
Prompt 1: "Basic auth with login and signup (email/password)"
Prompt 2: "Add password reset via email"
Prompt 3: "Add OAuth with Google"

**Why:** Each prompt should have one core goal.

---

### Mistake 3: No Verification Step

**Wrong:**
> "Create a payment integration with Stripe"

**Right:**
> "Create a payment integration with Stripe. **Checkpoint:** Use Stripe test keys to process a test payment of $1.00 and verify success response."

**Why:** Without checkpoints, you don't know if it actually works.

---

### Mistake 4: Skipping Setup

**Wrong:**
1. Build user dashboard
2. Oops, need to set up project first

**Right:**
1. Setup project with dependencies
2. Build user dashboard

**Why:** Setup is boring but essential. Do it first.

---

## Adaptive Sequencing

### For Simple Projects (Weekend Build)

**Pattern:** Linear, 4-6 prompts
1. Setup + layout
2. Core feature
3. Main UI
4. Polish

**Checkpoint frequency:** Every prompt
**Prompt length:** Short (100 words)

---

### For Medium Projects (Side Project MVP)

**Pattern:** Layer-by-layer or vertical slice, 8-12 prompts
1. Setup (frontend + backend)
2. Authentication
3. Data models
4. API layer
5. Frontend data fetching
6. Main UI components
7. Integration
8. Polish

**Checkpoint frequency:** Every prompt
**Prompt length:** Medium (150-200 words)

---

### For Complex Projects (Startup MVP)

**Pattern:** Risk-first + vertical slice, 15-20+ prompts
1. Setup
2. POC for risky part
3-N. Vertical slices (feature by feature)
N+1. Integration
N+2. Testing
N+3. Polish

**Checkpoint frequency:** Every prompt + milestone checkpoints
**Prompt length:** Detailed (200-250 words)

---

## Prompt Templates

### Template: Setup Prompt

```
Set up [project type] using [tech stack]. Initialize the project with [package manager], install [key dependencies], and configure [essential config files]. Create the basic folder structure: [list folders]. Add a [hello world / health check] endpoint/page to verify everything works.

**Goal:** Working development environment
**Checkpoint:**
- Run [dev command] and see [expected output]
- [Verification step 2]
```

---

### Template: Feature Prompt

```
We have [context - what exists]. Create [new feature] that [what it does]. The feature should [acceptance criteria 1], [acceptance criteria 2], and [acceptance criteria 3].

**Goal:** [One-sentence goal]
**Checkpoint:**
- [Action to test]
- [Expected result]
```

---

### Template: Integration Prompt

```
We have [Feature A] and [Feature B] working independently. Integrate them so that [how they work together]. Handle [edge case 1] and [edge case 2].

**Goal:** [Features working together]
**Checkpoint:**
- [End-to-end test scenario]
- [Expected outcome]
```

---

### Template: Polish Prompt

```
Improve the [area of app] by adding [enhancement 1], [enhancement 2], and [enhancement 3]. Ensure [quality criteria - responsive, accessible, performant].

**Goal:** Production-ready polish
**Checkpoint:**
- [Test scenario covering all enhancements]
- [Quality check - e.g., test mobile view, check accessibility]
```

---

## Final Tips

1. **Start small:** Better to have 10 small, focused prompts than 3 giant ones
2. **Test frequently:** Every prompt should end with working code
3. **Be specific:** Vague prompts get vague results
4. **Reference files:** "In `src/components/Header.jsx`..." is better than "in the header"
5. **Learn from failures:** If a prompt didn't work, split it smaller

**Remember:** The goal is incremental progress with frequent validation, not building everything at once.
