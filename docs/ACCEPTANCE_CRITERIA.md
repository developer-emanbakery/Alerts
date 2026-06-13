# ACCEPTANCE_CRITERIA.md

## Definition of Done

This project is considered complete only when every requirement below is satisfied.

If any item below fails, the project is not complete.

---

## 1. Repository and Workflow

- [ ] All work was performed directly on `main`
- [ ] No branch workflow was used
- [ ] No PR workflow was used
- [ ] No manual merge instruction was required
- [ ] Changes were committed directly on `main`
- [ ] Changes were pushed directly to `origin/main`
- [ ] Repository remains runnable
- [ ] Repository contains updated documentation

---

## 2. Authentication and Access

- [ ] Login works
- [ ] Protected routes work
- [ ] Unauthorized access is blocked
- [ ] Admin-restricted screens are properly restricted
- [ ] Role-aware access behavior is implemented

---

## 3. Supabase Data Layer

- [ ] Required tables exist
- [ ] Migrations exist in the repository
- [ ] Canonical employee records are stored correctly
- [ ] Import logs are stored correctly
- [ ] Automation rules are stored correctly
- [ ] Automation runs are stored correctly
- [ ] Delivery logs are stored correctly
- [ ] Auditability is preserved

---

## 4. Security

- [ ] User-facing data access is not left exposed
- [ ] Appropriate Row Level Security is enabled where required
- [ ] Appropriate access policies are created where required
- [ ] Secrets are not hardcoded in source code
- [ ] Server-only values are not exposed to client code
- [ ] Sensitive operations are protected

---

## 5. Muqeem Import Requirements

- [ ] The app accepts the Muqeem export file as downloaded
- [ ] The app does not require header renaming
- [ ] The parser handles the source structure in code
- [ ] Employee matching works by Iqama / resident ID
- [ ] New employees are inserted correctly
- [ ] Existing employees are updated correctly
- [ ] Import summary is generated
- [ ] Import details are logged
- [ ] Repeated uploads are supported safely

---

## 6. Dashboard Requirements

- [ ] Dashboard shows total active employees
- [ ] Dashboard shows Iqama expiry visibility
- [ ] Dashboard shows passport expiry visibility
- [ ] Dashboard shows expired status visibility
- [ ] Dashboard shows nationality summaries
- [ ] Dashboard shows recent imports
- [ ] Dashboard shows recent automation runs
- [ ] Dashboard supports useful filtering and sorting

---

## 7. Employee Module Requirements

- [ ] Employee list exists
- [ ] Employee search works
- [ ] Employee filtering works
- [ ] Employee sorting works
- [ ] Employee detail page exists
- [ ] Employee compliance data is visible clearly
- [ ] Employee history or change visibility exists

---

## 8. Automation Requirements

- [ ] Multiple automation rules can be created
- [ ] Rules support Email channel
- [ ] Rules support WhatsApp channel
- [ ] Rules support multiple recipients
- [ ] Rules support Iqama expiry trigger
- [ ] Rules support passport expiry trigger
- [ ] Rules support threshold configuration
- [ ] Rules support schedule configuration
- [ ] Rules can be enabled and disabled
- [ ] Rules can be duplicated
- [ ] Rule match preview exists
- [ ] Rule run history exists

---

## 9. Manual Run Requirements

- [ ] Saved rules can be executed manually
- [ ] Manual runs evaluate current data
- [ ] Preview counts are shown or made available
- [ ] Run results are logged
- [ ] Duplicate-send risk is reasonably controlled

---

## 10. Notification Requirements

- [ ] Email sending path is implemented
- [ ] WhatsApp sending path is implemented
- [ ] Notifications are triggered from saved rules
- [ ] Delivery attempts are logged
- [ ] Failures are logged
- [ ] Secret-dependent sending logic is server-side

---

## 11. Settings Requirements

- [ ] General settings screen exists
- [ ] Notification/integration settings support exists
- [ ] Admin-oriented controls exist
- [ ] Template or message-management support exists
- [ ] System health or operational visibility exists

---

## 12. Vercel Deployment Requirements

- [ ] Required environment configuration is present in Vercel
- [ ] Latest code is pushed to `origin/main`
- [ ] Vercel deployment was checked directly after push
- [ ] Build logs were reviewed if any failure occurred
- [ ] Build issues were fixed and redeployed if necessary
- [ ] Production deployment is healthy

---

## 13. Final Operational Completion

The implementation is complete only if all statements below are true:

- [ ] The app is a real working application
- [ ] The requested stack was respected
- [ ] The requested workflow was respected
- [ ] The requested features were not intentionally omitted
- [ ] Supabase work was completed fully
- [ ] GitHub work was completed fully
- [ ] Vercel work was completed fully
- [ ] Production deployment was verified after push
- [ ] The system is ready for real operational use after required platform access is available
