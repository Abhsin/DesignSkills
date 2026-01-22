# PRD: FocusFlow

## Overview

A Chrome extension that helps remote workers stay focused by blocking distracting websites during self-defined focus sessions, with behavioral friction (5-minute bypass cooldown) to prevent impulsive procrastination while allowing legitimate access needs.

## Problem Statement

Remote workers without dedicated office spaces lose 3+ hours daily to household distractions and context-switching, leading to missed deadlines, overtime work, and work-life boundary erosion.

## Target User

Remote knowledge workers (developers, designers, writers, analysts) who work from home full-time without a separate office space.

**Characteristics:**
- Work from bedroom, living room, or kitchen table
- Struggle with self-discipline around digital distractions
- Use Slack, email, and multiple browser tabs throughout the day
- Feel guilty about distracted time but can't seem to fix it
- Have tried and abandoned Pomodoro/blocking apps

## Goals & Success Metrics

| Goal | Metric | Target |
|------|--------|--------|
| Improve focus time | Completed session duration | 60+ min average |
| Reduce procrastination | Bypass rate per session | <30% of sessions |
| Drive daily usage | D1 retention | 60% |
| Validate value | User-reported focus improvement | 70% report improvement at 1 week |
| Prove differentiation | Churn from competitors | 40% of users previously used Freedom/Forest |

## User Stories

### Must Have (MVP)
- As a remote worker, I want to block distracting websites during focus time so that I can't impulsively check social media
- As a remote worker, I want to start and stop focus sessions manually so that I control when blocking is active
- As a remote worker, I want to customize my blocked site list so that blocking matches my specific distractions
- As a remote worker, I want a bypass option for emergencies so that I'm not completely locked out when I legitimately need access
- As a remote worker, I want to see how long I stayed focused so that I can track my progress

### Should Have (v1.1)
- As a remote worker, I want pre-configured block lists (social media, news) so that I don't have to manually add every distracting site
- As a remote worker, I want session presets (30/60/90 min) so that I don't have to choose a duration every time
- As a remote worker, I want to set a daily focus goal so that I have a target to work toward
- As a remote worker, I want to log why I bypassed a block so that I build awareness of my procrastination patterns

### Could Have (Future)
- As a remote worker, I want to see my focus trends over time so that I can measure long-term improvement
- As a remote worker, I want to schedule automatic focus sessions so that I don't have to remember to start them

## Features

### Feature 1: Website Blocking Engine
**Priority:** Must Have
**Description:** Intercepts requests to blocked sites and displays "You're in focus mode" page instead
**User value:** Core functionality - prevents impulsive distraction
**Acceptance criteria:**
- [ ] Blocks HTTP and HTTPS requests to sites on block list
- [ ] Shows custom "Focus mode active" page with session timer
- [ ] Persists block list across browser restarts
- [ ] Handles wildcards (*.twitter.com blocks all Twitter subdomains)
- [ ] Blocks sites within <100ms (feels instant)

### Feature 2: Focus Session Management
**Priority:** Must Have
**Description:** Start, pause, and end focus sessions with countdown timer
**User value:** User control over when blocking is active
**Acceptance criteria:**
- [ ] "Start Session" button launches blocking immediately
- [ ] Shows countdown timer in extension popup
- [ ] "End Session" button stops blocking and shows summary
- [ ] Session continues across browser restarts (persisted state)
- [ ] Maximum session length: 4 hours (prevent forgetting to end)

### Feature 3: Custom Block List
**Priority:** Must Have
**Description:** User can add/remove sites from block list
**User value:** Personalization for individual distraction patterns
**Acceptance criteria:**
- [ ] Add site by URL (auto-detects domain)
- [ ] Remove site from list
- [ ] View all blocked sites in settings
- [ ] Import common sites from current browsing history (one-click add)
- [ ] Validates URLs (shows error for invalid entries)

### Feature 4: Emergency Bypass with Cooldown
**Priority:** Must Have
**Description:** Allows access to blocked site after 5-minute cooldown
**User value:** Escape hatch for legitimate needs without making bypass easy
**Acceptance criteria:**
- [ ] "I need to access this site" button on block page
- [ ] Shows 5-minute countdown timer
- [ ] After cooldown, allows one-time access (15 minutes)
- [ ] Logs bypass event (for analytics)
- [ ] Asks "Why do you need this?" (optional text input)

### Feature 5: Session Summary
**Priority:** Must Have
**Description:** After session ends, shows focus duration and bypass attempts
**User value:** Immediate feedback on performance
**Acceptance criteria:**
- [ ] Displays total focus time
- [ ] Shows number of bypass attempts
- [ ] Shows websites most frequently blocked
- [ ] "Start another session" quick action button
- [ ] Summary auto-closes after 30 seconds

### Feature 6: Session Presets (v1.1)
**Priority:** Should Have
**Description:** Quick-start focus sessions with predefined durations (30/60/90 min)
**User value:** Reduces decision fatigue, faster session start
**Acceptance criteria:**
- [ ] Three preset buttons: 30min, 60min, 90min
- [ ] One-click start from extension popup
- [ ] Can still use custom duration

### Feature 7: Pre-configured Block Lists (v1.1)
**Priority:** Should Have
**Description:** Common distraction categories (Social Media, News, Entertainment)
**User value:** Reduces setup time for new users
**Acceptance criteria:**
- [ ] Social Media list (Twitter, Facebook, Instagram, TikTok, LinkedIn, Reddit)
- [ ] News list (CNN, Fox News, BBC, NYT, etc.)
- [ ] Entertainment list (YouTube, Netflix, Twitch, etc.)
- [ ] One-click enable/disable categories
- [ ] Can customize after enabling

## Scope

### In Scope (MVP)
- Chrome extension only (no Firefox, Safari, Edge)
- Desktop/laptop only (no mobile)
- Local storage (no cloud sync)
- Basic analytics (session duration, bypass count)
- Manual session start (no automation)

### Out of Scope
- Mobile app or mobile browser support
- Multi-browser support (just Chrome)
- Cloud sync across devices
- Social features (sharing, accountability partners)
- Native app blocking (only browser)
- Automatic scheduling
- Advanced analytics dashboard

### Future Considerations
- Firefox and Edge extensions (Manifest V3 compatible)
- Backend for cloud sync and cross-device support
- Mobile app (iOS/Android)
- Team/organization plans (admin controls)

## Assumptions & Risks

### Assumptions
- Remote workers primarily get distracted in web browsers (not native apps)
- 5-minute cooldown provides enough friction to prevent casual bypassing
- Users will manually start sessions (automation not required for MVP)
- Chrome extension permissions will be granted by users
- Desktop-only is acceptable for initial validation

### Risks
| Risk | Impact | Mitigation |
|------|--------|------------|
| Users disable extension during frustration | High | Make bypass available but with friction. Monitor disable rate. |
| Can't differentiate from Freedom/Cold Turkey | High | Focus on UX simplicity and behavioral friction (cooldown). Competitive interviews. |
| Users bypass by using different browser | Medium | Accept for MVP. Message: "Install on all browsers for best results." |
| Chrome extension review rejection | Medium | Review Chrome Web Store policies before submission. |
| Low retention (users abandon after Day 1) | High | Optimize onboarding, show immediate value in first session. |

## Technical Considerations

- **Platform:** Chrome Extension (Manifest V3)
- **Storage:** chrome.storage.local API (local persistence)
- **Blocking:** chrome.webRequest API (intercept requests)
- **Permissions:** tabs, storage, webRequest, webRequestBlocking
- **Frontend:** React (for popup and block page)
- **Build:** Webpack for bundling extension assets

## Open Questions
- Should bypass cooldown be configurable or fixed at 5 minutes?
- Do we ask "Why do you need this?" on bypass, or is it too much friction?
- Should we track specific sites visited during bypass for analytics?
- What icon/branding for extension? (Needs to feel calm, not punishing)

---

**Status:** ✅ Ready to feed into ux-specification
