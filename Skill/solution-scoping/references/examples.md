# Solution Scoping Examples

Complete solution scoping examples showing feature prioritization, MVP definition, and cut decisions for different project types.

---

## Example 1: Freelance Task Tracker

### Context

**Problem:** Freelance designers lose track of client deliverables across 3+ projects, leading to missed deadlines and damaged client relationships.

**Target User:** Freelance designers with 3-10 active clients juggling multiple concurrent projects.

**Core assumption to test:** If we automatically extract deliverables from email and show them in one view, freelancers will miss fewer deadlines.

**Constraints:**
- Timeline: MVP in 6 weeks (solo developer)
- Budget: $0 (side project, validate before spending)
- Skills: React, Node.js, basic design skills
- Other: Must work with Gmail (that's where client communication lives)

---

### Feature Inventory

All features considered during brainstorming:

| # | Feature | User Value | Effort | Notes |
|---|---------|------------|--------|-------|
| 1 | Gmail integration (read emails) | High | Medium | Core to value prop |
| 2 | Display deliverables in list view | High | Low | Essential for MVP |
| 3 | Mark deliverable complete | High | Low | Basic CRUD |
| 4 | Filter by client | High | Low | Common use case |
| 5 | Filter by date range | Medium | Low | Nice for planning |
| 6 | Calendar view | Medium | Medium | Alternate visualization |
| 7 | Email notifications for upcoming deadlines | High | Low | Prevents forgetting |
| 8 | Mobile app | High | High | Users check phone, but web-first is faster |
| 9 | Manual deliverable entry | Medium | Low | Backup for non-email tasks |
| 10 | Client contact info | Low | Low | Already in email/phone |
| 11 | Time tracking | Medium | Medium | Scope creep—different problem |
| 12 | Invoice generation | Medium | High | Scope creep—different problem |
| 13 | AI extraction of deliverables | High | High | Would be great but risky for MVP |
| 14 | Slack integration | Medium | Medium | Gmail first, Slack later if validated |
| 15 | Share status with clients | Medium | Medium | Assumes different workflow |
| 16 | Team collaboration | Low | High | Targeting solo freelancers first |
| 17 | Export to CSV | Low | Low | No one asked for this |
| 18 | Dark mode | Low | Low | Polish, not function |
| 19 | Custom tags/categories | Medium | Low | Could help organization |
| 20 | Archive completed deliverables | Medium | Low | Prevents clutter |

---

### Prioritization

#### Must Have (MVP)
*Product doesn't work without these*

| Feature | Rationale |
|---------|-----------|
| Gmail integration (read-only) | Core assumption: deliverables come from email. Without this, users must manually enter everything and we're just another todo app. |
| Display deliverables in list view | Users need to see what's due. Basic requirement. |
| Mark deliverable complete | Users need to track progress. Can't validate value without completion tracking. |
| Filter by client | Primary use case: "What does Client X need?" Tested in interviews. |
| Email notifications (daily digest) | Prevents the "forgot to check the app" problem. Push > Pull for this use case. |

#### Should Have (v1.1)
*Important, but MVP can ship without them*

| Feature | Rationale | Dependency |
|---------|-----------|------------|
| Manual deliverable entry | Handles edge cases (verbal requests, Slack messages). Workaround: users can email themselves. | Gmail integration working |
| Filter by date range | Helpful for planning but not core to "don't miss deadlines." | List view working |
| Calendar view | Alternate visualization. Some users prefer calendar. A/B test after launch. | List view validated |
| Archive completed deliverables | Prevents clutter long-term but not day-one issue. | Completion working |
| Custom tags/categories | Power user feature. Wait to see if users request it. | Core features stable |

#### Could Have (Future)
*Nice to have, low priority*

| Feature | Rationale |
|---------|-----------|
| Slack integration | Depends on user feedback. Gmail might be sufficient. |
| Mobile app | If web app succeeds, native mobile is next logical step. React Native for efficiency. |
| Dark mode | Polish feature. Build after core value proven. |
| Share status with clients | Interesting idea but assumes clients want this. Validate demand first. |

#### Won't Have (Cut)
*Explicitly out of scope*

| Feature | Reason for Cut |
|---------|----------------|
| Time tracking | Different problem space. Adds complexity. Many existing solutions. |
| Invoice generation | Scope creep. Not related to tracking deliverables. Use Stripe/PayPal. |
| AI deliverable extraction | Would be amazing but too risky for MVP. Start with simple keyword matching (due, deadline, deliverable). Upgrade to AI if traction. |
| Team collaboration | Targeting solo freelancers first. Teams are different personas with different needs. |
| Client contact info | Redundant with email/phone contacts. No user mentioned this pain. |
| Export to CSV | Zero user requests for this. Classic "might be nice" feature that never gets used. |

---

### MVP Definition

#### What We're Building

A Gmail-connected web app that automatically identifies deliverables from client emails and displays them in a simple list view, filterable by client, with daily email reminders for upcoming deadlines.

#### Core User Flow

1. User connects Gmail account (OAuth)
2. System scans emails for keywords ("deliverable," "due," "deadline," "by [date]")
3. User sees list of extracted deliverables grouped by client
4. User marks deliverable complete when done
5. User receives daily email digest of upcoming deliverables

#### What Success Looks Like

- 80% of deliverables correctly extracted from email (measured by user corrections)
- Users check app at least 5x per week (engagement metric)
- Zero reported missed deadlines in first month (core value prop)
- 20% of users opt into daily email digest

#### What We're NOT Building (Yet)

- Manual task entry (workaround: email yourself)
- Calendar view (list view first)
- Mobile app (responsive web first)
- AI-powered extraction (regex and keywords first)
- Time tracking or invoicing (out of scope entirely)

---

### Risk Check

#### Cuts That Might Hurt

| Cut | Risk | Mitigation |
|-----|------|------------|
| Manual entry | Users have non-email deliverables (calls, Slack) | Provide "email yourself" workaround. Add manual entry in v1.1 if users complain. |
| AI extraction | Simple keyword matching might miss deliverables or create false positives | Start with high-precision keywords. Let users correct false negatives. Monitor extraction accuracy. |
| Mobile app | Users might prefer checking on phone | Make web app mobile-responsive. Track mobile vs desktop usage. Build native app if mobile dominates. |

#### Scope Creep Triggers
*Watch out for these during development*

- "Just add time tracking—it's easy!" (It's not, and it's a different product)
- "We should support Outlook too!" (Validate Gmail version first)
- "What about automatic reminders to clients?" (Different feature, different complexity)

---

### Open Questions

- Should we limit to recent emails (last 30 days) or scan entire inbox? (Performance vs completeness trade-off)
- How do we handle recurring deliverables? (Monthly reports, etc.)
- What if users have 100+ deliverables? Do we need pagination or infinite scroll?

---

## Example 2: Recipe Scaling App

### Context

**Problem:** Home cooks preparing meals for families of 5+ waste ingredients and time when online recipes serve 2-4 people, requiring mental math that leads to measurement errors and failed dishes.

**Target User:** Parents cooking dinner for families of 5-7 people, 5+ nights per week.

**Core assumption to test:** If we automatically scale recipe ingredients, home cooks will try new recipes 2x more often.

**Constraints:**
- Timeline: MVP in 4 weeks (solo developer, part-time)
- Budget: $0 for MVP, $20/month for hosting if validated
- Skills: React, basic backend, no ML experience
- Other: Web-only (desktop and mobile responsive)

---

### Feature Inventory

| # | Feature | User Value | Effort | Notes |
|---|---------|------------|--------|-------|
| 1 | Input recipe URL | High | Low | Core entry point |
| 2 | Parse recipe ingredients | High | High | Many formats, fragile |
| 3 | Scale ingredient quantities | High | Medium | Math + fraction handling |
| 4 | Display scaled recipe | High | Low | Basic UI |
| 5 | Manual ingredient entry | Medium | Low | Backup for parsing failures |
| 6 | Save favorite recipes | Medium | Low | Convenience feature |
| 7 | Fraction simplification (2/4 → 1/2) | Medium | Low | Nice UX touch |
| 8 | Metric/imperial conversion | Medium | Medium | Users might want this |
| 9 | Dietary substitutions | High | High | Different problem—complex |
| 10 | Ingredient shopping list | Medium | Medium | Nice but not core |
| 11 | Meal planning calendar | Medium | High | Different use case |
| 12 | Recipe recommendations | Low | High | ML—too complex for MVP |
| 13 | User accounts | Low | Medium | Not needed for MVP |
| 14 | Recipe sharing | Low | Medium | Social feature—premature |
| 15 | Nutritional info | Medium | High | Requires food database API |
| 16 | Print-friendly format | High | Low | Common use case |
| 17 | Step-by-step cooking mode | Medium | Medium | Nice but not core scaling |
| 18 | Browser extension | High | Medium | Ideal UX but more complex |
| 19 | Support for volume/weight (cups ↔ grams) | Medium | Medium | International users |
| 20 | Adjust for high altitude | Low | Low | Niche use case |

---

### Prioritization

#### Must Have (MVP)

| Feature | Rationale |
|---------|-----------|
| Input recipe URL | Primary entry point. Users are already on recipe websites. |
| Parse recipe ingredients | Core value prop. Without parsing, users must manually enter (defeats purpose). |
| Scale ingredient quantities | The whole point. Must handle fractions, decimals, and mixed units. |
| Display scaled recipe | Users need to see the result. Clean, readable output. |
| Print-friendly format | Users cook from printed recipes. Print CSS is straightforward. |

#### Should Have (v1.1)

| Feature | Rationale | Dependency |
|---------|-----------|------------|
| Manual ingredient entry | Fallback when parsing fails. Let parsing fail gracefully first, then add this. | Parsing working |
| Save favorite recipes | Convenience. Requires user accounts. Defer until usage proves need. | User accounts |
| Fraction simplification | UX polish. "14/8 cups" looks weird. Math library can handle this. | Scaling working |
| Browser extension | Better UX than copy-paste URL. Build after web app validated. | Web app stable |

#### Could Have (Future)

| Feature | Rationale |
|---------|-----------|
| Ingredient shopping list | Adjacent use case. Validate core scaling first. |
| Metric/imperial conversion | International audience. Check analytics for non-US traffic first. |
| Step-by-step cooking mode | Different feature. Focus on scaling first. |

#### Won't Have (Cut)

| Feature | Reason for Cut |
|---------|----------------|
| Dietary substitutions | Completely different problem. Requires food knowledge database. Build separate product or integrate later. |
| Meal planning calendar | Different user need. Scaling is point-in-time, planning is longer-term. Scope creep. |
| Recipe recommendations | Requires ML and content database. No user asked for this. |
| User accounts | Not needed for MVP. Users can use the tool anonymously. Add if "save recipes" proves valuable. |
| Recipe sharing | Social features are complex. Zero evidence users want this. |
| Nutritional info | Requires third-party API (costs money). Nice-to-have, not core. |
| Support for volume/weight conversion | Complex (1 cup flour ≠ 1 cup water in grams). Defer unless international users demand it. |
| Adjust for high altitude | Extremely niche. Cut entirely. |

---

### MVP Definition

#### What We're Building

A web app that takes a recipe URL, extracts ingredients, scales them to a user-specified number of servings, and displays the result in a clean, printable format.

#### Core User Flow

1. User finds recipe on Pinterest/AllRecipes
2. User copies URL into our app
3. User enters target servings (e.g., 6)
4. System parses ingredients, scales quantities
5. User sees scaled recipe with original instructions
6. User prints or cooks from screen

#### What Success Looks Like

- 90% parsing success rate for top 20 recipe sites
- Users successfully scale a recipe in <30 seconds
- 50% of users print the scaled recipe
- Users return to scale 2+ recipes per week

#### What We're NOT Building (Yet)

- Manual ingredient entry (users can copy-paste into notes if parsing fails)
- User accounts or saved recipes (stateless for MVP)
- Dietary substitutions (different problem entirely)
- Shopping lists or meal planning (adjacent features, not core)

---

### Risk Check

#### Cuts That Might Hurt

| Cut | Risk | Mitigation |
|-----|------|------------|
| Manual ingredient entry | Parsing will fail for some recipe formats | Focus on top 10 recipe sites (AllRecipes, FoodNetwork, NYT Cooking). Show friendly error for unsupported sites. |
| User accounts | Users can't save recipes | Validate if users actually want this. Many users scale once and never return. |
| Dietary substitutions | Users with allergies/preferences won't get value | Out of scope. Recommend other tools for substitutions. |

#### Scope Creep Triggers

- "Can we add a shopping list?" (Different feature, defer to v1.1)
- "Can we recommend similar recipes?" (ML complexity, no user need)
- "Can we add cook timers?" (Kitchen timer apps exist)

---

### Open Questions

- Which recipe sites should we prioritize for parsing? (Start with top 5, expand based on usage)
- How do we handle recipes with vague quantities? ("A pinch of salt," "To taste")
- Do users want the original recipe instructions or scaled instructions? (Start with original, scale only ingredients)

---

## Example 3: Junior Dev Documentation Hub

### Context

**Problem:** Junior developers at fast-growing startups spend 40% of onboarding time hunting for architecture decisions that aren't documented anywhere, slowing time-to-first-commit from weeks to months.

**Target User:** Junior developers (0-2 years experience) joining engineering teams of 10-50 people.

**Core assumption to test:** If we make documenting architecture decisions trivially easy for senior devs, juniors will find answers 3x faster.

**Constraints:**
- Timeline: MVP in 8 weeks (team of 2 developers)
- Budget: $500 for tools/services
- Skills: React, Node.js, familiar with Markdown
- Other: Must integrate with GitHub (where code lives)

---

### Feature Inventory

| # | Feature | User Value | Effort | Notes |
|---|---------|------------|--------|-------|
| 1 | Markdown editor for decisions | High | Low | Simple, familiar format |
| 2 | Link decisions to code files/PRs | High | Medium | Maintains context |
| 3 | Search decisions by keyword | High | Medium | Critical for discoverability |
| 4 | Tag decisions by domain (auth, data, etc.) | Medium | Low | Helps organization |
| 5 | GitHub integration (auto-link PRs) | High | High | Reduces manual work |
| 6 | Decision templates (what, why, alternatives) | High | Low | Guides good documentation |
| 7 | Decision changelog (track updates) | Medium | Low | Keeps docs current |
| 8 | Suggest related decisions | Medium | High | ML-based, too complex |
| 9 | Comment/discuss on decisions | Medium | Medium | Collaboration feature |
| 10 | Decision approval workflow | Low | Medium | Too heavyweight for MVP |
| 11 | Auto-generate from code | High | High | Fragile, requires AI |
| 12 | Slack notifications on new decisions | Medium | Low | Keeps team aware |
| 13 | Decision metrics (views, searches) | Low | Medium | Analytics, not core |
| 14 | Export to PDF/docs | Low | Low | Nice-to-have |
| 15 | Multi-repo support | Medium | High | Start single-repo |
| 16 | WYSIWYG editor | Low | Medium | Markdown is fine |
| 17 | Decision voting/rating | Low | Medium | Premature optimization |
| 18 | Onboarding checklist for juniors | Medium | Medium | Different feature |
| 19 | AI summary of decisions | Medium | High | Cool but risky |
| 20 | Integration with Notion/Confluence | Medium | High | Many tools to integrate |

---

### Prioritization

#### Must Have (MVP)

| Feature | Rationale |
|---------|-----------|
| Markdown editor for decisions | Core input method. Developers know Markdown. Needs template (Context, Decision, Rationale, Alternatives). |
| Search decisions by keyword | Primary use case: junior dev searches "authentication" and finds relevant decisions. Full-text search. |
| Link decisions to code files/PRs | Maintains context. "This decision relates to src/auth/login.js and PR #342." Critical for understanding. |
| Decision templates | Forces good documentation structure. Prevents vague "We decided to use X" without rationale. |
| Tag decisions by domain | Organization. Helps filtering ("Show me all auth decisions"). |

#### Should Have (v1.1)

| Feature | Rationale | Dependency |
|---------|-----------|------------|
| GitHub integration (auto-link PRs) | Reduces manual linking burden. Parses PR descriptions for decision references. | Basic linking working |
| Decision changelog | Keeps docs current. "This decision was updated on X date." Important as codebase evolves. | CRUD working |
| Slack notifications | Keeps team aware of new decisions. Low effort, high value for adoption. | Core features stable |
| Comment/discuss on decisions | Useful for clarifications. Not critical for MVP—can use GitHub issues as workaround. | Core features stable |

#### Could Have (Future)

| Feature | Rationale |
|---------|-----------|
| Multi-repo support | Teams have multiple repos. Start with single-repo, expand if needed. |
| Decision metrics | Interesting for analytics but not core value. |
| Export to PDF | Some teams might want this for handbooks. Low priority. |

#### Won't Have (Cut)

| Feature | Reason for Cut |
|---------|----------------|
| Auto-generate decisions from code | Too fragile. Code doesn't explain "why." Requires AI and likely to hallucinate. |
| Suggest related decisions | ML complexity. Manual search is fine for MVP. |
| Decision approval workflow | Adds process overhead. Trust senior devs to document well. |
| WYSIWYG editor | Markdown is developer-friendly. WYSIWYG adds complexity without value. |
| Decision voting/rating | Premature. Unclear if teams want this. |
| Onboarding checklist | Different problem. Focus on documentation first. |
| AI summary | Cool demo but risky for accuracy. Juniors need precise info, not summaries. |
| Notion/Confluence integration | Too many tools. GitHub is the priority. |

---

### MVP Definition

#### What We're Building

A GitHub-integrated documentation hub where senior devs can quickly document architecture decisions using Markdown templates, and junior devs can search and find those decisions linked to relevant code and PRs.

#### Core User Flow

**For Senior Dev (Author):**
1. Make architecture decision (e.g., "Use JWT for auth")
2. Click "New Decision" in app
3. Fill in template (Context, Decision, Rationale, Alternatives Considered)
4. Tag it (auth, security)
5. Link to relevant code files or PRs
6. Save (takes <5 minutes)

**For Junior Dev (Reader):**
1. Encounter unfamiliar pattern in code
2. Search app for keyword (e.g., "JWT")
3. Find decision with full context
4. Click through to code/PR
5. Understand rationale without asking senior dev

#### What Success Looks Like

- Senior devs document 1+ decision per week
- Junior dev time-to-first-commit reduced by 30%
- Slack questions about architecture drop by 50%
- 90% of major decisions documented within 1 month

#### What We're NOT Building (Yet)

- Auto-generation (manual authoring is fine)
- AI suggestions or summaries (text search is sufficient)
- Approval workflows (trust-based documentation)
- Multi-repo support (single repo for MVP)

---

### Risk Check

#### Cuts That Might Hurt

| Cut | Risk | Mitigation |
|-----|------|------------|
| GitHub auto-linking | Manually linking PRs is tedious for senior devs | Start manual, measure pain. Add automation if adoption suffers. |
| Comments/discussion | Teams might want to discuss decisions | Workaround: Use GitHub issues or Slack threads. Add if requested. |
| Multi-repo support | Many teams have microservices | Launch with single-repo teams first. Add multi-repo in v1.1 if demand exists. |

#### Scope Creep Triggers

- "Can we add a decision approval flow?" (Adds bureaucracy)
- "Can we auto-generate from PRs?" (Too fragile, requires AI)
- "Can we integrate with Jira?" (Different tool, different complexity)

---

### Open Questions

- Should decisions be versioned (Git-backed) or database-backed? (Git = version control built-in, but harder to search)
- How do we handle deprecated decisions? (Archive vs delete vs "superseded by X")
- Should we support private repos only or public repos too? (Start private, expand if demand)

---

## Pattern Recognition

### Common Elements Across All Examples

**Clear Must Haves:**
- All MVPs have 3-5 Must Have features maximum
- Each Must Have directly tests the core assumption
- Without any Must Have, the product doesn't solve the problem

**Aggressive Cuts:**
- AI/ML features consistently cut (too risky for MVP)
- Social features cut (premature)
- Analytics/metrics cut (build after validation)
- Integration with multiple tools cut (focus on one)

**Scope Creep Awareness:**
- Explicitly document tempting features to avoid
- Recognize adjacent problems (time tracking, meal planning, onboarding checklists)
- Defer to v1.1 unless core to value prop

**Risk Mitigation:**
- Accept workarounds for cut features
- Provide manual alternatives
- Monitor pain points for future prioritization

### Red Flags in Bad Scoping

- **20+ Must Have features** — MVP is too big
- **No Won't Have section** — Everything is in scope (nothing prioritized)
- **"Nice to haves" in MVP** — Polish before function
- **Vague success metrics** — Can't measure if assumption validated
- **No identified risks** — Overconfidence or lack of critical thinking
