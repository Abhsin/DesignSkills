# User Modeling Examples

Complete persona and scenario examples from different domains.

---

## Example 1: Freelance Designer Tool

### Context
**Problem:** Freelance designers lose track of client deliverables across multiple projects
**Research basis:** 12 user interviews, analysis of 500+ r/freelance posts

---

### Persona 1: The Juggler

*Mid-career freelancer balancing 5-8 active clients with varying project sizes*

**Goals:**
- Keep all client deliverables visible without constant context-switching
- Maintain professional reputation despite high workload
- Scale business without hiring help

**Context:**
- Works from home office, 8am-6pm Monday-Friday
- Checks email/Slack every 30 minutes
- Uses 4-5 different tools daily (Figma, Notion, Gmail, Slack, Stripe)
- Juggles branding, web design, and illustration projects

**Pain points:**
- Forgets about small deliverables until client asks
- Spends 30 minutes every Monday reconstructing task list from email
- Clients with different communication styles (some over-email, some over-Slack)
- Anxiety on Sunday nights about what might be missed

**Current behavior:**
- Maintains Notion database of projects (updated weekly, if that)
- Stars emails with action items (loses them after 50+ starred)
- Sets phone reminders for major deadlines
- Keeps physical notebook for daily todos

**Constraints:**
- Budget: $10-20/month max for tools
- Time: Can't spend >5 min/day on admin
- Learning curve: Needs to work immediately
- Integration: Must work with existing tools

**What success looks like:**
- Zero "Oh crap, I forgot" moments
- Confident answering "What's the status?" questions
- End of week knowing everything is captured

**Quote:** *"I'm great at the work, but I'm drowning in keeping track of it all. I just want to see what's due when without opening 5 different apps."*

---

### Persona 2: The Newbie

*Recently turned freelance after 2 years at an agency, learning client management*

**Goals:**
- Appear professional and organized to first clients
- Avoid mistakes that damage reputation
- Build systems that scale as client base grows

**Context:**
- Working from coffee shops and library
- Has 2-3 clients currently, wants 5-6
- Coming from agency where PMs handled tracking
- Overcompensates with excessive communication

**Pain points:**
- Not sure what level of tracking is "normal"
- Sends too many status updates (clients find it annoying)
- Spends hours on admin trying to "do it right"
- Fears looking unprofessional

**Current behavior:**
- Uses Trello boards (one per client, meticulously maintained)
- Sends daily email updates to clients
- Checks email every 15 minutes anxiously
- Googles "how to manage freelance clients" weekly

**Constraints:**
- Budget: Prefers free tools
- Time: Has more time than The Juggler, less experience
- Learning curve: Willing to learn if it prevents mistakes
- Integration: Doesn't have established workflow yet

**What success looks like:**
- Clients say "You're so organized!"
- Spends <30 min/day on admin
- Confident onboarding new clients

**Quote:** *"I don't know if I'm tracking too much or too little. I just don't want to screw up and lose a client."*

---

### Persona 3: The Burnt-Out Veteran

*10+ years freelancing, tired of tools, considering agency work*

**Goals:**
- Reduce admin overhead to focus on creative work
- Decide if freelancing is sustainable long-term
- Maintain quality of life while earning enough

**Context:**
- Works 4 days/week (burned out from 7-day weeks)
- Has 3-4 long-term retainer clients
- Deliberately not growing client base
- Prioritizes boundaries over revenue

**Pain points:**
- Tool fatigue—tried everything, nothing sticks
- Resentment toward admin tasks
- Clients expect instant responses (boundary violation)
- Considering going in-house for structure

**Current behavior:**
- Email-only tracking (refuses to adopt new tools)
- Weekly client check-ins on Fridays
- Says "no" to new clients frequently
- Batches similar work to minimize context-switching

**Constraints:**
- Budget: Money isn't the issue
- Time: Won't spend ANY extra time on tools
- Learning curve: Zero tolerance for setup/config
- Integration: Email or bust

**What success looks like:**
- Admin takes <1 hour/week total
- No tool that requires "maintenance"
- Can take 2-week vacation without client chaos

**Quote:** *"I've tried every todo app and project manager out there. They all require more work than they save. Just give me email."*

---

## Scenarios

### Persona 1 Scenarios

**Scenario 1.1: Monday Morning Chaos**
- **Situation:** It's 8:30am Monday, coffee in hand, opening laptop to plan the week
- **Trigger:** Realizes there are 3 client meetings this week but can't remember what needs to be ready
- **Goal:** Build week's task list and identify any urgent gaps
- **Current approach:** Opens email, Slack, Notion, and calendar. Spends 45 minutes reconstructing. Finds one forgotten deliverable due tomorrow.
- **Frustration:** "I waste the first hour of every week playing detective with my own work"

**Scenario 1.2: Client Status Request**
- **Situation:** Client Slacks at 2pm: "Hey, what's the status on the logo concepts?"
- **Trigger:** Panic—which version did I promise? When was it due?
- **Goal:** Instantly recall project status and next deliverable
- **Current approach:** Searches email for original project brief. Checks Figma files. Guesses based on memory.
- **Frustration:** "I look disorganized even when I'm not. I just can't remember every detail instantly."

### Persona 2 Scenarios

**Scenario 2.1: Onboarding New Client**
- **Situation:** Just signed first $5k client (biggest project yet)
- **Trigger:** Wants to set up tracking "the right way" from the start
- **Goal:** Create system that makes them look professional
- **Current approach:** Creates elaborate Trello board with 20 lists. Spends 3 hours setting it up. Client never sees it.
- **Frustration:** "I don't know if this is overkill or not enough. What do experienced freelancers actually do?"

**Scenario 2.2: First Missed Deadline**
- **Situation:** Client emails "Did you forget about the wireframes?"
- **Trigger:** Realizes a small deliverable slipped through the cracks
- **Goal:** Never let this happen again
- **Current approach:** Creates MORE checklists and tracking. Now spending 2 hours/day on admin.
- **Frustration:** "I'm so afraid of messing up that I'm spending more time tracking work than doing work."

### Persona 3 Scenarios

**Scenario 3.1: Tool Fatigue**
- **Situation:** Another "productivity guru" recommends Notion/Asana/Monday.com
- **Trigger:** Considers trying it, remembers the last 10 tools that didn't stick
- **Goal:** Stick with email despite its limitations
- **Current approach:** Ignores recommendation. Uses email starring despite knowing it's broken.
- **Frustration:** "I've been doing this 10 years. If a magic tool existed, I would've found it by now."

---

## Key Insights

### Commonalities
*These are table-stakes features—all personas need these*

- Visual overview of upcoming deliverables without opening multiple apps
- Low setup/maintenance overhead (<5 min/day)
- Confidence that nothing is forgotten
- Quick status lookup when clients ask

### Divergences
*These inform prioritization and feature flags*

- **Juggler** needs capacity planning (how much can I take on?)
- **Newbie** needs templates/guidance (what should I track?)
- **Veteran** needs zero-config experience (email integration only?)

- **Juggler** will pay $20/month
- **Newbie** needs free tier first
- **Veteran** won't adopt unless it's truly effortless

### Design Implications

1. **Default to simple, offer complexity**
   - Newbie shouldn't feel overwhelmed
   - Juggler should be able to add advanced features
   - Veteran should never have to configure anything

2. **Email integration is non-negotiable**
   - All personas mentioned email as source of truth
   - Tool that requires manual entry will fail

3. **Mobile-first reminder system**
   - Pain point is "forgetting," not "organizing"
   - Push notifications > beautiful dashboard

4. **Onboarding must differentiate**
   - Ask: "How many clients?" to show relevant features
   - Newbie gets templates/guidance
   - Veteran gets "import from email" only

5. **Free tier must solve core problem**
   - Newbie can't pay upfront
   - If it works, Juggler will upgrade
   - Veteran might never pay (acceptable)

---

## Validation Needed

- [ ] Do freelancers actually check dedicated tools daily, or only email/Slack?
- [ ] Would Veterans adopt if it required zero manual entry (full email parsing)?
- [ ] What's the tipping point where Jugglers start losing track? (4 clients? 6?)
- [ ] Do Newbies convert to Jugglers, or do many quit freelancing?
- [ ] Would agencies pay for team version (different persona entirely)?

---

## Anti-Patterns Avoided

✅ **Not demographic personas** - Defined by goals/behaviors, not age/gender
✅ **Not based on one interview** - Synthesized patterns from 12+ conversations
✅ **Scenarios are specific** - Actual moments, not abstract use cases
✅ **Tensions identified** - Divergences show where one-size-fits-all fails
✅ **Validation flagged** - Assumptions marked for testing

❌ **Avoided**: "Sarah, 32, lives in Brooklyn, loves yoga" - irrelevant demographics
❌ **Avoided**: "Users want better organization" - vague, not actionable
❌ **Avoided**: Treating all freelancers as homogeneous group
