# Assumption Mapping: FocusFlow

## Context

**Product:** Focus management app for remote workers
**Core assumption to test:** Remote workers will use strict website blocking if it helps them stay focused

---

## Assumptions Identified

### 1. Users will tolerate restricted internet access during work hours
**Type:** Desirability
**What must be true:** Users value productivity more than unrestricted browsing
**Evidence for:** Personas mentioned using Freedom/Forest (shows willingness)
**Evidence against:** Also mentioned disabling those tools frequently
**Risk if wrong:** No one uses the app because blocking is too restrictive

---

### 2. Desktop-only MVP is sufficient (no mobile app needed)
**Type:** Desirability / Viability
**What must be true:** Users do focus work primarily on desktop/laptop
**Evidence for:** All personas mentioned working on laptops
**Evidence against:** People use phones for procrastination too
**Risk if wrong:** Users get distracted on phone, app becomes ineffective

---

### 3. Users will accurately self-report when they get distracted
**Type:** Usability / Reliability
**What must be true:** Users are honest about distraction moments
**Evidence for:** Personas seem self-aware about procrastination patterns
**Evidence against:** Shame might prevent honest tracking
**Risk if wrong:** Data is unreliable, can't measure success

---

### 4. Free tier is necessary to drive adoption
**Type:** Viability
**What must be true:** Users won't pay upfront without trying the product
**Evidence for:** Parent persona requires free tier, Developer prefers it
**Evidence against:** Writer persona already pays for tools (might skip free tier)
**Risk if wrong:** Build complex freemium model that doesn't drive paid conversions

---

### 5. Users work in defined "sessions" (not continuous all-day)
**Type:** Usability
**What must be true:** Remote work happens in discrete focus blocks
**Evidence for:** All personas mentioned specific work windows
**Evidence against:** Some work is continuous (Developer debugging might span hours)
**Risk if wrong:** Session-based UX doesn't match actual work patterns

---

### 6. Website blocking alone reduces distractions significantly
**Type:** Desirability / Feasibility
**What must be true:** Digital distractions are the primary productivity killer
**Evidence for:** Personas mentioned Twitter, YouTube, Reddit as main distractions
**Evidence against:** Parent persona distracted by household tasks (not digital)
**Risk if wrong:** Tool only solves 50% of distraction problem

---

### 7. Users will return daily without external accountability
**Type:** Desirability / Retention
**What must be true:** App provides enough value for daily habitual use
**Evidence for:** Pain point is daily, should drive daily usage
**Evidence against:** Personas mentioned abandoning similar tools
**Risk if wrong:** One-time usage spike, no retention

---

### 8. 5-minute bypass cooldown prevents abuse
**Type:** Feasibility
**What must be true:** Users won't wait 5 minutes just to procrastinate
**Evidence for:** Psychological friction works for behavioral change
**Evidence against:** Users might just wait or use phone instead
**Risk if wrong:** Bypass feature makes blocking meaningless

---

### 9. Users can build this into existing workflow without onboarding
**Type:** Usability
**What must be true:** UX is intuitive enough for zero-learning-curve usage
**Evidence for:** All personas mentioned "no time for setup"
**Evidence against:** Focus tools typically require configuration (blocked sites, durations)
**Risk if wrong:** Abandoned during onboarding before seeing value

---

### 10. Remote workers experience guilt about procrastination
**Type:** Desirability
**What must be true:** Guilt is a strong enough motivator to change behavior
**Evidence for:** Multiple personas mentioned guilt/shame
**Evidence against:** Guilt might demotivate rather than motivate
**Risk if wrong:** Shame-based messaging backfires, drives users away

---

### 11. We can differentiate from existing Pomodoro/blocking apps
**Type:** Viability / Market
**What must be true:** Our approach is meaningfully different from competitors
**Evidence for:** TBD - need competitive analysis
**Evidence against:** Freedom, Forest, Cold Turkey already exist
**Risk if wrong:** Users don't switch from existing tools

---

### 12. Users work primarily in web browsers (vs native apps)
**Type:** Feasibility
**What must be true:** Browser extension can block most distractions
**Evidence for:** Personas mentioned websites (Twitter, Reddit, YouTube)
**Evidence against:** Native apps (Slack, Discord) also distract
**Risk if wrong:** Browser blocking is insufficient

---

## Prioritization Matrix

### High Risk × High Importance (Test First)

**1. Website blocking alone reduces distractions** (Assumption #6)
- **Why critical:** Core value proposition
- **Why risky:** Parent persona has non-digital distractions
- **Test method:** Prototype with just blocking, measure if users report improved focus
- **Cost:** Low (can test with existing blocker + survey)
- **Timeline:** 1 week

**2. Users will tolerate restricted internet access** (Assumption #1)
- **Why critical:** If users won't use blocking, product has no value
- **Why risky:** Personas mentioned disabling Freedom frequently
- **Test method:** Beta test with strict blocking, measure disable rate
- **Cost:** Medium (need working MVP)
- **Timeline:** 2 weeks

**3. We can differentiate from existing tools** (Assumption #11)
- **Why critical:** If not differentiated, no reason to switch
- **Why risky:** No competitive analysis done yet
- **Test method:** User interviews - "Why did you stop using Freedom/Forest?"
- **Cost:** Low (just interviews)
- **Timeline:** 3 days

---

### High Risk × Medium Importance (Test Second)

**4. 5-minute bypass cooldown prevents abuse** (Assumption #8)
- **Why risky:** Might not create enough friction
- **Test method:** A/B test different cooldown durations (1 min / 5 min / 10 min)
- **Cost:** Low (feature flag)
- **Timeline:** During beta

**5. Users will return daily without external accountability** (Assumption #7)
- **Why risky:** Personas mentioned abandoning similar tools
- **Test method:** Measure D1, D7, D30 retention in beta
- **Cost:** Medium (need analytics)
- **Timeline:** 4 weeks (need time to measure retention)

---

### Medium Risk × High Importance (Test Third)

**6. Free tier is necessary** (Assumption #4)
- **Why important:** Affects monetization strategy
- **Why medium risk:** Writer persona willing to pay, but minority
- **Test method:** Landing page test with "Free" vs "$5/month" pricing
- **Cost:** Low (landing page only)
- **Timeline:** 1 week

**7. Desktop-only is sufficient** (Assumption #2)
- **Why important:** Affects scope/timeline
- **Why medium risk:** Phone procrastination is real
- **Test method:** Survey beta users - "Would you use mobile version?"
- **Cost:** Low (survey question)
- **Timeline:** During beta

---

### Low Risk × Medium Importance (Monitor, Don't Test)

**8. Users can build into workflow without onboarding** (Assumption #9)
- **Why low risk:** Can add onboarding if needed
- **Test method:** Monitor drop-off during first use
- **Cost:** Free (analytics)

**9. Users will accurately self-report distractions** (Assumption #3)
- **Why low risk:** Can verify with website tracking
- **Test method:** Compare self-reported vs actual blocked attempts
- **Cost:** Low (data already collected)

**10. Users work in defined sessions** (Assumption #5)
- **Why low risk:** Can support both session-based and continuous
- **Test method:** Analyze session duration distribution in beta
- **Cost:** Free (analytics)

---

### Low Risk × Low Importance (Defer)

**11. Remote workers experience guilt** (Assumption #10)
- **Why low importance:** Nice-to-have for messaging, not core
- **Test method:** Observe beta user reactions to messaging
- **Cost:** Free (qualitative feedback)

**12. Users work primarily in browsers** (Assumption #12)
- **Why low risk:** True for most knowledge work
- **Test method:** Survey users about native app distractions
- **Cost:** Low (survey)

---

## Recommended Validation Plan

### Week 1: Competitive Analysis & User Interviews
- [ ] Interview 5 users of Freedom/Forest/Cold Turkey: "Why did you stop using it?"
- [ ] Analyze competitor features and gaps
- [ ] **Validates:** Assumption #11 (differentiation)

### Week 1: Landing Page Test
- [ ] Create landing page with value prop
- [ ] A/B test: "Free forever" vs "$5/month trial"
- [ ] Drive 200 visitors, measure signup rate
- [ ] **Validates:** Assumption #4 (free tier necessity)

### Week 2: Prototype Test
- [ ] Build minimal blocking prototype (browser extension)
- [ ] Recruit 10 users matching personas
- [ ] Have them use for 5 days
- [ ] Survey: "Did you feel more focused?" + measure bypass attempts
- [ ] **Validates:** Assumptions #1 (tolerate blocking), #6 (blocking reduces distractions)

### Week 3-4: Beta with Analytics
- [ ] Launch working MVP with 30 beta users
- [ ] Track: D1/D7/D30 retention, bypass frequency, session patterns
- [ ] Survey after 2 weeks: "Would you pay $5/month for this?"
- [ ] **Validates:** Assumptions #7 (retention), #8 (bypass cooldown), #5 (sessions)

### Week 5: Decide
- [ ] Review all validation data
- [ ] If core assumptions validated → build full MVP
- [ ] If not → pivot or kill

---

## Success Criteria for Validation

**Must validate to proceed:**
- ✅ 70%+ of prototype users report improved focus (Assumption #6)
- ✅ <30% of users disable blocking daily (Assumption #1)
- ✅ Clear differentiation from competitors identified (Assumption #11)

**Nice to validate but not blockers:**
- ⚠️ 40%+ D7 retention in beta (Assumption #7)
- ⚠️ Free tier drives 3x more signups than paid (Assumption #4)

---

## Red Flags (Kill Signals)

**Stop if:**
- ❌ Users disable blocking >50% of the time → Core value prop broken
- ❌ Can't identify clear differentiation from Freedom → No reason to exist
- ❌ <20% report improved focus → Doesn't solve the problem

---

**Status:** ✅ Ready to inform solution-scoping decisions
