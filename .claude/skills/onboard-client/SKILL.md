\---

name: onboard-client

description: Use when setting up the entire system for a

new agency client — replaces all SmileCare references

with real client details across all workflows

\---



\# Onboard Client Skill



\## Information To Collect First

Before touching anything ask the user for:

1\. Clinic name (exact name as it should appear in messages)

2\. Clinic city

3\. Clinic WhatsApp number (E.164 format: +91XXXXXXXXXX)

4\. Agency name

5\. Agency WhatsApp number (E.164 format: +91XXXXXXXXXX)

6\. Calendly link for this client

7\. Services offered (list all — for Priya's script)

8\. Qualification questions agreed with clinic owner

9\. Bigin pipeline name for this client



Do not proceed until all 9 items are confirmed.



\## Pre-Onboarding Safety Steps

1\. Commit current state to GitHub:

&#x20;  git add . \&\& git commit -m "Before onboarding \[client name]"

2\. Export all 6 current workflow JSONs as backup

3\. Create duplicate test versions of all workflows

4\. Test on duplicates first — never on live workflows



\## Updates Required Across All Workflows



\### 01\_Lead\_Intake

\- Update Pipeline name in Create Bigin Deal node

\- Verify webhook URL is correct for this client



\### 02\_Vapi\_Callback

\- Update Vapi Assistant ID if new assistant created

&#x20; for this client

\- Verify all Bigin field names match this client's

&#x20; pipeline fields



\### 03\_Calendly\_Webhook

\- Update Calendly webhook URL for this client

\- Update clinic WhatsApp number in booking alert

\- Update agency WhatsApp number in booking alert



\### 04\_WhatsApp\_Flow

\- Update ALL WhatsApp message templates:

&#x20; - Replace SmileCare Dental Clinic with clinic name

&#x20; - Replace Mumbai with clinic city

&#x20; - Replace Calendly link with client Calendly link

&#x20; - Update From number if different per client

\- Update escalation alert recipient to clinic WhatsApp

\- Update Priya system prompt with client-specific

&#x20; clinic name, services, and qualification context



\### 05\_Reminder\_Scheduler

\- Update WhatsApp message templates with clinic name

\- Verify appointment field names match this client's

&#x20; Bigin pipeline



\### 07\_Report\_Scheduler

\- Update agency WhatsApp number for report delivery

\- Update clinic name in report header

\- Update dashboard link for this client



\### Vapi Assistant

\- Update system prompt with clinic name

\- Update service list with this client's services

\- Update qualification questions agreed with clinic

\- Update handoff line with clinic name

\- Update universal objection line



\### Bigin

\- Create new pipeline named for this client

\- Verify all 25 field slots — check what is available

\- Create pipeline stages matching the standard flow



\## Post-Update Testing

Run full stress test — all 15 scenarios from gaps list:

1\. In-hours lead qualifies and books

2\. In-hours lead does not qualify

3\. In-hours lead does not answer

4\. In-hours lead does not answer retry either

5\. After-hours lead replies on WhatsApp and books

6\. After-hours lead waits for 9AM call

7\. Full end to end — lead to clinic chair

8\. No-show flow complete

9\. Duplicate phone number

10\. Escalation detection

11\. Sunday lead

12\. Objection on call

13\. Weekly report triggers

14\. 24h reminder

15\. 2h reminder afternoon appointment



\## Only Go Live When

\- \[ ] All 15 stress test scenarios pass

\- \[ ] Agency WhatsApp receiving alerts correctly

\- \[ ] Clinic WhatsApp receiving alerts correctly

\- \[ ] Dashboard link shared with agency and clinic

\- \[ ] Twilio sandbox replaced with Interakt

\- \[ ] Vapi phone number updated to Indian number

\- \[ ] GitHub commit made with final live version

\- \[ ] SmileCare appears nowhere in any workflow



\## After Go-Live

1\. Monitor first 5 real leads manually

2\. Check Bigin deals are populating correctly

3\. Confirm clinic owner can see their dashboard

4\. Confirm agency is receiving weekly reports

5\. Send onboarding complete confirmation to agency

