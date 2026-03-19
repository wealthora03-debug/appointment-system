\---

name: build-n8n-node

description: Use when building, adding, or editing any node

in any n8n workflow for the appointment setting system

\---



\# Build N8N Node Skill



\## Before Touching Anything

1\. Read the target workflow via n8n-MCP using workflow ID

&#x20;  from CLAUDE.md

2\. Understand exactly what the workflow currently does

3\. Identify the exact insertion point for the new node

4\. Confirm the node type exists in n8n before building

5\. Commit current state to GitHub before making any changes:

&#x20;  git add . \&\& git commit -m "Before building \[gap name]"



\## Building The Node

1\. Write the complete node JSON with all required parameters

2\. Validate every field name matches n8n's exact naming

3\. Validate all expressions use correct n8n syntax

&#x20;  - Correct: {{ $json.field\_name }}

&#x20;  - Correct: {{ $('Node Name').item.json.field }}

&#x20;  - Never guess field names — read them from MCP first

4\. Check all connections are valid — every input and output

&#x20;  must connect to an existing node

5\. Never leave dangling connections or orphaned nodes



\## Deploying The Node

1\. Deploy via n8n API — never manually in the dashboard

2\. Use n8n-MCP to push the updated workflow

3\. Verify the workflow is still active after deployment

4\. Confirm no existing nodes were accidentally modified



\## Testing After Every Build

1\. Trigger manual test execution via n8n-MCP

2\. Read the full execution result — every single node

3\. Check every node shows green — no errors, no skips

4\. Verify Bigin deal updated with correct fields

5\. Verify WhatsApp message fired if applicable

6\. Verify Telegram alert fired if applicable

7\. Report result — PASS or FAIL with specific node details



\## If Test Fails

1\. Read exact error message from failed node

2\. Do not guess the fix — diagnose first

3\. Fix the specific node that failed

4\. Re-deploy and re-test

5\. Never mark a gap complete until test passes fully



\## Hard Rules — Never Break These

\- Never touch live workflows without testing on duplicate first

\- Never run DELETE on any live workflow under any circumstance

\- Never modify a working node unless explicitly required

\- Never use free text where a specific value is expected

\- Always commit to GitHub after successful build and test

\- Always report exactly which nodes were changed



\## After Successful Build

1\. Run: git add . \&\& git commit -m "Gap \[X] complete — \[name]"

2\. Run: git push

3\. Report back: gap number, what was built, test result,

&#x20;  which nodes were added or modified

