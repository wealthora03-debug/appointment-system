\# Appointment Setting Business — Full System Context



\## Business

AI appointment setting system sold to marketing agencies.

Agencies pay monthly retainer. System deploys for their clients.

Starting vertical: Indian dental clinics.

Only KPI: booked appointments.

Test client: SmileCare Dental Clinic, Mumbai.

Replace SmileCare with real client name before every go-live.



\## My Role

You are my n8n build assistant and system operator.

You know my entire system. Before doing anything read the

relevant workflow via MCP first. Always test before touching

live. Always commit to GitHub before any build session.



\## n8n Instance

URL: https://sairaj-26.app.n8n.cloud



\## Workflow IDs

01\_Lead\_Intake — snmZzx55VlC5wa6N

02\_Vapi\_Callback — neWZB87wWy2B1TNq

03\_Calendly\_Webhook — xtwV9YgJ1SkUhM1E

04\_WhatsApp\_Flow — hEomMiT7ElZhzh35

05\_Reminder\_Scheduler — VWXbH3xfwIVemD9Y

06\_Telegram\_Alerts — DxIgdmJIzYtMjXYv

07\_Report\_Scheduler — NOT BUILT YET (Gap 15)



\## Key Integration IDs

Vapi Assistant ID: 6634b358-4543-4059-9000-6ab3000fe123

Vapi Phone ID: 3a725b37-aa8c-45f3-82ec-2164ec3b9996

Vapi Phone Number: +1 350 252 1011

Twilio WhatsApp From: whatsapp:+14155238886

Twilio Account SID: ACefe880cb00935add04eb8a268f916c8a

Calendly: https://calendly.com/wealthora03/free-dental-consultation

WhatsApp Inbound Webhook: https://sairaj-26.app.n8n.cloud/webhook/whatsapp-trigger

Vapi Callback Webhook: https://sairaj-26.app.n8n.cloud/webhook/vapi-callback

Calendly Webhook: https://sairaj-26.app.n8n.cloud/webhook/calendly-events

Lead Intake Webhook: https://sairaj-26.app.n8n.cloud/webhook/lead-intake

Telegram Alert Webhook: https://sairaj-26.app.n8n.cloud/webhook/telegram-alert



\## Tech Stack

\- n8n cloud: workflow automation

\- Vapi: AI voice calls (GPT-4o mini testing / GPT-4o live)

\- Voice: 11Labs Indian voice

\- Transcriber: Deepgram Nova-2 hi-IN

\- Twilio: WhatsApp sandbox testing

\- Interakt: WhatsApp production (at go-live)

\- Zoho Bigin: CRM (Free plan, 25 custom field limit)

\- Calendly: Free plan appointment booking

\- Tally: Lead form for testing

\- Telegram: System alerts to me only

\- Claude API: Powers all inbound WhatsApp as Priya



\## Locked Decisions — Never Change These

\- No booking on call — everything goes to WhatsApp

\- Call max 4 minutes, ends naturally after handoff confirmed

\- Claude API powers all inbound WhatsApp responses as Priya

\- Calling hours: 7AM to 10PM IST Monday to Sunday

\- After-hours leads: immediate WhatsApp sent, call at 9AM next morning

\- After-hours leads can chat on WhatsApp immediately if they reply

\- If after-hours lead replies and books on WhatsApp, 9AM call cancels

\- Pre-call WhatsApp fires 15 seconds before every call

\- Post-call WhatsApp with 3 slots fires within 30 seconds of qualified call

\- Consultation is always free — never discuss treatment costs anywhere

\- Objection on call: universal line then handoff to WhatsApp

\- Duplicate lead: no error, redirect to WhatsApp as Priya

\- Twilio sandbox for testing, Interakt for production

\- Telegram for my system alerts only

\- Agency and clinic alerts go on WhatsApp

\- GPT-4o mini for testing, GPT-4o for live



\## Vapi Call Settings

Max duration: 4 minutes

Stability: 0.4 / Similarity: 0.75 / Style: 0.35

Interruption sensitivity: 0.3

Backchanneling: OFF

End of speech timeout: 1.5 seconds



\## Bigin Pipeline

Name: Lead Booking System

Stage flow: New Lead → Qualified → Booked → Disqualified

&#x20;          → No Show → Rescheduled → Needs Human



\## Bigin Fields In Use

Deal\_Name, Lead\_Name, Phone, Email, Service\_Interested,

Lead\_Source, Lead\_Timestamp, First\_Contact\_Timestamp,

Contacted\_60s, Attempt\_Count, Final\_Call\_Status,

Call\_Duration, Recording\_URL, Transcript, AI\_Summary,

Error\_Flag, Payment\_Method, Financial\_Qualified,

Error\_Details, Disqualification\_Reason, Booking\_Status,

Appointment\_Status, Appointment\_Date, No\_Show,

Rescheduled, Messaging\_Status, Lead\_Type, Lead\_Value,

Call\_Connected, Reactivation\_Sent



\## Disqualification Reason Categories (5 only)

1\. Not Ready Yet

2\. Payment Method Not Accepted

3\. Already Has Dentist

4\. Unreachable After 2 Attempts

5\. Other



\## Dashboard Structure

One shared dashboard for Agency and Clinic:

1\. Total Leads Received

2\. Leads Contacted

3\. Speed to Lead Rate (Contacted\_60s true / total leads %)

4\. Booking Rate (Booked / total leads %)

5\. Disqualification Breakdown by reason category

6\. No-Show Count with note: reactivation sent automatically



Internal dashboard for me only:

1\. Missed Call Recovery Rate

2\. Error Flag Count

3\. Reactivation Success Rate

4\. System health metrics



\## WhatsApp Messages — Final Versions



Pre-call message (in-hours):

"Hi \[Name] 👋 Thank you for your enquiry about \[service]

at SmileCare Dental Clinic. We just received your request

and someone from our team will be calling you in a moment

to assist you. Please keep your phone handy!

— SmileCare Team"



After-hours message:

"Hi \[Name] 👋 Thank you for reaching out to SmileCare

Dental Clinic about \[service]. We have received your

enquiry — our clinic is currently closed for the evening

but we did not want to keep you waiting without a response.

Our team will call you tomorrow morning at 9AM to assist you.

In the meantime if you have any questions feel free to reply

to this message and we will get back to you right away.

— SmileCare Team"



Missed call / no answer message:

"Hi \[Name] 👋 This is the team at SmileCare Dental Clinic.

We tried reaching you regarding your enquiry about \[service].

We would love to help you take the next step! Book your FREE

consultation here: \[Calendly link] — SmileCare Team"



Post-call slots message:

"Hi \[Name]! Here are 3 available slots for your free

consultation at SmileCare Dental Clinic:

📅 \[Slot 1]

📅 \[Slot 2]

📅 \[Slot 3]

Which works best for you? — SmileCare Team"



Booking confirmation:

"Your free consultation is confirmed! 🎉

📅 \[Date and Time]

📍 SmileCare Dental Clinic, Mumbai

Please bring any previous dental records.

See you soon! — SmileCare Team"



24h reminder:

"Hi \[Name] 👋 Just a reminder — your free consultation

at SmileCare Dental Clinic is TOMORROW at \[Time] 📅

📍 SmileCare Dental Clinic, Mumbai

Please bring any previous dental records or X-rays.

See you tomorrow! — SmileCare Team"



2h reminder:

"Hi \[Name] ⏰ Your free consultation at SmileCare Dental

Clinic is in just 2 hours!

📍 SmileCare Dental Clinic, Mumbai

We look forward to seeing you shortly!

— SmileCare Team"



No-show reactivation:

"Hi \[Name] 😊 We noticed you missed your consultation at

SmileCare Dental Clinic today — no worries at all.

We would love to find another time that works for you!

Book a new slot here: \[Calendly link]

The consultation is completely FREE and takes just 30 mins.

Hope to see you soon! — SmileCare Team"



Duplicate lead redirect:

"Hi \[Name], thanks for getting back to us.

How can we help you? — SmileCare Team"



Escalation alert to clinic (WhatsApp):

"⚠️ \[Name] needs human support on WhatsApp right now.

Please check and respond immediately.

— Appointment System"



Booking alert to clinic and agency (WhatsApp):

"✅ New consultation booked!

👤 \[Name]

🦷 \[Service]

📅 \[Date and Time]

— SmileCare Appointment System"



Weekly report prompt to agency (WhatsApp):

"📊 SmileCare weekly report ready.

This week: \[X] consultations booked from \[Y] leads.

Check your full dashboard here: \[Dashboard Link]

— \[Agency Name]"



\## 18 Gaps — Build In This Priority Order

Gap 3: Claude inbound WhatsApp handler — MOST CRITICAL

Gap 9: Conversation memory for Priya on WhatsApp

Gap 5: Post-call WhatsApp with 3 slots

Gap 4: Transcript, recording URL, duration written to Bigin

Gap 1: After-hours lead queue with 9AM scheduled callback

Gap 2: Sunday enabled — 7AM to 10PM Monday to Sunday

Gap 11: Booking alerts to clinic and agency on WhatsApp

Gap 13: Duplicate leads redirect to WhatsApp not error

Gap 10: Human escalation detection on WhatsApp

Gap 7: Reminder scheduler changed to run hourly

Gap 8: WhatsApp fired after failed retry call

Gap 14: Automatic no-show detection — time-based in n8n

Gap 6: Universal objection line and full Priya script in Vapi

Gap 15: Build 07\_Report\_Scheduler workflow

Gap 12: Weekly Monday report and monthly 1st report

Gap 16: Add Call\_Connected boolean, fix Disqualification\_Reason

Gap 17: Add missing Bigin fields

Gap 18: Build client-facing dashboard



\## Build Rules — Non Negotiable

\- Read current workflow via MCP before touching anything

\- Commit to GitHub before every build session

\- Test on duplicate workflow before touching live

\- Never run DELETE on live workflows

\- Never discuss treatment costs anywhere in system

\- Never confirm or deny Priya is an AI

\- Replace SmileCare before every client go-live

