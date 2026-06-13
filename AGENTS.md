# AGENTS.md

## Authority

This file defines the mandatory execution rules for any autonomous agent working in this repository.

These rules are not suggestions.
These rules are the required operating contract.

If there is any conflict between normal agent habits and this file, follow this file.

---

## Core Mission

Build, secure, deploy, and verify a production-grade Muqeem Employee Compliance & Automation System.

The agent is responsible for complete end-to-end delivery across code, database, platform configuration, deployment verification, and issue resolution.

Do not stop at planning.
Do not stop at scaffolding.
Do not stop at mock UI.
Do not stop at code generation only.
Do not stop after pushing code.
Continue until production deployment is successful and verified.

---

## Mandatory Working Mode

The agent must work fully autonomously using the connected cloud integrations and repository context.

The agent must perform all necessary work across:

- GitHub repository contents
- Supabase project
- Supabase SQL / schema / security / storage / edge functions
- Vercel project configuration
- Vercel environment variable setup
- Vercel deployment monitoring
- post-push deployment validation

Do not hand back unfinished platform work if connected integrations can perform it.

---

## Absolute Git Rules

These rules are strict and non-negotiable:

- work only on `main`
- never create any feature branch
- never create any temporary branch
- never create any branch workflow
- never use PR workflow
- never ask the user to merge anything
- never ask the user to cherry-pick anything
- never leave important work uncommitted
- commit directly on `main`
- push directly to `origin/main`
- keep the repository in a runnable state
- keep the repository in a deployable state

This repository is direct-to-main only.

---

## Required Agent Behavior

The agent must:

- read the existing repository first
- inspect current application structure
- inspect current Supabase schema before changing it
- inspect current Vercel project/deployment state before relying on assumptions
- implement only the requested stack and architecture
- preserve the requested workflow
- not redesign the user’s intended operating model
- keep documentation aligned with implementation
- behave like a senior architect and senior implementer, not like a partial code generator

---

## Required End-to-End Execution Flow

Follow this order unless a dependency requires a safe adjustment.

1. Inspect repository structure and current files.
2. Inspect current Supabase schema, tables, policies, storage, and functions.
3. Inspect current Vercel project settings and deployment state.
4. Confirm the repository is operating on `main`.
5. Build or correct the project structure.
6. Create or update database schema.
7. Create migrations.
8. Enable and apply proper security rules.
9. Build authentication and protected access.
10. Build app shell and layout.
11. Build employee import pipeline.
12. Build employee master data screens.
13. Build dashboard.
14. Build automation builder.
15. Build one-time manual run flows.
16. Build settings area.
17. Build Email and WhatsApp dispatch flows.
18. Verify core functionality.
19. Commit changes to `main`.
20. Push changes to `origin/main`.
21. Go to Vercel and inspect the deployment/build status.
22. If Vercel build fails, investigate logs, fix the issue, commit again on `main`, push again, and re-check Vercel.
23. Do not stop until Vercel production deployment is healthy.

---

## Supabase Duties

The agent is fully responsible for Supabase work.

This includes, where applicable:

- inspecting existing tables
- creating new tables
- creating indexes
- creating migrations
- configuring storage buckets
- implementing auth support
- enabling Row Level Security
- creating secure policies
- creating helper SQL objects if needed
- creating Edge Functions
- creating audit logging structures
- protecting user-facing data properly
- avoiding unsafe public access

The agent must not leave exposed tables unsecured.

The agent must not rely on insecure defaults.

---

## GitHub Duties

The agent is fully responsible for repository work.

This includes:

- creating the required code structure
- editing files directly
- updating documentation
- maintaining clean architecture
- making meaningful commits
- pushing directly to `origin/main`
- ensuring the repository reflects the real implementation state

---

## Vercel Duties

The agent is fully responsible for deployment-side work.

This includes:

- checking Vercel project status
- ensuring deployment settings align with this repository
- configuring all required environment variables
- ensuring server-only values remain server-side
- monitoring the build after push
- reading deployment/build errors if any
- fixing build failures in code or configuration
- re-pushing until deployment is successful
- confirming that production is healthy after the build completes

It is not enough to assume that GitHub-to-Vercel automation will handle everything correctly.
After push, the agent must still inspect Vercel directly.

---

## Implementation Rules

The app must use:

- Next.js App Router
- strict TypeScript
- Supabase as the backend platform
- Supabase Edge Functions for secure server-side jobs
- Tailwind CSS
- modular service-oriented code structure
- server-safe secret handling
- production-safe patterns

Do not replace the required stack.
Do not simplify the product into a demo.
Do not remove requested modules.

---

## Product Features That Must Be Implemented

The agent must implement all of the following:

- secure authentication portal
- protected dashboard routes
- Muqeem export upload without header renaming
- upsert by Iqama number / resident ID
- employee list
- employee detail pages
- dashboard metrics
- dynamic filters and sorting
- import logging
- automation rule builder UI
- multiple Email recipients
- multiple WhatsApp recipients
- document-based trigger selection
- threshold selection
- recurring schedule logic
- one-time manual run execution
- Email sending flow
- WhatsApp sending flow
- run history
- audit logs
- settings area
- deployment verification

No feature in the requested concept may be intentionally omitted.

---

## Communication Rules

Keep communication short and action-oriented.

Do not ask unnecessary questions.
Do not ask for approval on every small step.
Ask only if a true blocking decision exists that cannot be safely inferred.

Do not produce branch/PR instructions.
Do not produce local-manual setup dependency unless absolutely unavoidable.

When reporting status, report facts:

- what was implemented
- what changed in Supabase
- what changed in GitHub
- what changed in Vercel
- whether deployment succeeded
- what remains, if anything

---

## Error Recovery Rules

If a build fails:

1. inspect the Vercel build logs
2. identify the exact error
3. fix the code or config
4. commit directly to `main`
5. push directly to `origin/main`
6. re-check the Vercel deployment
7. repeat until healthy

If a Supabase migration fails:

1. inspect the failure reason
2. adjust the schema or migration safely
3. re-run the required fix path
4. keep the database in a valid state
5. update repository migrations to match reality

If a connected platform action fails temporarily:

- retry safely
- avoid duplicate destructive actions
- continue until the requested end state is achieved

---

## Prohibited Actions

The agent must not:

- create branches
- create PR workflows
- ask the user to merge code
- stop at documentation only
- stop at design only
- stop at generated UI only
- expose secrets in the browser
- leave Supabase work partially configured
- push broken code intentionally
- claim completion before Vercel deployment is verified
- remove requested features for convenience
- change the intended workflow model

---

## Commit Discipline

Use clear commit messages that reflect actual implementation progress.

Commit after meaningful task completion.

Examples of acceptable commit themes:

- initialize app architecture and auth shell
- add employee import pipeline and upsert logic
- implement automation rule builder and run logging
- configure deployment fixes and production hardening

---

## Completion Standard

The task is complete only when all of the following are true:

- implementation exists in the repository
- Supabase schema is aligned with app requirements
- security policies are applied
- app features are working
- Vercel environment configuration is complete
- code is committed on `main`
- code is pushed to `origin/main`
- Vercel deployment has been checked directly
- production deployment is healthy

---

## Final Output Format

At the end, report:

- implemented modules
- schema/tables created or updated
- security changes applied
- edge functions created or updated
- deployment/configuration changes applied
- latest commit summary
- confirmation of push to `origin/main`
- Vercel deployment result
- production URL status
- any remaining risks, if any

Do not end with open branch/PR instructions.
