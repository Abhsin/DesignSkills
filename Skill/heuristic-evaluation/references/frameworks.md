# Heuristic Frameworks Reference

Detailed definitions for usability evaluation frameworks.

## Contents
- Nielsen's 10 Usability Heuristics (full definitions)
- Shneiderman's 8 Golden Rules
- Cognitive Walkthrough method
- Choosing the right framework

---

## Nielsen's 10 Usability Heuristics

### 1. Visibility of System Status

The system should always keep users informed about what is going on, through appropriate feedback within reasonable time.

**Look for**:
- Loading states and progress indicators
- Success/failure confirmation after actions
- Current location in navigation
- Selected/active states
- Real-time validation feedback
- System availability indicators

**Violation examples**:
- Form submits with no feedback
- No indication of background processing
- Unclear which tab/section is active
- Save button doesn't confirm save completed

### 2. Match Between System and Real World

The system should speak the users' language, with words, phrases and concepts familiar to the user, rather than system-oriented terms.

**Look for**:
- Jargon-free language
- Domain-appropriate metaphors
- Logical information ordering (chronological, alphabetical, by importance)
- Icons that match real-world objects
- Conventions from the user's field

**Violation examples**:
- Technical error codes instead of plain language
- Features named for internal codenames
- Alphabetical order when priority order makes sense
- Unfamiliar iconography

### 3. User Control and Freedom

Users often choose system functions by mistake and will need a clearly marked "emergency exit" to leave the unwanted state.

**Look for**:
- Undo/redo functionality
- Cancel buttons on dialogs and processes
- Back navigation that works predictably
- Easy exit from flows
- Ability to edit/change after submission

**Violation examples**:
- No way to cancel mid-flow
- Destructive actions without undo
- Trapped in modal with no close
- Can't edit after save

### 4. Consistency and Standards

Users should not have to wonder whether different words, situations, or actions mean the same thing.

**Look for**:
- Same terminology throughout
- Same actions produce same results
- Platform conventions followed (iOS patterns on iOS, etc.)
- Visual consistency (colors, spacing, typography)
- Interaction patterns match expectations

**Violation examples**:
- "Save" in one place, "Submit" in another for same action
- Click vs double-click inconsistency
- Different icon styles mixed
- Breaking platform conventions

### 5. Error Prevention

Even better than good error messages is a careful design which prevents a problem from occurring in the first place.

**Look for**:
- Confirmation for destructive actions
- Constraints that prevent invalid input
- Smart defaults
- Undo instead of "are you sure?"
- Disable invalid options

**Violation examples**:
- Delete with no confirmation
- Date field accepts invalid dates
- No default value when one is sensible
- Options visible but not available

### 6. Recognition Rather Than Recall

Minimize the user's memory load by making objects, actions, and options visible.

**Look for**:
- Visible options (menus, buttons)
- Contextual help and hints
- Recent items / history
- Suggestions and autocomplete
- Instructions visible at point of need

**Violation examples**:
- Must remember keyboard shortcuts
- Hidden navigation requiring memorization
- No placeholder text or input hints
- Instructions on a previous screen

### 7. Flexibility and Efficiency of Use

Accelerators—unseen by the novice user—may often speed up the interaction for the expert user.

**Look for**:
- Keyboard shortcuts
- Customizable interface
- Recent/favorites
- Bulk actions
- Power user features that don't complicate basic use

**Violation examples**:
- No keyboard navigation
- Must click through every step, no shortcuts
- Can't customize frequent workflows
- One item at a time only

### 8. Aesthetic and Minimalist Design

Dialogues should not contain information which is irrelevant or rarely needed.

**Look for**:
- Clear visual hierarchy
- Only essential information visible
- Progressive disclosure of details
- Whitespace used effectively
- Signal-to-noise ratio

**Violation examples**:
- Cluttered interface
- All options visible regardless of frequency
- Decorative elements that distract
- Dense text walls

### 9. Help Users Recognize, Diagnose, and Recover from Errors

Error messages should be expressed in plain language (no codes), precisely indicate the problem, and constructively suggest a solution.

**Look for**:
- Plain language error messages
- Specific problem identification
- Actionable recovery suggestions
- Error message near the problem
- Preservation of user input on error

**Violation examples**:
- "Error 500"
- "Invalid input" (which one?)
- No suggestion how to fix
- Error clears the form

### 10. Help and Documentation

Even though it is better if the system can be used without documentation, it may be necessary to provide help.

**Look for**:
- Searchable help
- Task-oriented documentation
- Contextual help (tooltips, info icons)
- Concise, scannable content
- Accessible when needed, not intrusive

**Violation examples**:
- No help available
- Help is system-oriented not task-oriented
- Help opens in new window, loses context
- Tooltips are unhelpful ("Click to submit" on Submit button)

---

## Shneiderman's 8 Golden Rules

Use when evaluating interaction-heavy interfaces (data entry, complex forms, productivity tools).

### 1. Strive for Consistency
Consistent sequences of actions for similar situations.

### 2. Seek Universal Usability
Cater to novice and expert users. Allow customization.

### 3. Offer Informative Feedback
For every user action, provide system feedback.

### 4. Design Dialogs to Yield Closure
Sequences should have beginning, middle, end with clear completion feedback.

### 5. Prevent Errors
Design so users cannot make serious errors.

### 6. Permit Easy Reversal of Actions
Actions should be reversible to reduce anxiety.

### 7. Keep Users in Control
Users should feel they initiate actions, not respond to them.

### 8. Reduce Short-Term Memory Load
Don't require users to remember info across screens.

---

## Cognitive Walkthrough

Use when evaluating first-time user experience or onboarding flows.

For each step in the task, ask:
1. Will user know what to do? (Clear call to action?)
2. Will user see the correct action is available? (Visible?)
3. Will user know this action achieves their goal? (Clear mapping?)
4. Will user understand feedback after action? (Clear confirmation?)

If "no" to any question, document as an issue.

---

## Choosing the Right Framework

| Situation | Framework |
|-----------|-----------|
| General usability review | Nielsen's 10 |
| Data-heavy / forms | Shneiderman's 8 |
| First-time user experience | Cognitive Walkthrough |
| Accessibility focus | WCAG (use accessibility-audit skill) |
| Brand/visual consistency | Custom rubric |
| Domain-specific | Custom rubric based on domain standards |
