# PRD Examples

Complete PRD examples for different project sizes and contexts.

---

## Example 1: Simple Project - Recipe Scaling App

*Weekend build, solo developer, web-only MVP*

---

# PRD: RecipeScale

## Overview

A web app that automatically scales recipe ingredients from any URL to match the user's desired number of servings, eliminating mental math and measurement errors for home cooks preparing family meals.

## Problem Statement

Home cooks preparing meals for families of 5+ waste ingredients and time when online recipes serve 2-4 people, requiring mental math that leads to measurement errors and failed dishes.

## Target User

Parents (age 30-45) cooking dinner for families of 5-7 people, 5+ nights per week.

**Characteristics:**
- Limited time (30-45 min for dinner prep)
- Budget-conscious (meal planning to minimize waste)
- Moderate cooking skills
- Use Pinterest/AllRecipes for recipe discovery
- Cook while managing kids/homework/chaos

## Goals & Success Metrics

| Goal | Metric | Target |
|------|--------|--------|
| Eliminate scaling errors | User-reported scaling mistakes | Zero errors in first month |
| Increase recipe variety | New recipes tried per week | 2x increase from baseline |
| Save preparation time | Time spent on recipe prep | 5 min saved per recipe |
| Drive engagement | Return usage rate | 50% weekly active users |

## User Stories

### Must Have (MVP)
- As a home cook, I want to paste a recipe URL so that I don't have to manually type ingredients
- As a home cook, I want to specify my desired servings so that all ingredients scale automatically
- As a home cook, I want to see scaled ingredients clearly so that I can cook without recalculating
- As a home cook, I want to print the scaled recipe so that I can reference it while cooking
- As a home cook, I want fractions simplified (14/8 → 1¾) so that measurements are readable

### Should Have (v1.1)
- As a home cook, I want to manually enter ingredients when URL parsing fails
- As a home cook, I want to save my favorite recipes so that I can scale them again later
- As a home cook, I want to use a browser extension so that I don't have to copy-paste URLs

### Could Have (Future)
- As a home cook, I want to generate a shopping list from multiple recipes
- As a home cook, I want metric/imperial conversion for international recipes

## Features

### Feature 1: URL Recipe Parsing
**Priority:** Must Have
**Description:** Extracts recipe name, servings, and ingredient list from a pasted URL
**User value:** Eliminates manual data entry
**Acceptance criteria:**
- [ ] Supports top 10 recipe sites (AllRecipes, FoodNetwork, NYT Cooking, etc.)
- [ ] Parses recipe name, original servings, and ingredient list
- [ ] Shows error message for unsupported sites with clear explanation
- [ ] Completes parsing in <3 seconds

### Feature 2: Ingredient Scaling
**Priority:** Must Have
**Description:** Multiplies ingredient quantities by scaling factor (target servings ÷ original servings)
**User value:** Eliminates mental math and measurement errors
**Acceptance criteria:**
- [ ] Handles whole numbers (2 cups → 3 cups)
- [ ] Handles fractions (½ cup → ¾ cup)
- [ ] Handles decimals (1.5 tbsp → 2.25 tbsp)
- [ ] Handles mixed units (1½ cups → 2¼ cups)
- [ ] Simplifies fractions (4/8 → ½)
- [ ] Preserves original instructions unchanged

### Feature 3: Scaled Recipe Display
**Priority:** Must Have
**Description:** Shows scaled recipe with clear formatting
**User value:** Easy to read while cooking
**Acceptance criteria:**
- [ ] Displays recipe name and scaled servings prominently
- [ ] Lists all scaled ingredients with original quantities for reference
- [ ] Shows original instructions unchanged
- [ ] Mobile-responsive layout
- [ ] Print-friendly CSS

### Feature 4: Print Functionality
**Priority:** Must Have
**Description:** Generates clean printable version
**User value:** Many users cook from printed recipes
**Acceptance criteria:**
- [ ] Print button triggers browser print dialog
- [ ] Print CSS hides UI chrome (buttons, headers)
- [ ] Recipe fits on one page when possible
- [ ] Readable font size (12pt minimum)

## Scope

### In Scope (MVP)
- Web app (responsive for desktop and mobile browsers)
- URL-based recipe parsing for top 10 sites
- Ingredient scaling with fraction simplification
- Print-friendly output
- Stateless (no user accounts)

### Out of Scope
- User accounts or saved recipes (defer to v1.1)
- Manual ingredient entry (defer to v1.1)
- Dietary substitutions or modifications
- Shopping list generation
- Meal planning features
- Native mobile apps
- Support for cookbook/offline recipes

### Future Considerations
- Browser extension for one-click scaling
- User accounts with saved recipe library
- Shopping list aggregation
- Nutritional information

## Assumptions & Risks

### Assumptions
- Users find recipes on major recipe sites (not blogs or cookbooks)
- Recipe parsing can achieve 90%+ accuracy on top sites
- Users will tolerate web app vs. native mobile
- Stateless experience is acceptable for MVP

### Risks
| Risk | Impact | Mitigation |
|------|--------|------------|
| Parsing fails for many sites | High | Focus on top 10 sites, show clear error messages, add manual entry in v1.1 |
| Users want to save recipes | Medium | Launch without accounts, add if users request it |
| Mobile-only users have poor experience | Medium | Mobile-responsive design, analytics to measure mobile usage |

## Technical Considerations

- **Platform:** Web (React frontend, Node.js backend)
- **Key integrations:** Recipe site scraping (BeautifulSoup or Cheerio)
- **Data:** No persistent storage for MVP (stateless)
- **Constraints:** Must handle various recipe formats, fraction math libraries needed

## Open Questions
- Should we limit to recent recipes or handle archived/legacy recipe formats?
- How do we handle recipes with vague quantities ("a pinch," "to taste")?
- Do users want scaled instructions (e.g., cooking times) or just ingredients?

---

## Example 2: Medium Project - Freelance Task Tracker

*Side project MVP, solo developer, 6-8 weeks*

---

# PRD: TaskTracker

## Overview

An automated task tracking system that extracts client deliverables from Gmail and displays them in a unified dashboard, preventing missed deadlines for busy freelancers.

## Problem Statement

Freelance designers lose track of client deliverables when juggling 3+ projects simultaneously, leading to missed deadlines and damaged client relationships.

## Target User

Freelance designers (graphic, web, UX) working independently with 3-10 active clients.

**Characteristics:**
- Work from home or co-working spaces
- Use email, Slack, and Notion but lack unified view
- Prioritize creative work over administrative tasks
- Fear missing deadlines more than being disorganized
- Check email constantly throughout the day

## Goals & Success Metrics

| Goal | Metric | Target |
|------|--------|--------|
| Eliminate missed deadlines | User-reported missed deadlines | Zero in first month |
| Reduce admin overhead | Time spent on task management | <5 min/day |
| Drive daily engagement | Daily active users | 70% DAU |
| Improve deliverable visibility | Deliverables captured automatically | 80% extraction accuracy |

## User Stories

### Must Have (MVP)
- As a freelancer, I want to connect my Gmail account so that the system can read my client emails
- As a freelancer, I want deliverables automatically extracted from emails so that I don't manually enter tasks
- As a freelancer, I want to see all deliverables in one list so that I know what's due across all clients
- As a freelancer, I want to filter by client so that I can focus on one project at a time
- As a freelancer, I want to mark deliverables complete so that I track my progress
- As a freelancer, I want daily email reminders of upcoming deadlines so that I don't forget to check the app

### Should Have (v1.1)
- As a freelancer, I want to manually add deliverables for Slack/call-based requests
- As a freelancer, I want to see a calendar view for visual planning
- As a freelancer, I want to filter by date range for weekly planning

### Could Have (Future)
- As a freelancer, I want Slack integration for non-email communication
- As a freelancer, I want to share status updates with clients
- As a freelancer, I want time tracking integrated with deliverables

## Features

### Feature 1: Gmail OAuth Integration
**Priority:** Must Have
**Description:** Secure Gmail connection for read-only email access
**User value:** Automatic deliverable extraction without manual work
**Acceptance criteria:**
- [ ] Google OAuth flow for Gmail read-only scope
- [ ] Successful authentication stores encrypted token
- [ ] Graceful error handling for auth failures
- [ ] Re-authentication flow when token expires

### Feature 2: Email Parsing & Deliverable Extraction
**Priority:** Must Have
**Description:** Scans emails for deliverable keywords and extracts due dates
**User value:** Eliminates manual task entry
**Acceptance criteria:**
- [ ] Searches for keywords: "deliverable," "due," "deadline," "by [date]"
- [ ] Extracts client name from email sender or subject
- [ ] Parses dates in common formats (MM/DD, "next Friday," "by EOD")
- [ ] Creates deliverable record with title, client, due date, source email link
- [ ] 80% extraction accuracy on test dataset
- [ ] Scans emails from last 30 days on first sync

### Feature 3: Deliverable Dashboard
**Priority:** Must Have
**Description:** Main view showing all deliverables sorted by due date
**User value:** Single source of truth for all client work
**Acceptance criteria:**
- [ ] List view sorted by due date (soonest first)
- [ ] Shows deliverable title, client, due date, completion status
- [ ] Overdue items highlighted in red
- [ ] Due soon (<3 days) highlighted in yellow
- [ ] Click deliverable to view source email
- [ ] Mobile-responsive design

### Feature 4: Client Filtering
**Priority:** Must Have
**Description:** Filter deliverables by client
**User value:** Focus on one project context at a time
**Acceptance criteria:**
- [ ] Sidebar shows all unique clients
- [ ] Click client name to filter to that client only
- [ ] Show count of active deliverables per client
- [ ] "All clients" option to remove filter

### Feature 5: Completion Tracking
**Priority:** Must Have
**Description:** Mark deliverables complete/incomplete
**User value:** Track progress and reduce visual clutter
**Acceptance criteria:**
- [ ] Checkbox to mark complete/incomplete
- [ ] Completed items shown with strikethrough
- [ ] Toggle to show/hide completed items
- [ ] Completion state persists in database

### Feature 6: Daily Email Digest
**Priority:** Must Have
**Description:** Automated daily reminder of upcoming deliverables
**User value:** Push notification prevents forgetting to check app
**Acceptance criteria:**
- [ ] Sent every morning at 8am user's timezone
- [ ] Lists deliverables due today and next 3 days
- [ ] Includes link to app
- [ ] User can opt-out via email preference

## Scope

### In Scope (MVP)
- Web app (responsive for desktop and mobile)
- Gmail integration only (no Outlook, no Slack)
- Automatic deliverable extraction via keywords
- List view with client filtering
- Basic completion tracking
- Daily email reminders

### Out of Scope
- Manual deliverable entry (defer to v1.1)
- Calendar view (defer to v1.1)
- Slack integration (defer based on demand)
- Time tracking (different product entirely)
- Client status sharing (assumes different workflow)
- Team collaboration (targeting solo freelancers only)

### Future Considerations
- Slack integration for non-email communication
- Mobile native app if web usage is primarily mobile
- AI-powered extraction to improve accuracy beyond 80%

## Assumptions & Risks

### Assumptions
- Freelancers communicate deliverables primarily via email
- Gmail is dominant email provider for target users
- Keyword-based extraction can achieve 80% accuracy
- Users will check app daily or rely on email digests
- No need for real-time notifications (daily digest sufficient)

### Risks
| Risk | Impact | Mitigation |
|------|--------|------------|
| Low extraction accuracy | High | Start with conservative keywords (high precision). Let users correct false negatives. Monitor accuracy metrics. Add AI in v1.1. |
| Users want Slack integration | Medium | Launch with Gmail only. Survey users after 1 month. Add Slack if >40% request it. |
| Daily email becomes spam | Medium | Include clear opt-out link. Monitor unsubscribe rate. Adjust frequency if needed. |
| Gmail API rate limits | Medium | Implement incremental sync (only new emails). Cache results. Optimize query patterns. |

## Technical Considerations

- **Platform:** Web (React frontend, Node.js backend, PostgreSQL database)
- **Key integrations:** Gmail API (OAuth 2.0, read-only scope)
- **Data:** User accounts, Gmail tokens (encrypted), deliverable records
- **Constraints:** Gmail API rate limits (quota management needed), date parsing library required
- **Security:** OAuth tokens encrypted at rest, HTTPS required, no email content stored (only metadata)

## Open Questions
- Should we scan all emails or only from known client domains?
- How do we handle recurring deliverables (monthly reports)?
- What's the right pagination limit for 100+ deliverable lists?
- Should completed deliverables auto-archive after 30 days?

---

## Pattern Recognition

### Simple vs Medium Project Differences

**Simple (Recipe Scaler):**
- 4 features total
- No user accounts
- Stateless (no database)
- Single integration (recipe sites)
- 1-2 page PRD

**Medium (Task Tracker):**
- 6 features total
- User accounts required
- Database-backed
- OAuth integration (more complex)
- 3-4 page PRD
- Security considerations

### Common PRD Elements

Both examples include:
- Clear problem statement with specific user
- Quantifiable success metrics
- Must Have vs Should Have prioritization
- Explicit "Out of Scope" section
- Identified assumptions and risks
- Technical constraints documented

### Red Flags Avoided

- ✅ Not feature-stuffed (4-6 features max for MVP)
- ✅ Clear success metrics (not vague "user satisfaction")
- ✅ Honest prioritization (not everything is Must Have)
- ✅ Explicit cuts documented (Won't Have section)
- ✅ Assumptions identified and testable
