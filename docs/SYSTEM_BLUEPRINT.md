# SYSTEM_BLUEPRINT.md

## 1. System Overview

This application is a production-grade internal employee compliance and alerting system built around manual Muqeem file uploads.

There is no live Muqeem API sync in this operating model.

Operational truth is refreshed through repeated file uploads from Muqeem.

The system must convert these uploads into a canonical, queryable, secure employee compliance dataset in Supabase and expose it through a premium admin web application.

---

## 2. Primary Goals

The system must solve these core business problems:

- keep current employee compliance data updated from Muqeem exports
- track Iqama and passport expiry status
- allow fast admin review through dashboard and employee screens
- allow admin-defined automated alerting rules
- support both recurring runs and one-time manual runs
- support Email and WhatsApp delivery channels
- keep a complete operational audit trail
- remain continuously deployable through Vercel

---

## 3. Architecture

### Frontend

Use Next.js App Router.

Use server components by default.

Use client components only where interactivity requires it, such as:

- advanced filters
- data table interactions
- automation rule forms
- run-now actions
- upload progress UI
- theme handling if implemented

Use a clear layout system with:

- auth route group
- protected dashboard route group
- reusable layout shell
- reusable table/filter/form modules

### Backend

Use Supabase for:

- Postgres database
- authentication
- row-level security
- storage
- edge functions

Use Supabase Edge Functions for:

- secure file import processing
- notification dispatch
- scheduled automation evaluation
- manual automation execution
- testing notification channels
- summarization and logging jobs

### Hosting and Delivery

Use Vercel for:

- production hosting
- deployment pipeline
- environment variable injection
- deployment monitoring
- production verification

---

## 4. Core Product Modules

### 4.1 Authentication

Required behavior:

- secure login
- session-aware route protection
- role-aware access
- admin-restricted management screens
- safe logout flow

Suggested roles:

- super_admin
- admin
- viewer

### 4.2 Dashboard

Required behavior:

- operational summary at a glance
- total employee counts
- expiring soon summaries
- expired summaries
- nationality grouping
- recent imports
- recent automation runs
- quick actions
- filters and sorting support

### 4.3 Employees

Required behavior:

- searchable employee table
- sortable columns
- multiple filters
- employee detail page
- document status visibility
- last import visibility
- change history visibility

### 4.4 Imports

Required behavior:

- upload Muqeem file as-is
- preserve raw file
- parse without requiring header rename
- validate required identifiers
- map using Iqama / resident ID
- upsert employee records
- store row-level import results
- show import summary
- store detailed import logs

### 4.5 Automations

Required behavior:

- create multiple rules
- select Email or WhatsApp
- enter multiple recipients
- select document type
- select threshold
- select scheduling behavior
- preview matched employees
- save and edit rules
- duplicate rules
- enable / disable rules
- inspect rule run history

### 4.6 Manual Run Operations

Required behavior:

- run saved rules immediately
- evaluate current data at execution time
- show preview counts
- log results
- protect against careless duplicate re-send behavior

### 4.7 Settings

Required behavior:

- general operational settings
- notification settings
- template settings
- integration settings
- admin access settings
- testing actions
- system health visibility

---

## 5. Data Model

The data model must be normalized enough for auditability but practical enough for fast implementation.

### Core Tables

#### employee_records
Canonical latest employee state.

Suggested columns:

- id
- iqama_number
- employee_name
- nationality
- passport_number
- passport_expiry_date
- iqama_expiry_date
- active_status
- raw_status
- last_import_id
- last_imported_at
- created_at
- updated_at

#### employee_imports
One record per uploaded file/import operation.

Suggested columns:

- id
- file_name
- storage_path
- uploaded_by
- imported_at
- total_rows
- inserted_count
- updated_count
- unchanged_count
- failed_count
- status
- notes

#### employee_import_rows
Optional detailed processing rows for diagnostics and audit.

Suggested columns:

- id
- import_id
- row_number
- raw_payload_json
- mapped_iqama_number
- processing_status
- error_message

#### employee_change_logs
Track meaningful changes detected between imports.

Suggested columns:

- id
- employee_id
- import_id
- changed_fields_json
- previous_values_json
- new_values_json
- changed_at

#### automation_rules
Rule definitions created from the admin UI.

Suggested columns:

- id
- name
- channel
- document_type
- threshold_value
- threshold_unit
- schedule_type
- schedule_time
- timezone
- is_active
- description
- rule_config_json
- created_by
- created_at
- updated_at

#### automation_recipients
One recipient per row for flexible rule configuration.

Suggested columns:

- id
- rule_id
- recipient_type
- recipient_value

#### automation_runs
One row per scheduled or manual run.

Suggested columns:

- id
- rule_id
- run_type
- triggered_by
- started_at
- finished_at
- matched_count
- sent_count
- failed_count
- status
- run_summary_json

#### automation_run_items
One row per employee-recipient dispatch result.

Suggested columns:

- id
- run_id
- employee_id
- recipient
- channel
- status
- provider_message_id
- error_message
- payload_json
- created_at

#### notification_templates
Reusable Email / WhatsApp message definitions.

#### app_settings
Application-level non-secret settings.

#### user_profiles
App roles and profile metadata linked to auth users if needed.

---

## 6. Data Import Logic

The Muqeem import flow must behave as follows:

1. Admin uploads the file.
2. File is stored in Supabase Storage for audit.
3. File is parsed safely.
4. Required identification columns are validated.
5. Each row is normalized.
6. Employee is matched by Iqama number / resident ID.
7. If employee exists, update the canonical record.
8. If employee does not exist, insert a new canonical record.
9. If key fields changed, create change-log entries.
10. Save row-level status and import-level summary.
11. Refresh downstream dashboard and automation visibility.

Important rules:

- do not require header renaming
- do not depend on live sync from Muqeem
- keep parser isolated so future format changes can be handled in one place
- keep raw row payload available for diagnostics
- keep import processing idempotent

---

## 7. Automation Logic

Automation must be rule-driven.

Each rule must contain:

- channel
- recipients
- document type
- threshold
- schedule behavior
- activation status
- notes / metadata
- template reference or message configuration
- run history relationship

### Supported channels

- Email
- WhatsApp

### Supported trigger bases

- Iqama expiry
- passport expiry

### Supported run styles

- recurring scheduled
- one-time manual

### Manual rule behavior

- evaluate against current employee data at click time
- show a preview before sending where practical
- send using saved rule configuration
- log outcomes
- avoid careless duplicate sends

---

## 8. Notification Design

### Email

The system must support secure server-side Email dispatch.

Design requirements:

- multiple recipients
- rule-based content selection
- template support
- run logging
- error logging
- no client-side secret exposure

### WhatsApp

The system must support server-side WhatsApp dispatch.

Design requirements:

- multiple recipients
- provider-ready abstraction
- template-friendly design
- delivery logging
- error logging
- no client-side secret exposure

---

## 9. Edge Functions

Expected edge/server functions include responsibilities such as:

- import file processing
- batch row normalization
- rule evaluation
- run-now execution
- Email dispatch
- WhatsApp dispatch
- scheduled automation processing
- notification testing
- operational summarization

All secret-dependent actions must remain server-side.

---

## 10. Security Model

The security model must include:

- authenticated access
- role-aware access control
- protected admin operations
- secure route handling
- safe server/client boundary
- Row Level Security where applicable
- least-privilege data access
- audit logging for sensitive actions

Tables exposed to user-facing access paths must not be left unsecured.

---

## 11. Routing Model

Suggested application routes:

- `/login`
- `/dashboard`
- `/employees`
- `/employees/[id]`
- `/imports`
- `/automations`
- `/automations/[id]`
- `/automation-runs`
- `/settings/general`
- `/settings/notifications`
- `/settings/integrations`
- `/settings/users`

Adjust routes only if the final architecture remains clear and scalable.

---

## 12. UI/UX Direction

The UI must feel like a premium internal admin application.

Required characteristics:

- modern clean shell
- fast perceived performance
- clear information hierarchy
- responsive layout
- dashboard-first operational design
- excellent table usability
- clear filters
- strong status visibility
- loading states
- empty states
- error states
- audit visibility

The design must not degrade into a generic unfinished CRUD panel.

---

## 13. Deployment Model

Deployment is through Vercel.

The operating model is:

- agent implements code
- agent commits to `main`
- agent pushes to `origin/main`
- agent goes to Vercel
- agent checks build/deployment state
- if broken, fix and repeat
- finish only after healthy production deployment

---

## 14. Documentation Alignment

Implementation must stay aligned with:

- `README.md`
- `AGENTS.md`
- `docs/BUILD_CHECKLIST.md`
- `docs/ACCEPTANCE_CRITERIA.md`

If implementation changes architecture meaningfully, update these documents accordingly.
