# Candidate Submission Template

## Candidate Information
- Full Name: [Your Full Name]
- Email: [Your Email]
- LinkedIn or Portfolio: [Optional Link]
- Submission Date: 2026-03-17

## Overview
This submission provides an AI-powered enterprise onboarding automation design and a working prototype scaffold. The solution orchestrates intake, AI extraction/validation, profile enrichment, task routing, personalization, communication drafting, and milestone tracking across HR, IT, compliance, and hiring managers.

## Task 1: AI-Powered Automation Design

### Workflow Logic
1. Trigger starts from form/HRIS onboarding submission.
2. Intake data and uploaded documents are normalized and assigned an onboarding ID.
3. AI extracts structured fields from documents and validates completeness.
4. Confidence and issue checks decide auto-progress vs manual HR review.
5. Profile enrichment combines role, department, location, manager, and employment type.
6. Automation generates and routes tasks to HR, IT, compliance, and manager owners.
7. AI generates personalized first-week onboarding plan.
8. AI drafts communications (welcome email, manager summary, reminders).
9. Workflow updates onboarding status and triggers Day 1/7/30 milestone checks.

### Where AI Is Used
Explain how AI is used for:
- Classification
- Document processing
- Workflow decision logic
- Automatic drafting
- Recommendations or personalization

AI usage in this solution:
- Classification: onboarding path and support routing by employment type/role context.
- Document processing: extraction of key fields, missing document detection, and confidence scoring.
- Workflow decision logic: requirement recommendations for access, compliance, and training.
- Automatic drafting: welcome emails, HR summaries, and manager handoff notes.
- Recommendations/personalization: role/department/location-specific first-week onboarding plan.

### Prompt Engineering
Prompt pack is included in `starter/prompts/prompts.md` and contains:
- Intake + document extraction prompt with strict JSON schema
- Validation and quality control prompt
- Task routing prompt
- Personalized plan generation prompt
- Communication drafting prompt

Prompt design patterns used:
- explicit role instructions
- strict output schema and fallback behavior for missing values
- confidence thresholds for human review
- deterministic settings for extraction/routing and moderate creativity for drafting

### Data Flow and Integrations
Describe systems involved such as:
- Google Workspace
- HRIS
- Slack
- Email
- Calendar
- Document storage
- Automation platform

Proposed flow:
Form/HRIS trigger → normalize payload → AI extract/validate → structured onboarding profile → task routing → plan generation → notifications/scheduling → milestone tracking/feedback → status updates.

Integrations:
- Automation: n8n (prototype scaffold provided)
- AI: OpenAI API
- Data layer: Airtable / Google Sheets / HRIS
- Communication: Gmail/Outlook, Slack/Teams
- Scheduling: Google Calendar / Outlook Calendar
- Documentation: Notion / Confluence

### Business Impact
Explain how your solution improves:
- Efficiency
- Accuracy
- Personalization
- HR time savings
- New hire experience

Expected outcomes:
- Faster onboarding cycle time and reduced manual coordination
- Improved data accuracy and fewer missing documents before start date
- Better consistency in cross-functional handoffs (HR/IT/Manager)
- Personalized onboarding experience and clearer first-week guidance
- Improved visibility into blockers and milestone completion

## Task 2: Implementation Demo

### Demo Type
Examples:
- n8n
- Zapier
- Code scaffold
- Diagram
- Screenshots
- Video walkthrough

n8n workflow scaffold (JSON export) demonstrating core orchestration logic.

### Files Included
List the files you added.

- `starter/design-solution.md`
- `starter/prompts/prompts.md`
- `starter/workflows/onboarding-workflow.json`

### Flow of Data
Explain how data moves through your demo.

Webhook intake receives new hire record → normalization step standardizes payload → AI request performs extraction/validation → quality gate branches exceptions to HR review or continues happy path → structured profile is created → task list is generated and routed → personalized onboarding plan is generated → onboarding status is updated for milestone monitoring.

### Pain Points Solved
Explain what part of onboarding your demo improves and why.

- Eliminates manual re-entry from forms/documents into tracking sheets.
- Reduces delays from unclear ownership by routing tasks automatically.
- Improves consistency of communications and onboarding plans.
- Introduces scalable exception handling through confidence-based review.

## Assumptions
List any assumptions you made.

- Intake payload includes minimum employee metadata (name, role, department, start date).
- Document text is available to AI either via OCR upstream or platform-native parsing.
- API credentials and destination systems are configured in the automation environment.
- Prototype focuses on orchestration logic; some connectors are represented as scaffold nodes.

## Setup Instructions
Add any steps needed to review or run your solution.

1. Open `starter/workflows/onboarding-workflow.json` in n8n and import workflow.
2. Add required credentials (OpenAI API key and any notification/data connectors).
3. Configure webhook endpoint and send sample intake JSON payload.
4. Verify branch behavior for valid vs exception records.
5. Review generated task payload and onboarding plan output.

## Optional Notes
Anything else you want us to know.

The solution is intentionally modular so additional integrations (HRIS sync, identity provisioning, analytics dashboard) can be added with minimal workflow redesign.
