# UX Specification Examples

Complete UX spec showing flows, screens, and interactions.

---

## Example: Recipe Scaling App (Simple Project)

---

# UX Spec: RecipeScale

## Overview

A web app that scales recipe ingredients by parsing URLs and calculating new quantities based on desired servings. Primary user goal: Get scaled recipe in <30 seconds without manual math.

---

## Information Architecture

### Navigation Structure
```
RecipeScale (Home)
```
*Single-page app—no complex navigation needed*

### Key User Paths
1. **Happy path:** Home → Paste URL → Enter servings → View scaled recipe → Print
2. **Error path:** Home → Paste URL → Parsing error → Manual fallback

---

## User Flows

### Flow 1: Scale Recipe (Happy Path)

**Trigger:** User finds recipe online
**User goal:** Scale ingredients to desired servings

```
[Home Page - Empty State]
           ↓
[User pastes recipe URL]
           ↓
[System parses recipe]
           ↓
[User enters target servings]
           ↓
[System calculates scaled ingredients]
           ↓
[Scaled recipe displayed]
           ↓
[User prints or cooks]
```

**Steps:**
1. User navigates to RecipeScale.com
2. User copies recipe URL from Pinterest/AllRecipes
3. User pastes URL into input field
4. System fetches and parses recipe (2-3 seconds)
5. User sees original recipe with servings selector
6. User adjusts servings slider/input (e.g., 2 → 6)
7. System recalculates all ingredient quantities
8. User sees scaled recipe with simplified fractions
9. User clicks Print or cooks from screen

**Error paths:**
- If parsing fails: Show error + suggest manual entry (defer to v1.1)
- If URL invalid: Prompt for valid recipe URL
- If network error: Show retry button

---

## Screens

### Screen: Home (Empty State)

**URL/Route:** `/`
**Purpose:** Entry point for pasting recipe URL
**Entry points:** Direct navigation, bookmark, search

#### Layout
```
┌─────────────────────────────────────┐
│         RecipeScale                 │
├─────────────────────────────────────┤
│                                     │
│    Scale Any Recipe Instantly       │
│                                     │
│  ┌───────────────────────────────┐ │
│  │ Paste recipe URL here...      │ │
│  └───────────────────────────────┘ │
│         [Scale Recipe]              │
│                                     │
│  Works with AllRecipes, FoodNetwork,│
│  NYT Cooking, and more              │
└─────────────────────────────────────┘
```

#### Components
| Component | Description | Behavior |
|-----------|-------------|----------|
| Logo/Title | "RecipeScale" | Centered, large font |
| Input field | URL input | Accepts recipe URL, validates on paste |
| Scale button | Primary CTA | Disabled until valid URL entered |
| Supported sites | Footer text | Lists top recipe sites |

#### States
| State | Appearance | Trigger |
|-------|------------|---------|
| Default | Empty input, button disabled | Initial load |
| URL entered | Input filled, button enabled | User pastes URL |
| Loading | Button shows spinner | After click, during parsing |
| Error | Red border, error message | Parsing fails |

#### Actions
| Action | Trigger | Result |
|--------|---------|--------|
| Paste URL | User pastes in input | Button enables if valid URL |
| Click "Scale Recipe" | Click button | Navigate to Scaled Recipe screen |
| Clear input | Click X icon | Reset to default state |

---

### Screen: Scaled Recipe

**URL/Route:** `/?url=[encoded-recipe-url]&servings=[number]`
**Purpose:** Display scaled recipe with adjustable servings
**Entry points:** After successful parsing from Home screen

#### Layout
```
┌─────────────────────────────────────┐
│ ← RecipeScale                       │
├─────────────────────────────────────┤
│ Chocolate Chip Cookies              │
│                                     │
│ Original: 24 cookies (2 servings)   │
│ Scaled: 72 cookies                  │
│                                     │
│ Servings: [- 6 +]                   │
│                                     │
│ Ingredients:                        │
│ ☐ 3 cups flour (originally 1 cup)   │
│ ☐ 1½ cups sugar (originally ½ cup)  │
│ ☐ ...                               │
│                                     │
│ Instructions:                       │
│ 1. Mix flour and sugar...           │
│ 2. ...                              │
│                                     │
│  [Print Recipe]  [Scale Another]    │
└─────────────────────────────────────┘
```

#### Components
| Component | Description | Behavior |
|-----------|-------------|----------|
| Back button | Return to home | Clears current recipe |
| Recipe title | Parsed recipe name | Display only |
| Servings counter | +/- buttons, input | Recalculates on change |
| Ingredients list | Checkboxes + scaled quantities | Check off as you cook |
| Instructions | Original text | Unchanged from source |
| Print button | Print CTA | Opens print dialog |
| Scale Another | Secondary action | Return to home |

#### States
| State | Appearance | Trigger |
|-------|------------|---------|
| Default | Scaled to user's servings | Initial load |
| Recalculating | Disabled +/- buttons | During calculation (instant) |
| Print preview | Clean layout, no buttons | Print dialog opened |

#### Actions
| Action | Trigger | Result |
|--------|---------|--------|
| Adjust servings | Click +/- or type number | Recalculate all ingredients |
| Check ingredient | Click checkbox | Mark as used |
| Print | Click Print button | Open browser print dialog |
| Scale Another | Click button | Return to home, reset state |

---

## Components

### Component: Servings Counter

**Used in:** Scaled Recipe screen
**Purpose:** Adjust target servings for scaling

#### Props/Inputs
| Prop | Type | Description |
|------|------|-------------|
| initialValue | number | Starting servings count |
| min | number | Minimum servings (default: 1) |
| max | number | Maximum servings (default: 99) |
| onChange | function | Callback when value changes |

#### Variants
- **Default:** +/- buttons with input field
- **Slider:** Alternative UI (defer to v1.1)

#### States
- Default: Black text, enabled buttons
- Disabled: Gray text, disabled buttons (during calculation)
- Focus: Blue outline on input

---

## Interactions

### Interaction: Real-time Scaling

**Trigger:** User changes servings number
**Response:** All ingredient quantities recalculate
**Duration:** Instant (<50ms)
**Feedback:** No explicit loading (too fast to need it)

### Interaction: Print Recipe

**Trigger:** User clicks "Print Recipe" button
**Response:** Browser print dialog opens with print-friendly layout
**Duration:** Instant
**Feedback:** Print preview shows cleaned-up version (no buttons, header simplified)

---

## Responsive Behavior

**Breakpoints:**
- Mobile: < 768px
- Desktop: ≥ 768px

**Key adaptations:**
- Input field: Full width on mobile, max-width 500px on desktop
- Ingredients list: Single column always (no multi-column needed)
- Print button: Full width on mobile, auto width on desktop

---

## Design Notes

- **Style:** Minimal, clean, recipe-focused (not over-designed)
- **Typography:** Large, readable fonts (recipe viewed while cooking)
- **Colors:** Minimal—black text, blue accents, white background
- **Print-friendly:** Clean black-and-white print output

---

## Example: Freelance Task Tracker (Medium Project)

*(Abbreviated—showing key differences from simple project)*

---

# UX Spec: TaskTracker

## Information Architecture

### Navigation Structure
```
TaskTracker
├── Dashboard (default)
├── Settings
└── Help
```

### Key User Paths
1. **Onboarding:** Home → Connect Gmail → View parsed deliverables
2. **Daily usage:** Dashboard → Filter by client → Mark complete
3. **Settings:** Dashboard → Settings → Adjust email preferences

---

## User Flows

### Flow 1: First-Time Setup

**Trigger:** New user visits site
**User goal:** Connect Gmail and see deliverables

```
[Landing Page]
     ↓
[Click "Connect Gmail"]
     ↓
[Google OAuth dialog]
     ↓
[Grant permissions]
     ↓
[Parsing emails... loading]
     ↓
[Dashboard with deliverables]
```

### Flow 2: Daily Task Management

**Trigger:** User checks morning email, remembers to check app
**User goal:** See what's due, mark completed work

```
[Dashboard]
     ↓
[Filter to specific client]
     ↓
[Review deliverables]
     ↓
[Check completed items]
     ↓
[Items marked done, visual update]
```

---

## Screens

### Screen: Dashboard

**URL:** `/dashboard`
**Purpose:** Primary workspace showing all deliverables

#### Layout
```
┌────┬──────────────────────────────┐
│Logo│ Dashboard  Settings  Logout  │
├────┴──────────────────────────────┤
│                                   │
│ My Deliverables                   │
│                                   │
│ Sidebar:          Main Area:      │
│ All Clients (8)   ┌─────────────┐│
│ Client A (3)      │Due Today (2)││
│ Client B (2)      ├─────────────┤│
│ Client C (1)      │☐ Logo v3    ││
│ ...               │  Client A   ││
│                   │  Due: Today ││
│                   │             ││
│                   │☐ Wireframes ││
│                   │  Client B   ││
│                   │  Due: Jan 18││
│                   └─────────────┘│
│                                   │
│ [+ Refresh]       Show completed  │
└───────────────────────────────────┘
```

*(Continue with Components, States, Actions similar to Recipe Scaler example)*

---

## Key Differences: Simple vs Medium Project

**Simple (Recipe Scaler):**
- 2 screens total
- No authentication
- Single user flow
- Minimal state management
- No navigation

**Medium (Task Tracker):**
- 5+ screens
- OAuth authentication
- Multiple user flows
- Complex state (filters, syncing)
- Full navigation system
- Background data sync

Both specs include the same level of detail—the complexity shows in the number of screens and interactions, not the documentation depth.
