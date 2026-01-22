# UX Spec: FocusFlow

## Overview

A Chrome extension that blocks distracting websites during focus sessions. Primary user goal: Start a focus session and stay focused for 60+ minutes without impulsive distractions.

---

## Information Architecture

### Navigation Structure
```
FocusFlow Extension
├── Popup (default view when clicking extension icon)
├── Block Page (shown when visiting blocked site)
├── Settings (accessed from popup)
└── Session Summary (shown after session ends)
```

*Simple 4-screen structure—minimal navigation needed*

### Key User Paths
1. **Happy path:** Popup → Start Session → Work focused → Block page reminds if distracted → Session ends → Summary
2. **Bypass path:** Block page → Request bypass → 5-min wait → Access granted → Return to focus
3. **Setup path:** Popup → Settings → Add blocked sites → Save → Return to popup

---

## User Flows

### Flow 1: Start Focus Session (Happy Path)

**Trigger:** User wants to start focused work session
**User goal:** Begin focus session quickly without setup friction

```
[Click extension icon]
        ↓
[Popup shows "Start Session"]
        ↓
[Select duration: 30/60/90/Custom]
        ↓
[Confirm blocked sites (optional)]
        ↓
[Session starts - popup shows timer]
        ↓
[User closes popup, works normally]
        ↓
[If visits blocked site → Block Page]
        ↓
[Session ends → Summary modal]
```

**Steps:**
1. User clicks FocusFlow extension icon
2. Popup opens showing "Start Focus Session" button
3. User clicks "Start" (or selects duration preset)
4. Session begins immediately
5. Extension icon changes to "active" state (green)
6. User closes popup and returns to work
7. When timer ends, summary modal appears

**Error paths:**
- If no sites in block list → Prompt to add sites first
- If session already active → Show current session status

---

### Flow 2: Encounter Blocked Site

**Trigger:** User tries to visit blocked site during session
**User goal:** Be reminded of focus session / decide whether to bypass

```
[Navigates to blocked site]
        ↓
[Block page loads immediately]
        ↓
[User sees "You're in focus mode"]
        ↓
Decision: Return to work OR Request bypass
        ↓ (if bypass)
[Click "I need to access this"]
        ↓
[5-minute cooldown starts]
        ↓
[After 5 min, site accessible for 15 min]
```

**Steps:**
1. User types twitter.com in address bar (or clicks link)
2. Instead of Twitter, block page loads
3. Page shows: timer, reason for blocking, return to work button
4. User either closes tab (success) or clicks bypass
5. If bypass: 5-minute countdown displayed
6. After cooldown: One-time access granted (15 min window)

---

## Screens

### Screen: Extension Popup (Inactive State)

**URL/Route:** `popup.html` (opened via extension icon)
**Purpose:** Start focus session or access settings
**Entry points:** Click extension icon in browser toolbar

#### Layout
```
┌─────────────────────────────┐
│  🎯 FocusFlow               │
├─────────────────────────────┤
│                             │
│  Ready to focus?            │
│                             │
│ ┌───────────────────────┐   │
│ │  Start Focus Session  │   │
│ └───────────────────────┘   │
│                             │
│  Quick start:               │
│  [30 min] [60 min] [90 min] │
│                             │
│  ⚙️ Settings  📊 History    │
└─────────────────────────────┘
```

#### Components
| Component | Description | Behavior |
|-----------|-------------|----------|
| Header | "FocusFlow" with icon | Static branding |
| Start button | Primary action | Opens duration selector or starts immediately |
| Quick start buttons | 30/60/90 min presets | One-click session start |
| Settings link | Gear icon | Opens settings screen |
| History link | Chart icon | Shows past sessions (v1.1) |

#### States
| State | Appearance | Trigger |
|-------|------------|---------|
| Default | Start button enabled, presets visible | No active session |
| Loading | Button shows spinner | Session starting |

#### Actions
| Action | Trigger | Result |
|--------|---------|--------|
| Click Start | Click main button | Show duration picker |
| Click preset | Click 30/60/90 button | Start session immediately |
| Click Settings | Click gear icon | Navigate to settings |

---

### Screen: Extension Popup (Active State)

**URL/Route:** `popup.html` (during active session)
**Purpose:** Show session status and allow early end
**Entry points:** Click extension icon while session running

#### Layout
```
┌─────────────────────────────┐
│  🎯 FocusFlow    [End]      │
├─────────────────────────────┤
│                             │
│     Focus mode active       │
│                             │
│         ⏱️ 42:15             │
│     remaining                │
│                             │
│  Sites blocked: 8           │
│  Bypass attempts: 0         │
│                             │
│  ⚙️ Settings                 │
└─────────────────────────────┘
```

#### Components
| Component | Description | Behavior |
|-----------|-------------|----------|
| Timer display | Large countdown | Updates every second |
| End button | Secondary action (top right) | Ends session early |
| Stats | Sites blocked, bypass count | Real-time updates |

#### States
| State | Appearance | Trigger |
|-------|------------|---------|
| Running | Green icon, timer counting down | Session active |
| Paused | Yellow icon, timer stopped | Pause pressed (v1.1) |

---

### Screen: Block Page

**URL/Route:** Custom page loaded when accessing blocked site
**Purpose:** Prevent distraction, provide bypass option
**Entry points:** Navigate to blocked site during session

#### Layout
```
┌─────────────────────────────────────┐
│                                     │
│         🚫                          │
│                                     │
│   You're in focus mode              │
│                                     │
│   twitter.com is blocked            │
│   until session ends                │
│                                     │
│   ⏱️ 42:15 remaining                 │
│                                     │
│                                     │
│  ┌─────────────────────────────┐   │
│  │    Return to work           │   │
│  └─────────────────────────────┘   │
│                                     │
│  I need to access this site →      │
│                                     │
└─────────────────────────────────────┘
```

#### Components
| Component | Description | Behavior |
|-----------|-------------|----------|
| Block message | Shows blocked site + reason | Static |
| Timer | Session countdown | Updates every second |
| Return button | Primary action | Closes tab or goes back |
| Bypass link | Secondary action | Starts cooldown flow |

#### States
| State | Appearance | Trigger |
|-------|------------|---------|
| Default | Block message + return button | First load |
| Cooldown | Shows 5-min countdown timer | After clicking bypass |
| Access granted | Site loads normally | After cooldown completes |

#### Actions
| Action | Trigger | Result |
|--------|---------|--------|
| Return to work | Click button or close tab | Leave blocked site |
| Request bypass | Click "I need this" link | Show cooldown overlay |

---

### Screen: Bypass Cooldown Overlay

**URL/Route:** Overlay on block page
**Purpose:** Create friction before allowing bypass
**Entry points:** Click "I need to access this" on block page

#### Layout
```
┌─────────────────────────────────────┐
│  Bypass cooldown                    │
├─────────────────────────────────────┤
│                                     │
│   Are you sure you need access?     │
│                                     │
│   You can access this site in:      │
│                                     │
│         ⏱️ 4:37                      │
│                                     │
│   Why do you need this? (optional)  │
│   ┌─────────────────────────────┐   │
│   │ e.g., Work research...      │   │
│   └─────────────────────────────┘   │
│                                     │
│   [Cancel]    [Wait for access]    │
│                                     │
└─────────────────────────────────────┘
```

#### Components
| Component | Description | Behavior |
|-----------|-------------|----------|
| Cooldown timer | 5-minute countdown | Updates every second |
| Reason input | Optional text field | Logs reason for analytics |
| Cancel button | Secondary action | Return to block page |
| Wait button | Primary action | Disabled until countdown completes |

#### States
| State | Appearance | Trigger |
|-------|------------|---------|
| Counting down | Timer running, Wait button disabled | Initial state |
| Ready | Wait button enabled, changes to "Access site" | Countdown reaches 0:00 |

---

### Screen: Session Summary

**URL/Route:** Modal overlay shown at session end
**Purpose:** Provide feedback on session performance
**Entry points:** Session timer reaches 0:00 or user ends early

#### Layout
```
┌─────────────────────────────────────┐
│  Session complete! ✅               │
├─────────────────────────────────────┤
│                                     │
│   You focused for:                  │
│       60 minutes                    │
│                                     │
│   🚫 Sites blocked: 12 attempts     │
│   ⚠️  Bypasses: 0                   │
│                                     │
│   Most blocked: twitter.com (5x)    │
│                                     │
│  ┌─────────────────────────────┐   │
│  │  Start another session      │   │
│  └─────────────────────────────┘   │
│                                     │
│  [Close]                            │
│                                     │
└─────────────────────────────────────┘
```

#### Components
| Component | Description | Behavior |
|-----------|-------------|----------|
| Duration summary | Total focus time | Static |
| Block stats | Attempts and bypasses | Calculated |
| Top blocked site | Most frequently blocked | Insight |
| Start another button | Primary CTA | Quick restart |
| Close button | Secondary | Dismiss summary |

---

### Screen: Settings

**URL/Route:** `settings.html`
**Purpose:** Manage blocked sites and preferences
**Entry points:** Click Settings from popup

#### Layout
```
┌─────────────────────────────────────┐
│  ← Back         Settings            │
├─────────────────────────────────────┤
│                                     │
│  Blocked Sites                      │
│                                     │
│  ┌─────────────────────────────┐   │
│  │ Add site...                 │+  │
│  └─────────────────────────────┘   │
│                                     │
│  ☑ twitter.com              [×]    │
│  ☑ reddit.com               [×]    │
│  ☑ youtube.com              [×]    │
│  ☑ facebook.com             [×]    │
│                                     │
│  Quick add categories:              │
│  [ ] Social Media (8 sites)         │
│  [ ] News (12 sites)                │
│  [ ] Entertainment (6 sites)        │
│                                     │
│  Session Preferences                │
│  Default duration: [60 min ▼]      │
│  Bypass cooldown: [5 min ▼]        │
│                                     │
│  [Save]                             │
└─────────────────────────────────────┘
```

#### Components
| Component | Description | Behavior |
|-----------|-------------|----------|
| Back button | Return to popup | Saves changes |
| Add site input | Text input + button | Add to block list |
| Site list | Checkboxes + remove buttons | Toggle/remove sites |
| Category checkboxes | Pre-configured lists | Batch add sites |
| Preferences | Dropdowns | Configure defaults |

---

## Interactions

### Interaction: Start Session

**Trigger:** User clicks "Start Focus Session"
**Response:** Session begins, blocking activates
**Duration:** Instant
**Feedback:**
- Extension icon changes to green
- Popup shows active session state
- Browser notification: "Focus mode activated"

---

### Interaction: Block Site Access

**Trigger:** User navigates to blocked site
**Response:** Block page loads instead of requested site
**Duration:** <100ms (feels instant)
**Feedback:**
- Block page displays with site name
- Browser tab title: "🚫 Blocked - FocusFlow"

---

### Interaction: Request Bypass

**Trigger:** User clicks "I need to access this"
**Response:** Cooldown overlay appears
**Duration:** 5 minutes
**Feedback:**
- Timer counts down in real-time
- "Wait" button disabled during countdown
- Optional: Browser notification when ready

---

## Responsive Behavior

**Breakpoints:**
- Extension popup: Fixed 400px width (extension standard)
- Block page: Responsive (full browser window)

**Key adaptations:**
- Block page: Centers content, max-width 600px
- Summary modal: Centers on screen, adapts to content height

---

## Design Notes

- **Style:** Minimal, calm, non-punishing (avoid guilt/shame)
- **Colors:** Green (focus active), Red (blocked), Gray (inactive)
- **Typography:** Clean sans-serif, large readable text
- **Tone:** Encouraging, not scolding ("You're in focus mode" vs "Access denied")

---

**Status:** ✅ Ready to feed into prompt-export
