# BUILD_CHECKLIST.md

## Mandatory Execution Checklist

This checklist must be followed by the autonomous agent.

Do not skip sections.
Do not mark items complete unless they are truly complete.

---

## Phase 0 — Repository Control

- [ ] Confirm repository is operating on `main`
- [ ] Confirm no branch workflow is being used
- [ ] Read `README.md`
- [ ] Read `AGENTS.md`
- [ ] Read `docs/SYSTEM_BLUEPRINT.md`
- [ ] Read `docs/ACCEPTANCE_CRITERIA.md`
- [ ] Inspect current repository structure
- [ ] Inspect current application files
- [ ] Identify missing or incomplete foundational files

### Phase 0 completion rule
Repository context is understood and work remains direct-to-main only.

---

## Phase 1 — Platform Inspection

- [ ] Inspect current Supabase tables
- [ ] Inspect current Supabase auth-related structures
- [ ] Inspect current Supabase RLS / policies
- [ ] Inspect current storage buckets if relevant
- [ ] Inspect current edge functions if any
- [ ] Inspect current Vercel project configuration
- [ ] Inspect current Vercel deployment state
- [ ] Inspect whether required environment configuration is present in Vercel

### Phase 1 completion rule
Current platform reality is known before changes are made.

---

## Phase 2 — Foundation Setup

- [ ] Create or correct Next.js application structure
- [ ] Configure strict TypeScript
- [ ] Configure styling foundation
- [ ] Create app shell/layout
- [ ] Create auth route structure
- [ ] Create protected route structure
- [ ] Create shared utilities and service modules
- [ ] Ensure repository remains runnable

### Required commit
After completing this phase, commit directly on `main` and push to `origin/main`.

---

## Phase 3 — Database and Security

- [ ] Create or update required core tables
- [ ] Create indexes where necessary
- [ ] Create migration files in repository
- [ ] Create profile/role support if needed
- [ ] Enable Row Level Security where applicable
- [ ] Create secure policies
- [ ] Validate that user-facing data access is not left exposed
- [ ] Create audit-log structures
- [ ] Ensure schema and repository migrations match

### Required commit
After completing this phase, commit directly on `main` and push to `origin/main`.

---

## Phase 4 — Authentication

- [ ] Implement login flow
- [ ] Implement logout flow
- [ ] Implement session-aware protection
- [ ] Implement role-aware authorization
- [ ] Restrict admin-only pages properly
- [ ] Verify unauthorized users cannot access protected admin actions

### Required commit
After completing this phase, commit directly on `main` and push to `origin/main`.

---

## Phase 5 — Employee Import Pipeline

- [ ] Build upload UI
- [ ] Accept Muqeem file as downloaded
- [ ] Do not require header renaming
- [ ] Store uploaded file for audit
- [ ] Parse file safely
- [ ] Validate required identifier columns
- [ ] Match by Iqama number / resident ID
- [ ] Insert new employees
- [ ] Update existing employees
- [ ] Create import summary
- [ ] Create row-level result logging
- [ ] Create change-log behavior
- [ ] Ensure repeated uploads are safe

### Required commit
After completing this phase, commit directly on `main` and push to `origin/main`.

---

## Phase 6 — Dashboard and Employees

- [ ] Build dashboard screen
- [ ] Show total employee counts
- [ ] Show expiring-soon summaries
- [ ] Show expired summaries
- [ ] Show nationality views
- [ ] Show recent imports
- [ ] Show recent automation runs
- [ ] Build employee list screen
- [ ] Build employee search
- [ ] Build employee filters
- [ ] Build employee sorting
- [ ] Build employee detail screen
- [ ] Show employee status and history clearly

### Required commit
After completing this phase, commit directly on `main` and push to `origin/main`.

---

## Phase 7 — Automation Builder

- [ ] Build automation rules list
- [ ] Build create/edit rule form
- [ ] Support Email channel
- [ ] Support WhatsApp channel
- [ ] Support multiple recipients
- [ ] Support Iqama expiry trigger
- [ ] Support passport expiry trigger
- [ ] Support threshold configuration
- [ ] Support scheduling configuration
- [ ] Support enable/disable
- [ ] Support duplicate rule
- [ ] Support match preview
- [ ] Support run history display

### Required commit
After completing this phase, commit directly on `main` and push to `origin/main`.

---

## Phase 8 — Manual Run Operations

- [ ] Build one-time manual run action
- [ ] Evaluate rule against current data
- [ ] Show preview counts
- [ ] Execute run-now flow
- [ ] Log sent / failed / matched counts
- [ ] Protect against careless duplicate sends

### Required commit
After completing this phase, commit directly on `main` and push to `origin/main`.

---

## Phase 9 — Notifications and Edge Functions

- [ ] Build secure Email dispatch path
- [ ] Build secure WhatsApp dispatch path
- [ ] Create required edge/server functions
- [ ] Keep secret-dependent logic server-side
- [ ] Build test/send support where useful
- [ ] Save delivery logs
- [ ] Save failure logs

### Required commit
After completing this phase, commit directly on `main` and push to `origin/main`.

---

## Phase 10 — Settings and Hardening

- [ ] Build settings screens
- [ ] Build integration settings support
- [ ] Build template management support
- [ ] Build system health visibility
- [ ] Validate error states
- [ ] Validate loading states
- [ ] Validate empty states
- [ ] Check security boundaries again
- [ ] Update documentation where needed

### Required commit
After completing this phase, commit directly on `main` and push to `origin/main`.

---

## Phase 11 — Vercel Deployment Verification

- [ ] Ensure required environment configuration exists in Vercel
- [ ] Push latest code to `origin/main`
- [ ] Go to Vercel deployment/build page
- [ ] Inspect current build result
- [ ] If failed, inspect logs
- [ ] Fix failure in repository
- [ ] Commit directly on `main`
- [ ] Push directly to `origin/main`
- [ ] Re-check Vercel
- [ ] Repeat until production deployment is healthy

### Phase 11 completion rule
The deployment is confirmed healthy from Vercel, not merely assumed because a push occurred.

---

## Phase 12 — Final Validation

- [ ] Confirm import flow works
- [ ] Confirm employee upsert works by Iqama / resident ID
- [ ] Confirm dashboard reflects latest data
- [ ] Confirm employee filters and sorting work
- [ ] Confirm automation rules can be created
- [ ] Confirm one-time manual execution works
- [ ] Confirm Email flow works
- [ ] Confirm WhatsApp path is implemented
- [ ] Confirm logs are visible
- [ ] Confirm security protections are in place
- [ ] Confirm docs are aligned with implementation
- [ ] Confirm code is committed on `main`
- [ ] Confirm code is pushed to `origin/main`
- [ ] Confirm Vercel production deployment is healthy

---

## Final Reporting Checklist

The final status report must include:

- implemented modules
- database changes
- security changes
- edge/server functions added
- deployment status
- latest commit status
- confirmation of push to `origin/main`
- Vercel verification result
- production URL status
- remaining risks, if any

Completion is not valid until all required checklist items are actually satisfied.
