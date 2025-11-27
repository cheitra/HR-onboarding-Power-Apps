1. Splash / Role Selection
   - Controls: Buttons for HR, Hiring Manager, Candidate
   - Logic: Navigate to role-specific dashboards

2. HR Dashboard
   - KPIs: Count rows where status='Applied', Pending docs, Tasks due
   - Galleries: Recent candidates, tasks list, quick actions

3. Candidate Form (Create / Edit)
   - Controls: Form (frmCandidate) connected to Candidates table
   - Buttons:
       - Save -> SubmitForm(frmCandidate)
       - Save & Offer -> Patch(frmCandidate, {status: "Offered"}); trigger Flow_CreateOffer.Run(...)
       - Upload Resume -> Attachment control (store file in SharePoint) then call flow to create Documents record

4. Candidate Self-Service
   - Candidate login via link or email token (or Power Pages)
   - View tasks, upload docs, view orientation schedule

5. Tasks Screen
   - Gallery of tasks; actions: Accept, Mark Completed (Patch), Reassign

6. Assets Screen
   - Form to allocate assets (EmployeeAssets table)
   - Asset allocation wizard: choose asset type -> assign -> create record

7. Documents Screen
   - Upload control for PDFs/images
   - On upload, call Power Automate to validate and update the Documents row

8. Admin Settings
   - Manage positions, templates, onboarding task templates (use Dataverse or Choice tables)
