# Common UI Patterns

Reusable interaction patterns for common UX scenarios.

---

## Navigation Patterns

### Pattern: Primary Navigation (Top Bar)

**When to use:** Desktop web apps, content-heavy sites
**Components:** Logo, nav links, search, user menu
**States:** Default, hover, active, mobile collapsed

```
┌─────────────────────────────────────────────┐
│ [Logo]  Nav1  Nav2  Nav3    [Search] [User]│
└─────────────────────────────────────────────┘
```

**Behavior:**
- Logo links to home
- Active page highlighted
- User menu dropdown on click
- Mobile: Hamburger menu

---

### Pattern: Sidebar Navigation

**When to use:** Admin dashboards, complex multi-section apps
**Components:** Collapsible sidebar, nav items, sub-items
**States:** Expanded, collapsed, mobile overlay

```
┌──────┬──────────────────┐
│      │                  │
│ Nav1 │  Main Content    │
│ Nav2 │                  │
│ > N3 │                  │
│   S1 │                  │
│   S2 │                  │
└──────┴──────────────────┘
```

**Behavior:**
- Icons visible when collapsed
- Sub-items expand on click
- Active section highlighted
- Mobile: Overlay drawer

---

### Pattern: Tabs

**When to use:** Grouping related content, settings pages
**Components:** Tab labels, active indicator, content panels
**States:** Default, hover, active, disabled

```
┌──────┬──────┬──────┬──────┐
│ Tab1 │ Tab2 │ Tab3 │ Tab4 │
└──────┴──────┼──────┴──────┘
              │ Tab 2 Content
              │
```

**Behavior:**
- Click tab to switch content
- Active tab visually distinct
- Content swaps instantly (no loading)
- Keyboard: Arrow keys to navigate

---

## Form Patterns

### Pattern: Input Field

**When to use:** Text entry, email, numbers
**States:** Default, focus, filled, error, disabled

```
Label *
┌─────────────────────────────┐
│ Placeholder text            │
└─────────────────────────────┘
Helper text or error message
```

**Behavior:**
- Label above input
- Asterisk (*) for required fields
- Focus: Border highlight
- Error: Red border + error message below
- Success: Green border (optional)

---

### Pattern: Form Validation

**When to use:** User input forms
**Validation timing:** Inline (on blur) or on submit

**Error message display:**
```
┌─────────────────────────────┐
│ user@inval                  │
└─────────────────────────────┘
❌ Please enter a valid email address
```

**Success:**
```
┌─────────────────────────────┐
│ user@example.com            │
└─────────────────────────────┘
✓ Looks good
```

**Behavior:**
- Validate on field blur (not every keystroke)
- Show errors immediately
- Allow submission retry without resetting form
- Scroll to first error on submit

---

### Pattern: Multi-Step Form (Wizard)

**When to use:** Long forms, onboarding, checkouts
**Components:** Progress indicator, steps, navigation buttons

```
Step 1 of 3: Basic Info
●━━━○━━━○

[Form fields for step 1]

        [Back] [Continue →]
```

**Behavior:**
- Progress indicator shows current step
- Can't proceed with invalid inputs
- Back button preserves data
- Save progress (if applicable)

---

## List & Table Patterns

### Pattern: Data Table

**When to use:** Displaying tabular data, admin interfaces
**Components:** Headers, rows, sortable columns, actions

```
┌─────────┬──────────┬─────────┬─────────┐
│ Name ↑  │ Email    │ Status  │ Actions │
├─────────┼──────────┼─────────┼─────────┤
│ John    │ john@... │ Active  │ Edit 🗑 │
│ Jane    │ jane@... │ Pending │ Edit 🗑 │
└─────────┴──────────┴─────────┴─────────┘
```

**Behavior:**
- Click header to sort
- Hover row for highlight
- Actions appear on hover (or always visible)
- Bulk select with checkboxes (optional)

---

### Pattern: Card List

**When to use:** Visual content, products, articles
**Components:** Cards with image, title, description, action

```
┌──────────────┐  ┌──────────────┐
│  [Image]     │  │  [Image]     │
│ Title        │  │ Title        │
│ Description  │  │ Description  │
│ [Button]     │  │ [Button]     │
└──────────────┘  └──────────────┘
```

**Behavior:**
- Hover: Shadow or border effect
- Click card or button to navigate
- Responsive: 1-4 columns based on screen size

---

### Pattern: Empty State

**When to use:** Lists with no data
**Components:** Icon, message, CTA

```
     📭
  No items yet

Add your first item to get started

  [+ Create New]
```

**Behavior:**
- Friendly, encouraging message
- Clear call-to-action
- Illustrative icon or image

---

## Modal & Overlay Patterns

### Pattern: Modal Dialog

**When to use:** Forms, confirmations, focused tasks
**Components:** Overlay, modal container, close button

```
       ┌───────────────────────────┐
       │ Title              [×]    │
       ├───────────────────────────┤
       │                           │
       │ Content                   │
       │                           │
       ├───────────────────────────┤
       │        [Cancel] [Confirm] │
       └───────────────────────────┘
```

**Behavior:**
- Click overlay to close (optional)
- ESC key to close
- Focus trap (tab cycles within modal)
- Body scroll locked
- Animate in/out

---

### Pattern: Confirmation Dialog

**When to use:** Destructive actions (delete, cancel)
**Components:** Title, message, action buttons

```
┌─────────────────────────────────┐
│ Delete this item?               │
│                                 │
│ This action cannot be undone.   │
│                                 │
│      [Cancel] [Delete] (red)    │
└─────────────────────────────────┘
```

**Behavior:**
- Destructive action in red
- ESC = Cancel
- Enter = Confirm (with caution)

---

### Pattern: Dropdown Menu

**When to use:** Actions, settings, user menus
**Components:** Trigger button, menu items

```
[User ▼]

  ┌─────────────┐
  │ Profile     │
  │ Settings    │
  ├─────────────┤
  │ Log out     │
  └─────────────┘
```

**Behavior:**
- Click trigger to open
- Click outside to close
- Keyboard: Arrow keys to navigate, Enter to select
- Auto-closes on selection

---

## Feedback & Status Patterns

### Pattern: Toast Notification

**When to use:** Success messages, non-critical errors
**Components:** Message, icon, dismiss button
**Position:** Top-right or top-center

```
┌────────────────────────────┐
│ ✓ Item saved successfully │ [×]
└────────────────────────────┘
```

**Behavior:**
- Auto-dismiss after 3-5 seconds
- Manual dismiss with X
- Stack multiple toasts
- Animate in/out (slide or fade)

**Variants:**
- Success (green, ✓)
- Error (red, ✗)
- Warning (yellow, ⚠)
- Info (blue, ℹ)

---

### Pattern: Loading States

**When to use:** Async operations
**Types:** Spinner, skeleton, progress bar

**Spinner (indeterminate):**
```
     ⟳ Loading...
```

**Skeleton (better UX):**
```
┌────────────────┐
│ ▓▓▓▓           │
│ ▓▓▓▓▓▓▓        │
│ ▓▓▓▓▓          │
└────────────────┘
```

**Progress bar (determinate):**
```
Uploading file...
████████░░░░░░░░░░ 45%
```

**Behavior:**
- Show immediately for >500ms operations
- Replace with content when loaded
- Keep layout stable (no content jumping)

---

### Pattern: Error State

**When to use:** Failed requests, validation errors
**Components:** Error icon, message, retry action

```
     ❌
  Something went wrong

We couldn't load this data. Please try again.

  [Retry]
```

**Behavior:**
- Clear error message (no technical jargon)
- Actionable next step
- Optional: Support contact

---

## Search & Filter Patterns

### Pattern: Search Bar

**When to use:** Content discovery, filtering
**Components:** Input field, search icon, clear button

```
┌──────────────────────────────┐
│ 🔍 Search...              [×]│
└──────────────────────────────┘
```

**Behavior:**
- Search on Enter or button click
- Clear button appears when text entered
- Show search suggestions (optional)
- Loading state while searching

---

### Pattern: Filters

**When to use:** Narrowing large datasets
**Components:** Filter labels, dropdowns/checkboxes, active filters

```
Filter by:
[Category ▼] [Status ▼] [Date Range ▼]

Active filters: Category: Books [×]  Status: Active [×]
```

**Behavior:**
- Apply filters immediately or on "Apply"
- Show active filter chips with remove (×)
- Clear all filters button
- Preserve filters in URL

---

## Common Combinations

### Pattern: CRUD Table
Combines: Data Table + Modal + Toast + Empty State

**Use case:** Admin interfaces, data management

**Flow:**
1. Empty state → Click "+ Add" → Modal form
2. Submit → Toast success → Table with data
3. Click row → Edit modal
4. Delete → Confirmation → Toast → Updated table

---

### Pattern: Dashboard

Combines: Sidebar Nav + Cards + Charts + Empty States

**Use case:** Analytics, admin dashboards

**Layout:**
```
┌────┬──────────────────────────┐
│Nav │ ┌──────┐ ┌──────┐       │
│    │ │Card 1│ │Card 2│       │
│    │ └──────┘ └──────┘       │
│    │ ┌──────────────┐        │
│    │ │  Chart       │        │
│    │ └──────────────┘        │
└────┴──────────────────────────┘
```

---

## Responsive Patterns

### Desktop → Mobile Transformations

**Navigation:**
- Top bar → Hamburger menu
- Sidebar → Overlay drawer

**Tables:**
- Full table → Card list (stack rows)

**Multi-column:**
- 3 columns → 1 column stack

**Forms:**
- 2-column → 1-column

**Modals:**
- Centered → Full screen (mobile)
