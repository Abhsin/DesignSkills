# Solution Scoping: FocusFlow

## Context

**Problem:** Remote workers lose 3+ hours daily to distractions
**Target User:** Remote knowledge workers without dedicated office space
**Core assumption to test:** Website blocking with behavioral friction can improve focus time by 40%

**Constraints:**
- Timeline: MVP in 8 weeks (solo developer, part-time)
- Budget: $0 for MVP (validate before spending on infrastructure)
- Skills: React, Chrome extension API, basic backend (Node.js)
- Other: Desktop web/extension only (no mobile)

---

## Feature Inventory

| # | Feature | User Value | Effort | Notes |
|---|---------|------------|--------|-------|
| 1 | Website blocking during focus sessions | High | Medium | Core value prop |
| 2 | Focus session timer (start/pause/stop) | High | Low | Basic MVP functionality |
| 3 | Customizable blocked site list | High | Low | Users need control |
| 4 | Pre-configured block lists (social, news) | Medium | Low | Reduces setup friction |
| 5 | Emergency bypass with cooldown | High | Medium | Escape hatch for legitimate needs |
| 6 | Focus time tracking/analytics | Medium | Medium | Motivates continued use |
| 7 | Session presets (30/60/90 min) | Medium | Low | Reduces decision fatigue |
| 8 | Break timer (between sessions) | Medium | Low | Pomodoro-style breaks |
| 9 | Daily focus goal (hours per day) | Medium | Low | Goal-setting motivation |
| 10 | Distraction log ("Why did you bypass?") | Medium | Medium | Self-awareness tool |
| 11 | Browser notification when visiting blocked site | High | Low | Immediate feedback |
| 12 | Dashboard showing focus trends over time | Medium | High | Requires data persistence |
| 13 | Accountability partner (share progress) | Low | High | Social feature, complex |
| 14 | Slack/Discord integration (status updates) | Low | High | Integration complexity |
| 15 | Mobile app for session sync | High | High | Out of scope for MVP |
| 16 | Native app blocking (not just browser) | Medium | High | OS-level permissions needed |
| 17 | Automatic scheduling (block 9am-5pm daily) | Medium | Medium | Calendar integration |
| 18 | Pomodoro timer with automated breaks | Low | Medium | Commoditized feature |
| 19 | Website allowlist (only access specific sites) | Medium | Low | Alternate blocking approach |
| 20 | Focus score / gamification | Low | Medium | Premature optimization |

---

## Prioritization

### Must Have (MVP)
*Product doesn't work without these*

| Feature | Rationale |
|---------|-----------|
| Website blocking during sessions | Core value proposition. Without blocking, we're just a timer app. |
| Focus session timer (start/stop) | Users need to control when blocking is active. Basic CRUD for sessions. |
| Customizable blocked site list | Different users distracted by different sites. Must allow personalization. |
| Browser notification when blocked | Immediate feedback loop when user tries to visit blocked site. Reinforces behavior change. |
| Emergency bypass with 5-min cooldown | Safety valve for legitimate needs. Without it, users will uninstall. Cooldown prevents abuse. |

### Should Have (v1.1)
*Important, but MVP can ship without them*

| Feature | Rationale | Dependency |
|---------|-----------|------------|
| Pre-configured block lists | Reduces setup friction (social media, news, entertainment). Most users distracted by same sites. | Custom lists working first |
| Session presets (30/60/90 min) | Reduces decision fatigue. User research showed these common durations. | Timer working |
| Focus time tracking | Shows progress over time. Motivates continued use. Required for retention. | Sessions working |
| Distraction log | "Why did you bypass?" prompt when using emergency bypass. Builds self-awareness. | Bypass feature working |
| Daily focus goal | Simple goal-setting (e.g., "4 hours focused work today"). Gamification lite. | Tracking working |

### Could Have (Future)
*Nice to have, low priority*

| Feature | Rationale |
|---------|-----------|
| Break timer | Nice UX improvement but not critical. Users can take breaks manually. |
| Website allowlist mode | Alternate approach (block everything except approved sites). Might be too restrictive for MVP. |
| Dashboard with trends | Requires data persistence backend. Defer until retention proven. |
| Automatic scheduling | Complex edge cases (holidays, meetings). Nice convenience, not essential. |

### Won't Have (Cut)
*Explicitly out of scope*

| Feature | Reason for Cut |
|---------|----------------|
| Mobile app | Desktop-first strategy. Validate on desktop before expanding to mobile. Separate project entirely. |
| Accountability partner / sharing | Social features add complexity. Privacy concerns. Validate solo usage first. |
| Slack/Discord integration | Integration maintenance burden. Unclear if users want this. |
| Native app blocking | Requires OS-level permissions. Browser blocking is 80% of distractions. |
| Gamification / focus score | Premature. Solve core problem first, add motivation layer later if needed. |
| Automated Pomodoro | Commoditized feature. Differentiate on blocking strength, not timer complexity. |

---

## MVP Definition

### What We're Building

A Chrome extension that blocks distracting websites during user-defined focus sessions, with a 5-minute bypass cooldown for legitimate access needs and basic focus time tracking.

### Core User Flow

1. User clicks extension icon → "Start Focus Session"
2. Selects duration (30/60/90 min or custom)
3. Confirms blocked site list (default or customized)
4. Session starts → blocked sites show "You're in focus mode" page
5. If user tries to bypass → "Are you sure? 5-minute cooldown" prompt
6. Session ends → summary (time focused, bypass attempts)
7. Optional: Quick start next session or take break

### What Success Looks Like

- 70% of users complete first focus session without bypassing
- Average session length: 60+ minutes
- 60% D1 retention (return next day)
- Users report 40% reduction in distraction time after 1 week
- <30% of sessions have bypass attempts

### What We're NOT Building (Yet)

- Mobile app (desktop validation first)
- Social/sharing features (privacy concerns, complexity)
- Advanced analytics dashboard (data shows value first)
- Native app blocking (browser is sufficient for MVP)
- Automatic scheduling (manual session start is fine)

---

## Risk Check

### Cuts That Might Hurt

| Cut | Risk | Mitigation |
|-----|------|------------|
| Mobile app | Users get distracted on phone, undermining desktop progress | Message in-app: "Pro tip: Put phone in other room during sessions." Monitor feedback for mobile demand. |
| Break timer automation | Users forget to take breaks, burn out | Show reminder between sessions: "Take a 10-minute break?" Can build auto-breaks in v1.1. |
| Dashboard/trends | Users don't see long-term progress, lose motivation | Show basic summary after each session. Add dashboard in v1.1 based on retention data. |
| Automatic scheduling | Power users want "set it and forget it" | Can add if 40%+ of users request it. Manual start is fine for MVP. |

### Scope Creep Triggers
*Watch out for these during development*

- "Let's add Notion integration!" → Different product, massive scope
- "We should support Safari too!" → Multi-browser support = 3x testing effort
- "What about focus music / ambient sounds?" → Feature creep, not differentiated value
- "Can we add team dashboards for managers?" → B2B pivot, different market entirely

---

## Open Questions

- Should bypass cooldown be configurable (1 min / 5 min / 10 min) or fixed at 5 min?
- Do we need a "nuclear option" to forcibly end session early? Or no escape at all?
- Should blocked site list sync across devices (requires backend) or stored locally only?
- What happens if user force-quits browser during session? Resume or abandon?

---

## Prototype Planning

Based on assumption-mapping validation plan, we should test:

### Prototype 1: Blocking Mechanism (Week 2)
**Type:** Technical spike
**Goal:** Prove Chrome extension can reliably block sites without easy workarounds
**Fidelity:** Minimal UI, just blocking logic
**What we'll learn:** Is the core blocking mechanism technically feasible and effective?

### Prototype 2: Bypass Cooldown (Week 3)
**Type:** Behavioral test
**Goal:** Test if 5-minute cooldown creates enough friction to prevent abuse
**Fidelity:** Full blocking + bypass flow
**What we'll learn:** Do users respect the cooldown or find workarounds?

### Prototype 3: MVP Beta (Week 4-5)
**Type:** Feature-complete MVP
**Goal:** Validate full user experience and retention
**Fidelity:** All Must Have features
**What we'll learn:** Will users actually use this daily? Does it improve focus?

---

**Status:** ✅ Ready to feed into prd-generation
