# Cognitive Sanctuary — Screen TODO

> Audited against all `code.html` files, `DESIGN.md`, and `database.md`.
> Legend: `[x]` done · `[ ]` missing · `[~]` partial/UI-only

---

## Project Overview
Educational AI platform with Auth0 Token Vault, role-based screens for students, teachers, and admins.
Design system: Manrope + Inter, Material Symbols, Tailwind, glassmorphism, no-border tonal layering.

---

## 1. Student Screens

### 1.1 Student Dashboard (`student_dashboard`)
- [x] Page layout with sidebar + top nav
- [x] Welcome hero with user name + AI search bar
- [x] Learning progress bars (Math, Science, English)
- [x] Recent sessions cards (resume links)
- [x] Quick tools section (Math Solver, Writing, Science)
- [x] Secure Vault teaser widget
- [x] Upcoming deadlines widget
- [x] Responsive layout (md breakpoint sidebar)
- [ ] Stats cards row — total sessions, streak, accuracy (from `sessions` table)
- [ ] Loading skeleton states for all sections
- [ ] Mobile bottom navigation bar
- [ ] Connect progress bars to `user_progress` API
- [ ] Connect recent sessions to `sessions` API
- [ ] Connect deadlines to `user_assignments` API
- [ ] Notification badge on bell icon

### 1.2 Learning History (`learning_history_student`)
- [x] Page layout with sidebar + top nav
- [x] Page header with title
- [x] Search bar (text input)
- [x] Subject filter button
- [x] Date filter button
- [x] Session history list (article cards)
- [x] Session card: title, date, description, tags, accuracy badge
- [x] "Review Session" CTA per card
- [x] Secure Vault status banner at bottom
- [x] Mobile bottom navigation bar
- [ ] Status filter (completed / in-progress / archived)
- [ ] Pagination or infinite scroll
- [ ] Export sessions button (CSV/PDF)
- [ ] Empty state when no sessions match filter
- [ ] Loading skeleton state
- [ ] Connect to `sessions` API with filters

### 1.3 Resource Library (`resource_library_student`)
- [x] Page layout with sidebar + top nav
- [x] Page header
- [x] Search bar with label
- [x] Subject filter chips (All, Mathematics, Physics, History)
- [x] Resource grid (3-col bento)
- [x] PDF card with thumbnail, author, file size
- [x] Video card with play button overlay
- [x] Interactive lab card
- [x] Featured hero card (wide, dark)
- [x] Secure access card (vault-locked resource)
- [x] "Request Material" CTA footer
- [x] Floating vault status badge (bottom-right)
- [ ] Bookmark / favorite button on each card
- [ ] Grid / list view toggle
- [ ] Sort options (newest, most accessed, subject)
- [ ] Empty search state
- [ ] Loading skeleton cards
- [ ] Connect to `resources` API
- [ ] Connect bookmark to `resource_tag_mappings` or user favorites

### 1.4 Help & Support Center (`help_support_center_student`)
- [x] Page layout (full-width, no sidebar)
- [x] Hero section with headline + CTA buttons
- [x] AI Ethics & Guidelines bento card
- [x] Secure Token Vault info card
- [x] "Master the Art of Prompting" guide with steps + example
- [x] FAQ grid (3 cards)
- [x] "Still have questions?" dark CTA section with live chat button
- [x] Footer
- [ ] FAQ search bar (search within FAQs)
- [ ] Expandable/accordion FAQ items
- [ ] Contact / ticket submission form
- [ ] Ticket history list (past support requests)
- [ ] Category navigation sidebar or tabs
- [ ] Empty state for no search results

### 1.5 Profile Settings (`profile_settings`)
- [x] Page layout with sidebar + top nav
- [x] Profile information card (avatar, name, institution, email)
- [x] Avatar upload button
- [x] Edit profile button
- [x] Subscription / Pro plan card
- [x] Auth0 session management panel (active sessions, revoke)
- [x] Account security (change password, MFA)
- [x] Preferences section (appearance, notifications, language)
- [x] Danger zone (deactivate account)
- [x] Mobile bottom navigation bar
- [ ] Tab navigation (Profile / Account / Notifications / Privacy)
- [ ] Inline form validation (required fields, email format)
- [ ] Save / cancel action buttons
- [ ] Success toast / feedback on save
- [ ] Connect avatar upload to storage API
- [ ] Connect notification toggles to user preferences API

### 1.6 Session Review Deep Dive (`session_review_deep_dive`)
- [x] Page layout with sidebar + right sidebar
- [x] Breadcrumb navigation (History > Session Review)
- [x] Session header (title, date, subject badge)
- [x] Print + Export PDF buttons
- [x] Chat transcript (user bubbles + AI response bubbles)
- [x] AI accent bar on responses (left border)
- [x] Math formula rendering (italic serif)
- [x] Calculation block card
- [x] Suggested follow-up chips ("Explain as if I'm 5")
- [x] Key Concepts Mastered sidebar card
- [x] Progress highlight bar in sidebar
- [x] Follow-up Resources sidebar card
- [x] Secure Vault Protected sidebar card
- [x] Mobile bottom navigation bar
- [ ] Session metrics dashboard (accuracy %, tokens used, duration)
- [ ] Performance chart (score over time within session)
- [ ] Time-spent analytics per question
- [ ] AI insights summary section
- [ ] Share session button (generate link)
- [ ] Connect to `sessions` + `session_messages` API

### 1.7 AI Agent Interaction (`ai_agent_interaction_screen`)
- [x] Page layout with conversation sidebar + chat area
- [x] Top bar with AI avatar, name, Auth0 badge
- [x] Save Solution + Share buttons
- [x] Recent sessions list in sidebar
- [x] New Session button
- [x] User message bubble (primary color)
- [x] AI response bubble with left accent bar
- [x] Code block formatting in AI response
- [x] Suggested prompt chips (Solve for x, Check answer, Similar)
- [x] Message input textarea (auto-resize)
- [x] Attachment, image, mic buttons in input bar
- [x] Send button with gradient
- [x] Privacy footer note
- [ ] Typing indicator (animated dots while AI responds)
- [ ] Streaming response rendering (token-by-token)
- [ ] Conversation title / rename session
- [ ] Delete / archive session from sidebar
- [ ] File upload handler (attachment button wired)
- [ ] Image input handler (image button wired)
- [ ] Voice input handler (mic button wired)
- [ ] Connect to `session_messages` API (POST + GET)
- [ ] Handle `token_usage` display per session


---

## 2. Teacher Screens

### 2.1 Teacher Admin Panel (`teacher_admin_panel`)
- [x] Page layout with sidebar + main content
- [x] Page header with title + Export Data + New Session buttons
- [x] Student Engagement Trends bar chart (week/month toggle)
- [x] Secure Vault widget (API toggles: Wolfram, Khan, Pythagoras)
- [x] User Management table (student roster with engagement bars)
- [x] Struggle Area Analysis cards (High/Medium friction)
- [x] Suggested Supplemental Materials list
- [x] Footer
- [ ] Class overview stat cards (total students, active sessions, avg score)
- [ ] Quick stats widgets (sessions today, new students, alerts)
- [ ] Recent activity feed (latest student actions)
- [ ] Upcoming sessions calendar widget
- [ ] Mobile bottom navigation bar
- [ ] Connect roster table to `users` API (role=student)
- [ ] Connect engagement chart to `engagement_metrics` API
- [ ] Connect struggle areas to `user_progress` aggregation

### 2.2 Student Progress Deep Dive (`student_progress_deep_dive_teacher`)
- [x] Page layout with sidebar + top nav
- [x] Breadcrumb (Grade > Student name)
- [x] Page header with student name + vault status badge
- [x] Cognitive Growth Curve chart (bar + SVG trend line)
- [x] Subject Mastery progress bars (4 subjects)
- [x] Growth Recommendation card
- [x] Cognitive Frictions panel (struggle areas list)
- [x] "View AI Remediation Plan" button
- [x] Vault Interaction Logs list (session cards with status badges)
- [x] AI Mentor Sentiment section (quote + photo + grade badge)
- [x] Download PDF Full Report button
- [x] Compare with Cohort button
- [ ] Goal setting section (set/edit learning goals per student)
- [ ] Notes / comments section (teacher annotations)
- [ ] Cohort comparison chart (student vs class average)
- [ ] Connect to `user_progress` + `sessions` API by student ID
- [ ] Connect PDF export to report generation endpoint

### 2.3 Resource Management (`resource_management_teacher`)
- [x] Page layout with sidebar + top nav
- [x] Page header + "All Systems Secure" badge
- [x] External API Nodes list (Wolfram, Khan, Python — with toggles)
- [x] Inject Supplementary Materials form (URL + subject tag + submit)
- [x] Resource Allocation widget (token % remaining + status list)
- [x] Secure Token Vault display (masked keys + manage button)
- [x] Knowledge Coverage preview card
- [x] Active Supplementary Materials horizontal scroll list
- [x] Resource cards with delete button, subject tag, date added
- [x] Mobile bottom navigation bar
- [ ] Folder / category management for resources
- [ ] Bulk actions (select multiple, delete, move to folder)
- [ ] Sharing permissions UI (who can see each resource)
- [ ] Usage analytics per resource (access count from `resources.access_count`)
- [ ] Empty state when no materials added
- [ ] Connect API toggles to `api_endpoints` table
- [ ] Connect material injection to `resources` POST API

### 2.4 Custom AI Prompt Builder (`custom_ai_prompt_builder_teacher`)
- [x] Page layout with sidebar + top nav
- [x] Page header with "Persona Architect" badge + vault secured badge
- [x] System Instructions textarea (with token count)
- [x] "View Templates" button
- [x] Dynamic Variables grid (student_name, subject_difficulty, curriculum_id)
- [x] "Create Variable" button
- [x] Test Lab panel (student input simulation textarea)
- [x] "Simulate Interaction" button
- [x] AI persona response output area
- [x] Tone Score + Safety Compliance metrics
- [x] Encrypted System Prompt Vault section + "Manage Keys" button
- [x] Footer
- [ ] Prompt template selector / library sidebar
- [ ] Version history (save/restore previous prompt versions)
- [ ] Prompt library (browse saved prompts)
- [ ] Validation (required fields, max token warning)
- [ ] Save prompt button (persist to vault)
- [ ] Connect simulate to AI inference endpoint
- [ ] Connect save to `vault_configurations` or prompt storage API


---

## 3. Admin Screens

### 3.1 User Management (`user_management_admin`)
- [x] Page layout with sidebar + top nav
- [x] Page header with title + description
- [x] Total Users + Active Now stat cards
- [x] Search input (filter by name/email/role)
- [x] Role filter dropdown (All / Students / Teachers)
- [x] Export Data button
- [x] Invite User button
- [x] Users data table (name, role badge, last active + IP, status dot)
- [x] Edit + Permissions action buttons (hover reveal)
- [x] Suspended user row styling (error tint)
- [x] Pagination (Previous / Next)
- [x] System Insights AI panel
- [x] Auth0 Vault health widget (98% security score)
- [ ] Edit user drawer / modal (full profile edit)
- [ ] Create user modal (invite flow with role assignment)
- [ ] Bulk actions (select rows, bulk suspend/delete/export)
- [ ] Admin role filter (add Admin option)
- [ ] Connect table to `users` API with pagination
- [ ] Connect invite to Auth0 user creation API
- [ ] Connect status toggle to `users.status` PATCH API

### 3.2 Security Activity Logs (`security_activity_logs_admin`)
- [x] Page layout with sidebar + top nav + right vault panel
- [x] Page header with title
- [x] Date range toggle (Today / 7 Days / 30 Days)
- [x] Custom Range button
- [x] Export CSV button
- [x] Security stats cards (Token Rotations, Alert Flags, New Users, Active IPs)
- [x] Activity Logs table (timestamp, user, action, status, IP, view button)
- [x] Success / Alert row styling (teal vs red)
- [x] Success rate + Alert rate summary badges
- [x] Pagination (numbered pages)
- [x] Vault Status sticky sidebar (last rotation, security score, Auth0 sync)
- [x] Mobile bottom navigation bar
- [ ] Event type filter (login, token rotation, resource add, config change…)
- [ ] User filter (search by user email)
- [ ] Severity filter (info / warning / error / critical)
- [ ] Log detail view modal (expand full `details` JSONB)
- [ ] Real-time log streaming indicator (live badge)
- [ ] Connect to `security_audit_logs` API with filters + pagination

### 3.3 Token Vault Configuration (`token_vault_configuration_admin`)
- [x] Page layout with sidebar + top nav
- [x] Page header + Token Rotation button
- [x] Auth0 Secure Gateway panel (domain, client ID, JWKS public key)
- [x] Copy-to-clipboard on credential fields
- [x] Vault Health status panel (last rotation, encryption type, active keys)
- [x] Encrypted API Gateways list (WolframAlpha, OpenAI, VectorDB)
- [x] Per-endpoint settings button
- [x] Vault Audit Log timeline (3 recent events)
- [x] Mobile bottom navigation bar
- [ ] Add new endpoint form (provider name, URL, API key)
- [ ] Delete / disable endpoint action
- [ ] Environment selector (dev / staging / production)
- [ ] Auto-rotation schedule configuration (edit `auto_rotate_days`)
- [ ] Connect to `vault_configurations` API (GET/PATCH)
- [ ] Connect endpoints list to `api_endpoints` API
- [ ] Connect rotation button to key rotation endpoint

### 3.4 Institutional Analytics Macro (`institutional_analytics_macro`)
- [x] Page layout with sidebar + top nav
- [x] Average Academic Growth radar chart (5-axis polygon SVG)
- [x] Student Engagement heatmap (24h × 7d grid)
- [x] Total Token Consumption widget (8.4M, 84% capacity bar)
- [x] Top Active Subjects list (3 subjects with progress bars)
- [x] AI Insight card
- [x] Secure Vault card
- [x] Token Efficiency card
- [x] Footer
- [ ] KPI cards row (total students, sessions this week, avg accuracy, retention %)
- [ ] User growth graph (line chart over time)
- [ ] Retention analysis section
- [ ] Export Reports button (PDF/CSV)
- [ ] Date range / time period selector (week / month / semester)
- [ ] Connect radar chart to `user_progress` aggregation API
- [ ] Connect heatmap to `engagement_metrics` API
- [ ] Connect token consumption to `sessions.token_usage` aggregation

### 3.5 API Node Details (`api_node_details_admin`)
- [x] Page layout with sidebar + top nav
- [x] Node header (name, status dot, latency)
- [x] Node selector tabs (OpenAI / Wolfram Alpha / Claude 3)
- [x] Performance metric cards (Avg Latency, Token Usage, Success Rate)
- [x] Model Config panel (Temperature, Top P, Frequency Penalty sliders)
- [x] Safe Mode + Stream Responses toggles
- [x] Update Configuration button
- [x] Latency & Load Analytics bar chart (24h)
- [x] Time range selector (24h / 7d)
- [x] Secure Token Vault section (masked API key, copy, rotate)
- [ ] Error rate chart (separate from latency)
- [ ] Uptime statistics (% uptime over 30d)
- [ ] Alert configuration (set threshold for latency/error alerts)
- [ ] Add new API node button
- [ ] Connect metric cards to `api_endpoints` health API
- [ ] Connect sliders to model config PATCH API
- [ ] Connect key rotation to vault rotation endpoint


---

## 4. Auth & Landing Screens

### 4.1 Branded Login (`branded_login`)
- [x] Asymmetric layout (left branding panel + right form)
- [x] Left panel: gradient, grid pattern, brand logo, value props, social proof avatars
- [x] Mobile logo fallback
- [x] "Welcome back" heading + subtitle
- [x] Google + GitHub social login buttons
- [x] "Or continue with" divider
- [x] Email input with icon
- [x] Password input with show/hide toggle
- [x] Forgot password link
- [x] Sign In gradient button
- [x] "Create an account" link
- [x] Auth0 security assurance badge
- [x] Background decorative blurs
- [ ] Remember me checkbox
- [ ] MFA / 2FA prompt step (after password)
- [ ] Error state UI (wrong credentials, account locked)
- [ ] Loading state on submit button
- [ ] Connect form to Auth0 authentication API

### 4.2 Branded Register (`branded_register`)
- [x] Asymmetric layout (left dark grid panel + right form)
- [x] Left panel: brand logo, headline, security badges (Auth0, GDPR), illustration
- [x] "Begin your journey" heading
- [x] Google + GitHub social sign-up buttons
- [x] "or email registration" divider
- [x] Full Name input
- [x] Email input
- [x] Password + Confirm Password inputs (2-col grid)
- [x] Password strength indicator (4-segment bar)
- [x] Create Account gradient button
- [x] "Sign in" link
- [x] Sanctuary Shield Active footer note
- [ ] Role selector (Student / Teacher) — required for `users.role`
- [ ] Terms & Conditions checkbox
- [ ] Institution / school name field (maps to `institutions`)
- [ ] Error state UI (email taken, password mismatch)
- [ ] Loading state on submit
- [ ] Connect to Auth0 sign-up + `users` POST API

### 4.3 Landing Page (`landing_page_ai_helper_agent`)
- [x] Top navigation bar (sticky, glassmorphism)
- [x] Hero section (headline, subtitle, 2 CTA buttons, hero image)
- [x] "Secure AI Learning" badge
- [x] "How It Works" bento grid (Chat AI, Step-by-Step, External Knowledge, Focused Env)
- [x] Security First section (Auth0 Token Vault explanation + glass panel demo)
- [x] Student & Teacher role cards
- [x] Final CTA section (gradient card with 2 buttons)
- [x] Footer with links
- [ ] Testimonials section (student/teacher quotes)
- [ ] Pricing section (Free / Standard / Premium tiers)
- [ ] FAQ accordion section
- [ ] Social proof / stats bar (e.g. "2,000+ students, 98% satisfaction")
- [ ] Navigation links wired to actual routes
- [ ] Mobile hamburger menu

---

## 5. Security Screen

### 5.1 Cognition Shield (`cognition_shield`)
> ⚠️ No `code.html` exists yet — full build required. Design spec in `DESIGN.md`.

- [ ] Create page layout (sidebar + main canvas)
- [ ] Security dashboard header with overall threat level
- [ ] Threat overview cards (active threats, blocked attempts, risk score)
- [ ] Security score widget (circular gauge, 0–100)
- [ ] Incidents table (timestamp, type, severity, affected user, status)
- [ ] Severity indicators (info / warning / error / critical — use design system colors)
- [ ] Firewall status panel (rules active, last updated)
- [ ] Suspicious activity alerts feed (real-time list)
- [ ] Security settings panel (toggle rules, whitelist IPs)
- [ ] Export incidents button
- [ ] Connect to `security_audit_logs` API (severity filter)
- [ ] Connect to `active_tokens` API (revocation controls)


---

## 6. Cross-Cutting / Shared Tasks

### Design System Consistency
- [ ] Audit all screens for 1px solid borders — replace with tonal shifts per `DESIGN.md` "No-Line Rule"
- [ ] Ensure all primary CTAs use `linear-gradient(135deg, #2b3896, #4551af)`
- [ ] Verify `hover:scale-[1.02]` kinetic effect on all buttons
- [ ] Confirm `backdrop-filter: blur(12px)` on all floating/glass elements
- [ ] Replace any `#000000` text with `on-surface` (#191c1e)
- [ ] Ensure all cards use `xl` (1.5rem) border-radius minimum

### Navigation & Routing
- [ ] Wire all sidebar nav links to correct screen routes
- [ ] Wire all top nav links to correct screen routes
- [ ] Add active state highlighting to current route in sidebar
- [ ] Implement mobile hamburger menu on screens missing it

### Auth & Session
- [ ] Implement Auth0 SDK integration (login, logout, token refresh)
- [ ] Add protected route guards (redirect unauthenticated users to login)
- [ ] Role-based route guards (student/teacher/admin access control)
- [ ] Persist Auth0 session tokens in `active_tokens` table

### API Integration
- [ ] Define base API client with Auth0 JWT header injection
- [ ] Implement error boundary / error state components
- [ ] Implement global loading state / spinner
- [ ] Add API response caching strategy

### Accessibility
- [ ] Add `aria-label` to all icon-only buttons
- [ ] Ensure all form inputs have associated `<label>` elements
- [ ] Add keyboard navigation support to custom dropdowns and modals
- [ ] Verify color contrast ratios on all text/background combinations

---

## 7. Screen Status Summary

| Screen | Has Code | Priority | Key Missing Items |
|--------|----------|----------|-------------------|
| student_dashboard | ✅ | High | Stats cards, loading states, API |
| learning_history_student | ✅ | High | Pagination, export, empty state, API |
| resource_library_student | ✅ | High | Bookmark, sort, empty state, API |
| help_support_center_student | ✅ | Medium | FAQ search, accordion, ticket form |
| profile_settings | ✅ | Medium | Tab nav, form validation, save action |
| session_review_deep_dive | ✅ | High | Metrics dashboard, charts, API |
| ai_agent_interaction_screen | ✅ | High | Typing indicator, streaming, file handlers |
| teacher_admin_panel | ✅ | Medium | Stats cards, activity feed, calendar |
| student_progress_deep_dive_teacher | ✅ | Medium | Goal setting, notes, cohort compare |
| resource_management_teacher | ✅ | Medium | Folders, bulk actions, permissions |
| custom_ai_prompt_builder_teacher | ✅ | Medium | Template library, version history, save |
| user_management_admin | ✅ | Medium | Edit drawer, bulk actions, create modal |
| security_activity_logs_admin | ✅ | Medium | Event/user filters, detail modal |
| token_vault_configuration_admin | ✅ | Low | Add endpoint form, env selector |
| institutional_analytics_macro | ✅ | Low | KPI cards, export, date selector |
| api_node_details_admin | ✅ | Low | Error rate chart, uptime, alerts |
| branded_login | ✅ | High | Remember me, MFA step, error states |
| branded_register | ✅ | High | Role selector, terms checkbox, errors |
| landing_page_ai_helper_agent | ✅ | High | Testimonials, pricing, FAQ, stats bar |
| cognition_shield | ❌ | Medium | **Full build required — no code yet** |

---

## 8. Quick Stats

- **Total Screens:** 20
- **Screens with code:** 19 (95%)
- **Screens without code:** 1 (`cognition_shield`)
- **Student Screens:** 7
- **Teacher Screens:** 4
- **Admin Screens:** 5
- **Auth / Landing Screens:** 3
- **Security Screens:** 1
- **Shared / Cross-cutting tasks:** ~25
