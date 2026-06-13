# Muqeem Employee Compliance & Automation System

## Project Purpose

This repository contains a production-grade internal web application for managing employee document compliance using manually uploaded Muqeem export files.

The system must be built as a real working application, not a demo, not a mockup, and not a UI-only scaffold.

The system must support full cloud-based autonomous execution across GitHub, Supabase, and Vercel.

The application will be used to:

- upload active employee export files downloaded from Muqeem
- keep employee records updated in Supabase
- track Iqama and passport validity
- provide a modern dashboard
- allow dynamic filtering and sorting
- create admin-managed automation rules
- send alerts by Email and WhatsApp
- support recurring and one-time manual automation execution
- store audit logs for imports and notification runs
- stay continuously deployable through Vercel

---

## Mandatory Build Principles

The application must follow these principles:

- production-ready from the beginning
- fully cloud-managed
- no dependence on local manual engineering steps
- Next.js App Router architecture
- strict TypeScript
- Supabase as the backend platform
- Supabase Edge Functions for secure server-side operations
- Vercel as the hosting and deployment platform
- admin-first secure access model
- modular, scalable, maintainable architecture
- all secrets kept server-side only
- real implementation, not placeholder logic

---

## What The System Must Do

### 1. Employee Data Import

The system must allow manual upload of the active employee export file downloaded from Muqeem.

Strict rules:

- the uploaded file must be accepted exactly as downloaded
- column headers must not be renamed by the user
- the app must not ask the user to edit the file structure manually
- the parser must adapt to the existing Muqeem export structure
- employee matching must be based on Iqama number / resident ID
- employee records must be inserted or updated automatically
- repeated uploads must always be supported
- there is no live direct sync with Muqeem, so manual upload is the operational sync method

The upload process must:

1. accept the file
2. store the file for audit
3. parse the data safely
4. validate required identifier columns
5. map rows by Iqama number / resident ID
6. upsert employees into the main table
7. log inserted, updated, unchanged, and failed rows
8. update the current dashboard and reporting data
9. keep detailed import history

The import pipeline must be idempotent and safe to run repeatedly.

---

### 2. Employee Master Data

The app must maintain a canonical employee record per employee.

Each employee record should preserve the latest imported compliance-related data, such as:

- employee identity details from the Muqeem file
- Iqama number
- Iqama expiry date
- passport number
- passport expiry date
- nationality
- current active/compliance state
- last import reference
- last update time

The system must support future document types beyond Iqama and passport.

---

### 3. Dashboard

The dashboard must be modern, premium, clear, and operationally useful.

It must display at minimum:

- total active employees
- employees with Iqama expiring soon
- employees with passport expiring soon
- employees already expired
- nationality-based summaries
- latest imports
- latest automation runs
- alert statistics by channel
- quick action buttons
- direct access to upload and automation screens

The dashboard must support dynamic filtering and sorting.

Required filters and views include:

- nationality
- document type
- expiry window
- active / inactive state
- employee name
- Iqama number
- nearest expiry sorting
- latest updated sorting

---

### 4. Employee List and Details

The system must provide a strong employee list screen.

Required capabilities:

- search
- filtering
- sorting
- pagination or virtualization
- status indicators
- highlight expiring records cleanly
- last updated visibility
- row click to open employee details

Employee detail view must show:

- all relevant identity data from the file
- Iqama details
- passport details
- current document status
- import/change history
- automation relevance preview
- operational context for follow-up

---

### 5. Automation Rules Builder

The system must include an in-app admin UI for creating and managing automation rules.

Automation must not be limited to hardcoded backend-only rules.

The admin must be able to create multiple automation rules.

Each automation rule must support:

- rule name
- active / inactive status
- Email or WhatsApp channel
- multiple recipient entries
- document type selection
- threshold selection
- threshold unit selection
- recurring schedule selection
- manual run support
- chosen execution time
- timezone-aware scheduling
- preview of matching employees
- notes / description
- save
- edit
- duplicate
- enable / disable
- run history

Supported initial document triggers:

- Iqama expiry
- passport expiry

The design must remain extensible for future document types.

---

### 6. One-Time Manual Runs

The system must support one-time manual automation execution.

This means:

- the admin creates and saves a rule in advance
- later the admin can click a run-now action
- the app must evaluate current matching employees immediately
- the app must send alerts using the saved configuration
- the app must show matched, sent, and failed counts
- the app must save execution logs
- the app must prevent accidental duplicate repeated sends where appropriate

This feature is mandatory.

---

### 7. Email Notifications

The system must support Email-based automation.

The app must support:

- multiple recipient email addresses per rule
- secure server-side sending
- reusable templates
- testable sending flow
- run logs
- failure logs
- delivery attempt visibility

Any Email sending configuration must remain server-side only.

---

### 8. WhatsApp Notifications

The system must support WhatsApp-based automation.

The implementation must be provider-ready and secure.

The app must support:

- multiple target phone numbers per rule
- configurable provider integration
- server-side dispatch
- message template support where relevant
- delivery logging
- failure logging

The architecture must allow future extension to different WhatsApp providers without redesigning the whole app.

---

### 9. Settings Area

The app must contain an admin settings area.

It must support:

- general settings
- notification settings
- integration settings
- automation-related defaults
- admin access controls
- test actions
- template management
- system health visibility

Sensitive values must not be exposed back to the browser UI.

---

### 10. Authentication and Authorization

The app must implement secure user authentication and protected routing.

Minimum roles:

- super_admin
- admin
- viewer

Only appropriate admin users may:

- upload files
- modify employee data workflows
- create or edit automation rules
- execute one-time runs
- manage settings
- manage integrations
- review logs

---

## Required Technology

This project must use:

- Next.js App Router
- TypeScript
- Tailwind CSS
- Supabase Postgres
- Supabase Auth
- Supabase Storage
- Supabase Row Level Security
- Supabase Edge Functions
- Vercel deployment
- reusable typed service modules
- production-safe server/client separation

Do not replace the requested stack.

---

## Cloud-Managed Operating Requirement

This project is intended for autonomous cloud execution.

The connected agent must do the work fully across:

- GitHub
- Supabase
- Vercel
- connected platform integrations

The agent must not stop at planning only.

The agent must:

- inspect current repository state
- inspect current Supabase state
- implement code
- create database schema and migrations
- create security policies
- configure deployment requirements
- commit to main
- push to main
- then go to Vercel and inspect the build/deployment status
- fix any failures if they occur
- continue until the production deployment is successful

---

## Git Workflow Rules

This repository uses a strict direct-to-main workflow.

Required rules:

- work only on `main`
- do not create branches
- do not use PR workflow
- do not ask the user to merge
- commit directly on `main`
- push directly to `origin/main`
- keep the repository runnable
- keep the repository deployment-ready
- keep documentation updated as the system evolves

---

## Deployment Rule

Vercel is the production hosting platform.

The repository is expected to stay continuously aligned with Vercel deployment behavior.

After each major implementation or fix:

- commit to `main`
- push to `origin/main`
- inspect the Vercel deployment/build
- fix errors if the deployment fails
- repeat until production deployment is healthy

The work is not complete just because the code was pushed.
The work is complete only when the Vercel deployment is successful and the app is working.

---

## Security Rule

The project must be implemented securely.

This includes:

- secure authentication
- proper authorization
- secure data access policies
- server-side handling of secrets
- protected admin operations
- audit logging
- safe input validation
- no hardcoded private keys in source code
- no exposure of server-only values to client code

---

## Required Documentation Files

This repository must always keep these control documents:

- `README.md` — product and business master document
- `AGENTS.md` — strict operating rules for the autonomous agent
- `docs/SYSTEM_BLUEPRINT.md` — architecture and technical design
- `docs/BUILD_CHECKLIST.md` — execution checklist
- `docs/ACCEPTANCE_CRITERIA.md` — final definition of done

---

## Final Delivery Standard

The project is complete only when all of the following are true:

- the app is fully implemented
- the import flow works
- employee upsert works by Iqama number / resident ID
- dashboard works on latest uploaded data
- automation rules work from the UI
- one-time manual runs work
- Email notification flow works
- WhatsApp automation path is implemented
- security is properly applied
- Supabase is fully configured
- Vercel deployment is successful
- changes are committed on `main`
- changes are pushed to `origin/main`
- deployment has been verified in Vercel after push

For exact technical design, execution order, and success criteria, follow the documents inside the `docs` folder and the strict operating rules in `AGENTS.md`.
