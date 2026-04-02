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
- [ ] Page layout with sidebar + top nav
- [ ] Welcome hero with user name + AI search bar
- [ ] Learning progress bars (Math, Science, English)
- [ ] Recent sessions cards (resume links)
- [ ] Quick tools section (Math Solver, Writing, Science)
- [ ] Secure Vault teaser widget
- [ ] Upcoming deadlines widget
- [ ] Responsive layout (md breakpoint sidebar)
- [ ] Stats cards row — total sessions, streak, accuracy (from `sessions` table)
- [ ] Loading skeleton states for all sections
- [ ] Mobile bottom navigation bar
- [ ] Connect progress bars to `user_progress` API
- [ ] Connect recent sessions to `sessions` API
- [ ] Connect deadlines to `user_assignments` API
- [ ] Notification badge on bell icon

### 1.2 Learning History (`learning_history_student`)
- [ ] Page layout with sidebar + top nav
- [ ] Page header with title
- [ ] Search bar (text input)
- [ ] Subject filter button
- [ ] Date filter button
- [ ] Session history list (article cards)
- [ ] Session card: title, date, description, tags, accuracy badge
- [ ] "Review Session" CTA per card
- [ ] Secure Vault status banner at bottom
- [ ] Mobile bottom navigation bar
- [ ] Status filter (completed / in-progress / archived)
- [ ] Pagination or infinite scroll
- [ ] Export sessions button (CSV/PDF)
- [ ] Empty state when no sessions match filter
- [ ] Loading skeleton state
- [ ] Connect to `sessions` API with filters

### 1.3 Resource Library (`resource_library_student`)
- [ ] Page layout with sidebar + top nav
- [ ] Page header
- [ ] Search bar with label
- [ ] Subject filter chips (All, Mathematics, Physics, History)
- [ ] Resource grid (3-col bento)
- [ ] PDF card with thumbnail, author, file size
- [ ] Video card with play button overlay
- [ ] Interactive lab card
- [ ] Featured hero card (wide, dark)
- [ ] Secure access card (vault-locked resource)
- [ ] "Request Material" CTA footer
- [ ] Floating vault status badge (bottom-right)
- [ ] Bookmark / favorite button on each card
- [ ] Grid / list view toggle
- [ ] Sort options (newest, most accessed, subject)
- [ ] Empty search state
- [ ] Loading skeleton cards
- [ ] Connect to `resources` API
- [ ] Connect bookmark to `resource_tag_mappings` or user favorites

### 1.4 Help & Support Center (`help_support_center_student`)
- [ ] Page layout (full-width, no sidebar)
- [ ] Hero section with headline + CTA buttons
- [ ] AI Ethics & Guidelines bento card
- [ ] Secure Token Vault info card
- [ ] "Master the Art of Prompting" guide with steps + example
- [ ] FAQ grid (3 cards)
- [ ] "Still have questions?" dark CTA section with live chat button
- [ ] Footer
- [ ] FAQ search bar (search within FAQs)
- [ ] Expandable/accordion FAQ items
- [ ] Contact / ticket submission form
- [ ] Ticket history list (past support requests)
- [ ] Category navigation sidebar or tabs
- [ ] Empty state for no search results

### 1.5 Profile Settings (`profile_settings`)
- [ ] Page layout with sidebar + top nav
- [ ] Profile information card (avatar, name, institution, email)
- [ ] Avatar upload button
- [ ] Edit profile button
- [ ] Subscription / Pro plan card
- [ ] Auth0 session management panel (active sessions, revoke)
- [ ] Account security (change password, MFA)
- [ ] Preferences section (appearance, notifications, language)
- [ ] Danger zone (deactivate account)
- [ ] Mobile bottom navigation bar
- [ ] Tab navigation (Profile / Account / Notifications / Privacy)
- [ ] Inline form validation (required fields, email format)
- [ ] Save / cancel action buttons
- [ ] Success toast / feedback on save
- [ ] Connect avatar upload to storage API
- [ ] Connect notification toggles to user preferences API

### 1.6 Session Review Deep Dive (`session_review_deep_dive`)
- [ ] Page layout with sidebar + right sidebar
- [ ] Breadcrumb navigation (History > Session Review)
- [ ] Session header (title, date, subject badge)
- [ ] Print + Export PDF buttons
- [ ] Chat transcript (user bubbles + AI response bubbles)
- [ ] AI accent bar on responses (left border)
- [ ] Math formula rendering (italic serif)
- [ ] Calculation block card
- [ ] Suggested follow-up chips ("Explain as if I'm 5")
- [ ] Key Concepts Mastered sidebar card
- [ ] Progress highlight bar in sidebar
- [ ] Follow-up Resources sidebar card
- [ ] Secure Vault Protected sidebar card
- [ ] Mobile bottom navigation bar
- [ ] Session metrics dashboard (accuracy %, tokens used, duration)
- [ ] Performance chart (score over time within session)
- [ ] Time-spent analytics per question
- [ ] AI insights summary section
- [ ] Share session button (generate link)
- [ ] Connect to `sessions` + `session_messages` API

### 1.7 AI Agent Interaction (`ai_agent_interaction_screen`)
- [ ] Page layout with conversation sidebar + chat area
- [ ] Top bar with AI avatar, name, Auth0 badge
- [ ] Save Solution + Share buttons
- [ ] Recent sessions list in sidebar
- [ ] New Session button
- [ ] User message bubble (primary color)
- [ ] AI response bubble with left accent bar
- [ ] Code block formatting in AI response
- [ ] Suggested prompt chips (Solve for x, Check answer, Similar)
- [ ] Message input textarea (auto-resize)
- [ ] Attachment, image, mic buttons in input bar
- [ ] Send button with gradient
- [ ] Privacy footer note
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
- [ ] Page layout with sidebar + main content
- [ ] Page header with title + Export Data + New Session buttons
- [ ] Student Engagement Trends bar chart (week/month toggle)
- [ ] Secure Vault widget (API toggles: Wolfram, Khan, Pythagoras)
- [ ] User Management table (student roster with engagement bars)
- [ ] Struggle Area Analysis cards (High/Medium friction)
- [ ] Suggested Supplemental Materials list
- [ ] Footer
- [ ] Class overview stat cards (total students, active sessions, avg score)
- [ ] Quick stats widgets (sessions today, new students, alerts)
- [ ] Recent activity feed (latest student actions)
- [ ] Upcoming sessions calendar widget
- [ ] Mobile bottom navigation bar
- [ ] Connect roster table to `users` API (role=student)
- [ ] Connect engagement chart to `engagement_metrics` API
- [ ] Connect struggle areas to `user_progress` aggregation

### 2.2 Student Progress Deep Dive (`student_progress_deep_dive_teacher`)
- [ ] Page layout with sidebar + top nav
- [ ] Breadcrumb (Grade > Student name)
- [ ] Page header with student name + vault status badge
- [ ] Cognitive Growth Curve chart (bar + SVG trend line)
- [ ] Subject Mastery progress bars (4 subjects)
- [ ] Growth Recommendation card
- [ ] Cognitive Frictions panel (struggle areas list)
- [ ] "View AI Remediation Plan" button
- [ ] Vault Interaction Logs list (session cards with status badges)
- [ ] AI Mentor Sentiment section (quote + photo + grade badge)
- [ ] Download PDF Full Report button
- [ ] Compare with Cohort button
- [ ] Goal setting section (set/edit learning goals per student)
- [ ] Notes / comments section (teacher annotations)
- [ ] Cohort comparison chart (student vs class average)
- [ ] Connect to `user_progress` + `sessions` API by student ID
- [ ] Connect PDF export to report generation endpoint

### 2.3 Resource Management (`resource_management_teacher`)
- [ ] Page layout with sidebar + top nav
- [ ] Page header + "All Systems Secure" badge
- [ ] External API Nodes list (Wolfram, Khan, Python — with toggles)
- [ ] Inject Supplementary Materials form (URL + subject tag + submit)
- [ ] Resource Allocation widget (token % remaining + status list)
- [ ] Secure Token Vault display (masked keys + manage button)
- [ ] Knowledge Coverage preview card
- [ ] Active Supplementary Materials horizontal scroll list
- [ ] Resource cards with delete button, subject tag, date added
- [ ] Mobile bottom navigation bar
- [ ] Folder / category management for resources
- [ ] Bulk actions (select multiple, delete, move to folder)
- [ ] Sharing permissions UI (who can see each resource)
- [ ] Usage analytics per resource (access count from `resources.access_count`)
- [ ] Empty state when no materials added
- [ ] Connect API toggles to `api_endpoints` table
- [ ] Connect material injection to `resources` POST API

### 2.4 Custom AI Prompt Builder (`custom_ai_prompt_builder_teacher`)
- [ ] Page layout with sidebar + top nav
- [ ] Page header with "Persona Architect" badge + vault secured badge
- [ ] System Instructions textarea (with token count)
- [ ] "View Templates" button
- [ ] Dynamic Variables grid (student_name, subject_difficulty, curriculum_id)
- [ ] "Create Variable" button
- [ ] Test Lab panel (student input simulation textarea)
- [ ] "Simulate Interaction" button
- [ ] AI persona response output area
- [ ] Tone Score + Safety Compliance metrics
- [ ] Encrypted System Prompt Vault section + "Manage Keys" button
- [ ] Footer
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
- [ ] Page layout with sidebar + top nav
- [ ] Page header with title + description
- [ ] Total Users + Active Now stat cards
- [ ] Search input (filter by name/email/role)
- [ ] Role filter dropdown (All / Students / Teachers)
- [ ] Export Data button
- [ ] Invite User button
- [ ] Users data table (name, role badge, last active + IP, status dot)
- [ ] Edit + Permissions action buttons (hover reveal)
- [ ] Suspended user row styling (error tint)
- [ ] Pagination (Previous / Next)
- [ ] System Insights AI panel
- [ ] Auth0 Vault health widget (98% security score)
- [ ] Edit user drawer / modal (full profile edit)
- [ ] Create user modal (invite flow with role assignment)
- [ ] Bulk actions (select rows, bulk suspend/delete/export)
- [ ] Admin role filter (add Admin option)
- [ ] Connect table to `users` API with pagination
- [ ] Connect invite to Auth0 user creation API
- [ ] Connect status toggle to `users.status` PATCH API

### 3.2 Security Activity Logs (`security_activity_logs_admin`)
- [ ] Page layout with sidebar + top nav + right vault panel
- [ ] Page header with title
- [ ] Date range toggle (Today / 7 Days / 30 Days)
- [ ] Custom Range button
- [ ] Export CSV button
- [ ] Security stats cards (Token Rotations, Alert Flags, New Users, Active IPs)
- [ ] Activity Logs table (timestamp, user, action, status, IP, view button)
- [ ] Success / Alert row styling (teal vs red)
- [ ] Success rate + Alert rate summary badges
- [ ] Pagination (numbered pages)
- [ ] Vault Status sticky sidebar (last rotation, security score, Auth0 sync)
- [ ] Mobile bottom navigation bar
- [ ] Event type filter (login, token rotation, resource add, config change…)
- [ ] User filter (search by user email)
- [ ] Severity filter (info / warning / error / critical)
- [ ] Log detail view modal (expand full `details` JSONB)
- [ ] Real-time log streaming indicator (live badge)
- [ ] Connect to `security_audit_logs` API with filters + pagination

### 3.3 Token Vault Configuration (`token_vault_configuration_admin`)
- [ ] Page layout with sidebar + top nav
- [ ] Page header + Token Rotation button
- [ ] Auth0 Secure Gateway panel (domain, client ID, JWKS public key)
- [ ] Copy-to-clipboard on credential fields
- [ ] Vault Health status panel (last rotation, encryption type, active keys)
- [ ] Encrypted API Gateways list (WolframAlpha, OpenAI, VectorDB)
- [ ] Per-endpoint settings button
- [ ] Vault Audit Log timeline (3 recent events)
- [ ] Mobile bottom navigation bar
- [ ] Add new endpoint form (provider name, URL, API key)
- [ ] Delete / disable endpoint action
- [ ] Environment selector (dev / staging / production)
- [ ] Auto-rotation schedule configuration (edit `auto_rotate_days`)
- [ ] Connect to `vault_configurations` API (GET/PATCH)
- [ ] Connect endpoints list to `api_endpoints` API
- [ ] Connect rotation button to key rotation endpoint

### 3.4 Institutional Analytics Macro (`institutional_analytics_macro`)
- [ ] Page layout with sidebar + top nav
- [ ] Average Academic Growth radar chart (5-axis polygon SVG)
- [ ] Student Engagement heatmap (24h × 7d grid)
- [ ] Total Token Consumption widget (8.4M, 84% capacity bar)
- [ ] Top Active Subjects list (3 subjects with progress bars)
- [ ] AI Insight card
- [ ] Secure Vault card
- [ ] Token Efficiency card
- [ ] Footer
- [ ] KPI cards row (total students, sessions this week, avg accuracy, retention %)
- [ ] User growth graph (line chart over time)
- [ ] Retention analysis section
- [ ] Export Reports button (PDF/CSV)
- [ ] Date range / time period selector (week / month / semester)
- [ ] Connect radar chart to `user_progress` aggregation API
- [ ] Connect heatmap to `engagement_metrics` API
- [ ] Connect token consumption to `sessions.token_usage` aggregation

### 3.5 API Node Details (`api_node_details_admin`)
- [ ] Page layout with sidebar + top nav
- [ ] Node header (name, status dot, latency)
- [ ] Node selector tabs (OpenAI / Wolfram Alpha / Claude 3)
- [ ] Performance metric cards (Avg Latency, Token Usage, Success Rate)
- [ ] Model Config panel (Temperature, Top P, Frequency Penalty sliders)
- [ ] Safe Mode + Stream Responses toggles
- [ ] Update Configuration button
- [ ] Latency & Load Analytics bar chart (24h)
- [ ] Time range selector (24h / 7d)
- [ ] Secure Token Vault section (masked API key, copy, rotate)
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
- [ ] Asymmetric layout (left branding panel + right form)
- [ ] Left panel: gradient, grid pattern, brand logo, value props, social proof avatars
- [ ] Mobile logo fallback
- [ ] "Welcome back" heading + subtitle
- [ ] Google + GitHub social login buttons
- [ ] "Or continue with" divider
- [ ] Email input with icon
- [ ] Password input with show/hide toggle
- [ ] Forgot password link
- [ ] Sign In gradient button
- [ ] "Create an account" link
- [ ] Auth0 security assurance badge
- [ ] Background decorative blurs
- [ ] Remember me checkbox
- [ ] MFA / 2FA prompt step (after password)
- [ ] Error state UI (wrong credentials, account locked)
- [ ] Loading state on submit button
- [ ] Connect form to Auth0 authentication API

### 4.2 Branded Register (`branded_register`)
- [ ] Asymmetric layout (left dark grid panel + right form)
- [ ] Left panel: brand logo, headline, security badges (Auth0, GDPR), illustration
- [ ] "Begin your journey" heading
- [ ] Google + GitHub social sign-up buttons
- [ ] "or email registration" divider
- [ ] Full Name input
- [ ] Email input
- [ ] Password + Confirm Password inputs (2-col grid)
- [ ] Password strength indicator (4-segment bar)
- [ ] Create Account gradient button
- [ ] "Sign in" link
- [ ] Sanctuary Shield Active footer note
- [ ] Role selector (Student / Teacher) — required for `users.role`
- [ ] Terms & Conditions checkbox
- [ ] Institution / school name field (maps to `institutions`)
- [ ] Error state UI (email taken, password mismatch)
- [ ] Loading state on submit
- [ ] Connect to Auth0 sign-up + `users` POST API

### 4.3 Landing Page (`landing_page_ai_helper_agent`)
- [ ] Top navigation bar (sticky, glassmorphism)
- [ ] Hero section (headline, subtitle, 2 CTA buttons, hero image)
- [ ] "Secure AI Learning" badge
- [ ] "How It Works" bento grid (Chat AI, Step-by-Step, External Knowledge, Focused Env)
- [ ] Security First section (Auth0 Token Vault explanation + glass panel demo)
- [ ] Student & Teacher role cards
- [ ] Final CTA section (gradient card with 2 buttons)
- [ ] Footer with links
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
