# Multilingual-Volunteer-Intake-Automation
Automated multilingual volunteer intake and routing system built with Make.com, Google Gemini API, and Google Workspace (AI Tech Corps Capstone.   

MULTILINGUAL VOLUNTEER INTAKE AND ROUTING AUTOMATION
========================================================================

Built as an AI Tech Corps Fellow capstone project with OptimaNova AI.

An automated, AI-powered intake workflow built on Make.com that eliminates manual translation and triage bottlenecks for community organizations. It ingests multilingual form submissions, translates and classifies applicant intent using the Google Gemini API, logs structured records in Google Sheets, and dispatches localized confirmation emails via Gmail.

Demo Video: [Watch the 2-Minute Walkthrough](https://drive.google.com/file/d/1l0vM5l5rhexW74ZDiPk4MfJ51KHg35qS/view?usp=drive_link)

------------------------------------------------------------------------
Community organizations receiving volunteer applications in multiple languages face severe administrative bottlenecks:

- Manual Translation Overhead: Staff spent roughly 15 to 20 minutes per submission translating responses and deciphering availability or skill sets.
- Delayed Response Times: Applicants waited 3 to 5 business days for initial acknowledgment, leading to high volunteer drop-off rates.
- Inconsistent Data Entry: Unstructured text entries created messy spreadsheets that made filtering volunteers by language or role nearly impossible.


2. THE BUILD (ARCHITECTURE AND WORKFLOW)
------------------------------------------------------------------------
The pipeline connects four core tools into a zero-touch automated workflow:

1. Ingestion (Google Forms + Google Sheets)
   Captures raw applicant data (contact info, preferred language, availability, skills, and free-text motivation) and triggers the automation watcher.

2. AI Processing and Classification (Google Gemini API via Make.com)
   - Detects the source language automatically.
   - Translates free-text responses into standardized English for staff review.
   - Extracts structured role tags (Technical, Event Support, Translation) and drafts a culturally appropriate, localized reply.

3. Structured Logging (Google Sheets)
   Writes the normalized English summary, original text, assigned role tag, and status flag (Pending Human Review) back to a master tracking sheet.

4. Automated Outreach (Gmail)
   Sends an immediate confirmation email to the volunteer in their native language while alerting the coordinator queue.


SYSTEM SCREENSHOTS
------------------------------------------------------------------------
<img width="1280" height="800" alt="Make Scenario Screenshot" src="https://github.com/user-attachments/assets/c332ebd4-53e8-43ac-b56d-e7a7d4704a0e" />
End-to-end Make.com scenario showing the trigger, Gemini API module, Gmail draft module, and Google Sheets logging.

<img width="1280" height="800" alt="Linden Street googlesheet" src="https://github.com/user-attachments/assets/4775492d-0c36-4172-b204-e2dce6f895cc" />
Normalized multilingual volunteer data logged with human-review status flags ("Draft ready for Gloria").


3. THE HUMAN CHECK (GUARDRAILS AND VERIFICATION)
------------------------------------------------------------------------
Because automated translations and role assignments impact real people, the system enforces a Human-in-the-Loop (HITL) design rather than blind auto-assignment:

- Confidence and Flagging: Submissions with ambiguous intent, incomplete availability, or low-confidence translations are automatically flagged Needs Review in Google Sheets rather than routed directly to placement.
- Side-by-Side Audit Trail: Both the raw original-language input and the Gemini-generated English translation are stored together so bilingual staff can spot-check accuracy in seconds.
- Security and Access Controls: API keys are stored strictly within Make.com's encrypted connection manager, and spreadsheet access is restricted via role-based permissions.


4. BEFORE AND AFTER IMPACT
------------------------------------------------------------------------
(Update the numbers below with your exact test or pilot metrics)

Metric                    Before (Manual Process)         After (Automated Pipeline)       Improvement
-----------------------------------------------------------------------------------------------------------
Intake Processing Time    ~18 mins per applicant          ~15 seconds per applicant        98% reduction
First-Response Latency    3 to 5 business days            Under 1 minute                   Instant acknowledgment
Data Standardization      ~60% (manual cleanup needed)    100% structured schema           Zero manual re-entry
Language Coverage         Limited to staff hours          24/7 multilingual support        Round-the-clock intake


5. PROGRAM CONTEXT AND CONTRIBUTIONS
------------------------------------------------------------------------
Developed as part of the AI Tech Corps Fellowship with OptimaNova AI.

- Architected the end-to-end Make.com orchestration logic, data mapping, and error-handling routes.
- Engineered the Google Gemini API prompts for deterministic JSON output, language detection, and localized email drafting.
- Built the Google Sheets schema and validation rules to enforce human-in-the-loop review gates.
