Flow A: Candidate created -> Offer email + Create onboarding tasks
Trigger: When a row is added (Dataverse) - Table: Candidates
Actions:
  1. Condition: If status == 'Offered'
  2. Create HTML email body with candidate details
     - Use: Create HTML table or Compose with dynamic content
  3. Send email (Office 365 Outlook - Send an email V2)
  4. Create multiple rows in Dataverse (OnboardingTasks)
     - Create row: Title = 'Complete Documents', assignedTo = HRTeam@company.com
     - Create row: Title = 'IT asset assignment', assignedTo = ITTeam@company.com
  5. Create Teams meeting for orientation
     - Action: Create a Teams meeting
  6. Post message to Teams channel for HR notification

Useful expressions:
- Format date: formatDateTime(triggerBody()?['createdon'],'yyyy-MM-dd')
- Candidate full name: concat(triggerBody()?['firstname'],' ', triggerBody()?['lastname'])

Flow B: Document uploaded -> Validate & Notify
Trigger: When a row is added - Table: Documents
Actions:
  1. Get file content from SharePoint or Blob depending on storage
  2. Run AI Builder Form Processing or Azure Form Recognizer to extract fields
  3. Condition: If validation passes -> Update Documents row set validated=true
  4. Start and wait for approval (optional) with Approvals connector
  5. Send email to candidate & HR with status

Flow C: Onboarding milestone reminder (Scheduled)
Trigger: Recurrence (daily)
Actions:
  1. List rows (OnboardingTasks) where DueDate within next 2 days and status != Completed
     - Use Filter Query (OData) example: status ne 'Completed' and dueDate le @{addDays(utcNow(),2)}
  2. Apply to each -> Send reminder email to assignedTo
  3. Log reminder in a Monitoring table
