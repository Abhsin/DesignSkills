# FocusFlow — Development Prompts

## Context

A Chrome extension that blocks distracting websites during self-defined focus sessions, helping remote workers stay focused. Targets users who have tried and abandoned Pomodoro/blocking apps due to either being too easy to disable or too restrictive.

**Tech stack:** Chrome Extension (Manifest V3), React, chrome.storage.local API
**Key constraints:** Desktop Chrome only, no backend/cloud sync for MVP, must handle blocking reliably

---

## Prompt 1: Chrome Extension Setup & Manifest

> Set up a new Chrome extension project using Manifest V3. Create the basic file structure: manifest.json, popup.html, popup.js, background.js, and content script. Configure the manifest with these permissions: "tabs", "storage", "webRequest", "webRequestBlocking", and "declarativeNetRequest". Set up a React development environment using Webpack to bundle the extension. The popup should be 400px wide and load a React component. Create a simple "Hello FocusFlow" popup to verify the extension loads correctly in Chrome.

**Goal:** Working Chrome extension scaffold that loads in browser
**Checkpoint:**
- Load unpacked extension in Chrome (chrome://extensions/)
- Click extension icon and see "Hello FocusFlow" popup
- No console errors in extension pages

---

## Prompt 2: Website Blocking Engine

> Implement the core website blocking mechanism using chrome.declarativeNetRequest API (Manifest V3 compatible). Create a BlockingService module that maintains a list of blocked domains in chrome.storage.local. When a site is in the blocked list AND a focus session is active, redirect requests to that domain to a custom block page (block.html). Create the block.html page with a centered message showing "You're in focus mode - [domain] is blocked" and a countdown timer showing remaining session time. Store session state (active/inactive, endTime) in chrome.storage.local and sync it to the block page.

**Goal:** Functional website blocking when session active
**Checkpoint:**
- Add "twitter.com" to block list and start a session
- Navigate to twitter.com and see custom block page load
- Session timer on block page shows correct countdown
- Blocking stops when session ends

---

## Prompt 3: Popup UI with Session Controls

> Build the extension popup UI using React. Create two states: inactive (showing "Start Focus Session" button with 30/60/90 min quick-start buttons) and active (showing countdown timer, sites blocked count, and "End Session" button). Add a simple settings icon that opens chrome.runtime.openOptionsPage(). When user clicks a preset button (30/60/90 min), immediately start a focus session by storing {active: true, endTime: Date.now() + duration} in chrome.storage. Update the popup UI every second to show remaining time. When session ends (timer reaches 0), set active to false and show a simple summary: "Session complete! You focused for [X] minutes."

**Goal:** Working session start/stop controls
**Checkpoint:**
- Click "60 min" button and see session start immediately
- Popup shows countdown timer (updates every second)
- Click "End Session" and session stops, blocking deactivates
- Session state persists across popup open/close

---

## Prompt 4: Settings Page for Block List Management

> Create an options page (settings.html) for managing the blocked sites list. Use React to build a form with: (1) an input field to add new sites (extract domain from URL automatically), (2) a list showing all currently blocked sites with remove buttons, (3) three category checkboxes ("Social Media", "News", "Entertainment") that batch-add predefined site lists. Store the blocked sites array in chrome.storage.local. Validate that URLs are valid domains before adding. Pre-populate these category lists: Social Media (twitter.com, facebook.com, instagram.com, tiktok.com, linkedin.com, reddit.com), News (cnn.com, foxnews.com, bbc.com, nytimes.com), Entertainment (youtube.com, netflix.com, twitch.tv).

**Goal:** User can customize blocked sites list
**Checkpoint:**
- Open settings, add "linkedin.com" manually and see it appear in list
- Check "Social Media" category and see 6 sites added
- Remove a site and verify it's no longer blocked during sessions
- Settings persist across browser restarts

---

## Prompt 5: Emergency Bypass with Cooldown

> Implement the bypass flow on the block page. Add an "I need to access this site" link at the bottom of the block page. When clicked, show an overlay modal with: (1) text "Are you sure you need access?", (2) a 5-minute countdown timer, (3) an optional text input "Why do you need this? (optional)", (4) a "Cancel" button and a "Wait" button (disabled until countdown completes). Store bypass state in chrome.storage: {bypassActive: true, bypassEndTime: Date.now() + 5min, site: domain}. When countdown reaches 0:00, allow access to that specific site for 15 minutes by temporarily removing it from the block rules. Log the bypass event with reason (if provided) for future analytics.

**Goal:** Bypass works with 5-minute friction
**Checkpoint:**
- Click "I need to access this" on block page
- See 5-minute countdown start
- Wait 5 minutes (or shorten for testing) and verify access is granted
- After 15 minutes, blocking resumes for that site
- Bypass event logged in chrome.storage

---

## Prompt 6: Session Summary Modal

> Create a summary modal component that appears when a session ends (either naturally or user-ended early). The modal should display: (1) "Session complete!" message, (2) total focus duration in minutes, (3) number of site block attempts ("Sites blocked: X attempts"), (4) number of bypass uses ("Bypasses: X"), (5) most frequently blocked site ("Most blocked: twitter.com (5x)"). Add a "Start another session" button that immediately starts a new session with the same duration, and a "Close" button. Show this modal as a browser notification or as a popup that auto-opens when the extension icon is clicked. Store session history in chrome.storage.local as an array of session objects: {duration, blockAttempts, bypasses, date}.

**Goal:** User sees session performance feedback
**Checkpoint:**
- Complete a session and see summary modal appear
- Summary shows accurate stats (compare to stored data)
- Click "Start another session" and new session begins
- Session history stored in chrome.storage

---

## Prompt 7: Background Service Worker & Session Timer

> Refactor the background script (background.js) to use a Service Worker (Manifest V3 requirement). Implement a reliable session timer that survives browser restarts and extension reloads. Use chrome.alarms API to check session status every minute. When a session should end (current time >= endTime), update storage to {active: false}, remove blocking rules, and trigger the summary modal. Handle edge cases: (1) browser closed during session (resume on restart), (2) extension updated/reloaded during session (preserve state), (3) system sleep/wake (adjust timer accordingly). Add a chrome.storage.onChanged listener to sync session state across all extension pages (popup, block page, background).

**Goal:** Reliable session management across browser events
**Checkpoint:**
- Start a 5-minute session
- Close and reopen browser - session continues
- Reload extension - session state preserved
- Session ends exactly when timer reaches 0 (not early/late)

---

## Prompt 8: Polish, Error Handling & Final Testing

> Add comprehensive error handling throughout the extension. Handle cases where: (1) user has no sites in block list (prompt to add sites before starting session), (2) chrome.storage quota exceeded (warn user to clear history), (3) extension permissions denied (show help message), (4) network errors on block page (graceful fallback). Add loading states for all async operations (storage reads/writes). Improve UX: (1) show toast notifications for important events ("Session started", "Blocking active"), (2) add keyboard shortcuts (Ctrl+Shift+S to start session), (3) improve block page design (better typography, calming colors, motivational message). Test the complete flow end-to-end: install extension → add sites → start session → test blocking → test bypass → end session → review summary. Fix any bugs found during testing.

**Goal:** Production-ready extension with polish
**Checkpoint:**
- Empty block list shows helpful prompt (not error)
- All async operations show loading states
- Keyboard shortcut starts session
- Block page feels calm and encouraging (not punishing)
- Full flow works without errors or console warnings
- Chrome Web Store submission-ready

---

## Final Checklist

- [ ] Website blocking works reliably (no sites load when blocked)
- [ ] Session timer accurate across browser restart
- [ ] Bypass cooldown enforced (can't skip 5-minute wait)
- [ ] Settings persist across sessions
- [ ] Session summary shows correct stats
- [ ] No console errors or warnings
- [ ] Extension icon changes state (inactive/active)
- [ ] Works on fresh Chrome install (no external dependencies)
- [ ] Manifest V3 compliant (passes Chrome Web Store validation)

---

**Estimated Timeline:** 6-8 weeks part-time (solo developer)
**Testing Strategy:** Use extension yourself daily for 2 weeks before public release

---

**Status:** ✅ Ready to build with Claude Code
