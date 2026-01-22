# PRD Templates

Alternative PRD templates for different contexts and project types.

---

## Template 1: API Product PRD

*For backend services, developer tools, integrations*

```markdown
# PRD: [API Product Name]

## Overview
[What the API does and who it serves]

## Problem Statement
[What problem does this API solve for developers/integrations?]

## Target Users
**Primary:** [e.g., Frontend developers, Integration engineers]
**Secondary:** [e.g., DevOps, Product managers]

**Characteristics:**
- [Technical skill level]
- [Current tools/stack]
- [Pain points with existing solutions]

## Goals & Success Metrics

| Goal | Metric | Target |
|------|--------|--------|
| Adoption | Active API keys | [number] in first quarter |
| Reliability | Uptime SLA | 99.9% |
| Performance | P95 latency | <200ms |
| Developer satisfaction | NPS score | >40 |

## API Endpoints

### Endpoint 1: [Name]
**Method:** GET/POST/PUT/DELETE
**Path:** `/api/v1/resource`
**Description:** [What it does]
**Priority:** Must Have

**Request:**
```json
{
  "param1": "string",
  "param2": 123
}
```

**Response:**
```json
{
  "status": "success",
  "data": {...}
}
```

**Acceptance criteria:**
- [ ] Validates required parameters
- [ ] Returns proper HTTP status codes
- [ ] Includes error messages for failures
- [ ] Rate limited to X requests/minute
- [ ] Documented in API reference

### Endpoint 2: [Name]
[Same structure]

## Authentication & Authorization

**Method:** [API keys, OAuth 2.0, JWT]
**Scopes:** [read, write, admin]

**Acceptance criteria:**
- [ ] Secure token generation
- [ ] Token expiration handling
- [ ] Scope-based permissions enforced

## Rate Limiting

- **Free tier:** X requests/hour
- **Paid tier:** Y requests/hour
- **Burst allowance:** Z requests/minute

## Error Handling

| Error Code | Scenario | Response |
|------------|----------|----------|
| 400 | Bad Request | Invalid parameters |
| 401 | Unauthorized | Invalid/missing API key |
| 429 | Rate Limit | Too many requests |
| 500 | Server Error | Internal failure |

## Scope

### In Scope (v1)
- [Core endpoints]
- [Authentication method]
- [Error handling]
- [API documentation]

### Out of Scope
- [Webhooks - defer to v2]
- [GraphQL support - defer to v2]
- [Bulk operations - defer to v2]

## Assumptions & Risks

### Assumptions
- Developers will use REST over GraphQL for v1
- API key authentication is sufficient (OAuth not required yet)
- [Other technical assumptions]

### Risks
| Risk | Impact | Mitigation |
|------|--------|------------|
| Performance degradation at scale | High | Load testing, caching strategy, CDN |
| Breaking changes needed | High | Versioning strategy (/api/v1), deprecation policy |
| Security vulnerabilities | High | Penetration testing, rate limiting, input validation |

## Technical Requirements

- **Infrastructure:** [AWS, GCP, self-hosted]
- **Database:** [PostgreSQL, MongoDB, etc.]
- **Caching:** [Redis, Memcached]
- **Monitoring:** [Datadog, New Relic, CloudWatch]
- **Documentation:** [Swagger/OpenAPI spec]

## Developer Experience

- **Getting started guide:** Step-by-step onboarding
- **Code examples:** Python, JavaScript, curl
- **Playground:** Test API without writing code
- **SDKs:** Official libraries for [languages]
- **Changelog:** Version history and migration guides

## Open Questions
- What's the right balance between free/paid tier limits?
- Should we support webhooks in v1 or defer?
- What monitoring/alerting do we expose to users?
```

---

## Template 2: Mobile App PRD

*For iOS, Android, or cross-platform mobile applications*

```markdown
# PRD: [Mobile App Name]

## Overview
[What the app does in 2-3 sentences]

## Problem Statement
[WHO has WHAT problem WHEN, specifically on mobile]

## Target User
[Demographics, mobile usage patterns, device preferences]

**Characteristics:**
- Device: [iOS, Android, both]
- OS versions: [Minimum supported]
- Usage context: [On the go, at home, commuting]
- Data connectivity: [WiFi required, works offline]

## Goals & Success Metrics

| Goal | Metric | Target |
|------|--------|--------|
| Downloads | App Store/Play Store installs | [number] in first month |
| Engagement | Daily active users (DAU) | [percentage] of downloads |
| Retention | D7 retention rate | >[percentage]% |
| Performance | Crash-free rate | >99.5% |

## User Flows

### Flow 1: [Primary Flow Name]
**Entry point:** [App launch, deep link, notification]
**Steps:**
1. User [action]
2. App [response]
3. User [action]
4. User reaches [goal]

**Success criteria:** [What defines successful completion]

### Flow 2: [Secondary Flow Name]
[Same structure]

## Features

### Feature 1: [Name]
**Priority:** Must Have
**Screens:** [List of screens involved]
**User value:** [Why this matters on mobile]

**Acceptance criteria:**
- [ ] Works offline [if applicable]
- [ ] Loads in <2 seconds
- [ ] Touch targets min 44x44pt (iOS) / 48x48dp (Android)
- [ ] Supports dark mode
- [ ] Accessible (VoiceOver/TalkBack compatible)

## Scope

### In Scope (v1.0)
- **Platforms:** [iOS only, Android only, or both]
- **OS versions:** [iOS 15+, Android 10+]
- **Devices:** [iPhone/iPad, phone/tablet]
- **Features:** [Core features list]

### Out of Scope
- [Apple Watch/Wear OS]
- [Tablet optimization - phone-only for MVP]
- [Widgets]
- [Siri/Google Assistant shortcuts]

## Platform-Specific Considerations

### iOS
- **Design:** Follow Human Interface Guidelines
- **Notifications:** APNs integration
- **App Store:** Screenshots, ratings prompts, in-app purchases
- **Permissions:** Camera, location, notifications

### Android
- **Design:** Follow Material Design
- **Notifications:** FCM integration
- **Play Store:** Feature graphic, content rating
- **Permissions:** Runtime permission handling

## Offline Support

**What works offline:**
- [Feature 1]
- [Feature 2]

**What requires connectivity:**
- [Feature 3]
- [Feature 4]

**Sync strategy:** [Background sync, manual sync, real-time]

## Performance Requirements

- **Cold start:** <2 seconds
- **Memory usage:** <100MB typical
- **Battery impact:** <5% per hour of active use
- **App size:** <50MB download

## Assumptions & Risks

### Assumptions
- Users will grant [camera/location/notifications] permissions
- Users have [iOS 15+ / Android 10+]
- Users have reliable internet connectivity
- Native app preferred over web wrapper

### Risks
| Risk | Impact | Mitigation |
|------|--------|------------|
| App Store/Play Store rejection | High | Review guidelines compliance, beta TestFlight/internal testing |
| Poor performance on older devices | Medium | Performance testing on target minimum OS |
| Permission denials break features | Medium | Graceful degradation, clear permission rationale |

## Technical Considerations

- **Platform:** [Native iOS/Android, React Native, Flutter]
- **Backend:** [API endpoints, authentication]
- **Analytics:** [Firebase, Mixpanel, Amplitude]
- **Crash reporting:** [Crashlytics, Sentry]
- **Push notifications:** [APNs/FCM, notification service]

## Launch Checklist

### Pre-Launch
- [ ] App Store/Play Store assets ready
- [ ] Privacy policy and terms published
- [ ] Analytics and crash reporting integrated
- [ ] Beta testing completed (TestFlight/internal track)
- [ ] App Store Optimization (ASO) keywords researched

### Post-Launch
- [ ] Monitor crash rates daily
- [ ] Respond to reviews within 24 hours
- [ ] Track funnel metrics (install → signup → engagement)
- [ ] Plan v1.1 based on user feedback

## Open Questions
- Should we support iPad/tablet in v1 or phone-only?
- What's the minimum OS version we can realistically support?
- Do we need push notifications for MVP or can it wait?
```

---

## Template 3: Internal Tool PRD

*For company-internal tools, admin dashboards, employee products*

```markdown
# PRD: [Internal Tool Name]

## Overview
[What the tool does and which team/role it serves]

## Problem Statement
[WHO (which team/role) has WHAT problem WHEN in their workflow]

## Target Users
**Primary:** [Role, e.g., Customer Support team]
**Secondary:** [Role, e.g., Product managers for reporting]

**User count:** [Estimated users - important for internal tools]
**Technical skill level:** [Non-technical, technical, engineers]
**Current workaround:** [What they do today without this tool]

## Goals & Success Metrics

| Goal | Metric | Target |
|------|--------|--------|
| Efficiency | Time saved per task | -50% vs current process |
| Adoption | % of team using tool | 100% within 1 month |
| Accuracy | Error rate reduction | <1% errors |
| Satisfaction | Team NPS score | >50 |

## User Stories

### Must Have (v1)
- As a [role], I want to [action] so that [outcome that saves time/reduces errors]
- As a [role], I want to [action] so that [outcome]

### Should Have (v1.1)
- As a [role], I want to [nice-to-have] so that [marginal improvement]

## Features

### Feature 1: [Name]
**Priority:** Must Have
**User:** [Which role uses this]
**Frequency:** [How often - daily, weekly, monthly]
**Time saved:** [Estimated time savings vs current process]

**Acceptance criteria:**
- [ ] [Criteria 1]
- [ ] [Criteria 2]
- [ ] Permissions: Only [role] can access
- [ ] Audit log: All actions logged for compliance

## Scope

### In Scope (v1)
- [Core workflow automation]
- [Basic reporting]
- [Role-based permissions]

### Out of Scope
- [Advanced analytics - defer to v2]
- [External user access - internal only]
- [Mobile app - desktop web only for MVP]

## Permissions & Access Control

| Role | Permissions |
|------|-------------|
| [Role 1] | Read, write, delete |
| [Role 2] | Read only |
| [Admin] | Full access + user management |

## Assumptions & Risks

### Assumptions
- Team size won't exceed [number] users in first year
- Single sign-on (SSO) via company auth is acceptable
- Desktop web interface is sufficient (no mobile needed)
- [Other internal assumptions]

### Risks
| Risk | Impact | Mitigation |
|------|--------|------------|
| Low adoption (team keeps using old process) | High | Training sessions, mandate usage, sunset old process |
| Scope creep from stakeholders | Medium | Clear roadmap, defer non-critical requests to v2 |
| Dependency on external API/service | Medium | Fallback manual process, SLA monitoring |

## Technical Considerations

- **Platform:** Internal web app
- **Authentication:** [Company SSO, Google Workspace, Okta]
- **Hosting:** [Internal infrastructure, AWS, etc.]
- **Database:** [Access to production DB (read-only), separate DB]
- **Integrations:** [Slack, email, company APIs]

## Rollout Plan

**Phase 1:** Pilot with 5 users (1 week)
**Phase 2:** Expand to 50% of team (2 weeks)
**Phase 3:** Full team rollout

**Training:** [Documentation, video walkthrough, live demo session]

## Open Questions
- Do we need approval workflows or trust-based access?
- Should this integrate with existing [tool X] or replace it?
- What's the retention policy for old data?
```

---

## Template 4: Consumer Web App PRD

*For SaaS products, consumer web applications, productivity tools*

```markdown
# PRD: [Product Name]

## Overview
[Elevator pitch in 2-3 sentences]

## Problem Statement
[WHO has WHAT problem WHEN, with evidence if possible]

## Target User
[Persona name or description]

**Characteristics:**
- [Demographics if relevant]
- [Behavioral traits]
- [Current tools/workarounds]
- [Tech savviness]

## Goals & Success Metrics

| Goal | Metric | Target |
|------|--------|--------|
| Acquisition | Weekly signups | [number] per week |
| Activation | Completed core action | [percentage]% of signups |
| Engagement | Weekly active users | [percentage]% of signups |
| Retention | 4-week retention | >[percentage]% |
| Revenue | Paid conversion rate | >[percentage]% (if applicable) |

## User Stories

### Must Have (MVP)
- As a [user type], I want to [action] so that [benefit]
- As a [user type], I want to [action] so that [benefit]

### Should Have (v1.1)
- As a [user type], I want to [action] so that [benefit]

### Could Have (Future)
- As a [user type], I want to [action] so that [benefit]

## Features

### Feature 1: [Name]
**Priority:** Must Have
**Description:** [What it does]
**User value:** [Why it matters]
**Acceptance criteria:**
- [ ] [Functional requirement]
- [ ] [Performance requirement]
- [ ] [UX requirement]

## Onboarding Flow

1. **Landing page** → User understands value prop in <5 seconds
2. **Signup** → Email + password (or OAuth)
3. **First-time user experience** → Guided tour or empty state with clear CTA
4. **Aha moment** → User completes core action within first session

**Success metric:** X% reach aha moment in first session

## Monetization (if applicable)

**Free tier:**
- [Limited features or usage]
- [What's included]

**Paid tier ($X/month):**
- [Additional features]
- [Increased limits]

**Pricing validation:** [How you'll test pricing, or deferred for later]

## Scope

### In Scope (MVP)
- [Core features]
- [Free tier only, or both free + paid]
- [Desktop web only, or mobile-responsive]

### Out of Scope
- [Mobile native apps]
- [Team/collaboration features]
- [Advanced analytics]
- [Third-party integrations]

## Assumptions & Risks

### Assumptions
- Users will sign up without social proof (testimonials, case studies)
- Free tier is sufficient to demonstrate value
- Email/password auth is acceptable (vs. social login)
- [Other product assumptions]

### Risks
| Risk | Impact | Mitigation |
|------|--------|------------|
| Low signups (poor product-market fit) | High | User interviews, landing page testing, iterate on value prop |
| High churn (aha moment not reached) | High | Improve onboarding, user analytics to identify drop-off points |
| Competition from established players | Medium | Focus on niche, differentiate on [X], move fast |

## Technical Considerations

- **Platform:** Web (React/Vue/etc.)
- **Backend:** [Node.js, Python, etc.]
- **Database:** [PostgreSQL, MongoDB, etc.]
- **Hosting:** [Vercel, AWS, Heroku]
- **Auth:** [Auth0, Firebase Auth, custom]
- **Analytics:** [Mixpanel, Amplitude, Segment]

## Go-to-Market

**Launch channels:**
- [ProductHunt, HackerNews, Twitter]
- [Targeted communities, Reddit, forums]
- [SEO, content marketing]

**Launch goal:** [X signups in first week]

## Open Questions
- Should we offer a free trial or freemium model?
- What's the minimum feature set for paid tier to be worth $X/month?
- Do we need user onboarding or is the product self-explanatory?
```

---

## Choosing the Right Template

| Project Type | Use Template |
|--------------|--------------|
| Backend service, API, webhook platform | API Product PRD |
| iOS/Android app, React Native, Flutter | Mobile App PRD |
| Company tool, admin dashboard, internal system | Internal Tool PRD |
| SaaS, productivity tool, consumer web app | Consumer Web App PRD |
| Simple MVP, weekend project | Use simplified version of Consumer Web App template |
