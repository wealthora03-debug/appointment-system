\---

name: test-workflow

description: Use when testing any workflow after a build

or when verifying a workflow is running correctly

\---



\# Test Workflow Skill



\## Before Testing

1\. Identify the workflow ID from CLAUDE.md

2\. Read the current workflow via n8n-MCP to understand

&#x20;  what nodes should execute and in what order

3\. Know exactly what the expected outcome is before

&#x20;  running the test — do not test blindly



\## Running The Test

1\. Trigger manual execution via n8n-MCP

2\. Use test data that represents a real scenario

3\. For 01\_Lead\_Intake use a real Indian mobile number

&#x20;  format: +91XXXXXXXXXX

4\. For 02\_Vapi\_Callback simulate the correct Vapi

&#x20;  webhook payload format

5\. For 03\_Calendly\_Webhook simulate correct Calendly

&#x20;  event payload

6\. For 04\_WhatsApp\_Flow send a real inbound message

7\. For 05\_Reminder\_Scheduler trigger manually and

&#x20;  check for active scheduled appointments



\## Reading The Result

1\. Read the full execution result — every single node

2\. Check every node shows success — no errors no skips

3\. If any node shows error — read the exact error

&#x20;  message before doing anything else

4\. Check the output data of each node matches expected

5\. Never assume a test passed — verify every node



\## Verification Checklist Per Workflow



\### 01\_Lead\_Intake

\- \[ ] Consent check passed

\- \[ ] Phone normalized to +91XXXXXXXXXX format

\- \[ ] Duplicate check ran correctly

\- \[ ] Working hours check ran correctly

\- \[ ] Bigin deal created with all fields populated

\- \[ ] Pre-call WhatsApp fired

\- \[ ] Vapi call triggered after 15 seconds



\### 02\_Vapi\_Callback

\- \[ ] Event type routed correctly

\- \[ ] Tool call extracted correctly

\- \[ ] Bigin deal found by phone number

\- \[ ] Call\_Duration written to Bigin

\- \[ ] Transcript written to Bigin

\- \[ ] AI\_Summary written to Bigin

\- \[ ] Recording\_URL written to Bigin

\- \[ ] Call\_Connected set correctly

\- \[ ] Post-call WhatsApp with slots fired if qualified

\- \[ ] Disqualification reason saved if disqualified

\- \[ ] Retry logic triggered if dropped call



\### 03\_Calendly\_Webhook

\- \[ ] Event type routed correctly

\- \[ ] Bigin deal found and updated

\- \[ ] Booking confirmation WhatsApp fired

\- \[ ] Clinic WhatsApp alert fired

\- \[ ] Agency WhatsApp alert fired

\- \[ ] Your Telegram alert fired



\### 04\_WhatsApp\_Flow

\- \[ ] Inbound message received correctly

\- \[ ] Conversation history retrieved for phone number

\- \[ ] History passed to Claude API correctly

\- \[ ] Claude responded as Priya

\- \[ ] Response sent back to lead via Twilio

\- \[ ] Conversation history updated after response

\- \[ ] Escalation detected if applicable



\### 05\_Reminder\_Scheduler

\- \[ ] Appointments fetched from Bigin correctly

\- \[ ] 24h window calculated correctly

\- \[ ] 2h window calculated correctly

\- \[ ] Correct reminders fired

\- \[ ] No-show detection ran for past appointments

\- \[ ] No-show flow triggered where applicable



\### 07\_Report\_Scheduler

\- \[ ] Bigin queried for correct date range

\- \[ ] All 6 metrics calculated correctly

\- \[ ] WhatsApp sent to agency number

\- \[ ] Dashboard link included in message



\## Reporting The Result

Always report in this exact format:



WORKFLOW: \[name]

GAP TESTED: \[number and name]

RESULT: PASS or FAIL

NODES PASSED: \[count]

NODES FAILED: \[count and which ones]

BIGIN UPDATED: YES or NO — which fields

WHATSAPP FIRED: YES or NO — which message type

TELEGRAM FIRED: YES or NO

NEXT ACTION: \[what to do next]



\## If Test Fails

1\. Do not re-run immediately

2\. Read the exact error on the failed node first

3\. Diagnose the root cause

4\. Fix only the broken node

5\. Re-deploy and re-test from beginning

6\. Never mark gap complete until full test passes

