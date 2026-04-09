# NutriFlow — Meeting Notes (Jan 13 – Apr 7, 2026)

The NutriFlow team met most **Tuesdays and Thursdays** during the Spring semester from **3:30 to ~5:30 pm**.

---

## Week of Jan 12, 2026

### **Tue, Jan 13, 2026 — Spring Kickoff & Repo Status Review**
**Topics**
- Reviewed Fall deliverables and current repository state to identify gaps between MVP plan and what was implementable by Expo.
- Reconfirmed the “final build” scope: cross-platform Expo app with core authenticated workflows and a polished public landing.
- Identified the highest-risk areas for Spring: authentication stability, API contract integration, and consistent UI across web/mobile.

**Decisions**
- Prioritize **end-to-end user workflows** (auth → home → meal plan → shopping/pantry → insights) over adding new experimental features.
- Reaffirm role split for Spring execution: **Sam** leads course deliverables + UI design + ~half of UI implementation; **Randy** leads backend development + API/UI integration + ~half of UI implementation.

**Action Items**
- Sam: create a checklist of “Expo-ready” screens and the minimum behaviors each must support.
- Randy: audit the navigation and theming approach for cross-platform consistency.

### **Thu, Jan 15, 2026 — Architecture Alignment (Frontend ↔ API Contract)**
**Topics**
- Reviewed API interaction patterns and how the frontend should consume typed endpoints.
- Discussed state management boundaries: React Query for server state; lightweight local state for UI.
- Walked through authentication token persistence approach for web vs native.

**Decisions**
- Use a typed contract layer for requests and response validation to reduce integration errors.
- Standardize error/loading states for all data-fetching pages.

**Action Items**
- Both: align page shells to a “thin route” pattern with shared layout components.
- Randy: focus on API/UI integration patterns (typed endpoints, query keys, error handling contracts).

---

## Week of Jan 19, 2026

### **Tue, Jan 20, 2026 — Expo Router Route Groups & Layouts**
**Topics**
- Confirmed file-based routing structure and finalized route group intent: `(public)`, `(auth)`, `(main)`.
- Reviewed protected route behavior and redirect strategy when unauthenticated.
- Planned web navigation vs mobile navigation differences.

**Decisions**
- Web uses a navigation bar; mobile uses tab navigation for primary sections.
- Auth guard should redirect unauthenticated users away from main routes without exposing partial content.

**Action Items**
- Randy: implement/finish main navigation configuration and ensure routes match screen names.
- Sam: validate route group mapping and identify any missing pages needed for final flow.

### **Thu, Jan 22, 2026 — Theme & Styling Consistency**
**Topics**
- Revisited styling pain points from Fall (web CSS differences, component inconsistencies).
- Confirmed standards for spacing, typography, and reusable page layouts.
- Checked dark mode support and ensured consistent semantic colors.

**Decisions**
- Maintain a single design language across pages using shared components (headers, cards, page layout wrappers).

**Action Items**
- Both: refactor remaining screens to shared layout primitives and ensure consistent background behavior.

---

## Week of Jan 26, 2026

### **Tue, Jan 27, 2026 — Auth Flows Stabilization**
**Topics**
- Verified sign-in/sign-up screens for web + mobile.
- Reviewed edge cases: cold start, token hydration, sign-out, and navigation after auth changes.
- Ensured “signed out” state can’t access main navigation.

**Decisions**
- Treat auth as a global provider concern with a predictable “loading → authenticated/unauthenticated” lifecycle.

**Action Items**
- Sam: run a full sign-in → sign-out → sign-in regression pass on web.
- Randy: tighten redirect logic so main layout never flashes protected content.

### **Thu, Jan 29, 2026 — Landing Page Finalization Plan**
**Topics**
- Reviewed landing page sections and content structure.
- Ensured landing content clearly communicates NutriFlow’s purpose and directs users to sign-in/sign-up.
- Identified small UI polish items (spacing, section separators, responsiveness).

**Decisions**
- Landing page will serve as the professional “front door” for the repo/demo.

**Action Items**
- Both: apply final UI polish to landing page and ensure consistent typography and section alignment.

---

## Week of Feb 2, 2026

### **Tue, Feb 3, 2026 — Home Dashboard: Core Widgets & Daily Workflow**
**Topics**
- Designed the home dashboard to support “daily use” without forcing deep navigation.
- Reviewed what should be visible immediately: greeting, quick actions, progress summary, pantry highlights.
- Discussed adding light motion/scroll reveal for polish while keeping performance acceptable.

**Decisions**
- Home page should emphasize **actionable next steps** (log intake, check plan, review pantry/shopping).

**Action Items**
- Randy: implement/refine home widgets and ensure loading states are graceful.
- Sam: verify home navigation paths cover all critical screens.

### **Thu, Feb 5, 2026 — Insights: Weekly Summary & Progress Signals**
**Topics**
- Reviewed insights goals: lightweight progress signals that encourage consistency.
- Discussed how insights should fail gracefully when data is missing (new users).
- Confirmed UI expectations: clear headings, readable summaries, and consistent cards.

**Decisions**
- Insights will focus on “useful and readable” rather than complex analytics for Expo readiness.

**Action Items**
- Both: ensure insights screen has consistent error + retry states and no dead ends.

---

## Week of Feb 9, 2026

### **Tue, Feb 10, 2026 — Dietary Preferences Screen**
**Topics**
- Confirmed preference categories: diet type, allergens, and food category preferences.
- Ensured preference options map to shared enums/schemas to avoid mismatch.
- Reviewed UX: chip/toggle patterns, save feedback, and persisted selections.

**Decisions**
- Use a single, clear save flow with success/error feedback and visible “unsaved changes” behavior.

**Action Items**
- Sam: test preference save persistence (navigate away/back; reload on web).
- Randy: polish preference UI (icons, spacing, selection states).

### **Thu, Feb 12, 2026 — Profile & Settings Hub**
**Topics**
- Defined profile page role as the “account hub”: links to preferences, household, sign-out.
- Reviewed premium/upgrade messaging placement and ensured it doesn’t block core flows.
- Confirmed consistent layout and spacing with other main screens.

**Decisions**
- Profile must remain simple and reliable; no complex settings buried behind unclear navigation.

**Action Items**
- Both: align profile links with the final navigation structure and verify sign-out returns to landing.

---

## Week of Feb 16, 2026

### **Tue, Feb 17, 2026 — Meal Plan Page Shell & Planning Workflow**
**Topics**
- Confirmed meal plan screen as a “thin route” that delegates heavy UI/logic to shared components.
- Reviewed the planning flow users should be able to complete for the demo: view days/slots, add/remove planned items.
- Discussed boundaries for Expo scope (avoid overbuilding advanced calendar features).

**Decisions**
- Implement and demo the **core planning workflow** first; treat advanced planning modules as future work.

**Action Items**
- Randy: ensure meal plan interactions are stable and handle empty states well.
- Sam: verify meal plan navigation integrates with recipes/shopping flow where applicable.

### **Thu, Feb 19, 2026 — Recipes: Discovery & Navigation**
**Topics**
- Reviewed recipes screen responsibilities: browse/search, view details, and connect to planning actions.
- Ensured recipe navigation does not break back behavior (web + mobile).
- Discussed how to present recipe information clearly and consistently.

**Decisions**
- Keep recipes UX focused on discovery + selection with reliable navigation, avoiding overly complex editing flows.

**Action Items**
- Both: run navigation regression checks across recipes → meal plan → back.

---

## Week of Feb 23, 2026

### **Tue, Feb 24, 2026 — Shopping: List Management**
**Topics**
- Confirmed shopping list interactions: add item, mark complete, remove item, revisit and persist.
- Discussed the “cart” concept in final build and clarified it should not be a separate, fragile workflow.
- Reviewed UI feedback: toasts, disabled states, empty states.

**Decisions**
- Shopping is treated as the central “procurement list” flow for the final demo.

**Action Items**
- Sam: verify shopping list persistence and edge cases (empty/whitespace input).
- Randy: improve list item interaction affordances for touch devices.

### **Thu, Feb 26, 2026 — Pantry: Inventory & Expiring Items**
**Topics**
- Reviewed pantry screen goals: maintain inventory awareness and support “expiring soon” surfacing.
- Confirmed expected item actions and list behavior.
- Ensured pantry ties into home dashboard highlights (expiring items section).

**Decisions**
- Pantry should prioritize clarity (what do we have, what’s expiring) over dense data entry.

**Action Items**
- Both: confirm pantry screens and home “expiring items” widget are consistent and stable.

---

## Week of Mar 2, 2026

### **Tue, Mar 3, 2026 — Household Screen & Collaboration Readiness**
**Topics**
- Reviewed household screen purpose and minimum “Expo demo” behavior: view household info/members and navigate reliably.
- Discussed collaboration messaging for presentation (what’s implemented vs planned).
- Confirmed the profile → household navigation path.

**Decisions**
- Keep household features minimal but polished; avoid partially implemented flows that confuse users.

**Action Items**
- Sam: validate household data loads with a fresh account and handles “no household” states.
- Randy: refine household UI to match the app’s standard layout and spacing.

### **Thu, Mar 5, 2026 — Store Finder Screen**
**Topics**
- Reviewed store finder purpose and expected behavior for demo (search + results rendering).
- Confirmed handling of “no results” states.
- Ensured navigation is consistent with other secondary screens.

**Decisions**
- Store finder is included as a supporting feature; keep it stable and straightforward.

**Action Items**
- Both: sanity test store finder on web and mobile for responsiveness and empty results.

---

## Week of Mar 9, 2026

### **Tue, Mar 10, 2026 — Cross-Platform UX Pass (Web + Mobile)**
**Topics**
- Ran a full navigation sweep through main tabs and secondary screens.
- Logged UI issues unique to web (spacing, min width, scroll behavior) and mobile (safe area, tab bar spacing).
- Reviewed loading spinners/skeletons and error states for consistency.

**Decisions**
- Prioritize fixing cross-platform visual inconsistencies before adding any new features.

**Action Items**
- Randy: address top-priority layout issues and navigation rough edges.
- Sam: compile a bug list and verify fixes as they land.

### **Thu, Mar 12, 2026 — Error Handling & Reliability**
**Topics**
- Reviewed common failure modes: network errors, invalid sessions, empty data for new users.
- Ensured screens show appropriate fallback UI (empty states, retry affordances).
- Confirmed no screen “dead-ends” during demo flow.

**Decisions**
- A “graceful failure” is better than a broken workflow; error states must be user-readable.

**Action Items**
- Both: run a demo rehearsal under poor network conditions (where possible) and confirm recovery paths.

---

## Week of Mar 16, 2026

### **Tue, Mar 17, 2026 — Demo Flow Rehearsal**
**Topics**
- Walked through the planned Expo demo script from landing → auth → home → meal plan → shopping/pantry → insights → profile/preferences.
- Verified the story: “plan meals, stay aware of pantry, and shop intentionally.”
- Identified any screens that needed better headings/subtitles for clarity.

**Decisions**
- The demo should highlight the integrated workflow and show at least one “save” action (preferences or list item).

**Action Items**
- Sam: prepare screenshot checklist for user docs.
- Randy: polish any remaining navigation labels and page headers for consistency.

### **Thu, Mar 19, 2026 — Performance & Interaction Polish**
**Topics**
- Reviewed perceived performance (initial loads, scrolling smoothness, animation feel).
- Adjusted motion usage to avoid distracting or heavy animations on lower-end devices.
- Ensured list interactions remain responsive and predictable.
- Confirmed **Expo poster printing deadline** and submitted a print-ready draft for production.

**Decisions**
- Keep animations subtle and purposeful; do not compromise usability.

**Action Items**
- Both: final pass on “feel” issues (tap targets, hover states on web, scroll spacing).
- Both: incorporate any last poster edits immediately after print submission (for final assembled version later).

---

## Week of Mar 23, 2026

### **Tue, Mar 24, 2026 — Repository Polish & Demo Readiness**
**Topics**
- Reviewed repo presentation requirements: clean structure and clear README.
- Verified no sensitive tokens or secrets are committed.

**Decisions**
- Treat the repo as the final deliverable: it must be professional and easy to navigate.

**Action Items**
- Sam: collect and organize demo assets (screenshots, quick links) for Expo use; keep course deliverables aligned with the final demo.
- Randy: final sweep for UI inconsistencies and cleanup items.

### **Thu, Mar 26, 2026 — Bug Fix Session**
**Topics**
- Addressed remaining UI bugs found during rehearsal: navigation edge cases, missing empty-state copy, minor spacing issues.
- Verified sign-out and sign-in transitions do not leave stale UI state.

**Decisions**
- Freeze scope after this week except for bug fixes and presentation polish.

**Action Items**
- Both: run full regression checklist before end of March.

---

## Week of Mar 30, 2026

### **Tue, Mar 31, 2026 — Final QA Checklist**
**Topics**
- Re-ran key flows: auth, preferences save, shopping add/complete/remove, pantry updates, meal plan edits, insights load.
- Confirmed behavior on web and at least one mobile target.
- Verified that the demo path is resilient and understandable.

**Decisions**
- Any remaining work must be “low risk, high value” and avoid destabilizing core flows.

**Action Items**
- Sam: mount poster and prepare demo flow.
- Randy: implement any last high-impact UI polish changes.

### **Thu, Apr 2, 2026 — Expo Prep & Presentation Alignment**
**Topics**
- Assembled the Expo poster content and finalized the layout (final version completed in early April).
- Confirmed slide deck readiness.
- Practiced demo timing and transitions.
- Verified that the app’s look and feel aligns with the narrative used in the poster/presentation.

**Decisions**
- Lock the final demo build and avoid last-minute feature changes.

**Action Items**
- Both: final rehearsal before Expo; ensure environment is ready (devices charged, links prepared).

---

## Week of Apr 6, 2026

### **Tue, Apr 7, 2026 — Expo Day / Final Freeze**
**Topics**
- Final pre-Expo check of the demo flow.
- Verified that the repository is presentable and demo assets are organized.
- Confirmed backup plan: web demo as primary, mobile demo as secondary (or vice versa, based on reliability).

**Decisions**
- Final build considered complete for Expo; post-Expo work restricted to minor cleanup only.

**Action Items**
- N/A (Expo completed)

