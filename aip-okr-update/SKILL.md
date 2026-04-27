---
name: aip-okr-update
description: Generate the monthly AI Platform OKR status update using Atlassian and GitHub MCPs. Use when asked to write or generate the OKR update.
disable-model-invocation: true
---

Using the Atlassian and GitHub MCPs, generate a monthly OKR status update for the AI Platform team, then create and populate a Confluence page for the current month.

**Step 0 — Determine the current month**

Note today's date. The page title and column header will use the format `YYYY-MM-AI Platform OKRs Update` (e.g. `2026-05-AI Platform OKRs Update` for May 2026). The column header inside the table will be the month and year (e.g. `May 2026 Update`).

**Step 1 — Fetch the OKR data**

1. Fetch the previous month's OKR Confluence page to get the list of OKRs and their owners. The parent page listing all monthly updates is: https://datadoghq.atlassian.net/wiki/spaces/AIP/pages/5679153211/AI+Platform+Monthly+Updates — find the most recent child page and read it to get the OKR list (ticket numbers + owners).
2. For each OKR listed, fetch the linked Jira tickets and all their child tickets (projects: AIPAW, AIPSTO, AIPAE)
3. For each ticket, check GitHub MCP for merged PRs in DataDog/dd-source — use whichever source (Jira or GitHub) has the most recent update
4. Only include work updated between the 1st of the current month and today

**Step 2 — Create the Confluence page for the current month**

Create a new Confluence page as a child of page ID `5679153211` (AI Platform Monthly Updates space: `AIP`, cloudId: `datadoghq.atlassian.net`) using `contentFormat: markdown`.

- Title: `YYYY-MM-AI Platform OKRs Update` for the current month
- Body: a 3-column markdown table with headers `| **OKR** | **Related KRs** | **[Month Year] Update** |`
- One row per OKR (AIPOKRS-65 through AIPOKRS-81, skipping AIPOKRS-72), with:
  - Column 1: Jira smart link for the ticket + owner name on the next line (e.g. `[AIPOKRS-65](https://datadoghq.atlassian.net/browse/AIPOKRS-65) Owner: Zied Kallel`)
  - Column 2: leave blank
  - Column 3: the 5 bold section headings with `<br>` between them, no content yet (placeholders)

**Step 3 — Write the OKR updates**

Write a separate update for each OKR using this structure:

**[AIPOKRS-XX — OKR Title]**
Owner: [owner name]

**What shipped or meaningfully progressed this month?**
- [bullet points]

**What measurable impact did this create (or is expected to create)?**
- [bullet points]

**What's coming next month that stakeholders should know about?**
- [bullet points]

**What are the top risks, dependencies, or blockers?**
- [bullet points]

**Any cross-team asks or decisions needed?**
- [bullet points]

**Step 4 — Populate the Confluence page**

Update the page created in Step 2 using `updateConfluencePage` with `contentFormat: markdown`. Replace the placeholder column 3 content for each row with the full 5-section update generated in Step 3. Format each cell using `<br>` between lines (bold questions + bullet items). The final table must have all 16 OKR rows fully populated in the current month column.

**Output rules**

- Audience is stakeholders and the Director of AI Platform — focus on customer impact and business outcomes, not PR-level or ticket-level details
- Do not list every completed item; summarize at the theme or capability level
- Use GitHub PR data only to verify the status of items — do not cite PR numbers in the output
- Keep each section concise: 2–4 bullets max
- If an OKR has no update or no owner, note it explicitly rather than leaving it blank
- After completing Step 4, respond with the URL of the newly created and populated Confluence page
