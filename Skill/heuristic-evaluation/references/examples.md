# Heuristic Evaluation Examples

Sample evaluations demonstrating the process.

## Contents
- Example 1: E-commerce checkout flow
- Example 2: SaaS dashboard
- Example 3: Mobile onboarding

---

## Example 1: E-commerce Checkout Flow

**Context**: Multi-step checkout for clothing retailer. User flow: Cart → Shipping → Payment → Confirmation.

### Critical Issues

#### No progress indicator
- **Heuristic**: #1 — Visibility of system status
- **Location**: All checkout pages
- **Problem**: User cannot tell how many steps remain or current position
- **Impact**: Users abandon unsure of time commitment
- **Recommendation**: Add step indicator (e.g., "Step 2 of 4 — Shipping")
- **Severity**: 3 (Major)

#### Payment error clears form
- **Heuristic**: #9 — Help users recover from errors
- **Location**: Payment page
- **Problem**: Invalid card error clears all payment fields
- **Impact**: User must re-enter all information, high frustration
- **Recommendation**: Preserve input, highlight only invalid field
- **Severity**: 4 (Catastrophic)

### Major Issues

#### No back button on payment page
- **Heuristic**: #3 — User control and freedom
- **Location**: Payment page
- **Problem**: Cannot return to shipping to change address
- **Impact**: Must restart checkout to change shipping info
- **Recommendation**: Add "Edit shipping" link or back navigation
- **Severity**: 3 (Major)

### Minor Issues

| Issue | Heuristic | Severity |
|-------|-----------|----------|
| "Submit order" button says "Process" | #2 — Match real world | 2 |
| Promo code field has no hint text | #6 — Recognition over recall | 1 |
| No keyboard shortcuts | #7 — Flexibility | 1 |

### Strengths
- Clear error messages on form validation
- Order summary visible throughout
- Guest checkout available

---

## Example 2: SaaS Dashboard

**Context**: Analytics dashboard for marketing team. Evaluated: Main dashboard and report builder.

### Critical Issues

#### No loading state on data refresh
- **Heuristic**: #1 — Visibility of system status
- **Location**: Dashboard widgets, report builder
- **Problem**: Data updates with no indication, numbers change unexpectedly
- **Impact**: Users unsure if data is current, trust issues
- **Recommendation**: Add loading spinners, "Last updated" timestamps
- **Severity**: 4 (Catastrophic)

### Major Issues

#### Delete report has no confirmation
- **Heuristic**: #5 — Error prevention
- **Location**: Report list
- **Problem**: Single click deletes report permanently
- **Impact**: Accidental data loss
- **Recommendation**: Add confirmation modal or undo
- **Severity**: 3 (Major)

#### Mixed terminology: "Campaign" vs "Initiative"
- **Heuristic**: #4 — Consistency
- **Location**: Throughout dashboard
- **Problem**: Same concept called different names in different sections
- **Impact**: User confusion, searching in wrong places
- **Recommendation**: Audit and standardize terminology
- **Severity**: 3 (Major)

### Minor Issues

| Issue | Heuristic | Severity |
|-------|-----------|----------|
| Help opens external site | #10 — Help | 2 |
| Dense data tables | #8 — Minimalist design | 2 |
| No bulk export | #7 — Flexibility | 2 |

---

## Example 3: Mobile Onboarding

**Context**: Fitness app onboarding. User creates account, sets goals, connects devices.

### Critical Issues

#### No skip option for device connection
- **Heuristic**: #3 — User control and freedom
- **Location**: Device pairing screen
- **Problem**: Users without compatible devices are stuck
- **Impact**: Cannot complete onboarding, app unusable
- **Recommendation**: Add "Skip for now" with clear path to connect later
- **Severity**: 4 (Catastrophic)

### Major Issues

#### Goal selection uses slider with no labels
- **Heuristic**: #6 — Recognition over recall
- **Location**: Goal setting screen
- **Problem**: Slider from "less" to "more" with no numbers
- **Impact**: Users guess at values, can't set specific goals
- **Recommendation**: Show actual values (minutes, calories, etc.)
- **Severity**: 3 (Major)

#### Permissions requested all at once
- **Heuristic**: #5 — Error prevention
- **Location**: Start of onboarding
- **Problem**: 5 permission dialogs in sequence, users decline reflexively
- **Impact**: Features break later, users don't know why
- **Recommendation**: Request permissions in context when needed
- **Severity**: 3 (Major)

### Minor Issues

| Issue | Heuristic | Severity |
|-------|-----------|----------|
| Small back button | #3 — Control | 2 |
| No progress dots | #1 — Visibility | 2 |
| Terms link opens in-app browser | #4 — Consistency | 1 |

### Strengths
- Clean visual design
- Good use of illustrations
- Clear value proposition on first screen
