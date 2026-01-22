# Prompt Export Examples

Complete prompts.md files for different project complexities.

---

## Example 1: Simple Project - Recipe Scaling App

*4 prompts, weekend build, solo developer*

---

# Recipe Scaling App — Development Prompts

## Context

A web app that takes recipe URLs, parses ingredients, and scales quantities to match user's desired servings. Solves the problem of home cooks manually calculating scaled measurements when cooking for larger families.

**Tech stack:** React, Vite, TailwindCSS, no backend (client-side parsing)
**Key constraints:** Stateless (no user accounts), supports top 10 recipe sites only

---

## Prompt 1: Project Setup & Layout

> Set up a new React project using Vite with Tailwind CSS. Create the basic application structure with two main views: a home page with a URL input field and a button, and a results page placeholder. Include a simple header with "RecipeScale" branding. Use React Router for navigation. The home page should have centered layout with a large input field for pasting recipe URLs and a "Scale Recipe" button below it. Make it mobile-responsive.

**Goal:** Working React app with routing and basic layout
**Checkpoint:**
- Run `npm run dev` and see home page with input field
- Input field and button are properly styled with Tailwind
- Mobile-responsive (test in DevTools)

---

## Prompt 2: Recipe URL Parsing

> Create a recipe parser module that fetches recipe HTML from a URL and extracts the recipe name, original servings, and ingredient list. Support the following recipe sites: AllRecipes, FoodNetwork, and NYT Cooking. Use a CORS proxy (like `https://api.allorigins.win/raw?url=`) to fetch the recipes client-side. Parse the HTML using DOMParser to extract ingredients using CSS selectors specific to each site. Return a structured object with recipeName, originalServings, and ingredients array (each ingredient as {quantity, unit, name}). Handle errors gracefully and return null if parsing fails.

**Goal:** Module that can parse recipes from URLs
**Checkpoint:**
- Test with 3 different recipe URLs (one from each supported site)
- Console.log should show parsed recipe object with ingredients
- Error handling works for unsupported sites (returns null)

---

## Prompt 3: Scaling Logic & Results Display

> Implement the ingredient scaling logic. Create a `scaleIngredients` function that takes an ingredients array and a scale factor (targetServings / originalServings), then multiplies all quantities. Handle fractions by converting to decimals, scaling, then converting back to simplified fractions using a fraction library (install `fraction.js`). Create the results page component that displays the scaled recipe with: recipe title, original and target servings, a servings counter (+/- buttons), the scaled ingredients list with checkboxes, and original instructions. The servings counter should allow users to adjust servings and see ingredients recalculate in real-time.

**Goal:** Working scaling logic and results display
**Checkpoint:**
- Scale a recipe from 2 to 6 servings and verify math is correct
- Fractions are simplified (14/8 becomes 1¾)
- Servings counter buttons work and trigger recalculation

---

## Prompt 4: Print Functionality & Polish

> Add print functionality with a "Print Recipe" button that opens the browser print dialog. Create print-specific CSS (using `@media print`) that hides the header, buttons, and shows only the recipe title, ingredients, and instructions. Add checkboxes to ingredients so users can check them off as they cook. Improve error handling: show a friendly error message when URL parsing fails, and add a "Try Another Recipe" button on the results page to return home. Add loading state (spinner) while fetching and parsing the recipe. Test the entire flow and fix any bugs.

**Goal:** Fully functional MVP with print support and polish
**Checkpoint:**
- Print preview shows clean recipe (no buttons/header)
- Error states display correctly for bad URLs
- Loading spinner shows during parsing
- Full flow works: paste URL → parse → scale → print

---

## Final Checklist

- [ ] Recipe parsing works for AllRecipes, FoodNetwork, NYT Cooking
- [ ] Ingredient scaling math is accurate (test with fractions and decimals)
- [ ] Print functionality produces clean printable output
- [ ] Mobile-responsive on phone screens (320px+)
- [ ] Error messages guide users when parsing fails
- [ ] No console errors in browser DevTools

---

## Example 2: Medium Project - Freelance Task Tracker

*8 prompts, 6-8 weeks, solo developer with backend*

---

# TaskTracker — Development Prompts

## Context

An automated task tracking system for freelance designers that connects to Gmail, extracts client deliverables from emails, and displays them in a unified dashboard with filtering and completion tracking.

**Tech stack:** React frontend, Node.js/Express backend, PostgreSQL database, Gmail API
**Key constraints:** Gmail-only for MVP, read-only email access, supports single user for MVP

---

## Prompt 1: Project Setup (Frontend + Backend)

> Set up a monorepo with two folders: `client` (React + Vite + TailwindCSS) and `server` (Node.js + Express). In the client, create a basic app structure with React Router and pages for: login, dashboard, and settings. In the server, set up Express with CORS, dotenv for environment variables, and a `/api/health` endpoint that returns `{status: "ok"}`. Use PostgreSQL (local or Docker) and configure the database connection using `pg` package. The client should call the health endpoint on load and display the status.

**Goal:** Full-stack project scaffold with database connection
**Checkpoint:**
- Client runs on localhost:5173 and makes API call to server
- Server runs on localhost:3000 and responds to `/api/health`
- Database connection successful (test with a simple query)

---

## Prompt 2: Gmail OAuth Flow

> Implement Google OAuth 2.0 for Gmail API access. In the server, create `/auth/google` and `/auth/google/callback` endpoints using the Google APIs client library. Store the user's refresh token in the database (users table with columns: id, email, refresh_token, created_at). In the client, create a login page with a "Connect Gmail" button that redirects to `/auth/google`. After successful auth, redirect to the dashboard with the user's email. Store the user's session using httpOnly cookies. Add middleware to protect dashboard routes (redirect to login if not authenticated).

**Goal:** Working Gmail OAuth login flow
**Checkpoint:**
- Click "Connect Gmail" and complete Google auth
- After auth, redirected to dashboard with email displayed
- Refresh page and still authenticated (session persists)
- Can access Gmail API with stored token

---

## Prompt 3: Email Fetching & Storage

> Create a background job that fetches emails from Gmail for the authenticated user. Use Gmail API to search for emails from the last 30 days with keywords: "deliverable", "due", "deadline". Create a database table `emails` with columns: id, user_id, message_id, subject, from_email, body_snippet, received_date. Store fetched emails in the database, avoiding duplicates (check message_id before inserting). Create an API endpoint `/api/sync` that triggers the sync and returns status. In the client dashboard, add a "Sync Emails" button that calls this endpoint and shows a loading state.

**Goal:** Fetch and store Gmail data
**Checkpoint:**
- Click "Sync Emails" and see loading spinner
- After sync, database contains emails with deliverable keywords
- Check database manually: `SELECT * FROM emails` shows results
- Duplicate messages not created on re-sync

---

## Prompt 4: Deliverable Extraction

> Create a deliverable extraction service that parses email subjects and bodies for deliverables and due dates. Use regex patterns to find dates (formats: "MM/DD/YYYY", "by Friday", "due tomorrow", "EOD") and natural language processing to identify deliverable items (keywords: "deliver", "send", "submit", "complete", "finish", "need by"). Create a database table `deliverables` with columns: id, user_id, email_id, title, client_name, due_date, completed, created_at. Extract client name from email sender domain or "from" name. Store extracted deliverables in the database. Create API endpoint `/api/deliverables` that returns all deliverables for the user.

**Goal:** Automated deliverable extraction from emails
**Checkpoint:**
- After email sync, deliverables table populated with extracted items
- Each deliverable has title, client, and due_date (where parseable)
- Test extraction accuracy with sample emails (aim for >70% correct)
- API endpoint returns deliverables as JSON

---

## Prompt 5: Dashboard UI with Deliverables List

> Build the dashboard main view with a sidebar and main content area. Sidebar shows "All Clients" with a count of total deliverables, followed by a list of unique clients with their deliverable counts. Main area displays deliverables in a list sorted by due date (soonest first). Each deliverable shows: checkbox for completion, title, client name, due date, and a link to the source email (Gmail URL). Overdue items (due date < today) highlighted in red, due soon (< 3 days) in yellow. Mobile-responsive: sidebar becomes a dropdown on small screens.

**Goal:** Functional dashboard displaying deliverables
**Checkpoint:**
- Dashboard loads and shows all deliverables from API
- Deliverables sorted by due date correctly
- Color coding works (red for overdue, yellow for soon)
- Mobile view: sidebar collapses into dropdown

---

## Prompt 6: Filtering & Completion Tracking

> Add client filtering functionality. When a client is clicked in the sidebar, filter the deliverables list to show only that client's items. Add a checkbox to each deliverable that marks it complete/incomplete. When checked, call PUT `/api/deliverables/:id` to update the `completed` field in the database. Completed items show with strikethrough text. Add a toggle at the top of the main area: "Show completed" (default: off) to hide/show completed deliverables. Persist filter state in URL query params so users can bookmark filtered views.

**Goal:** Interactive filtering and completion tracking
**Checkpoint:**
- Click client name and see filtered deliverables
- Check deliverable checkbox and see strikethrough + database updates
- Toggle "Show completed" to show/hide completed items
- URL updates with filter params (e.g., `?client=ClientA&showCompleted=true`)

---

## Prompt 7: Daily Email Digest

> Create a scheduled job (using `node-cron`) that runs every day at 8am server time. The job queries all users and their upcoming deliverables (due today or next 3 days, not completed). Use Nodemailer to send each user an email digest with subject "Your deliverables for today" listing the items with due dates. Include a link to the dashboard. Add a user settings page in the client where users can toggle email notifications on/off (store in database: users.email_notifications boolean). Only send emails to users with notifications enabled. Test the email job manually by triggering it via API endpoint `/api/test-email`.

**Goal:** Automated email reminders
**Checkpoint:**
- Trigger test email endpoint and receive email
- Email contains correct upcoming deliverables
- Settings page allows toggling email notifications
- Cron job configured (check logs that it runs daily)

---

## Prompt 8: Error Handling, Loading States & Final Polish

> Add comprehensive error handling throughout the app. In the client: show error messages for failed API calls, add loading spinners for all async operations (sync, dashboard load, completion toggle). In the server: wrap all routes in try-catch blocks, return proper HTTP status codes (400 for bad requests, 401 for unauthorized, 500 for server errors), log errors to console. Add Gmail token refresh logic (handle expired tokens by using refresh token to get new access token). Improve empty states: when no deliverables exist, show friendly message with "Sync Emails" CTA. Add a "Last synced" timestamp to dashboard. Test the entire flow end-to-end and fix any bugs.

**Goal:** Production-ready application with proper error handling
**Checkpoint:**
- All loading states work (no blank screens during operations)
- Error messages display when things fail (e.g., bad network)
- Gmail token refresh works (test by waiting for token expiration)
- Empty state shows when no deliverables
- No unhandled promise rejections or console errors

---

## Final Checklist

- [ ] Gmail OAuth flow works for new users
- [ ] Email sync extracts deliverables with >70% accuracy
- [ ] Dashboard displays and filters deliverables correctly
- [ ] Completion tracking persists to database
- [ ] Daily email digest sends at 8am to users with notifications enabled
- [ ] Mobile-responsive (test on phone screen)
- [ ] Error handling prevents app crashes
- [ ] Gmail token refresh handles expiration gracefully

---

## Pattern Recognition

### Simple Project (4 prompts):
1. Setup + layout
2. Core feature (parsing)
3. Main functionality (scaling + display)
4. Polish (print + error handling)

### Medium Project (8 prompts):
1. Project setup (frontend + backend + database)
2. Authentication (OAuth)
3. Data fetching (API integration)
4. Data processing (extraction logic)
5. UI for main feature (dashboard)
6. Interactive features (filtering, completion)
7. Background jobs (email digest)
8. Polish (error handling, loading states)

### Key Differences:
- Simple: Client-side only, minimal state
- Medium: Full-stack, database, authentication, background jobs
- Simple: 4 prompts, ~1 week
- Medium: 8 prompts, ~6-8 weeks

Both include clear checkpoints and final checklists for validation.
