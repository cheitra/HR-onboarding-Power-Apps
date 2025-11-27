# Power Apps HR Onboarding - Sample Project

This repository contains a full guide + sample snippets to build an HR Onboarding application using Microsoft Power Platform (Power Apps Canvas App, Dataverse, Power Automate).  
It covers candidate intake → offer → document collection → orientation scheduling → asset assignment → onboarding completion.

## What’s included
- README (this file)
- dataverse_schema.json — suggested Dataverse tables & schema
- powerfx_snippets.txt — Power Fx formulas
- flow_instructions.md — Power Automate flow designs & expressions
- canvas_app_screen_notes.md — UI screen descriptions & control mapping
- deployment_notes.md — ALM and deployment tips

## Quick Architecture
1. **Dataverse** (Tables): Candidates, OnboardingTasks, EmployeeAssets, Documents
2. **Power Apps (Canvas App)**: HR portal & Candidate self-service
3. **Power Automate**:
   - Flow A: When candidate created → send offer email + create onboarding tasks
   - Flow B: When document uploaded → validate & notify HR
   - Flow C: Onboarding reminders & orientation scheduling
4. **Integrations**: SharePoint / Azure Blob (documents), Outlook/Teams, Azure AD for user provisioning

## How to use
1. Create Dataverse tables (see dataverse_schema.json).
2. Build Canvas App (Tablet) with screens described in canvas_app_screen_notes.md.
3. Create Power Automate flows (see flow_instructions.md).
4. Use Power Fx snippets for forms, validations and flows.
5. Version docs and snippets in GitHub (store exported packages separately).

## Next steps / Optional
- Create Power Pages candidate portal for public uploads.
- Add Azure Function for heavy validation/ETL or HRIS sync.
- Implement ALM: pac CLI or Power Platform Build Tools.


